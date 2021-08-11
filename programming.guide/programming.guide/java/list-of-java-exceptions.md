



## Java Exceptions

1.  [Throw, Try and Catch](exceptions-throw-try-catch.html)
2.  [Java Exception Types](exception-types.html)
3.  [Chained Exceptions](chained-exceptions.html)
4.  [Custom Exception](custom-exception.html)
5.  [Difference between Checked and Unchecked Exceptions](difference-between-checked-and-unchecked-exceptions.html)
6.  [Choosing between Checked and Unchecked Exceptions](choosing-between-checked-and-unchecked-exceptions.html)
7.  [Checked Exceptions: Good or Bad?](checked-exceptions-good-or-bad.html)
8.  [Return Values vs Exceptions](return-values-vs-exceptions.html)
9.  [try + finally](try-finally.html)
10. [try-with-resources](try-with-resources.html)
11. [Stack Traces](stack-trace.html)
12. [Suppressed Exceptions](suppressed-exceptions.html)
13. [throw vs throws vs Throwable](throw-vs-throws-vs-throwable.html)
14. List of Java Exceptions

## Exception Related Keywords

1.  [throw](throw.html)
2.  [throws](throws.html)
3.  [catch](catch.html)
4.  [try](try.html)
5.  [finally](finally.html)

## Featured Stack Overflow Post

