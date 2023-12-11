# OOP-Concept

Object-oriented programming (OOP) is **a programming paradigm** that organizes code into **reusable objects** that interact with one another. This concept is widely used in Android development using Kotlin and Java. In OOP, there are several **principles** that **guide the design and development process**. Let's cover some of these principles with examples in Kotlin for Android.

## 1. Encapsulation: 
This principle emphasizes **bundling data and methods together in a class** and **controlling access to them using access modifiers** such as private, protected, or public. Here's an example:

class Car {
    private var speed: Int = 0
    fun accelerate() {
        speed += 10
    }
    fun brake() {
        speed -= 5
    }
}
In this example, the speed property is encapsulated within the Car class, allowing controlled access through the accelerate, and brake methods.


## 2. Inheritance:
Inheritance allows classes to inherit properties and methods from a parent class. It enables code reuse and the creation of specialized classes. Here's an example:
open class Shape {
    open fun area(): Double {
        return 0.0
    }
}
class Rectangle(private val width: Double, private val height: Double) : Shape() {
    override fun area(): Double {
        return width * height
    }
}
In this example, the Rectangle class inherits the area method from the Shape class and overrides it to calculate the area of a rectangle.

## 3. Polymorphism:
Polymorphism is a concept that allows you to define methods in the superclass that the subclasses can override. It refers to the ability of an object to change its behavior depending on the type of object it is being referred to.
Here's an example to illustrate polymorphism in Android Kotlin:
open class Shape {
    open fun draw() {
        println("Drawing a shape")
    }
}


class Circle : Shape() {
    override fun draw() {
        println("Drawing a circle")
    }
}
class Square : Shape() {
    override fun draw() {
        println("Drawing a square")
    }
}
fun main() {
    val shape1: Shape = Circle()
    shape1.draw()    // Output: Drawing a circle
    
    val shape2: Shape = Square()
    shape2.draw()    // Output: Drawing a square
}
In the example above, we have a superclass called `Shape` that has a method `draw()`. This method is marked as `open`, which allows its subclasses to override it. 
We have two subclasses `Circle` and `Square` that inherit from the `Shape` class and override the `draw()` method with their own implementations. 
In the `main()` function, we demonstrate polymorphism by creating objects of the `Circle` and `Square` classes and assigning them to variables of type `Shape`. Even though the variables are of type `Shape`, they can invoke the `draw()` method specific to their respective classes, thus exhibiting polymorphic behavior.
The output of the example shows that the `draw()` method is called based on the type of object being referred to.
Types of Polymorphism
There are two types of polymorphism in Kotlin:
1. Static Polymorphism (Compile-time Polymorphism):
   - Method Overloading: It allows defining multiple methods with the same name but different parameters in the same class.
    fun add(num1: Int, num2: Int): Int {
        return num1 + num2
    }
    fun add(num1: Int, num2: Int, num3: Int): Int {
        return num1 + num2 + num3
    }


   - Operator Overloading: It allows defining operators to work with custom types.
    data class Point(val x: Int, val y: Int) {
        operator fun plus(other: Point): Point {
            return Point(x + other.x, y + other.y)
        }
    }
   
2. Dynamic Polymorphism (Run-time Polymorphism):
   - Method Overriding: It allows a subclass to provide a specific implementation of a method that is already implemented in its parent class.
    open class Animal {
        open fun sound() {
            println("Animal makes a sound")
        }
    }
    class Cat : Animal() {
        override fun sound() {
            println("Meow")
        }
    }
   - Implementing Interfaces: It allows a class to implement multiple interfaces and provide its own implementation of methods defined in those interfaces.
    interface Vehicle {
        fun start()
        fun stop()
    }


    class Car : Vehicle {
        override fun start() {
            println("Car started")
        }
        override fun stop() {
            println("Car stopped")
        }
    }
With polymorphism, objects of different classes can be treated as objects of their parent class, allowing for more flexibility and code reusability.

## 4. Abstraction:
Abstraction focuses on defining interfaces and hiding implementation details. It allows for the separation of concerns and enables code modularity. Here's an example:
interface Drawable {
    fun draw()
}


class Circle : Drawable {
    override fun draw() {
        println("Drawing a circle")
    }
}
class Square : Drawable {
    override fun draw() {
        println("Drawing a square")
    }
}
In this example, the Drawable interface provides a common draw method that classes like Circle and Square implement. The implementation details are hidden, and you can treat objects uniformly through the interface.


