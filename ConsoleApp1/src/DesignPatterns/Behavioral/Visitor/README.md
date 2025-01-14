Separates the algorithms, or behaviors, from the objects on which
they operate.

## In Practice

### Bad Example

```cs
// Get list of clients (e.g. from db)
var clients = new List<Client> {
new Retail("Debinhams", "team@debinhams.co.uk"),
new Restaurant("Frankie and Bennys", "frank@fandb.com"),
new Law("Hamlin McGil Law Firm", "howard@handm.com")
};

// Loop through clients and send marketing email
foreach (var client in clients)
{
client.SendEmail(); // polymorphism makes this easy
}

// Logs:
// Sending retail marketing tips email to team@debinhams.co.uk
// Sending restaurant marketing tips email to frank@fandb.com
// Sending law marketing tips email to howard@handm.com
```

### Good Example

```cs
// Get list of clients (e.g. from db)
var clients = new List<Client> {
    new Retail("Debinhams", "team@debinhams.co.uk"),
    new Restaurant("Frankie and Bennys", "frank@fandb.com"),
    new Law("Hamlin McGil Law Firm", "howard@handm.com")
};

// Loop through clients and send marketing email
foreach (var client in clients)
{
    client.Accept(new EmailVisitor()); // pass the operation that we want to do to the client
    client.Accept(new PDFExportVisitor());
}

// Logs:
// Sending retail marketing tips email to team@debinhams.co.uk
// Sending restaurant marketing tips email to frank@fandb.com
// Sending law marketing tips email to howard@handm.com

// Logs:
// Exporting retail client as PDF.
// Exporting restaurant client as PDF.
// Exporting law client as PDF.
```
