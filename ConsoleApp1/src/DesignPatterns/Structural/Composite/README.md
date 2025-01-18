Enables the creation of tree-like structures to represent collections of objects, where both individual objects and groups of objects are treated in a unified manner.

## When To Use

Useful for representing tree structures.

## In Practice

### Bad Example

```cs
// the big package to deliver, containing box1 and box2
var package = new Box();

// box1 contains a microphone
var box1 = new Box();
box1.Add(new Microphone());

// box2 contains box3 and box4
var box2 = new Box();

// box3 contains a mouse
var box3 = new Box();
box3.Add(new Mouse());

// box4 contains a keyboard
var box4 = new Box();
box4.Add(new Keyboard());

box2.Add(box3);
box2.Add(box4);

package.Add(box1);
package.Add(box2);

System.Console.WriteLine("Total price of package = " + package.CalculateTotalPrice());
// Total price of package = 87.99
```

### Good Example

```cs
// the big package to deliver, containing box1 and box2
var package = new Box();

// box1 contains a microphone
var box1 = new Box();
box1.Add(new Microphone());

// box2 contains box3 and box4
var box2 = new Box();

// box3 contains a mouse
var box3 = new Box();
box3.Add(new Mouse());

// box4 contains a keyboard
var box4 = new Box();
box4.Add(new Keyboard());
box2.Add(box3);
box2.Add(box4);
package.Add(box1);
package.Add(box2);
System.Console.WriteLine("Total price of package = " + package.GetPrice());
// Total price of package = 87.99
```