## OOP Interview Q&A

1-What is the difference between a constructor and a method?
The name of the constructor is same as that of the class name, whereas the name of the method can be anything.
There is no return type of a constructor.
When you make an object of a class, then the constructor of that class will be called automatically. But for methods, we need to call it explicitely.
Constructors can't be inherited but you can call the constructor of the parent class by calling super().
Constructor and a method they both run a block of code but the difference is in calling them.
We can call method directly using their name.
Constructor Syntax -
public class SomeClassName{
    SomeClassName(parameter_list){ 
    } 
}
Note: In the above syntax, the name of the constructor is the same as that of class and it has no return type.
Method Syntax
public class SomeClassName{
    public void someMethodName(parameter_list){
        ...
    }
    // call method
    someMethodName(parameter_list)
}


2-Differences between abstract classes and interfaces?
An abstract class, is a class that contains both concrete and abstract methods (methods without implementations). An abstract method must be implemented by the abstract class sub-classes. Abstract classes cannot be instantiated and need to be extended to be used.
An interface is like a blueprint/contract of a class (or it may be thought of as a class with methods, but without their implementation). It contains empty methods that represent, what all of its subclasses should have in common. The subclasses provide the implementation for each of these methods. Interfaces are implemented.


3-What is the difference between iterator and enumeration in java?
In Enumeration we don't have remove() method and we can only read and traverse through a collection.
Iterators can be applied to any collection. In Iterator, we can read and remove items from a collection.


4-Do you agree we use composition over inheritance?
Yes, it is generally recommended to use composition over inheritance when designing object-oriented programs. Composition allows for greater flexibility and code reuse, as it enables objects to be composed of or contain other objects rather than inheriting their behavior. This way, you can achieve greater modularity, avoid potential pitfalls related to tight coupling, and make your code more maintainable.
Here's an example in Kotlin to demonstrate the use of composition:
class Engine {
    fun start() {
        println("Engine started")
    }
}
class Car(private val engine: Engine) {
    fun startEngine() {
        engine.start()
    }
}


fun main() {
    val engine = Engine()
    val car = Car(engine)
    car.startEngine()
}
In this example, instead of inheriting the behavior of the `Engine` class, the `Car` class contains an instance of the `Engine` class as a private property. This composition relationship allows the `Car` class to delegate the responsibility of starting the engine to the `Engine` class. By doing so, the `Car` class can reuse the functionalities provided by the `Engine` class without the need for inheritance.
Using composition provides more flexibility, as you can easily substitute the `Engine` instance with a different implementation or even update its behavior without modifying the `Car` class. Additionally, it reduces coupling between classes, making the code more modular and maintainable.


5-Difference between method overloading and overriding.

Overloading happens at compile-time while Overriding happens at runtime: The binding of overloaded method call to its definition happens at compile-time however binding of overridden method call to its definition happens at runtime. 
  Overloaded methods are bonded using static binding while overridden methods are bonded using dynamic binding at runtime.

Static methods can be overloaded which means a class can have more than one static method of same name. Static methods cannot be overridden, even if you declare a same static method in child class it has nothing to do with the same method of parent class as overridden static methods are chosen by the reference class and not by the class of the object.
So, for example:
public class Animal {
    public static void testClassMethod() {
        System.out.println("The static method in Animal");
    }
    public void testInstanceMethod() {
        System.out.println("The instance method in Animal");
    }
}
public class Cat extends Animal {
    public static void testClassMethod() {
        System.out.println("The static method in Cat");
    }
    public void testInstanceMethod() {
        System.out.println("The instance method in Cat");
    }
    public static void main(String[] args) {
        Cat myCat = new Cat();
        myCat.testClassMethod(); —-------> output : The static method in Cat
        Animal myAnimal = myCat;
        myAnimal.testClassMethod(); —-------> output : The static method in Animal //ignoring actual object inside it (Cat)
        myAnimal.testInstanceMethod();------------>output: The instance method in Cat
    }
}

The most basic difference is that overloading is being done in the same class while for overriding base and child classes are required. Overriding is all about giving a specific implementation to the inherited method of parent class.
Static binding is being used for overloaded methods and dynamic binding is being used for overridden/overriding methods.
 Performance: Overloading gives better performance compared to overriding. The reason is that the binding of overridden methods is being done at runtime.
