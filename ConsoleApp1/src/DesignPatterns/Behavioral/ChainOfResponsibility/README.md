Allows building a chain of objects to handle a request. A request is passed through a chain of handlers, each capable of either handling the request or passing it to the next handler in the chain.

## In Practice

### Bad Example

```cs
var server = new WebServer();
var request = new HttpRequest("danny", "123");
server.Handle(request);
```

### Good Example

```cs
var validator = new Validator();
var authenticator = new Authenticator();
var logger = new Logger();

validator.SetNext(authenticator).SetNext(logger);

var server = new WebServer(validator);

// Request with valid credentials
var request1 = new HttpRequest("danny", "123");
server.Handle(request1);

// Logs:
// Validating
// Authenticating
// Logging

// Request with invalid password
var request2 = new HttpRequest("danny", "abcde");
server.Handle(request2);
// Logs (notice how there is no "Logging" – since authentication failed, the request chain was cut short and didn't go to the next link):
// Validating
// Authenticating

// Request with no empty credentials will cause validation to fail
var request3 = new HttpRequest("","");
server.Handle(request3);

// Logs:
// Validating
```
