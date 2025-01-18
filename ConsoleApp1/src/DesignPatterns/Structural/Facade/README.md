Provides a simplified interface to a complex system, encapsulating the complexities of multiple subsystems into a single unified interface for clients.

## In Practice

### Bad Example

```cs
// Order request contains info that user has submitted when requesting to make an order
var orderReq = new OrderRequest();

var auth = new Authenticate();

var inventory = new Inventory();

foreach (var id in orderReq.ItemIds)
{
    inventory.CheckInventory(id);
}

var payment = new Payment(orderReq.Name, orderReq.CardNumber, orderReq.Amount);
payment.Pay();

var orderFulfillment = new OrderFulfillment(inventory);
orderFulfillment.Fulfill(orderReq.Name, orderReq.Address, orderReq.ItemIds);

// Logs:
// Charging card with name danny
// Inserting order into database
// Reducing inventory of 123 by 1
// Reducing inventory of 423 by 1
// Reducing inventory of 555 by 1
// Reducing inventory of 989 by 1
```

### Good Example

```cs
var orderReq = new OrderRequest();
var orderService = new OrderService();
orderService.Order(orderReq);

// Logs:
// Charging card with name danny
// Inserting order into database
// Reducing inventory of 123 by 1
// Reducing inventory of 423 by 1
// Reducing inventory of 555 by 1
// Reducing inventory of 989 by 1
```
