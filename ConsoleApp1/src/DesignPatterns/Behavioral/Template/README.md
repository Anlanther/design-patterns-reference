Allows you to define a template method, or skeleton, for an operation. The specific steps can then be implemented in subclasses.

## Template Method vs Strategy Pattern

- If you primarily need to customize or override specific steps of an algorithm while keeping the overall structure intact, the Template Method Pattern is a good choice.
- If you need to encapsulate entire algorithms or behaviors as interchangeable components that can be dynamically selected or replaced, the Strategy Pattern is more appropriate.

## When To Use

When you want to allow clients to implement only particular steps in an algorithm, and not the whole algorithm. It’s a good pattern to use when you have a bunch of classes with the same logic, or algorithm, but with differences in a few steps. So, if the algorithm changes, it only has to be modified in one place – the base class.

## Pros and Cons

- PRO: Reduce code duplication
- PRO: Clients are only allowed to modify certain steps in an algorithm, reducing the risk of breaking clients if the algorithm changes
- CON: Some clients may be limited by the provided template
- CON: Template methods can be hard to maintain if they have lots of steps

## In Practice

### Bad Example

```cs
var tea = new Tea();
tea.MakeBeverage();

// Logs:
// Boiling water
// Pouring water into cup
// Brewing tea for 3 minutes
// Would you like lemon with your tea? (y/n)
// "y"
// Adding lemon to tea
```

### Good Example

Using the strategy pattern with polymorphism:

```cs
var beverageMaker = new BeverageMaker(new Tea());
beverageMaker.MakeBeverage();
// Tea Logs:
// Boiling water
// Pouring water into cup
// Brewing tea for 3 minutes
// Would you like lemon with your tea? (y/n)
// "y"
// Adding lemon to tea

beverageMaker.SetBeverage(new Coffee());
beverageMaker.MakeBeverage();
// Coffee Logs:
// Boiling water
// Pouring boiled water into cup
// Brewing coffee for 5 minutes
// Would you like cream with your coffee? (y/n)
// "n"
```

Using inheritance:

```cs
var tea = new Tea();
tea.Prepare();
// Tea logs:
// Boiling water
// Pouring into cup
// Brewing for 3 mins
// Would you like lemon with your tea? (y/n)
// n

var coffee = new Coffee();
coffee.Prepare();
// Coffee logs:
// Boiling water
// Pouring into cup
// Brewing coffee for 5 mins
// Would you like cream with your coffee? (y/n)
// y
// Adding cream to coffee

var camomile = new Camomile();
camomile.Prepare();
// Camomile logs:
// Boiling water
// Pouring into cup
// Brewing for 3 mins
```
