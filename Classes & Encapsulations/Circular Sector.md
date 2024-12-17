_**Circular Sector**_

In this assignment, we will work with circular sectors of circles centred at (0,0). Such sectors will be specified by three numbers:
the angle (in degrees between 0 and 359) that the segment starts from (fr)
the angle (in degrees between 0 and 359) that the segment ends (to)
the radius (rad)
The angles are counted from the direction of the positive x axis, see below. Moreover, you may assume that the from angle is always smaller or equal to the to angle (fr <= to).


![image](https://github.com/user-attachments/assets/e6813299-5dc6-4593-83f9-e1a8085e912c)




from __future__ import annotations    #keep this in because of recursive annotations

class Sector: 
     fr: int
     to: int
     rad: int
    
     def __init__(self):
          '''Creates a circular sector with from and to angles 0 and radius 0.'''
          self.fr = 0
          self.to = 0
          self.rad = 0

     def rotate(self, angle: int)-> None:
          '''Rotates sector by the angle. For simplicity, assume that the rotation will result in a sector with fr <= to'''
          ### Adjust angles by rotation and normalize to the range [0, 359]
          self.fr = (self.fr + angle) % 360
          self.to = (self.to + angle) % 360

          ### Ensure the sector maintains fr <= to for simplicity
          if self.fr > self.to:
               self.fr, self.to = self.to, self.fr

     def intersect(self, other: Sector)-> Sector:
          '''Returns a new sector that is the result of the intersection of this sector with the other one. For simplicity, assume that the two sectors have non-empty intersection (overlap).'''
          ### Calculate the intersection of angles
          new_fr = max(self.fr, other.fr)
          new_to = min(self.to, other.to)
          
          ### The radius of the intersection is the minimum of the two radii
          new_rad = min(self.rad, other.rad)

          ### Create the new intersected sector
          intersection = Sector()
          intersection.fr = new_fr
          intersection.to = new_to
          intersection.rad = new_rad

          return intersection

     def is_empty(self)-> bool:
          '''Returns True if the sector has empty area, otherwise returns False.'''
          return self.fr == self.to or self.rad == 0

     def __eq__(self, other: Sector)-> bool:
          '''Returns True this sector is the same as the other, otherwise False.'''
          return self.fr == other.fr and self.to == other.to and self.rad == other.rad

     def __str__(self)-> str:
          '''Returns string "F T R" where F is from angle, T is to, and R is radius.'''
          return f"{self.fr} {self.to} {self.rad}"
