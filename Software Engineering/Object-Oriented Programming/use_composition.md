# Use Composition

## Summary
* Use object composition instead of inheritance or mixin.
* Goods
  * **Inheritance Weakens Encapsulation** -  If the child class depends on the action of the parent class for its behavior, it suddenly becomes fragile. When parent class behavior changes, child class behavior can be broken without any modification on its part.
  * **More Flexible** - Lets you change behavior at runtime as long as the object you’re composing with implements the correct behavior interface.
  * **Makes Testing Easier** - Thanks to weaker encapsulation and if one class consists of another class, you can easily construct a Mock Object!

### Useful Links:
[OOP Series — Composition](https://medium.com/geekculture/oop-series-composition-6c67a19cabd1)