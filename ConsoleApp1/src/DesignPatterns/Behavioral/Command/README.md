Encapsulates a request as an object, allowing you to parameterize clients with queues, requests, or operations.

It is commonly used in UI frameworks, especially for handling user interactions with buttons or menu items. Each button or menu item can be associated with a specific command object, allowing the framework to execute the appropriate action when the user interacts with the UI element. This decouples the UI components from the actual operations they perform, providing flexibility and maintainability in UI development.

## When To Use

When you want to implement reversible operations while using less RAM. It is great when you want to queue operations, or schedule their execution, as command objects can be serialized (converted into strings) and stored in databases or sent over networks, then, at a later time, they can be converted back into objects and executed.

## Pros and Cons

- PRO: Satisfies SRP: classes that invoke operations are decoupled from classes that perform these operations.
- PRO: Satisfies Open/closed principle: new commands can be added to the codebase without having to modify existing code.
- CON: Code may become more complex as you’re adding a new layer between senders and receivers.

## In Practice

### Bad Example

```cs
Light light = new Light();
RemoteControl remoteControl = new RemoteControl(light);

remoteControl.PressButton(true); // Light is on
remoteControl.PressButton(false); // Light is off
```

### Good Example

```cs
var light = new Light();
var remote = new RemoteControl(new TurnOnCommand(light));

remote.PressButton(); // Light is on
remote.SetCommand(new DimCommand(light));
remote.PressButton(); // Light is dim
```

With undo pattern:

```cs
var htmlDoc = new HtmlDocument();
var history = new History();
htmlDoc.Content = "Hello world";
System.Console.WriteLine(htmlDoc.Content); // Hello world

var italicCommand = new ItalicCommand(htmlDoc, history);
italicCommand.Execute();
System.Console.WriteLine(htmlDoc.Content); // <i>Hello world</i>

var undoCommand = new UndoCommand(history);
undoCommand.Execute();
System.Console.WriteLine(htmlDoc.Content); // Hello world
```
