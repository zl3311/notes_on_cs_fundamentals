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
  * 
