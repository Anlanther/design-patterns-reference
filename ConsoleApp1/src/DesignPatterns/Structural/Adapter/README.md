Allows incompatible interfaces between classes to work together by providing a wrapper that translates one interface into another.

## In Practice

### Bad Example

```cs
var video = new Video();
var videoEditor = new VideoEditor(video);
videoEditor.ApplyColor(new BlackAndWhiteColor());
```

### Good Example

```cs
videoEditor.ApplyColor(new RainbowColor(new Rainbow()));
```
