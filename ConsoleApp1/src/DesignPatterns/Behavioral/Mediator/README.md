Defines an object (the Mediator) that describes how a set of
objects interact with each other, therefore reducing lots of chaotic dependencies between those objects.

## In Practice

```cs
var postsDialogBox = new PostsDialogBox();
postsDialogBox.SimulateUserInteraction();

// Logs:
// Title text box: Post 2
// Button enabled: True
```
