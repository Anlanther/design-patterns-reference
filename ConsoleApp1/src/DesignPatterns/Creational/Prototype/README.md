Allows objects to be copied or cloned, providing a mechanism to create new instances by copying existing objects without explicitly invoking their constructors, and it is used to efficiently produce new instances with identical properties to existing objects.

## In Practice

### Bad Example

```cs
// User adds a new circle to GUI
var circle = new Circle();
circle.Draw();
// User clicks and drags on circle to resize
circle.Radius = 12;

// User adds a new rectangle to GUI
var rectangle = new Rectangle();
rectangle.Draw();
// User clicks and drags rectangle to resize
rectangle.Width = 20;
rectangle.Height = 12;

// User right-clicks the shapes and clicks "duplicate"
var shapeActions = new ShapeActions();
shapeActions.Duplicate(circle);
shapeActions.Duplicate(rectangle);

// Logs:
// Drawing circle
// Drawing rectangle
// Drawing circle
// Drawing rectangle
```

### Good Example

```cs
// User adds a new circle to GUI
var circle = new Circle();
circle.Draw();
// User clicks and drags on circle to resize
circle.Radius = 12;

// User adds a new rectangle to GUI
var rectangle = new Rectangle();
rectangle.Draw();
// User clicks and drags rectangle to resize
rectangle.Width = 20;
rectangle.Height = 12;

// User right-clicks the shapes and clicks "duplicate"
var shapeActions = new ShapeActions();
var circleClone = shapeActions.Duplicate(circle);
circleClone.Draw();
var rectangleClone = shapeActions.Duplicate(rectangle);
rectangleClone.Draw();

// Logs:
// Drawing circle
// Drawing rectangle
// Duplicating shape
// Drawing circle
// Duplicating shape
// Drawing rectangle
```
