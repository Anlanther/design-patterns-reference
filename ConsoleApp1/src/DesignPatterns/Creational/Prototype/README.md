```cs
var circle = new Circle();
circle.Draw():

// user clicks and drags to resize
circle.Radius = 12;

// User adds a new rectangle to GUI
var rectangle = new Rectangle();
rectangle.Draw():
// User clicks and drags rectangle to resize
rectangle.Width = 20;
rectangle. Height = 12;

// user right-clicking and selecting "duplicate"
var shapeActions = new ShapeActions();

Shape newCircle = shapeActions-Duplicate(circle);
newCircle.Draw()

Shape newRect = shapeActions.Duplicate( rectangle);
newRect.Draw()
```
