# OOP Concept

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

`open class Shape {`

    open fun area(): Double {
    
        return 0.0
    
    }

`}`


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

# Types of Polymorphism
There are two types of polymorphism in Kotlin:
## 1. Static Polymorphism (Compile-time Polymorphism):
   ### - Method Overloading: It allows defining multiple methods with the same name but different parameters in the same class.
    fun add(num1: Int, num2: Int): Int {
    
        return num1 + num2
        
    }
    
    fun add(num1: Int, num2: Int, num3: Int): Int {
    
        return num1 + num2 + num3
        
    }
    


   ### - Operator Overloading: It allows defining operators to work with custom types.
    data class Point(val x: Int, val y: Int) {
    
        operator fun plus(other: Point): Point {
        
            return Point(x + other.x, y + other.y)
            
        }
        
    }
   
## 2. Dynamic Polymorphism (Run-time Polymorphism):
   ### - Method Overriding: It allows a subclass to provide a specific implementation of a method that is already implemented in its parent class.
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
    
  ### - Implementing Interfaces: It allows a class to implement multiple interfaces and provide its own implementation of methods defined in those interfaces.
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


