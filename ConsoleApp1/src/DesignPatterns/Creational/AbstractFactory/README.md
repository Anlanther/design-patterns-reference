Provides an interface for creating families of related objects without specifying their concrete classes, promoting encapsulation and allowing for the creation of object families that can vary independently.

## In Practice

### Bad Example

```cs
var os = OperatingSystemType.Mac;
var userSettingsForm = new UserSettingsForm();
userSettingsForm.Render(os);

// Logs:
// Mac: render button
// Mac: render checkbox
```

### Good Example

```cs
// App initialisation -- we only have to do these operating
system checks upon starting the app, so that we can begin using
the correct UI library for this operating system throughout the
app.
var os = OperatingSystemType.Mac;
IUIComponentFactory uiComponentFactory;
if (os == OperatingSystemType.Windows)
{
uiComponentFactory = new WindowsUIComponentFactory();
else if (os == OperatingSystemType.Mac)
}
{
uiComponentFactory = new MacUIComponentFactory();
}
else
{
throw new Exception("Unsupported operating system");
297
}
new UserSettingsForm().Render(uiComponentFactory);
// Logs:
// Mac: render button
// Mac: render checkbox
```
