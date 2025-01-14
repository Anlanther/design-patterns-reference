Bad Example

```cs
var sportsCar = new Car(CarType. Sports, 2, false, new Engine(), new Dashboard (hasRevCounter:
true), new Wheels(diameterInInches: 20), new GPSNavigator());
sportsCar. Fuel = 100;
var suvCar = new Car(CarType. SUV, seats: 5, isConvertible: false, new Engine(), new Dashboard
(hasRevCounter: true), new Wheels (diameterInInches: 19), new GPSNavigator()):
suvCar.Fuel = 40;
var sportsCarManual = new Manual (CarType.Sports, 2, false, new Engine(), new Dashboard
(hasRevCounter: true), new Wheels (diameterInInches: 20), new GPSNavigator());
System.Console.WriteLine(sportsCarManual.Print());
var suvManual = new Manual(CarType.SUV, 5, false, new Engine(), new Dashboard (hasRevCounter:
true), new Wheels(diameterInInches: 19), new GPSNavigator));
System. Console WriteLine(suvManual. Print());
```

```cs
var carBuilder = new CarBuilder();
carBuilder.SetCarType(CarType.Sports)
•SetSeats (2)
•SetEngine(new Engine())
•SetDashboard (new Dashboard (hasRevCounter: true))
• SetWheels (new Wheels(diameter InInches: 20)):|
var sportsCar = carBuilder.GetCar();
sportsCar.Fuel = 100;
var manualBuilder = new CarManualBuilder();
manualBuilder.SetCarType(CarType.Sports)
•SetSeats (2)
•SetEngine(new Engine())
•SetDashboard (new Dashboard (hasRevCounter: true))
•SetWheels (new Wheels(diameterInInches: 20));
var sportsCarManual = manualBuilder.GetManual):
System. Console.WriteLine(sportsCarManual.Print());
```

```cs
var carBuilder = new CarBuilder();
var director = new Director();
director.ConstructSportsCar(carBuilder);
var sportsCar = carBuilder.GetCar():
sportsCar.Fuel = 100;
director.ConstructSUV(carBuilder);
var suvCar = carBuilder.GetCar();
suvCar. Fuel = 40;
var manualBuilder = new CarManualBuilder();
director.ConstructSportsCar(manualBuilder);
var sportsCarManual = manualBuilder.GetManual();
System. Console.WriteLine(sportsCarManual.Print());
director.ConstructSUV(manualBuilder);
var suManual = manualBuilder.GetManual();
System. Console.WriteLine(suvManual.Print());
```
