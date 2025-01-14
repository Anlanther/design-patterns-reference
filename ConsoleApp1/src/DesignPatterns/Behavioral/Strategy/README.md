Used to pass different algorithms, or behaviors, to an object.

## Difference Between Strategy and State

- States store a reference to the context object that contains them. Strategies do not.
- States are allowed to replace themselves (IE: to change the state of the context object to something else), while Strategies are not.
- Strategies only handle a single, specific task, while States provide the underlying implementation for everything (or almost everything) the context object does.

## When To Use

When you have a class with a large number of conditional statements that switch between variants of the same algorithm.

## Pros and Cons

- PRO: Satisfies open/closed principle: can add new strategies without modifying the
  context.
- PRO: Can swap algorithms used inside an object at runtime.
- CON: Clients have to be aware of the different algorithms and select the
  appropriate one.
- CON: If you only have a few algorithms that rarely change, then using the Strategy
  Pattern may be over-engineering.

## In Practice

### Good Example

```cs
VideoStorage videoStorage = new VideoStorage(new CompressorMOV(), new OverlayBlackAndWhite());
videoStorage.Store("/videos/dannys-movies");

videoStorage.SetOverlay(new OverlayNone());
videoStorage.Store("/videos/dannys-movies");

// Logs:
// Compressing video using MOV
// Applying black and white overlay
// Storing video to /videos/dannys-movies
// Compressing video using MOV
// Not applying an overlay
// Storing video to /videos/dannys-movies
```
