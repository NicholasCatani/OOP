_**My integer**_


Implement the class My_integer using the pattern in another panel.
Furthermore, implement the overloading of == operator on My_integer objects. 
That is, for two My_integer objects o1 and o2, o1 == o2 must return True, if the integers represented by o1 and o2 are equal, otherwise it must return False.





from __future__ import annotations  #keep this in because of recursive annotations

class My_integer:

  #you can add instance variables and their types here
  
     def __init__(self, x: int):
          '''creates My_integer object that represents x'''
          self.value = x

     def increase(self, o: My_integer) -> None:
          '''increases the value of this object by the value represented by another My_integer object o'''
          self.value += o.value

     def plus(self, o: My_integer)-> My_integer:
          '''returns the object representing the sum of the value represented by this object and the value represented by o'''
          return My_integer(self.value + o.value)

     def __eq__(self, other: My_integer) -> bool:
          '''overloads the == operator to compare two My_integer objects'''
          if isinstance(other, My_integer):
               return self.value == other.value
          return False

     def __repr__(self) -> str:
          '''returns a string representation of the My_integer object'''
          return f"My_integer({self.value})"
