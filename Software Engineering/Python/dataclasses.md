# Dataclasses

Docs: [Python](https://docs.python.org/3/library/dataclasses.html)

## Summary

* If you need to make a class that holds data and attributes, use dataclasses.
* Way less boilerplate.
* Some of the methods like `__init__`, `__repr__`, and `__eq__` are pre-populated for you.
* You can still do things after initialization using `def __post_init__(self, ...):`
* Convenience properties/methods like: `fields`, `asdict`, `astuple`, `make_dataclass`, and `is_dataclass`.
* You can have defaults even if its another class (think of composition). Use `dataclasses.field`
* Still supports granular control.
* Still supports proper inheritance (Python >= 3.10). However, it is tricky, see [#2](#2-python-dataclass-inheritance-finally)

### Useful Links:
#### 1. Why you should start using Python Dataclasses
[Source](https://python.plainenglish.io/why-you-should-start-using-pythons-dataclasses-cd6a73ae5614)  

#### 2. Python dataclass inheritance, finally ! 
[Source](https://medium.com/@aniscampos/python-dataclass-inheritance-finally-686eaf60fbb5)

### Code Examples
Some examples from [#1](#1-why-you-should-start-using-python-dataclasses)

#### **Without dataclass**:
```python
class Car(object):

    def __init__(self, name: str, make: str, year: int, vehicle_type: str):
        """
        :param name: Name of the care
        :param make: Brand(Hyundai/Toyota)
        :param year: Making year
        :param vehicle_type: Sedan/SUV/Hatch
        """

        self.name = name
        self.make = make
        self.year = year
        self.vehicle_type = vehicle_type


car = Car("Jazz", "Honda", 2008, "Hatch")

print(car.make)
print(car.name)
print(car)
```
Output
```shell
Output:
Honda
Jazz
<__main__.Car object at 0x000001D2CC934FD0>
```

#### **With dataclass (pretty repr, equals all work)**:
```python
@dataclass
class Car:
    name: str
    make: str
    year: int
    vehicle_type: str

car = Car("Jazz", "Honda", 2008, "Hatch")
print(car)
print(car.name)
print(car.make)
print(car.year)
print(car == Car("Jazz", "Honda", 2008, "Hatch"))
```
Output
```shell
Car(name='Jazz', make='Honda', year=2008, vehicle_type='Hatch')
Jazz
Honda
2008
True
```
