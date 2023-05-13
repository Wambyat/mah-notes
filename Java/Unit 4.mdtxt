# Unit 4

## Design Patterns:

<img title="" src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-13-22-59-image.png" alt="" data-align="center">

## Creational Patterns:

### Singleton

+ This is to ensure only one instance of the object exists in the JVM.

+ The global access point creates an object the first time and the subsequent calls returns the old object.

+ Good for a shared resource like a database object.

+ 3 things in the implementation:
  
  + Static object stored somewhere.
  
  + The default constructor is private.
  
  + A static creation method which in turns calls the constructor. Subsequent calls should return the cached object.

This is eager initialization.

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-13-28-19-image.png" title="" alt="" data-align="center">

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-13-28-27-image.png" title="" alt="" data-align="center">

This is a more proper example. Lazy initialization.

```java
public class Printer {
    private static Printer printer;
    
    private Printer() {
    }

    public static Printer getInstance() {
        return printer == null ? printer = new Printer() : printer;
    }
} 
```

This is **not thread safe** however.

```java
class Singleton
{
    private static Singleton obj;
 
    private Singleton() {}
 
    // Only one thread can execute this at a time
    public static synchronized Singleton getInstance()
    {
        if (obj==null)
            obj = new Singleton();
        return obj;
    }
}
```

This is **thread safe**.

A combo of these gives us Double Checked Locking

```java
class Singleton
{
    private static volatile Singleton obj  = null;
 
    private Singleton() {}
 
    public static Singleton getInstance()
    {
        if (obj == null)
        {
            // To make thread safe
            synchronized (Singleton.class)
            {
                // check again as multiple threads
                // can reach above step
                if (obj==null)
                    obj = new Singleton();
            }
        }
        return obj;
    }
}
```

This has a few issues:

+ SRP is usually violated.

+ It can potentially mask bad design.

+ It needs these extra bits for implementation in multi threaded environment.

+ Harder to test

---

### Factory

> defines an interface for creating an object, but let subclasses decide which class to instantiate

+ This is for creating objects but we don't specify the exact class. We can instead specify requirements or something like its name.

+ Subclasses override the creation method.



<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-14-08-30-image.png" title="" alt="" data-align="center">

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-14-08-51-image.png" title="" alt="" data-align="center">

Here we can send the shape name to ShapeFactroy and it will return the appropriate Shape based object.

Times to use factory:

+ Can't anticipate the class of objects we must create. 

+ We want the subclasses to specify the objects it creates.

Pros:

+ Coupling down

+ SRP

+ Open / Close

Cons:

+ Complex

---

### Builder

+ Creational Design Pattern. Encapsulation. Maybe by default abstraction also?

+ Builder Pattern says that "construct a complex object from simple objects using step-by-step approach"

+ Usually good for making SRP type classes. Also to make complex objects.

+ Useful for breaking huge constructors with large number of parameters.

+ Useful for making diff representations of the same object. Ex: burger thingy below.

+ SOLID compliance is improved. => code-reuse.

One stupid implementation is an open ended conversion. Lets say that we are trying convert from one text format to another. A class called DocxToPdf will be converting a Docx object to pdf object.



<img title="" src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-08-14-47-image.png" alt="" data-align="center">

Let's see an implementation.

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-08-07-49-image.png" title="" alt="" data-align="center">

To be more accurate there will be more implementations of BurgerBuilder like HamBurgerBuilder or CornCheeseBuilder etc.

The director type implementation will also have **polymorphism**.

---

### Prototype

+ This is for when creating new objects is expensive. So instead we will be cloning.

+ Useful when we the required objects are specified at run time.

+ When a object has a few different states, it is easier to clone rather than make new one from scratch.

+ Easier to add and remove objects.

+ Harder to make more complex objects.

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-08-39-24-image.png" title="" alt="" data-align="center">

We can have a prototype registry which is kinda like a factory.



---

## Structural Patterns:

### Adapter

+ A convertor lol. Structural pattern.

+ Makes a bridge between objects that need to interact with each other.

+ This is sometimes considered like a wrapper.

<img title="" src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-08-58-53-image.png" alt="" data-align="center">

The MP4 ,VLC problem.

Adaptee is the class getting converted. This is "controversial".

##### Object Adaptor vs Class Adaptor

<img title="" src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-09-08-36-image.png" alt="" width="863" data-align="center">

---

### Façade

+ It gives a interface to let us use much more complex classes and objects.

+ Can be created using an overarching `interface` or a regular`class`

+ It defines an entry point. 

+ It decouples the subsystems from the clients. It can sometimes remove circular dependencies.

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-10-31-42-image.png" title="" alt="" data-align="center">

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-10-33-30-image.png" title="" alt="" data-align="center">

---

### Proxy

+ Provides a surrogate/placeholder for another object.

+ Can be used for various things:
  
  + Lazy loading => Virtual Proxy: Lightweight replacement when the real object is very heavy.
  
  + Access Control => Protection Proxy
  
  + Remote loading => Remote Proxy: Has basic stuff of something in a remote location.
  
  + Caching => Cache Proxy

+ It follows open/closed principle

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-12-22-28-image.png" title="" alt="" data-align="center">

One way to look at this is that proxy image will be shown until the real image gets loaded.

---

### Flyweight

+ These objects do not store their state. It is stored outside. Intrinsic and Extrinsic State.

+ Good for sharing objects with many instances but a few types.

+ "parts of state" can be shared between objects. All the above let us reduce RAM usage.

+ This lets us propagate changes more efficiently. Cuz of the kinda centralized nature.

+ Extrinsic state calculations can sometimes be very taxing.

<img src="file:///C:/Users/Anirudha/AppData/Roaming/marktext/images/2023-05-11-13-00-35-image.png" title="" alt="" data-align="center">

A document editing software.

![](C:\Users\Anirudha\AppData\Roaming\marktext\images\2023-05-11-13-01-06-image.png)

UML

![](C:\Users\Anirudha\AppData\Roaming\marktext\images\2023-05-11-13-01-27-image.png)

Class Diagram

Example for flyweight:

> A pen that has various different refill ink colors. Everything else is shared. So intrinsic attributes will be pen nib, body etc. Extrinsic will be refill color.


