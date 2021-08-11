<span class="underline"></span>

<span class="underline"></span>

## Resources

[Shallow vs Deep Copy (with examples)](../shallow-vs-deep-copy.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Clone and Cloneable](clone-and-cloneable.html)  
<span style="color: grey; font-style: italic; font-size: smaller">Programming.Guide</span>

[Javadoc for Object.clone](<https://docs.oracle.com/javase/10/docs/api/java/lang/Object.html#clone()>)  
<span style="color: grey; font-style: italic; font-size: smaller">docs.oracle.com</span>

[Javadoc for the Cloneable interface](https://docs.oracle.com/javase/10/docs/api/java/lang/Cloneable.html)  
<span style="color: grey; font-style: italic; font-size: smaller">docs.oracle.com</span>

[Josh Bloch on Design: Copy Constructor versus Cloning](https://www.artima.com/intv/bloch13.html)  
<span style="color: grey; font-style: italic; font-size: smaller">by Bill Venners</span>

[Effective Java, Item 13: Override clone judiciously](https://books.google.se/books?id=BIpDDwAAQBAJ)  
<span style="color: grey; font-style: italic; font-size: smaller">by Joshua Bloch</span>

<span class="underline"></span>

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

# Java: Copying Objects

Unlike C++ and JavaScript, there's no easy and direct way of copying objects. The built-in clone capability is poorly designed and is rarely the best alternative.

This article lists the pros and cons of all the common approaches, with examples.

- Copy Constructors
- Copy Factory Methods
- Serialization
- Cloning
- Copy methods
- Builders

## Copy Constructors

A simple example:

    public class Car {

        private String make;
        private int doors;
        private Motor motor;
        private Gearbox gearbox;

        public Car(Car other) {
            this.make = other.make;
            this.doors = other.doors;
            this.motor = other.motor;
            this.gearbox = other.gearbox;
        }
        …
    }

**Usage:**

    Car copy = new Car(original);

Note that this produces a **shallow copy**. (See [Shallow vs Deep Copy, with examples](../shallow-vs-deep-copy.html).) If you do `original.getGearbox().setGear(4)`, then `copy`'s gear will change as well. To get a **deep copy**, change to…

    …
        public Car(Car other) {
            this.make = other.make;
            this.doors = other.doors;
            this.motor = new Motor(other.motor);
            this.gearbox = new Gearbox(other.gearbox);
        }
    …

### Copy Constructors and Inheritance

Adding a subclass, `Taxi` is straight forward:

    public class Taxi extends Car {

        boolean isAvailable;

        public Taxi(Taxi other) {
            // Invoke copy constructor of Car
            super(other);

            this.isAvailable = other.isAvailable;
        }
        …
    }

However, when using a copy constructor you must **know the actual runtime type**. If you're not careful, you may inadvertently create a `Car` when trying to create a copy of a `Taxi`.

    Car copy = new Car(someCar); // What if someCar is a Taxi?!

You could use `instanceof` (often considered bad practice) or the visitor pattern to sort it out, but in this case you're probably better off using one of the other techniques described in this article.

### Pros

- Simple and straight forward
- Easy to get right, debug and maintain
- No casts required

### Cons

- You need to know the runtime type
- Requires some boilerplate

## Copy Factory Methods

A copy factory method encapsulates the object copying logic and provides finer control over the process. In the example below, this capability is used to tacle the problem of inheritance mentioned in the previous section.

    public class CarFactory {
        …
        public Car copyOf(Car c) {
            Class<?> cls = c.getClass();
            if (cls == Car.class) {
                return new Car(
                        c.make,
                        c.doors,
                        c.motor,
                        c.gearbox);
            }
            if (cls == Taxi.class) {
                return new Taxi(
                        c.make,
                        c.doors,
                        c.motor,
                        c.gearbox,
                        ((Taxi) c).isAvailable);
            }
            if (cls == Ambulance.class) {
                return new Ambulance(
                        c.make,
                        c.doors,
                        c.motor,
                        c.gearbox,
                        ((Ambulance) c).beaconsOn);
            }
            throw new IllegalArgumentException("Can't copy car of type " + cls);
        }
        …
    }

**Usage:**

    Car copy = myCarFactory.copyOf(car);

### Pros

- Finer control over object creation
- All copying logic in one place

### Cons

- Another level of indirection
- Not as easy to extend
- Might require access to internal state

## Serialization / Deserialization

By serializing an object into a byte array, then deserializing the byte array back into an object, you end up with a deep copy of the original.

    // Serialize to byte[]
    ByteArrayOutputStream os = new ByteArrayOutputStream();
    new ObjectOutputStream(os).writeObject(original);
    byte[] buf = os.toByteArray();

    // Deserialize back into a Car object
    ByteArrayInputStream is = new ByteArrayInputStream(buf);
    Car copy = (Car) new ObjectInputStream(is).readObject();

With [Apache Commons Lang](https://commons.apache.org/proper/commons-lang/) the whole snippet can be replaced by…

    Car copy = SerializationUtils.clone(original);

…which does not throw any checked exceptions and infers the correct return type.

Note that the serialization mechanism does not call any constructors. Customizing the serialization / deserialization—which is needed when dealing with non-serializable external classes—requires you to "override" private methods. This kind of unintuitive semantics makes it tricker to understand, debug, and maintain code.

### Pros

- Handles inheritance
- Very little boilerplate
- Provides deep copying out of the box
  - Even object graphs with cycles!

### Cons

- All objects must be `Serializable`
- Requires extra temporary memory
- Relies on black magic
  - Overriding private methods
  - No constructor calls
- No compile time checks
- Requires casts

That being said, **any serialization library would do**. If you already have for example Jackson or Gson set up, you can reuse your `ObjectMapper` or `Gson` objects for copying purposes, and do away without "black magic" and casts.

## Object.clone

`Object.clone` offers a shortcut for creating exact, field-by-field, copies of objects. A lot of the boilerplate otherwise required in copy constructors or static factory methods goes away.

    class Car implements Cloneable {

        private String make;
        private int doors;
        private Motor motor;
        private Gearbox gearbox;

        …
        @Override
        public Car clone() {
            try {
                Car c = (Car) super.clone();

                // Already copied by Object.clone
                // c.doors = doors;

                c.motor = motor.clone();
                c.gearbox = gearbox.clone();

                // No need to clone immutable objects
                // c.make = make;

                return c;
            } catch (CloneNotSupportedException e) {
                // Will not happen in this case
                return null;
            }
        }
        …
    }

**Usage:**

    Car copy = (Car) originalCar.clone();

Unfortunately the cloning API is poorly designed and should almost always be avoided. Copying arrays is a notable exception where cloning is the preferred method.

Continue reading here: [Java: Clone and Cloneable](clone-and-cloneable.html)

### Pros

- Automatic shallow copying
- Deals with inheritance
- Works well for arrays

### Cons

- Casts required
- No constructors called
- Incompatible with final fields
- CloneNotSupported is checked
- Can't opt out from being Cloneable

## Simple copy method

    class Car {
        …
        public Car copy() {
            Car copy = new Car();
            copy.make = this.make;
            copy.doors = this.doors;
            copy.motor = this.motor.copy();
            copy.gearbox = this.gearbox.copy();
            return copy;
        }
        …
    }

As it stands, it's not easy to add a subclass to the above example. If a subclass, say `Taxi`, where to override `Car.copy`, it would need to call `super.copy()` to make sure private fields in `Car` are copied. `super.copy()` however, would return a `Car` object, which would be of little use to `Taxi.copy` since it needs to return a `Taxi` object.

If your situation involves a class hierarchy, a better solution would be:

    class Car {
        …
        protected void copyFrom(Car car) {
            this.make = car.make;
            this.doors = car.doors;
            this.motor = car.motor;
            this.gearbox = car.gearbox;
        }

        public Car copy() {
            Car copy = new Car();
            copy.copyFrom(this);
            return copy;
        }
        …
    }

    class Taxi extends Car {
        …
        protected void copyFrom(Taxi taxi) {
            super.copyFrom(taxi);
            this.isAvailable = taxi.isAvailable;
        }

        public Taxi copy() {
            Taxi copy = new Taxi();
            copy.copyFrom(this);
            return copy;
        }
        …
    }

In the above example, the public `copy` method delegates to the protected `copyFrom` method which can easily be overridden in subclasses.

### Pros

- Simple and straight forward
- Easy to understand and debug
- No casts required
- Don't need to know the runtime type

### Cons

- A bit clumbsy with inheritance
- Requires some boilerplate

## Builders

If the class has a builder, you could add a `from` method that initiates the builder with the values from a given object.

    class Car {

        public static class Builder {

            private String make;
            private int doors;
            …

            public Builder() {
            }

            public Builder make(String make) {
                this.make = make;
                return this;
            }

            // other builder methods…

            public Builder from(Car toCopyFrom) {
                make(toCopyFrom.make);
                doors(toCopyFrom.doors);
                …
                return this;
            }

            public Car build() {
                return new Car(
                        make,
                        doors,
                        buildMotor(),
                        buildGearbox());
            }
        }

        // Rest of Car class
        …
    }

**Usage:**

    Car copy = new Car.Builder()
                      .from(original)
                      .build();

This is precisely what the [Immutables library](https://immutables.github.io) does when generating a builder for value classes.

### Pros

- Easy to tweak the copy
- Good if there's already a builder

### Cons

- Builder pattern is verbose
- Another level of indirection
- Not easy to extend

## Comments

Be the first to comment!

© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