Private and final methods can be overloaded but they cannot be overridden. It means a class can have more than one private/final methods of same name but a child class cannot override the private/final methods of their base class.
Return type of method does not matter in case of method overloading, it can be same or different. However in case of method overriding the overriding method can have more specific return type (meaning if, for example, base method returns an instance of Number class, all overriding methods can return any class that is extended from Number, but not a class that is higher in the hierarchy, like, for example, Object is in this particular case).
Argument list should be different while doing method overloading. Argument list should be same in method Overriding. It is also a good practice to annotate overridden methods with @Override to make the compiler be able to notify you if child is, indeed, overriding parent's class method during compile-time.


6-What are the access modifiers you know? What does each one do?
There are four access modifiers in Java language (from strictest to the most lenient):
private variables, methods, constructors or inner classes are only visible to its' containing class and its' methods. This modifier is most commonly used, for example, to allow variable access only through getters and setters or to hide underlying implementation of classes that should not be used by user and therefore maintain encapsulation. Singleton constructor is also marked private to avoid unwanted instantiation from outside.
Default (no keyword is used) this modifier can be applied to classes, variables, constructors and methods and allows access from classes and methods inside the same package.
protected can be used on variables, methods and constructors therefore allowing access only to subclasses and classes that are inside the same package as protected members' class.
public modifier is widely-used on classes, variables, constructors and methods to grant access from any class and method anywhere. It should not be used everywhere as it implies that data marked with public is not sensitive and can not be used to harm the program.


7-Can an Interface implement another Interface?
Yes, an interface can implement another interface (and more than one), but it needs to use extends, rather than implements keyword. And while you can not remove methods from parent interface, you can add new ones freely to your sub-interface.
What is Polymorphism? What about Inheritance?
Polymorphism in Java has two types: Compile time polymorphism (static binding) and Runtime polymorphism (dynamic binding). Method overloading is an example of static polymorphism, while method overriding is an example of dynamic polymorphism.
An important example of polymorphism is how a parent class refers to a child class object. In fact, any object that satisfies more than one IS-A relationship is polymorphic in nature.
For instance, let’s consider a class Animal and let Cat be a subclass of Animal. So, any cat IS animal. Here, Cat satisfies the IS-A relationship for its own type as well as its super class Animal.
Inheritance can be defined as the process where one class acquires the properties (methods and fields) of another. With the use of inheritance the information is made manageable in a hierarchical order.
The class which inherits the properties of other is known as subclass (derived class, child class) and the class whose properties are inherited is known as superclass (base class, parent class).
Inheritance uses the keyword extends to inherit the properties of a class. Following is the syntax of extends keyword.
class Super {}
class Sub extends Super {}


8-Multiple inheritance in Classes and Interfaces in java
In Java and Kotlin, multiple inheritance refers to the ability of a class or interface to inherit from more than one class or interface. Java supports multiple interface inheritance, while Kotlin supports both multiple class inheritance and multiple interface inheritance through the use of interfaces.
Java Example:
interface Interface1 {
void method1();
}
interface Interface2 {
   void method2();
}
class MyClass implements Interface1, Interface2 {
    public void method1() {
        System.out.println("Method 1");
    }
    public void method2() {
        System.out.println("Method 2");
    }
}
public class Main {
    public static void main(String[] args) {
        MyClass myClass = new MyClass();
        myClass.method1();  // Output: Method 1
        myClass.method2();  // Output: Method 2
    }
}
Kotlin Example:
interface Interface1 {
    fun method1()
}
interface Interface2 {
    fun method2()
}


open class Class1 {
    open fun method3() {
        println("Method 3")
    }
}
class MyClass : Class1(), Interface1, Interface2 {
    override fun method1() {
        println("Method 1")
    }
    override fun method2() {
        println("Method 2")
    }
}
fun main() {
    val myClass = MyClass()
    myClass.method1()  // Output: Method 1
    myClass.method2()  // Output: Method 2
    myClass.method3()  // Output: Method 3
}
In the above examples, `MyClass` implements both `Interface1` and `Interface2`, thereby achieving multiple interface inheritance. In Kotlin, `MyClass` also extends `Class1`, which demonstrates multiple class inheritance. The methods `method1` and `method2` are overridden to provide their specific implementation, while `method3` is inherited from `Class1`.




