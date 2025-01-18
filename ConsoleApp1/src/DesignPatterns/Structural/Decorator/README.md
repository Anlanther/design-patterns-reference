Allows behavior to be added to individual objects dynamically, enhancing functionality without altering the object's structure, and it's used to extend or modify the behavior of objects by wrapping them with additional functionality through composition.

## In Practice

### Bad Example

```cs
// User input data:
var url = "https://google.cloud.com";
var data = "This is some data. Hello world. Facade Facade :)";
var compress = true;
var encrypt = true;

// Now we have to select the correct cloud storage object
var cloudData = new CloudData(url);
if (compress && encrypt)
{
    cloudData = new CompressedAndEncryptedData(url);
}
else if (compress)
{
    cloudData = new CompressedData(url);
}
else if (encrypt)
{
    cloudData = new EncryptedData(url);
}
// We have the correct data storage object, so now we can save
the data
cloudData.Save(data);
```

### Good Example

```cs
// User input data:
var url = "https://google.cloud.com";
var data = "This is some data. Hello world. Facade Facade :)";
var compress = true;
var encrypt = true;

Data cloudData = new CloudData(url);

if (encrypt)
{
    cloudData = new EncryptionDecorator(cloudData);
}
if (compress)
{
cloudData = new CompressionDecorator(cloudData);
}
cloudData.Save(data);

// Logs:
// Compressing data
// Encryping data
// Saving data '$dc&^*()';,,£@%%*(~)`' to cloud at 'https://google.cloud.com'
```
