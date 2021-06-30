Object-oriented design notes
----

Object-oriented design is a programming principle that is useful when building a system with complex hierarchies. It well-captures the intra- and inter-relationships among different components and is popular in modern software system designs.

I took a series of lectures on OOD in Python from [realpython.com](https://realpython.com/learning-paths/object-oriented-programming-oop-python/) and summarized my takeaways from it.

* ```class``` vs ```instance```
  * ```class``` is like a blueprint of a component. You need to design the way how the component is expected to function without creating the actual component (say in the memory on the computer).
  * ```instance``` is the actual component that is created using way it was defined, and it "lives" in the memory of computer (with an memory address). The process of creating the ```instance``` from ```class``` is called **instantiate**.
  * It's tempting to say ```object``` when describing ```class``` and ```instance```, but in python3, object is reserved to describe the most fundamental data type, which is the root of everything in python3. That being said, the correct technical term to call ```class``` and ```instance``` in this case are ***class object*** and ***instance object*** respectively.

* ```class``` basics
  * a ```class``` is consisted of ***attributes*** and ***methods***. ***Attribute*** describes the properties of the class, and ***method*** describes the behaviors of the class. Of course, as you might think, a ***method*** can involves changing its ***attributes*** given some internal/external parameters.
  * In python, defining a ```class``` is REALLY straight-forward, simply ```class MyClass```. Here, ```class``` is a clarification of defining a new ```class```, and ```MyClass``` is the name of the defined ```class```. By convention, the intial letter of class name should be in captial.
  * Some initialization is need for the class, like setting the initial values of different ***attributes***. In python, initialization is declared using ```def __init__```.

* ```__str__``` vs ```__repr__```
  * Sometime, you might want to print out an instance and check out some useful information about it. By default, python returns the name of class and its memory location when you call ```print(myInstance)```. This may not provide you with enough information, and in this case, ```__str__``` and ```__repr__``` become useful.
  * ```__str__``` method is used when you try to print the instance (either ```str(myInstance)``` or ```print(myInstance)```). The goal of introducing ```def __str__``` is to make the instance more **readable** to human readers. 
  * Similarly, ```__repr__``` method is used to clarify specifications about the instance. The difference between ```__str__``` and ```__repr__``` is that ```__repr__``` is designed to make the instance **unambiguous** to machine (and maybe developers).
  * In fact, the ```__str__``` method by default calls ```__repr__`` method if no ```__str__``` method is explicitly defined. But it would be better to define both methods for interpretability.

* ```super()```charge!
  * As mentioned earlier, OOD is useful when designing hierarchies of relationships, and one of the common relationships is the parent-child type of relationship. In OOD, this type of ***is-a*** relationship is called **inheritance**, and I'll talk more about it together with another common relationship called **composition** later this markdown.
  * Let's say you defined a class called ```class Parent```, and you would like to have another class that has everything of ```class Parent``` plus some additional features. You can simply do it as ```class Child(Parent)``` in python, which simply means ```class Child``` adopted everything from ```class Parent``` and has the potential to do additional things beyond that. In python, this type of relationship is sometimes referred to as base/parent class and subclass.
  * Let's say for initialization, if you simply want to use however the base class initializes, you don't even need to re-initialize inside the subclass. It's automatically managed by default in python. However, if you would like to use the initialization of base class but do it slightly different upon that, ```super()``` becomes useful. You can do it as follows.
  
  ```
  class Child(Parent):
      def __init__(self):
          super().__init__() # Initialize the same as Parent class first
          # Then do something special for Child class specifically
  ```
  
  * In case of multiple layers of inheritance, which specific function you are trying to retrieve becomes messy. In this case, python handles this situation by using **Method Resolution Order (MRO)**, which is generated using C3 Linearization Algorithm. You can have access to the MRO for any method by calling ```object.__mro__```.