[In Java, difference between default, public, protected, and private](https://stackoverflow.com/a/33627846/276052)

[<img src="../images/so-featured-33627846.png" alt="StackOverflow screenshot thumbnail" class="screenshot" />](https://stackoverflow.com/a/33627846/276052)



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

# List of Java Exceptions

All public exceptions and errors in the Java API, grouped by package.

✔: Checked exception  
<span class="small">&lt;version&gt;</span>: Since version

## Package `java­.lang`

- [`Throwable`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Throwable.html) <sup>✔</sup>
  - [`Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Exception.html) <sup>✔</sup>
    - [`Clone­Not­Supported­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/CloneNotSupportedException.html) <sup>✔</sup>
    - [`Interrupted­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/InterruptedException.html) <sup>✔</sup>
    - [`Reflective­Operation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ReflectiveOperationException.html) <sup>✔</sup>
      - [`Class­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ClassNotFoundException.html) <sup>✔</sup>
      - [`Illegal­Access­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IllegalAccessException.html) <sup>✔</sup>
      - [`Instantiation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/InstantiationException.html) <sup>✔</sup>
      - [`No­Such­Field­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NoSuchFieldException.html) <sup>✔</sup>
      - [`No­Such­Method­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NoSuchMethodException.html) <sup>✔</sup>
    - [`Runtime­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/RuntimeException.html)
      - [`Arithmetic­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ArithmeticException.html)
      - [`Array­Store­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ArrayStoreException.html)
      - [`Class­Cast­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ClassCastException.html)
      - [`Enum­Constant­Not­Present­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/EnumConstantNotPresentException.html)
      - [`Illegal­Argument­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IllegalArgumentException.html)
        - [`Illegal­Thread­State­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IllegalThreadStateException.html)
        - [`Number­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NumberFormatException.html)
      - [`Illegal­Caller­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IllegalCallerException.html) <sup>9</sup>
      - [`Illegal­Monitor­State­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IllegalMonitorStateException.html)
      - [`Illegal­State­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IllegalStateException.html)
      - [`Index­Out­Of­Bounds­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IndexOutOfBoundsException.html)
        - [`Array­Index­Out­Of­Bounds­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ArrayIndexOutOfBoundsException.html)
        - [`String­Index­Out­Of­Bounds­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/StringIndexOutOfBoundsException.html)
      - [`Layer­Instantiation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/LayerInstantiationException.html) <sup>9</sup>
      - [`Negative­Array­Size­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NegativeArraySizeException.html)
      - [`Null­Pointer­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NullPointerException.html)
      - [`Security­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/SecurityException.html)
      - [`Type­Not­Present­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/TypeNotPresentException.html)
      - [`Unsupported­Operation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/UnsupportedOperationException.html)
  - [`Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Error.html)
    - [`Assertion­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/AssertionError.html)
    - [`Linkage­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/LinkageError.html)
      - [`Bootstrap­Method­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/BootstrapMethodError.html)
      - [`Class­Circularity­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ClassCircularityError.html)
      - [`Class­Format­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ClassFormatError.html)
        - [`Unsupported­Class­Version­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/UnsupportedClassVersionError.html)
      - [`Exception­In­Initializer­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ExceptionInInitializerError.html)
      - [`Incompatible­Class­Change­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IncompatibleClassChangeError.html)
        - [`Abstract­Method­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/AbstractMethodError.html)
        - [`Illegal­Access­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/IllegalAccessError.html)
        - [`Instantiation­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/InstantiationError.html)
        - [`No­Such­Field­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NoSuchFieldError.html)
        - [`No­Such­Method­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NoSuchMethodError.html)
      - [`No­Class­Def­Found­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/NoClassDefFoundError.html)
      - [`Unsatisfied­Link­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/UnsatisfiedLinkError.html)
      - [`Verify­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/VerifyError.html)
    - [`Thread­Death`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/ThreadDeath.html)
    - [`Virtual­Machine­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/VirtualMachineError.html)
      - [`Internal­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/InternalError.html)
      - [`Out­Of­Memory­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/OutOfMemoryError.html)
      - [`Stack­Overflow­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/StackOverflowError.html)
      - [`Unknown­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/UnknownError.html)

## Package `java­.util`

- [`Service­Configuration­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/ServiceConfigurationError.html)
- [`Invalid­Properties­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/InvalidPropertiesFormatException.html) <sup>✔</sup>
- [`Concurrent­Modification­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/ConcurrentModificationException.html)
- [`Empty­Stack­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/EmptyStackException.html)
- [`Illegal­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/IllegalFormatException.html)
  - [`Duplicate­Format­Flags­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/DuplicateFormatFlagsException.html)
  - [`Format­Flags­Conversion­Mismatch­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/FormatFlagsConversionMismatchException.html)
  - [`Illegal­Format­Code­Point­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/IllegalFormatCodePointException.html)
  - [`Illegal­Format­Conversion­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/IllegalFormatConversionException.html)
  - [`Illegal­Format­Flags­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/IllegalFormatFlagsException.html)
  - [`Illegal­Format­Precision­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/IllegalFormatPrecisionException.html)
  - [`Illegal­Format­Width­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/IllegalFormatWidthException.html)
  - [`Missing­Format­Argument­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/MissingFormatArgumentException.html)
  - [`Missing­Format­Width­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/MissingFormatWidthException.html)
  - [`Unknown­Format­Conversion­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/UnknownFormatConversionException.html)
  - [`Unknown­Format­Flags­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/UnknownFormatFlagsException.html)
- [`Formatter­Closed­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/FormatterClosedException.html)
- [`Illformed­Locale­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/IllformedLocaleException.html)
- [`Missing­Resource­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/MissingResourceException.html)
- [`No­Such­Element­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/NoSuchElementException.html)
  - [`Input­Mismatch­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/InputMismatchException.html)
- [`Too­Many­Listeners­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/TooManyListenersException.html) <sup>✔</sup>

## Package `java­.io`

- [`I­O­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/IOError.html)
- [`I­O­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/IOException.html) <sup>✔</sup>
  - [`Char­Conversion­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/CharConversionException.html) <sup>✔</sup>
  - [`E­O­F­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/EOFException.html) <sup>✔</sup>
  - [`File­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/FileNotFoundException.html) <sup>✔</sup>
  - [`Interrupted­I­O­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/InterruptedIOException.html) <sup>✔</sup>
  - [`Object­Stream­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/ObjectStreamException.html) <sup>✔</sup>
    - [`Invalid­Class­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/InvalidClassException.html) <sup>✔</sup>
    - [`Invalid­Object­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/InvalidObjectException.html) <sup>✔</sup>
    - [`Not­Active­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/NotActiveException.html) <sup>✔</sup>
    - [`Not­Serializable­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/NotSerializableException.html) <sup>✔</sup>
    - [`Optional­Data­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/OptionalDataException.html) <sup>✔</sup>
    - [`Stream­Corrupted­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/StreamCorruptedException.html) <sup>✔</sup>
    - [`Write­Aborted­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/WriteAbortedException.html) <sup>✔</sup>
  - [`Sync­Failed­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/SyncFailedException.html) <sup>✔</sup>
  - [`U­T­F­Data­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/UTFDataFormatException.html) <sup>✔</sup>
  - [`Unsupported­Encoding­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/UnsupportedEncodingException.html) <sup>✔</sup>
- [`Unchecked­I­O­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/UncheckedIOException.html) <sup>1.8</sup>

## Package `java­.awt`

- [`A­W­T­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/AWTError.html)
- [`A­W­T­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/AWTException.html) <sup>✔</sup>
- [`Font­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/FontFormatException.html) <sup>✔</sup>
- [`Illegal­Component­State­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/IllegalComponentStateException.html)
- [`Headless­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/HeadlessException.html)

## Package `java­.awt­.color`

- [`C­M­M­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/color/CMMException.html)
- [`Profile­Data­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/color/ProfileDataException.html)

## Package `java­.awt­.datatransfer`

- [`Mime­Type­Parse­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.datatransfer/java/awt/datatransfer/MimeTypeParseException.html) <sup>✔</sup>
- [`Unsupported­Flavor­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.datatransfer/java/awt/datatransfer/UnsupportedFlavorException.html) <sup>✔</sup>

## Package `java­.awt­.dnd`

- [`Invalid­Dn­D­Operation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/dnd/InvalidDnDOperationException.html)

## Package `java­.awt­.geom`

- [`Noninvertible­Transform­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/geom/NoninvertibleTransformException.html) <sup>✔</sup>
- [`Illegal­Path­State­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/geom/IllegalPathStateException.html)

## Package `java­.awt­.image`

- [`Imaging­Op­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/image/ImagingOpException.html)
- [`Raster­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/image/RasterFormatException.html)

## Package `java­.awt­.print`

- [`Printer­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/print/PrinterException.html) <sup>✔</sup>
  - [`Printer­Abort­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/print/PrinterAbortException.html) <sup>✔</sup>
  - [`Printer­I­O­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/awt/print/PrinterIOException.html) <sup>✔</sup>

## Package `java­.beans`

- [`Introspection­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/beans/IntrospectionException.html) <sup>✔</sup>
- [`Property­Veto­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/java/beans/PropertyVetoException.html) <sup>✔</sup>

## Package `java­.lang­.annotation`

- [`Annotation­Format­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/annotation/AnnotationFormatError.html)
- [`Annotation­Type­Mismatch­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/annotation/AnnotationTypeMismatchException.html)
- [`Incomplete­Annotation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/annotation/IncompleteAnnotationException.html)

## Package `java­.lang­.instrument`

- [`Illegal­Class­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.instrument/java/lang/instrument/IllegalClassFormatException.html) <sup>✔</sup>
- [`Unmodifiable­Module­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.instrument/java/lang/instrument/UnmodifiableModuleException.html) <sup>9</sup>
- [`Unmodifiable­Class­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.instrument/java/lang/instrument/UnmodifiableClassException.html) <sup>✔</sup>

## Package `java­.lang­.invoke`

- [`Lambda­Conversion­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/invoke/LambdaConversionException.html) <sup>✔,\ 1.8</sup>
- [`Wrong­Method­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/invoke/WrongMethodTypeException.html)
- [`String­Concat­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/invoke/StringConcatException.html) <sup>✔,\ 9</sup>

## Package `java­.lang­.module`

- [`Find­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/module/FindException.html) <sup>9</sup>
- [`Invalid­Module­Descriptor­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/module/InvalidModuleDescriptorException.html) <sup>9</sup>
- [`Resolution­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/module/ResolutionException.html) <sup>9</sup>

## Package `java­.lang­.reflect`

- [`Generic­Signature­Format­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/reflect/GenericSignatureFormatError.html)
- [`Invocation­Target­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/reflect/InvocationTargetException.html) <sup>✔</sup>
- [`Inaccessible­Object­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/reflect/InaccessibleObjectException.html) <sup>9</sup>
- [`Malformed­Parameterized­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/reflect/MalformedParameterizedTypeException.html)
- [`Malformed­Parameters­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/reflect/MalformedParametersException.html) <sup>1.8</sup>
- [`Undeclared­Throwable­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/reflect/UndeclaredThrowableException.html)

## Package `java­.net`

- [`Http­Retry­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/HttpRetryException.html) <sup>✔</sup>
- [`Socket­Timeout­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/SocketTimeoutException.html) <sup>✔</sup>
- [`Malformed­U­R­L­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/MalformedURLException.html) <sup>✔</sup>
- [`Protocol­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/ProtocolException.html) <sup>✔</sup>
- [`Socket­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/SocketException.html) <sup>✔</sup>
  - [`Bind­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/BindException.html) <sup>✔</sup>
  - [`Connect­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/ConnectException.html) <sup>✔</sup>
  - [`No­Route­To­Host­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/NoRouteToHostException.html) <sup>✔</sup>
  - [`Port­Unreachable­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/PortUnreachableException.html) <sup>✔</sup>
- [`Unknown­Host­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/UnknownHostException.html) <sup>✔</sup>
- [`Unknown­Service­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/UnknownServiceException.html) <sup>✔</sup>
- [`U­R­I­Syntax­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URISyntaxException.html) <sup>✔</sup>

## Package `java­.net­.http`

- [`Http­Timeout­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.net.http/java/net/http/HttpTimeoutException.html) <sup>✔,\ 11</sup>
  - [`Http­Connect­Timeout­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.net.http/java/net/http/HttpConnectTimeoutException.html) <sup>✔,\ 11</sup>
- [`Web­Socket­Handshake­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.net.http/java/net/http/WebSocketHandshakeException.html) <sup>✔,\ 11</sup>

## Package `java­.nio`

- [`Buffer­Overflow­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/BufferOverflowException.html)
- [`Buffer­Underflow­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/BufferUnderflowException.html)
- [`Invalid­Mark­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/InvalidMarkException.html)
- [`Read­Only­Buffer­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/ReadOnlyBufferException.html)

## Package `java­.nio­.channels`

- [`Closed­Channel­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/ClosedChannelException.html) <sup>✔</sup>
  - [`Asynchronous­Close­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/AsynchronousCloseException.html) <sup>✔</sup>
    - [`Closed­By­Interrupt­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/ClosedByInterruptException.html) <sup>✔</sup>
- [`File­Lock­Interruption­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/FileLockInterruptionException.html) <sup>✔</sup>
- [`Interrupted­By­Timeout­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/InterruptedByTimeoutException.html) <sup>✔</sup>
- [`Illegal­Channel­Group­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/IllegalChannelGroupException.html)
- [`Illegal­Selector­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/IllegalSelectorException.html)
- [`Unresolved­Address­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/UnresolvedAddressException.html)
- [`Unsupported­Address­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/UnsupportedAddressTypeException.html)
- [`Accept­Pending­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/AcceptPendingException.html)
- [`Already­Bound­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/AlreadyBoundException.html)
- [`Already­Connected­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/AlreadyConnectedException.html)
- [`Cancelled­Key­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/CancelledKeyException.html)
- [`Closed­Selector­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/ClosedSelectorException.html)
- [`Connection­Pending­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/ConnectionPendingException.html)
- [`Illegal­Blocking­Mode­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/IllegalBlockingModeException.html)
- [`No­Connection­Pending­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/NoConnectionPendingException.html)
- [`Non­Readable­Channel­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/NonReadableChannelException.html)
- [`Non­Writable­Channel­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/NonWritableChannelException.html)
- [`Not­Yet­Bound­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/NotYetBoundException.html)
- [`Not­Yet­Connected­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/NotYetConnectedException.html)
- [`Overlapping­File­Lock­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/OverlappingFileLockException.html)
- [`Read­Pending­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/ReadPendingException.html)
- [`Shutdown­Channel­Group­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/ShutdownChannelGroupException.html)
- [`Write­Pending­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/channels/WritePendingException.html)

## Package `java­.nio­.charset`

- [`Coder­Malfunction­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/charset/CoderMalfunctionError.html)
- [`Character­Coding­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/charset/CharacterCodingException.html) <sup>✔</sup>
  - [`Malformed­Input­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/charset/MalformedInputException.html) <sup>✔</sup>
  - [`Unmappable­Character­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/charset/UnmappableCharacterException.html) <sup>✔</sup>
- [`Illegal­Charset­Name­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/charset/IllegalCharsetNameException.html)
- [`Unsupported­Charset­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/charset/UnsupportedCharsetException.html)

## Package `java­.nio­.file`

- [`File­System­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/FileSystemException.html) <sup>✔</sup>
  - [`Access­Denied­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/AccessDeniedException.html) <sup>✔</sup>
  - [`Atomic­Move­Not­Supported­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/AtomicMoveNotSupportedException.html) <sup>✔</sup>
  - [`Directory­Not­Empty­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/DirectoryNotEmptyException.html) <sup>✔</sup>
  - [`File­Already­Exists­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/FileAlreadyExistsException.html) <sup>✔</sup>
  - [`File­System­Loop­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/FileSystemLoopException.html) <sup>✔</sup>
  - [`No­Such­File­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/NoSuchFileException.html) <sup>✔</sup>
  - [`Not­Directory­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/NotDirectoryException.html) <sup>✔</sup>
  - [`Not­Link­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/NotLinkException.html) <sup>✔</sup>
- [`Directory­Iterator­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/DirectoryIteratorException.html)
- [`File­System­Already­Exists­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/FileSystemAlreadyExistsException.html)
- [`File­System­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/FileSystemNotFoundException.html)
- [`Invalid­Path­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/InvalidPathException.html)
- [`Provider­Mismatch­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/ProviderMismatchException.html)
- [`Closed­Directory­Stream­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/ClosedDirectoryStreamException.html)
- [`Closed­File­System­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/ClosedFileSystemException.html)
- [`Closed­Watch­Service­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/ClosedWatchServiceException.html)
- [`Provider­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/ProviderNotFoundException.html)
- [`Read­Only­File­System­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/ReadOnlyFileSystemException.html)

## Package `java­.nio­.file­.attribute`

- [`User­Principal­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/attribute/UserPrincipalNotFoundException.html) <sup>✔</sup>

## Package `java­.rmi`

- [`Already­Bound­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/AlreadyBoundException.html) <sup>✔</sup>
- [`Remote­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/RemoteException.html) <sup>✔</sup>
  - [`Access­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/AccessException.html) <sup>✔</sup>
  - [`Connect­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/ConnectException.html) <sup>✔</sup>
  - [`Connect­I­O­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/ConnectIOException.html) <sup>✔</sup>
  - [`Marshal­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/MarshalException.html) <sup>✔</sup>
  - [`No­Such­Object­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/NoSuchObjectException.html) <sup>✔</sup>
  - [`Server­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/ServerError.html) <sup>✔</sup>
  - [`Server­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/ServerException.html) <sup>✔</sup>
  - [`Server­Runtime­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/ServerRuntimeException.html) <sup>✔</sup>
  - [`Stub­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/StubNotFoundException.html) <sup>✔</sup>
  - [`Unexpected­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/UnexpectedException.html) <sup>✔</sup>
  - [`Unknown­Host­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/UnknownHostException.html) <sup>✔</sup>
  - [`Unmarshal­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/UnmarshalException.html) <sup>✔</sup>
- [`Not­Bound­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/NotBoundException.html) <sup>✔</sup>
- [`R­M­I­Security­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/RMISecurityException.html)

## Package `java­.rmi­.activation`

- [`Activation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/activation/ActivationException.html) <sup>✔</sup>
  - [`Unknown­Group­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/activation/UnknownGroupException.html) <sup>✔</sup>
  - [`Unknown­Object­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/activation/UnknownObjectException.html) <sup>✔</sup>
- [`Activate­Failed­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/activation/ActivateFailedException.html) <sup>✔</sup>

## Package `java­.rmi­.server`

- [`Server­Clone­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/server/ServerCloneException.html) <sup>✔</sup>
- [`Export­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/server/ExportException.html) <sup>✔</sup>
  - [`Socket­Security­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/server/SocketSecurityException.html) <sup>✔</sup>
- [`Skeleton­Mismatch­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/server/SkeletonMismatchException.html) <sup>✔</sup>
- [`Skeleton­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/server/SkeletonNotFoundException.html) <sup>✔</sup>
- [`Server­Not­Active­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.rmi/java/rmi/server/ServerNotActiveException.html) <sup>✔</sup>

## Package `java­.security`

- [`General­Security­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/GeneralSecurityException.html) <sup>✔</sup>
  - [`Digest­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/DigestException.html) <sup>✔</sup>
  - [`Invalid­Algorithm­Parameter­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/InvalidAlgorithmParameterException.html) <sup>✔</sup>
  - [`Key­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/KeyException.html) <sup>✔</sup>
    - [`Invalid­Key­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/InvalidKeyException.html) <sup>✔</sup>
    - [`Key­Management­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/KeyManagementException.html) <sup>✔</sup>
  - [`Key­Store­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/KeyStoreException.html) <sup>✔</sup>
  - [`No­Such­Algorithm­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/NoSuchAlgorithmException.html) <sup>✔</sup>
  - [`No­Such­Provider­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/NoSuchProviderException.html) <sup>✔</sup>
  - [`Signature­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/SignatureException.html) <sup>✔</sup>
  - [`Unrecoverable­Entry­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/UnrecoverableEntryException.html) <sup>✔</sup>
    - [`Unrecoverable­Key­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/UnrecoverableKeyException.html) <sup>✔</sup>
- [`Privileged­Action­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/PrivilegedActionException.html) <sup>✔</sup>
- [`Invalid­Parameter­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/InvalidParameterException.html)
- [`Provider­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/ProviderException.html)
- [`Access­Control­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/AccessControlException.html)

## Package `java­.security­.acl`

- [`Acl­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/acl/AclNotFoundException.html) <sup>✔</sup>
- [`Last­Owner­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/acl/LastOwnerException.html) <sup>✔</sup>
- [`Not­Owner­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/acl/NotOwnerException.html) <sup>✔</sup>

## Package `java­.security­.cert`

- [`Certificate­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertificateException.html) <sup>✔</sup>
  - [`Certificate­Encoding­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertificateEncodingException.html) <sup>✔</sup>
  - [`Certificate­Expired­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertificateExpiredException.html) <sup>✔</sup>
  - [`Certificate­Not­Yet­Valid­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertificateNotYetValidException.html) <sup>✔</sup>
  - [`Certificate­Parsing­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertificateParsingException.html) <sup>✔</sup>
  - [`Certificate­Revoked­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertificateRevokedException.html) <sup>✔</sup>
- [`Cert­Path­Builder­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertPathBuilderException.html) <sup>✔</sup>
- [`Cert­Path­Validator­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertPathValidatorException.html) <sup>✔</sup>
- [`Cert­Store­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CertStoreException.html) <sup>✔</sup>
- [`C­R­L­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/cert/CRLException.html) <sup>✔</sup>

## Package `java­.security­.spec`

- [`Invalid­Key­Spec­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/spec/InvalidKeySpecException.html) <sup>✔</sup>
- [`Invalid­Parameter­Spec­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/security/spec/InvalidParameterSpecException.html) <sup>✔</sup>

## Package `java­.sql`

- [`S­Q­L­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLException.html) <sup>✔</sup>
  - [`Batch­Update­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/BatchUpdateException.html) <sup>✔</sup>
  - [`S­Q­L­Client­Info­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLClientInfoException.html) <sup>✔</sup>
  - [`S­Q­L­Non­Transient­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLNonTransientException.html) <sup>✔</sup>
    - [`S­Q­L­Data­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLDataException.html) <sup>✔</sup>
    - [`S­Q­L­Feature­Not­Supported­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLFeatureNotSupportedException.html) <sup>✔</sup>
    - [`S­Q­L­Integrity­Constraint­Violation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLIntegrityConstraintViolationException.html) <sup>✔</sup>
    - [`S­Q­L­Invalid­Authorization­Spec­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLInvalidAuthorizationSpecException.html) <sup>✔</sup>
    - [`S­Q­L­Non­Transient­Connection­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLNonTransientConnectionException.html) <sup>✔</sup>
    - [`S­Q­L­Syntax­Error­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLSyntaxErrorException.html) <sup>✔</sup>
  - [`S­Q­L­Recoverable­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLRecoverableException.html) <sup>✔</sup>
  - [`S­Q­L­Transient­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLTransientException.html) <sup>✔</sup>
    - [`S­Q­L­Timeout­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLTimeoutException.html) <sup>✔</sup>
    - [`S­Q­L­Transaction­Rollback­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLTransactionRollbackException.html) <sup>✔</sup>
    - [`S­Q­L­Transient­Connection­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLTransientConnectionException.html) <sup>✔</sup>
  - [`S­Q­L­Warning`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLWarning.html) <sup>✔</sup>
    - [`Data­Truncation`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/DataTruncation.html) <sup>✔</sup>

## Package `java­.text`

- [`Parse­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/text/ParseException.html) <sup>✔</sup>

## Package `java­.time`

- [`Date­Time­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/DateTimeException.html) <sup>1.8</sup>

## Package `java­.time­.format`

- [`Date­Time­Parse­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/format/DateTimeParseException.html) <sup>1.8</sup>

## Package `java­.time­.temporal`

- [`Unsupported­Temporal­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/temporal/UnsupportedTemporalTypeException.html) <sup>1.8</sup>

## Package `java­.time­.zone`

- [`Zone­Rules­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/zone/ZoneRulesException.html) <sup>1.8</sup>

## Package `java­.util­.concurrent`

- [`Broken­Barrier­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/concurrent/BrokenBarrierException.html) <sup>✔</sup>
- [`Execution­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/concurrent/ExecutionException.html) <sup>✔</sup>
- [`Completion­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/concurrent/CompletionException.html) <sup>1.8</sup>
- [`Cancellation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/concurrent/CancellationException.html)
- [`Rejected­Execution­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/concurrent/RejectedExecutionException.html)
- [`Timeout­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/concurrent/TimeoutException.html) <sup>✔</sup>

## Package `java­.util­.jar`

- [`Jar­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/jar/JarException.html) <sup>✔</sup>

## Package `java­.util­.prefs`

- [`Backing­Store­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.prefs/java/util/prefs/BackingStoreException.html) <sup>✔</sup>
- [`Invalid­Preferences­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.prefs/java/util/prefs/InvalidPreferencesFormatException.html) <sup>✔</sup>

## Package `java­.util­.regex`

- [`Pattern­Syntax­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/regex/PatternSyntaxException.html)

## Package `java­.util­.zip`

- [`Zip­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/zip/ZipError.html)
- [`Data­Format­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/zip/DataFormatException.html) <sup>✔</sup>
- [`Zip­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/zip/ZipException.html) <sup>✔</sup>

## Package `com­.sun­.jdi`

- [`Absent­Information­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/AbsentInformationException.html) <sup>✔</sup>
- [`Class­Not­Loaded­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/ClassNotLoadedException.html) <sup>✔</sup>
- [`Incompatible­Thread­State­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/IncompatibleThreadStateException.html) <sup>✔</sup>
- [`Invalid­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InvalidTypeException.html) <sup>✔</sup>
- [`Invocation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InvocationException.html) <sup>✔</sup>
- [`Class­Not­Prepared­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/ClassNotPreparedException.html)
- [`Inconsistent­Debug­Info­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InconsistentDebugInfoException.html)
- [`Internal­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InternalException.html)
- [`Invalid­Code­Index­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InvalidCodeIndexException.html)
- [`Invalid­Line­Number­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InvalidLineNumberException.html)
- [`Invalid­Module­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InvalidModuleException.html) <sup>9</sup>
- [`Invalid­Stack­Frame­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/InvalidStackFrameException.html)
- [`Native­Method­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/NativeMethodException.html)
- [`Object­Collected­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/ObjectCollectedException.html)
- [`V­M­Cannot­Be­Modified­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/VMCannotBeModifiedException.html)
- [`V­M­Disconnected­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/VMDisconnectedException.html)
- [`V­M­Mismatch­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/VMMismatchException.html)
- [`V­M­Out­Of­Memory­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/VMOutOfMemoryException.html)

## Package `com­.sun­.jdi­.connect`

- [`Illegal­Connector­Arguments­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/connect/IllegalConnectorArgumentsException.html) <sup>✔</sup>
- [`Transport­Timeout­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/connect/TransportTimeoutException.html) <sup>✔</sup>
- [`V­M­Start­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/connect/VMStartException.html) <sup>✔</sup>

## Package `com­.sun­.jdi­.connect­.spi`

- [`Closed­Connection­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/connect/spi/ClosedConnectionException.html) <sup>✔</sup>

## Package `com­.sun­.jdi­.request`

- [`Duplicate­Request­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/request/DuplicateRequestException.html)
- [`Invalid­Request­State­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jdi/com/sun/jdi/request/InvalidRequestStateException.html)

## Package `com­.sun­.nio­.sctp`

- [`Invalid­Stream­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.sctp/com/sun/nio/sctp/InvalidStreamException.html)
- [`Illegal­Receive­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.sctp/com/sun/nio/sctp/IllegalReceiveException.html)
- [`Illegal­Unbind­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.sctp/com/sun/nio/sctp/IllegalUnbindException.html)

## Package `com­.sun­.tools­.attach`

- [`Agent­Initialization­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.attach/com/sun/tools/attach/AgentInitializationException.html) <sup>✔</sup>
- [`Agent­Load­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.attach/com/sun/tools/attach/AgentLoadException.html) <sup>✔</sup>
- [`Attach­Not­Supported­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.attach/com/sun/tools/attach/AttachNotSupportedException.html) <sup>✔</sup>
- [`Attach­Operation­Failed­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.attach/com/sun/tools/attach/AttachOperationFailedException.html) <sup>✔,\ 9</sup>

## Package `javax­.annotation­.processing`

- [`Filer­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/annotation/processing/FilerException.html) <sup>✔</sup>

## Package `javax­.crypto`

- [`Bad­Padding­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/crypto/BadPaddingException.html) <sup>✔</sup>
  - [`A­E­A­D­Bad­Tag­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/crypto/AEADBadTagException.html) <sup>✔</sup>
- [`Exemption­Mechanism­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/crypto/ExemptionMechanismException.html) <sup>✔</sup>
- [`Illegal­Block­Size­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/crypto/IllegalBlockSizeException.html) <sup>✔</sup>
- [`No­Such­Padding­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/crypto/NoSuchPaddingException.html) <sup>✔</sup>
- [`Short­Buffer­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/crypto/ShortBufferException.html) <sup>✔</sup>

## Package `javax­.imageio`

- [`I­I­O­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/imageio/IIOException.html) <sup>✔</sup>

## Package `javax­.imageio­.metadata`

- [`I­I­O­Invalid­Tree­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/imageio/metadata/IIOInvalidTreeException.html) <sup>✔</sup>

## Package `javax­.lang­.model`

- [`Unknown­Entity­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/lang/model/UnknownEntityException.html)

## Package `javax­.lang­.model­.element`

- [`Unknown­Annotation­Value­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/lang/model/element/UnknownAnnotationValueException.html)
- [`Unknown­Directive­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/lang/model/element/UnknownDirectiveException.html) <sup>9</sup>
- [`Unknown­Element­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/lang/model/element/UnknownElementException.html)

## Package `javax­.lang­.model­.type`

- [`Mirrored­Types­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/lang/model/type/MirroredTypesException.html)
  - [`Mirrored­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/lang/model/type/MirroredTypeException.html)
- [`Unknown­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.compiler/javax/lang/model/type/UnknownTypeException.html)

## Package `javax­.management`

- [`Bad­Attribute­Value­Exp­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/BadAttributeValueExpException.html) <sup>✔</sup>
- [`Bad­Binary­Op­Value­Exp­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/BadBinaryOpValueExpException.html) <sup>✔</sup>
- [`Bad­String­Operation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/BadStringOperationException.html) <sup>✔</sup>
- [`Invalid­Application­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/InvalidApplicationException.html) <sup>✔</sup>
- [`J­M­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/JMException.html) <sup>✔</sup>
  - [`M­Bean­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/MBeanException.html) <sup>✔</sup>
    - [`M­Bean­Registration­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/MBeanRegistrationException.html) <sup>✔</sup>
  - [`Operations­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/OperationsException.html) <sup>✔</sup>
    - [`Attribute­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/AttributeNotFoundException.html) <sup>✔</sup>
    - [`Instance­Already­Exists­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/InstanceAlreadyExistsException.html) <sup>✔</sup>
    - [`Instance­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/InstanceNotFoundException.html) <sup>✔</sup>
    - [`Introspection­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/IntrospectionException.html) <sup>✔</sup>
    - [`Invalid­Attribute­Value­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/InvalidAttributeValueException.html) <sup>✔</sup>
    - [`Listener­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/ListenerNotFoundException.html) <sup>✔</sup>
    - [`Malformed­Object­Name­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/MalformedObjectNameException.html) <sup>✔</sup>
    - [`Not­Compliant­M­Bean­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/NotCompliantMBeanException.html) <sup>✔</sup>
    - [`Service­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/ServiceNotFoundException.html) <sup>✔</sup>
  - [`Reflection­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/ReflectionException.html) <sup>✔</sup>
- [`J­M­Runtime­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/JMRuntimeException.html)
  - [`Runtime­Error­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/RuntimeErrorException.html)
  - [`Runtime­M­Bean­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/RuntimeMBeanException.html)
  - [`Runtime­Operations­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/RuntimeOperationsException.html)

## Package `javax­.management­.modelmbean`

- [`Invalid­Target­Object­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/modelmbean/InvalidTargetObjectTypeException.html) <sup>✔</sup>
- [`X­M­L­Parse­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/modelmbean/XMLParseException.html) <sup>✔</sup>

## Package `javax­.management­.monitor`

- [`Monitor­Setting­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/monitor/MonitorSettingException.html)

## Package `javax­.management­.openmbean`

- [`Open­Data­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/openmbean/OpenDataException.html) <sup>✔</sup>
- [`Invalid­Key­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/openmbean/InvalidKeyException.html)
- [`Invalid­Open­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/openmbean/InvalidOpenTypeException.html)
- [`Key­Already­Exists­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/openmbean/KeyAlreadyExistsException.html)

## Package `javax­.management­.relation`

- [`Relation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/RelationException.html) <sup>✔</sup>
  - [`Invalid­Relation­Id­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/InvalidRelationIdException.html) <sup>✔</sup>
  - [`Invalid­Relation­Service­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/InvalidRelationServiceException.html) <sup>✔</sup>
  - [`Invalid­Relation­Type­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/InvalidRelationTypeException.html) <sup>✔</sup>
  - [`Invalid­Role­Info­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/InvalidRoleInfoException.html) <sup>✔</sup>
  - [`Invalid­Role­Value­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/InvalidRoleValueException.html) <sup>✔</sup>
  - [`Relation­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/RelationNotFoundException.html) <sup>✔</sup>
  - [`Relation­Service­Not­Registered­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/RelationServiceNotRegisteredException.html) <sup>✔</sup>
  - [`Relation­Type­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/RelationTypeNotFoundException.html) <sup>✔</sup>
  - [`Role­Info­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/RoleInfoNotFoundException.html) <sup>✔</sup>
  - [`Role­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/relation/RoleNotFoundException.html) <sup>✔</sup>

## Package `javax­.management­.remote`

- [`J­M­X­Provider­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/remote/JMXProviderException.html) <sup>✔</sup>
- [`J­M­X­Server­Error­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.management/javax/management/remote/JMXServerErrorException.html) <sup>✔</sup>

## Package `javax­.naming`

- [`Naming­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/NamingException.html) <sup>✔</sup>
  - [`Cannot­Proceed­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/CannotProceedException.html) <sup>✔</sup>
  - [`Communication­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/CommunicationException.html) <sup>✔</sup>
  - [`Configuration­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/ConfigurationException.html) <sup>✔</sup>
  - [`Context­Not­Empty­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/ContextNotEmptyException.html) <sup>✔</sup>
  - [`Insufficient­Resources­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/InsufficientResourcesException.html) <sup>✔</sup>
  - [`Interrupted­Naming­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/InterruptedNamingException.html) <sup>✔</sup>
  - [`Invalid­Name­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/InvalidNameException.html) <sup>✔</sup>
  - [`Limit­Exceeded­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/LimitExceededException.html) <sup>✔</sup>
    - [`Size­Limit­Exceeded­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/SizeLimitExceededException.html) <sup>✔</sup>
    - [`Time­Limit­Exceeded­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/TimeLimitExceededException.html) <sup>✔</sup>
  - [`Link­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/LinkException.html) <sup>✔</sup>
    - [`Link­Loop­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/LinkLoopException.html) <sup>✔</sup>
    - [`Malformed­Link­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/MalformedLinkException.html) <sup>✔</sup>
  - [`Name­Already­Bound­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/NameAlreadyBoundException.html) <sup>✔</sup>
  - [`Name­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/NameNotFoundException.html) <sup>✔</sup>
  - [`Naming­Security­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/NamingSecurityException.html) <sup>✔</sup>
    - [`Authentication­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/AuthenticationException.html) <sup>✔</sup>
    - [`Authentication­Not­Supported­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/AuthenticationNotSupportedException.html) <sup>✔</sup>
    - [`No­Permission­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/NoPermissionException.html) <sup>✔</sup>
  - [`No­Initial­Context­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/NoInitialContextException.html) <sup>✔</sup>
  - [`Not­Context­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/NotContextException.html) <sup>✔</sup>
  - [`Operation­Not­Supported­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/OperationNotSupportedException.html) <sup>✔</sup>
  - [`Partial­Result­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/PartialResultException.html) <sup>✔</sup>
  - [`Referral­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/ReferralException.html) <sup>✔</sup>
  - [`Service­Unavailable­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/ServiceUnavailableException.html) <sup>✔</sup>

## Package `javax­.naming­.directory`

- [`Attribute­In­Use­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/AttributeInUseException.html) <sup>✔</sup>
- [`Attribute­Modification­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/AttributeModificationException.html) <sup>✔</sup>
- [`Invalid­Attribute­Identifier­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/InvalidAttributeIdentifierException.html) <sup>✔</sup>
- [`Invalid­Attributes­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/InvalidAttributesException.html) <sup>✔</sup>
- [`Invalid­Attribute­Value­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/InvalidAttributeValueException.html) <sup>✔</sup>
- [`Invalid­Search­Controls­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/InvalidSearchControlsException.html) <sup>✔</sup>
- [`Invalid­Search­Filter­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/InvalidSearchFilterException.html) <sup>✔</sup>
- [`No­Such­Attribute­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/NoSuchAttributeException.html) <sup>✔</sup>
- [`Schema­Violation­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/directory/SchemaViolationException.html) <sup>✔</sup>

## Package `javax­.naming­.ldap`

- [`Ldap­Referral­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.naming/javax/naming/ldap/LdapReferralException.html) <sup>✔</sup>

## Package `javax­.net­.ssl`

- [`S­S­L­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/net/ssl/SSLException.html) <sup>✔</sup>
  - [`S­S­L­Handshake­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/net/ssl/SSLHandshakeException.html) <sup>✔</sup>
  - [`S­S­L­Key­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/net/ssl/SSLKeyException.html) <sup>✔</sup>
  - [`S­S­L­Peer­Unverified­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/net/ssl/SSLPeerUnverifiedException.html) <sup>✔</sup>
  - [`S­S­L­Protocol­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/net/ssl/SSLProtocolException.html) <sup>✔</sup>

## Package `javax­.print`

- [`Print­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/print/PrintException.html) <sup>✔</sup>

## Package `javax­.print­.attribute`

- [`Unmodifiable­Set­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/print/attribute/UnmodifiableSetException.html)

## Package `javax­.script`

- [`Script­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.scripting/javax/script/ScriptException.html) <sup>✔</sup>

## Package `javax­.security­.auth`

- [`Destroy­Failed­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/DestroyFailedException.html) <sup>✔</sup>
- [`Refresh­Failed­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/RefreshFailedException.html) <sup>✔</sup>

## Package `javax­.security­.auth­.callback`

- [`Unsupported­Callback­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/callback/UnsupportedCallbackException.html) <sup>✔</sup>

## Package `javax­.security­.auth­.login`

- [`Login­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/LoginException.html) <sup>✔</sup>
  - [`Account­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/AccountException.html) <sup>✔</sup>
    - [`Account­Expired­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/AccountExpiredException.html) <sup>✔</sup>
    - [`Account­Locked­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/AccountLockedException.html) <sup>✔</sup>
    - [`Account­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/AccountNotFoundException.html) <sup>✔</sup>
  - [`Credential­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/CredentialException.html) <sup>✔</sup>
    - [`Credential­Expired­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/CredentialExpiredException.html) <sup>✔</sup>
    - [`Credential­Not­Found­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/CredentialNotFoundException.html) <sup>✔</sup>
  - [`Failed­Login­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/auth/login/FailedLoginException.html) <sup>✔</sup>

## Package `javax­.security­.cert`

- [`Certificate­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/cert/CertificateException.html) <sup>✔</sup>
  - [`Certificate­Encoding­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/cert/CertificateEncodingException.html) <sup>✔</sup>
  - [`Certificate­Expired­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/cert/CertificateExpiredException.html) <sup>✔</sup>
  - [`Certificate­Not­Yet­Valid­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/cert/CertificateNotYetValidException.html) <sup>✔</sup>
  - [`Certificate­Parsing­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/javax/security/cert/CertificateParsingException.html) <sup>✔</sup>

## Package `javax­.security­.sasl`

- [`Sasl­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.security.sasl/javax/security/sasl/SaslException.html) <sup>✔</sup>
  - [`Authentication­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.security.sasl/javax/security/sasl/AuthenticationException.html) <sup>✔</sup>

## Package `javax­.smartcardio`

- [`Card­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.smartcardio/javax/smartcardio/CardException.html) <sup>✔</sup>
  - [`Card­Not­Present­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.smartcardio/javax/smartcardio/CardNotPresentException.html) <sup>✔</sup>

## Package `javax­.sound­.midi`

- [`Invalid­Midi­Data­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/sound/midi/InvalidMidiDataException.html) <sup>✔</sup>
- [`Midi­Unavailable­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/sound/midi/MidiUnavailableException.html) <sup>✔</sup>

## Package `javax­.sound­.sampled`

- [`Line­Unavailable­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/sound/sampled/LineUnavailableException.html) <sup>✔</sup>
- [`Unsupported­Audio­File­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/sound/sampled/UnsupportedAudioFileException.html) <sup>✔</sup>

## Package `javax­.sql­.rowset`

- [`Row­Set­Warning`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql.rowset/javax/sql/rowset/RowSetWarning.html) <sup>✔</sup>

## Package `javax­.sql­.rowset­.serial`

- [`Serial­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql.rowset/javax/sql/rowset/serial/SerialException.html) <sup>✔</sup>

## Package `javax­.sql­.rowset­.spi`

- [`Sync­Factory­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql.rowset/javax/sql/rowset/spi/SyncFactoryException.html) <sup>✔</sup>
- [`Sync­Provider­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql.rowset/javax/sql/rowset/spi/SyncProviderException.html) <sup>✔</sup>

## Package `javax­.swing`

- [`Unsupported­Look­And­Feel­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/UnsupportedLookAndFeelException.html) <sup>✔</sup>

## Package `javax­.swing­.text`

- [`Bad­Location­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/text/BadLocationException.html) <sup>✔</sup>
- [`Changed­Char­Set­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/text/ChangedCharSetException.html) <sup>✔</sup>

## Package `javax­.swing­.tree`

- [`Expand­Veto­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/tree/ExpandVetoException.html) <sup>✔</sup>

## Package `javax­.swing­.undo`

- [`Cannot­Redo­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/undo/CannotRedoException.html)
- [`Cannot­Undo­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.desktop/javax/swing/undo/CannotUndoException.html)

## Package `javax­.transaction­.xa`

- [`X­A­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.transaction.xa/javax/transaction/xa/XAException.html) <sup>✔</sup>

## Package `javax­.xml­.catalog`

- [`Catalog­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/catalog/CatalogException.html) <sup>9</sup>

## Package `javax­.xml­.crypto`

- [`Key­Selector­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml.crypto/javax/xml/crypto/KeySelectorException.html) <sup>✔</sup>
- [`Marshal­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml.crypto/javax/xml/crypto/MarshalException.html) <sup>✔</sup>
- [`No­Such­Mechanism­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml.crypto/javax/xml/crypto/NoSuchMechanismException.html)
- [`U­R­I­Reference­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml.crypto/javax/xml/crypto/URIReferenceException.html) <sup>✔</sup>

## Package `javax­.xml­.crypto­.dsig`

- [`Transform­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml.crypto/javax/xml/crypto/dsig/TransformException.html) <sup>✔</sup>
- [`X­M­L­Signature­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml.crypto/javax/xml/crypto/dsig/XMLSignatureException.html) <sup>✔</sup>

## Package `javax­.xml­.datatype`

- [`Datatype­Configuration­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/datatype/DatatypeConfigurationException.html) <sup>✔</sup>

## Package `javax­.xml­.parsers`

- [`Factory­Configuration­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/parsers/FactoryConfigurationError.html)
- [`Parser­Configuration­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/parsers/ParserConfigurationException.html) <sup>✔</sup>

## Package `javax­.xml­.stream`

- [`Factory­Configuration­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/stream/FactoryConfigurationError.html)
- [`X­M­L­Stream­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/stream/XMLStreamException.html) <sup>✔</sup>

## Package `javax­.xml­.transform`

- [`Transformer­Factory­Configuration­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/transform/TransformerFactoryConfigurationError.html)
- [`Transformer­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/transform/TransformerException.html) <sup>✔</sup>
  - [`Transformer­Configuration­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/transform/TransformerConfigurationException.html) <sup>✔</sup>

## Package `javax­.xml­.validation`

- [`Schema­Factory­Configuration­Error`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/validation/SchemaFactoryConfigurationError.html) <sup>1.8</sup>

## Package `javax­.xml­.xpath`

- [`X­Path­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/xpath/XPathException.html) <sup>✔</sup>
  - [`X­Path­Expression­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/xpath/XPathExpressionException.html) <sup>✔</sup>
    - [`X­Path­Function­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/xpath/XPathFunctionException.html) <sup>✔</sup>
  - [`X­Path­Factory­Configuration­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/javax/xml/xpath/XPathFactoryConfigurationException.html) <sup>✔</sup>

## Package `jdk­.dynalink`

- [`No­Such­Dynamic­Method­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.dynalink/jdk/dynalink/NoSuchDynamicMethodException.html)

## Package `jdk­.jshell`

- [`J­Shell­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/JShellException.html) <sup>✔,\ 9</sup>
  - [`Eval­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/EvalException.html) <sup>✔,\ 9</sup>
  - [`Unresolved­Reference­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/UnresolvedReferenceException.html) <sup>✔,\ 9</sup>

## Package `jdk­.jshell­.spi`

- [`Execution­Control­Execution­Control­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.ExecutionControlException.html) <sup>✔</sup>
  - [`Execution­Control­Class­Install­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.ClassInstallException.html) <sup>✔</sup>
  - [`Execution­Control­Engine­Termination­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.EngineTerminationException.html) <sup>✔</sup>
  - [`Execution­Control­Internal­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.InternalException.html) <sup>✔</sup>
    - [`Execution­Control­Not­Implemented­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.NotImplementedException.html) <sup>✔</sup>
  - [`Execution­Control­Run­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.RunException.html) <sup>✔</sup>
    - [`Execution­Control­Resolution­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.ResolutionException.html) <sup>✔</sup>
    - [`Execution­Control­Stopped­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.StoppedException.html) <sup>✔</sup>
    - [`Execution­Control­User­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/ExecutionControl.UserException.html) <sup>✔</sup>
- [`S­P­I­Resolution­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jshell/jdk/jshell/spi/SPIResolutionException.html) <sup>9</sup>

## Package `jdk­.nashorn­.api­.scripting`

- [`Nashorn­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.scripting.nashorn/jdk/nashorn/api/scripting/NashornException.html) <sup>1.8u40</sup>

## Package `jdk­.nashorn­.api­.tree`

- [`Unknown­Tree­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.scripting.nashorn/jdk/nashorn/api/tree/UnknownTreeException.html) <sup>9</sup>

## Package `jdk­.security­.jarsigner`

- [`Jar­Signer­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jartool/jdk/security/jarsigner/JarSignerException.html) <sup>9</sup>

## Package `netscape­.javascript`

- [`J­S­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.jsobject/netscape/javascript/JSException.html)

## Package `org­.ietf­.jgss`

- [`G­S­S­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.security.jgss/org/ietf/jgss/GSSException.html) <sup>✔</sup>

## Package `org­.w3c­.dom`

- [`D­O­M­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/w3c/dom/DOMException.html)

## Package `org­.w3c­.dom­.events`

- [`Event­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/w3c/dom/events/EventException.html)

## Package `org­.w3c­.dom­.ls`

- [`L­S­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/w3c/dom/ls/LSException.html)

## Package `org­.w3c­.dom­.ranges`

- [`Range­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/w3c/dom/ranges/RangeException.html) <sup>9,\ DOM\ Level\ 2</sup>

## Package `org­.w3c­.dom­.xpath`

- [`X­Path­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.xml.dom/org/w3c/dom/xpath/XPathException.html)

## Package `org­.xml­.sax`

- [`S­A­X­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/xml/sax/SAXException.html) <sup>✔</sup>
  - [`S­A­X­Not­Recognized­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/xml/sax/SAXNotRecognizedException.html) <sup>✔</sup>
  - [`S­A­X­Not­Supported­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/xml/sax/SAXNotSupportedException.html) <sup>✔</sup>
  - [`S­A­X­Parse­Exception`](https://docs.oracle.com/en/java/javase/11/docs/api/java.xml/org/xml/sax/SAXParseException.html) <sup>✔</sup>

## Comments



© 2016–2021 Programming.Guide, [Terms and Conditions](../terms-and-conditions.html)
