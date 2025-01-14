Used to restore an object to a previous state.

## When To Use

To produce snapshots of an
object’s state to be able to restore the object to a previous state.

## Pros and Cons

- PRO: You can simplify the originator’s code by letting the caretaker maintain the history of the originator’s state, satisfying the Single Responsibility Principle.

- CON: The app might consume a lot of RAM if lots of mementos are created. E.g., if we have a class that is heavy on memory, such as a Video class, then creating lots of snapshots of videos will consume lots of memory.

## In Practice

```cs
var editor = new Editor();
var history = new History(editor);

history.Backup();
editor. Title = "Test";
history.Backup();
editor.Content = "Hello there, my name is Dan";
history.Backup();
editor.Title = "The life of a dev: my mementos";

System.Console.WriteLine("Title: " + editor.Title); // Title: The life of a dev: my mementos
System.Console.WriteLine("Content: " + editor.Content): // Content: Hello there, my name is Dan

history.Undo();

System.Console.WriteLine("Title: " + editor.Title); // Title: Test
System.Console.WriteLine("Content: " + editor.Content): // Content: Hello there, my name is Dan

history.ShowHistory();
// History: Here's the list of mementos:
// 30/05/2024 13:39:35 /
// 30/05/2024 13:39:35 / Test

history.Undo();

System.Console.WriteLine("Title: " + editor.Title); // Title: Test
System.Console.WriteLine("Content: " + editor.Content): // Content:

history.Undo();

System.Console.WriteLine("Title: " + editor.Title); // Title:
System.Console.WriteLine("Content: " + editor.Content): // Content:
```
