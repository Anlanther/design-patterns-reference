```cs
var url = "https://google.cloud.com";
var data = "This is some data. Hello world. Facade Facade :)";
var compress = true;
var encrypt = true;

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
    cloudData = new EncryptedData(url);|
    cloudData.Save(data);
}

cloudData.Save(data);
```
