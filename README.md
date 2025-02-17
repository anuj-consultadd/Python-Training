# Python-Training
This repository is created for the purpose of Python training, i.e., for the submission of Python exercise files and to add the summary of the tutorial videos shared by the mentor for future reference.

[Link To Exercise 1](Excercise1-Basics.ipynb)

[Link To Exercise 2](Excercises2-Basics.ipynb)

[Link To Exercise 3](Python_Practice_Excercises.ipynb)


# Summary of OOPS tutorail video shared by the mentor:

## Classes and Objects
An oblject is a instance of a Class

and a Class basically determines what actions or in many ways we can interact with its object.

all these data types and the variables we create are all objects belonging to  int, string etc. Classes.

And these classes determine what different actions can we perform with their objects. 


![](oops_training_files/Class_Type.png)
Here Hello is a method or a function that is a object of a 'function' class.




## Create a Classs
Here we are basiacally creating a blue print for a dog object and also to define what are the differnet operations a dog is able to do.

![](oops_training_files/Class_Interaction_example.png)

Here upper() method when used on a int data type gives an error because int class does not define any interaction(methods) named Upper for its objects.


### __main__
![](oops_training_files/main__example.png)
here we took a variable d and assigned it to a instance(object) of a Dog Class.
The __main__ meaning this dog class was defined in the main Module.


### __init__
![](oops_training_files/init__example.png)
The __init__ method is basicaaly is the 'Constructor' method in python which instantiate the Object the very first time is is created.

Can also be parameterised or not.

## Self
The "self" passes the actual refernce to the specific dog object for which the Class methods are called.

![](oops_training_files/self_usage_example.png)

## Attributes
Attributes are variables that belong to an object class. They store data associated with the object.

Attributes are defined inside an instance (object) and are unique to that object.

![](oops_training_files/Self_missing_error.png)

Here the error came because everytime the object tries to use a Class method to which it belong it also invisibly passes itself  to the method as the "self" parameter. So that we know which object we are talking about.

## Example: How diff classes can interact with each other 
``` python
class Student:
    def __init__(self, name, age, grade):
        self.name= name
        self.age = age
        self.grade= grade #0 -100

    def get_grade(self):
        return self.grade
        
class Course:
    def __init__ ( self, name, max_students):
        self.name = name
        self.max_students = max_students
        self.students = []

    def add_student(self, student):
        if len(self.students) < self.max_students:
            self.students.append(student)
            return True 
        return False
    
    def get_average_grade(self):
        value = 0
        for student in self.students:
            value += student.get_grade()

        return value / len(self.students)
    

s1 = Student("Tim", 19 , 95)
s2 = Student("Bill", 19 , 75)
s3 = Student("Gill", 19 , 65)

course = Course("Science" , 2)
course.add_student(s1)
course.add_student(s2)

print(course.add_student(s3)) # max_students capacity is already full
print(course.get_average_grade())
print()
```

## Inheritence
``` python
class Pet:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def show(self):
        print(f"I am {self.name} and I am {self.age} years old ")
    
    def speak(self):
        print("I donno what I say")
```

## Super():
references the super class or the parent class 
``` python class Cat(Pet):
    def __init__(self, name, age, color):
        super().__init__(name,age)
        self.color = color 

    def speak(self):
        print("meow")

    def show(self):
        print(f"I am {self.name} and I am {self.age} years old and also I am {self.color} colored")


class Dog(Pet):
    def speak(self):
        print("bark")

p = Pet("Tim", 19)
p.speak()

c = Cat("Bill", 34, "orange")
c.show()

d = Dog("Jill", 19)
d.speak()

print()
```

## Class Attributes and methods:
belong to a specific class and not to any object

```python
class Person:
    number_of_people = 0

    def __init__(selff, name):
        self.name = name 
        Person.add_person()

    @classmethod
    def number_of_people_(cls):
        return cls.number_of_people  
    
    @classmethod
    def add_person(cls):
        cls.number_of_people  += 1

p1 = Person("Tim")
p2 = Person("Jim") 
print(Person.number_of_people_())
```

## Static Methods:
A static method in Python is a method inside a class that does not depend on an instance of the class. It behaves like a regular function but belongs to the class's namespace.

Static methods:  Do not modify or access instance (self) or class (cls) attributes.