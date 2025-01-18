Aims to minimize memory usage by sharing common state between multiple objects, allowing efficient handling of large numbers of lightweight objects with shared characteristics.

## In Practice

### Bad Example

```cs
var cropService = new CropService();
foreach (var crop in cropService.GetCrops())
{
    crop.Render();
}

// Logs:
// Drawing Carrot at (1, 4)
// Drawing Carrot at (1, 5)
// Drawing Carrot at (1, 6)
```

### Good Example

```cs
// the only difference from before is that we now have to pass a CropIconFactory object to CropService, to ensure icons are cached, created only once, and reused between the same crops
var cropService = new CropService(new CropIconFactory());
foreach (var crop in cropService.GetCrops())
{
    crop.Render();
}

// Logs:
// Drawing Carrot at (1, 4)
// Drawing Carrot at (1, 5)
// Drawing Carrot at (1, 6)
```
