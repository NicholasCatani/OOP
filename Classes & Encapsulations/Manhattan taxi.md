_**Manhattan taxi**_


Implement a class ManhattanTaxi that keeps track of the following features of a taxi vehicle:
cons: number of litres consumed per km of distance
pos: position of the taxi on a map (assume that the taxi can only be in one of the positions of the grid where the distance between adjacent nodes is 1 km)
fuel: the current fuel level in litres
Provide your implementation by expanding the pattern in the other panel.
Note that the taxi operates in Manhattan, therefore when it travels from the position 
 to 
 it follows the street block grid and covers the distance .






class ManhattanTaxi:
    cons: float  # Fuel consumption in litres per km
    pos: tuple[int, int]  # Current position on the grid
    fuel: float  # Current fuel level in litres

    def __init__(self, initX: int, initY: int, consumption: float, init_fuel: float):
        '''Creates a new ManhattanTaxi positioned in (initX, initY) with the specified consumption and initial level of fuel.'''
        self.pos = (initX, initY)
        self.cons = consumption
        self.fuel = init_fuel

    def moveto(self, X: int, Y: int) -> bool:
        '''If the taxi has enough fuel to drive from its position to (X,Y), then its position is updated to (X,Y), 
        the fuel level updated according to the distance travelled, and True is returned.
        Otherwise, the position and the fuel level are not updated and False is returned.'''
        # Calculate Manhattan distance
        distance = abs(X - self.pos[0]) + abs(Y - self.pos[1])
        required_fuel = distance * self.cons

        if self.fuel >= required_fuel:  # Check if there's enough fuel
            self.fuel -= required_fuel  # Update fuel level
            self.pos = (X, Y)  # Update position
            return True
        else:
            return False  # Not enough fuel to make the trip

    def add_fuel(self, litres: int) -> None:
        '''Adds the given number of litres of fuel to the taxi.'''
        self.fuel += litres
 
