The state pattern allows an object to behave differently depending on the state that it is in.

## When To Use

If you have a class that behaves differently depending on its state, and you have a large number of conditionals (if/else statements).

## Pros and Cons

- PRO: Improve readability and simplicity of the context class by eliminating conditionals.
- PRO: Satisfies the Single Responsibility Principle by abstracting state-specific logic into separate classes.
- PRO: Satisfies the Open/Closed Principle: we can introduce new states without modifying existing classes.
- CON: This pattern can be overkill if there are only a few states or if state logic rarely changes (e.g. our Stopwatch example above)

## In Practice

### Bad Example

```cs
var doc = new Document();
doc.State = DocumentStates.Moderation;
doc. CurrentUserRole = UserRoles.Editor;

System.Console.WriteLine(doc.State); // MODERATION

doc.Publish();

System.Console.WriteLine(doc. State): // PUBLISHED
```

### Good Example

```cs
Document doc = new Document(UserRoles.EDITOR);

System.Console.WriteLine(doc.State); // DraftState
doc.Publish();
System.Console.WriteLine(doc.State); // ModerationState
doc.Publish();
System.Console.WriteLine(doc.State); // ModerationState - editors can't create published documents

// Simulate Admin logging in and publishing the document
doc.CurrentUserRole = UserRoles.ADMIN;
doc.Publish();
System.Console.WriteLine(doc.State); // PublishedState

// Can also switch to any state like so:
doc.State = new DraftState(doc);
System.Console.WriteLine(doc.State); // DraftState
```
