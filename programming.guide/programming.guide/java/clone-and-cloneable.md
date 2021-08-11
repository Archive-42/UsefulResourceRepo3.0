



## Related

[Copying Objects](copying-objects-deep-and-shallow.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Javadoc for Object.clone](<https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#clone()>)  
<span style="color: grey; font-style: italic; font-size: smaller">docs.oracle.com</span>

[Javadoc for the Cloneable interface](https://docs.oracle.com/javase/10/docs/api/java/lang/Cloneable.html)  
<span style="color: grey; font-style: italic; font-size: smaller">docs.oracle.com</span>

[Josh Bloch on Design: Copy Constructor versus Cloning](https://www.artima.com/intv/bloch13.html)  
<span style="color: grey; font-style: italic; font-size: smaller">by Bill Venners</span>

[Effective Java, Item 13: Override clone judiciously](https://books.google.se/books?id=BIpDDwAAQBAJ)  
<span style="color: grey; font-style: italic; font-size: smaller">by Joshua Bloch</span>



## Top Java Articles

1.  [Do interfaces inherit from Object?](do-interfaces-inherit-from-object.html)
2.  [Executing code in comments?!](executing-code-in-comments.html)
3.  [Functional Interfaces](functional-interfaces.html)
4.  [Handling InterruptedException](handling-interrupted-exceptions.html)
5.  [Why wait must be called in a synchronized block](why-wait-must-be-in-synchronized.html)

[**See all 190 Java articles**](index.html)

## Top Algorithm Articles

1.  [Dynamic programming vs memoization vs tabulation](../dynamic-programming-vs-memoization-vs-tabulation.html)
2.  [Big O notation explained](../big-o-notation-explained.html)
3.  [Sliding Window Algorithm with Example](../sliding-window-example.html)
4.  [What makes a good loop invariant?](../what-makes-a-good-loop-invariant.html)
5.  [Generating a random point within a circle (uniformly)](../random-point-within-circle.html)

# Java: Clone and Cloneable

`Object.clone` offers a shortcut for creating exact, field-by-field, copies of objects. A lot of the boiler plate typically required in copy constructors or static factory methods goes away.

Unfortunately the cloning API is poorly designed and should almost always be avoided. See sections [_Critique_](clone-and-cloneable.html#critique) and [_Alternatives to Cloning_](clone-and-cloneable.html#alternatives-to-cloning) for more information.

Both arrays and objects can be cloned. Apart from the section specifically on arrays, this article focuses on cloning objects.

## Example

Here's how to make a `Car` class cloneable:

    class Car implements CloneableThis tells Object.clone that it's safe to clone of Car objects. If we omit this, Object.clone will throw a CloneNotSupportedException. {






        private String make;
        private int doors;
        private Motor motor;
        private Gearbox gearbox;

        public Car(String make,
                   int doors,
                   Motor motor,
                   Gearbox gearbox) {
            …
        }

        @Override
        public Car clone() {Object.clone is protected, so we need to override it to make it public




            try {
                Car c = (Car) super.clone()Use Object.clone to create a copy of the correct type
    and do a field-by-field copy;





                // c.doors = doors;Already copied by Object.clone




                c.motor = motor.clone();
                c.gearbox = gearbox.clone();Clone children to produce a deep copy




                // c.make = make;No need to clone make, since strings are immutable




                return c;
            } catch (CloneNotSupportedException e) {
                // Will not happen in this case
                return null;
            }
        }

        …
    }

Then, clone away…

    Car car1 = new Car("BMW", 4, someMotor, someGearbox);
    Car car2 = p1.clone();

    // car1 and car2 refer to distinct objects

## Shallow vs Deep Cloning

_See [Shallow vs Deep Copy (with examples)](../shallow-vs-deep-copy.html) if you're not familiar with these terms._

According to convention, clone should return a **deep copy**. This is typically the expected / most useful alternative. Consider the `Car` example at the top of the article. It would be quite annoying if `car1.getGearbox().setGear(4)` would affect the current gear of `car2`!

`Object.clone` however, creates a **shallow copy**. This means that the object returned by `super.clone()` refers to the same "children" as the original object. It's therefore important that the `clone` method clones the referenced objects and updates the references before returning the result, as was done with `motor` and `gearbox` in the example above.

Original Car make: BMW engine: gearbox: Gearbox gears: 6 Engine cylinders: 12 After super.clone() Car make: BMW engine: gearbox: After completed clone Car make: BMW engine: gearbox: Gearbox gears: 6 Engine cylinders: 12

Returning a deep clone is not a strict requirement though. There are situations when a shallow copy makes more sense, and sometimes cloning the children is not even an option. The clone methods of all standard collections for example (`ArrayList`, `HashMap`, …) return shallow clones.

## The black magic of `Object.clone`

`Object.clone` achieves two things that ordinary Java methods can't:

1.  It creates an instance of the same type as `this`, i.e. the following always holds:

    super.clone().getClass() == this.getClass()

2.  It then copies all fields from the original object to the clone.

It manages to do this without invoking any constructors and the field-by-field copy includes private and final fields.

**But… how!?** The `Object.clone` method is _native_:

    protected native Object clone() throws CloneNotSupportedException;

This means that it's implemented as part of a system library, typically written in C or C++. This allows it to use low level calls such as `memcpy`, ignore access modifiers, and do other things ordinary Java methods can't.

## Why use `super.clone()` instead of `new Car(…)`?

Had we used `new Car(…)` instead of `super.clone()` **subclasses would run into trouble**.

Suppose there's a subclass, `Minivan`. `Minivan.clone` would have to call `super.clone()` to make sure private fields in the `Car` class was cloned properly. This would however return a `Car` object which would be of little use to `Minivan.clone` which needs to return an `Minivan` object!

If the `clone` method of every class in the hierarchy starts with `super.clone()` we ensure that `Object.clone` is always called, and as noted in the previous section, this guarantees that the correct type is instantiated. In this case `Minivan.clone` would get an `Minivan` object from `super.clone()`.

Note that if `Car` had been declared final, there would be no subclasses, and using `new Car(…)` would have been completely fine.

## Gotchas

A few things to keep in mind when overriding `clone`:

Don't leak `this`  
Just as for constructors, you **shouldn't leak the `this` reference** from within a `clone` method as code elsewhere might access the object before it's in an initialized state. This implies that you **should not call overridable methods** from within `clone`.

Concurrency  
If the object is shared among other threads, make sure you **synchronize** so you don't make a copy when the object is in a bad state. Also, `Object.clone` is not an atomic operation, (and even if it was, you'd still need to worry about word tearing).

Design for extension  
Design for inheritance, or prohibit it (Effective Java, item 19). In a non-final class you have three options when it comes to cloning:

1.  Make the class itself `Cloneable` with a proper public `clone` method.
2.  Don't implement `Cloneable` but leave the door open for subclasses to do so. In this case you should mimic the behavior of `Object.clone` by providing a functioning `clone` method, but leave it as protected and with the `throws CloneNotSupportedException` declaration.
3.  Prevent cloning altogether by creating a protected final `clone` method that throws a `CloneNotSupportedException` exception.

Extending a cloneable class  
If you extend a cloneable class, directly or indirectly, your will automatically implement `Cloneable` and inherit a public `clone` method. There's no way to opt out from this, so you must play along and override `clone` properly. If this is not possible, you could throw an `CloneNotSupportedException`, but only if the signature of the super class's `clone` method allows for it.

## Why implement `Cloneable`? It has no methods!

If you don't implement `Cloneable`, then `Object.clone` will throw a [`CloneNotSupportedException`](https://docs.oracle.com/javase/8/docs/api/java/lang/CloneNotSupportedException.html).

An interface with no methods is called a _marker interface_ (see [Java: Marker interfaces, with examples](marker-interface.html)).

## The Contract of `clone`

The contract says that it should _"return a copy of this object"_ where the meaning of copy _"…may depend on the class of the object"_. In other words, **the contract doesn't specify any absolute requirements**. It does however list the following conventions:

- `x.clone() != x`
- `x.clone().getClass() == x.getClass()`
- `x.clone().equals(x)`
- The returned object should be independent of the object being cloned

The first two items can be achieved by following the convention to always start with `super.clone()`.

As mention further up in the article `Object.clone` produces a shallow copy, which means that overriding `clone` methods should take care of cloning referenced objects to adhere to the last convention. This only applies to mutable objects however, since it's always safe to share references to immutable objects.

The method should throw `CloneNotSupportedException` if the object's class doesn't implement `Cloneable` (again, achieved by always calling `super.clone`). Furthermore, subclasses are allowed to throw this exception to indicate that an object can't be cloned for other reasons.

## Critique

The general consensus is that the cloneable API is poorly designed and should be avoided. Here's why:

Marker interfaces in general…  
…are considered a bad idea in the first place. Instead of describing what clients can do with an object, they describe an internal capability. They require out of band knowledge and encourages a procedural programming style.

There's no way to "opt out" from them in subclasses. If a `Car` is `Cloneable`, then so is a `Minivan` and there's nothing you can do about it.

Since the first marker interfaces were introduced, annotations have been added to the language which are better suited for expressing this type of meta data.

`Cloneable` in particular lacks a clone method  
This means for example that if you have an array of `Cloneable` objects you can't iterate over it and create a deep copy of the array.

If you cast something to a `Cloneable`, and the runtime type really do implement the interface, you _still_ can't call the `clone` method, since it's `protected` in `Object`.

If you implement `Cloneable` but forget to implement a public `clone` method, the compiler will not catch the error. And just being `Cloneable` is pretty useless, since there's still no way for clients to clone objects.

`Object.clone` bends the rules of the language  
The `Object.clone` creates an instance without going through any constructor. This is easy to forget when maintaining code, which may result in class invariants being broken.

Incompatibility with `final` references  
Since references to mutable objects should be updated by the clone method, such fields can't be marked as `final`.

CloneNotSupportedException is a checked exception…  
…while it should have been unchecked. The client may know for sure that a clone will succeed, yet it is forced to wrap the call in a `try`/`catch`.

See [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html).

It's hard to get right  
Even though you know the rules of the game, it's hard to override `clone` correctly. What if you have cycles in the object graph you're trying to clone? What if you reference mutable third party classes that don't support cloning?

`Object.clone` returns an `Object`…  
…which means you must resort to casts.

## Cloning Arrays

Arrays implement `Cloneable` and provide a public `clone` method. None of the drawbacks mentioned in previous section applies to arrays. In fact `arr.clone()` is the preferred idiom for cloning arrays. You don't even have to cast the result as the return type of the array `clone` method is the same as the type of the array being cloned.

Keep in mind however, that the result is a **shallow copy**. If the array stores references to other objects, the clone will reference the same objects.

Original array Cloned array Car make: BMW

## Alternatives to Cloning

For full details and examples please refer to the full article [Java: Copying Objects, Deep and Shallow)](copying-objects-deep-and-shallow.html).

Copy Constructors / Copy Factory Methods  
A copy constructor, `public Car(Car c) { … }`, or a static copy factory method, `public Car newInstance(Car c) { … }`, is the simplest and most straight forward way of creating copies. It easy to understand (no black magic) which also makes it easy to debug and maintain.

Homegrown copy method  
A home grown copy method that doesn't rely on the `Cloneable`/`Object.clone` mechanism may be a viable option. It's more verbose but that may be a an acceptable price to pay considering the alternative. It's possible to name it "`clone`" but you may want to go for something different (`copy`, `copyOf`, `deepCopy`, `shallowCopy`, …) to avoid confusion.

Builders  
When using the builder pattern it's common to provide a way to initialize the state of the builder with the state of a given object. Creating a copy of a car `c` could look like `new Car.Builder(c).build()`. The [Immutables library](https://immutables.github.io) for example, generates a builder with a `from(…)` method for this purpose.

Serialization / deserialization  
By serializing an object, then deserializing the result you end up with a copy. If you already have a library such as Jackson set up for json serialization, you can reuse this for cloning.

Another alternative is to use the `Serializable` mechanism and `ObjectInputStream`/`ObjectOutputStream` but then you trade one type of black magic for another.

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
