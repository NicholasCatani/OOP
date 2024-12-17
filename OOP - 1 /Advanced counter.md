_**Advanced counter**_

Implement a class for an advanced counter (as compared to the counter example in our lectures) which can keep track of the quantity of each item registered and the price of a unit.
You must expand the pattern in another panel.


class Counter:
     id : str   
     _items: dict[str, list[int, float]]   # {"item_name": [amount, price_of_unit]}
  
     def __init__(self, ID: str):
          '''creates a new counter with a given ID'''
          self.id = ID
          self._items = {} 
  
     def add(self, item_name: str, amount: int, price_of_unit: float)-> None:
          '''Adds amount of items with item_name and specifies price_of_unit. You can assume that every addition for the same item_name will have the same price_of_unit.'''
          if item_name in self._items:
            self._items[item_name][0] += amount ## increase the amount
          else:
            self._items[item_name] = [amount, price_of_unit]

     def remove(self, item_name: str, amount: int)->None:
          '''Removes the given amount of items with the given item name.'''  
          if item_name in self._items:
            self._items[item_name][0] -= amount
            if self._items[item_name][0] <= 0: ## remove item if amount becomes zero or negative
              del self._items[item_name]

     def reset(self):
          '''Removes all the records of items previously added.'''
          self._items.clear()

     def get_total(self)-> float:
          '''Returns the total sum rounded to two digits after decimal point .'''
          total = sum(amount * price for amount, price in self._items.values())
          return round(total, 2)

     def status(self)-> str:    
          '''Returs string of form "Id N M", where Id is id of counter, N is total amount of all items and M total price of them rounded to two digits after decimal point (with both digits printed).'''
          total_amount = sum(amount for amount, _ in self._items.values())
          total_price = self.get_total()
          return f"{self.id} {total_amount} {total_price:.2f}"


