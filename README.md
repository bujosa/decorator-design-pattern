# Decorator Design Pattern
The Decorator Pattern is a structural design pattern that allows you to add new behaviors to objects dynamically by placing these objects inside special wrapper objects.

Using decorators, you can stack behaviors dynamically, as the pattern allows to use multiple decorators to wrap an object. Each decorator not only performs its own behavior, but also delegates the action to the wrapped object.

The main advantage of this pattern is that it follows the open-closed principle, as you can introduce new behavior without changing existing code. Decorators offer a flexible alternative to subclassing for extending functionality.

Here's a simple analogy: consider a plain pizza. You can choose to add toppings (decorators) like cheese, tomatoes, ham, etc. Each topping adds new behavior to the pizza (changing its taste) without altering the base pizza class. You can add or remove toppings dynamically according to your preference.

# Decorator Pattern in the Pizza Project

The decorator pattern is a design pattern used in this project to add new functionality to an object dynamically, without altering its implementation. This pattern creates a decorator class which wraps the original class and provides additional functionality keeping class methods signature intact.

## Classes Involved

1. **IngredientAdder**: This is the interface that defines a method `AddIngredient()`. All types that need to add an ingredient must implement this interface.

2. **Meat** and **Onion**: These are concrete classes that implement the `IngredientAdder` interface. They add their respective ingredients to the pizza.

## How it works

When `AddIngredient()` is called on a `Meat` or `Onion` object, it first delegates the call to the `AddIngredient()` method of the `Ingredient` it wraps (if any), then adds its own ingredient. This allows to build a pizza by stacking decorators.

For example, if you have a `Meat` object that wraps an `Onion` object, calling `AddIngredient()` on the `Meat` object will first add the onion, then the meat.

## Error Handling

If the `Ingredient` field of a `Meat` or `Onion` object is `nil`, the `AddIngredient()` method will return an error. This is to ensure that an `IngredientAdder` is always present on the `Ingredient` field.
