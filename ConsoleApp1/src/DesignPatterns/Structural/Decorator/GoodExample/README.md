Each decorator is capable of wrapping over each other.
Whereas in the bad example, there has to be a conditional for each combination.

```cs
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
```
