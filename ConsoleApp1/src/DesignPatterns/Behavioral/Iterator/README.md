Provides a way of iterating over an object without having to expose the object’s internal structure, which may change in the future. Changing the internals of an object should not affect its consumers.

## When to Use

When your collection possesses a complex internal data structure, or a data structure that is likely to change, so that clients can iterate over the collection without any knowledge of the data structure.

## Pros and Cons

- PRO: Satisfies SRP: traversal logic is abstracted into separate classes.
- PRO: Satisfied Open/closed principle: you can create new collections and iterators
  without breaking the code that uses them.
- CON: Can be overengineering if your app only works with simple collections.

## In Practice

### Bad Example

This is problematic because what if shopping list was a fixed array instead? Or if the list requires fixed values inside of it?

```cs
ShoppingList shoppingList = new ShoppingList();
shoppingList.Push("Milk");
shoppingList.Push("Bread");
shoppingList.Push("Steak");

for (int i = 0; i < shoppingList.GetList().Count; i++)
{
    var item = shoppingList.GetList()[i];
    System.Console.WriteLine(item);
}
```

### Good Example

Delegate iteration to another method/class that exists within the object. This fixes the single responsibility violation.

```cs
ShoppingList shoppingList = new ShoppingList();
shoppingList.Push("Milk");
shoppingList.Push("Bread");
shoppingList.Push("Steak");

IIterator<string> iterator = shoppingList.CreateIterator();

while (iterator.HasNext())
{
    System.Console.WriteLine(iterator.Current());
    iterator.Next();
}
```
