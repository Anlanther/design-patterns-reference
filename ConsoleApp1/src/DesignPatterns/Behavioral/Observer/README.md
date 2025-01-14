Also known as the PubSub pattern. It involves an object, known as the subject, maintaining a list of its dependent objects, called observers, and notifying them automatically of any state changes.

## Communication Styles

PUSH: Uses `update()` where the subject pushes the changes to the observers. Has the advantage of the observers not dependent and has no knowledge to the subject.

PULL: If the observer requires different sets of values and therefore the observers has a reference of the subject with a `getValue()` method.

## Pros and Cons

- PRO: Follows the Single Responsibility Principle, splitting the storing and managing of the data into different places
- PRO: Follows Open Close Principle in that we no longer have to constantly modify data source classes

## In Practice

### Bad Example

```cs
DataSource dataSource = new DataSource();
Sheet2 sheet2 = new Sheet2();
BarChart barChart = new BarChart();
dataSource.AddDependent(sheet2);
dataSource.AddDependent(barChart);

// Calling SetValues() triggers the total and bar chart to also be updated:
dataSource.SetValues([5, 5, 1, 10]);
// Logs:
// Total: 21
// Rendering bar chart with new values

dataSource.SetValues([1, 2, 3]);
// Logs:
// Total: 21
// Rendering bar chart with new values
```

### Good Example

```cs
DataSource dataSource = new DataSource();
Sheet2 sheet2 = new Sheet2(dataSource);
BarChart barChart = new BarChart(dataSource);

dataSource.AddObserver(sheet2);
dataSource.AddObserver(barChart);

// Calling SetValues() triggers the total and bar chart to also be updated:
dataSource.SetValues([5, 5, 1, 10]);
// Logs:
// Total: 21
// Rendering bar chart with new values

dataSource.SetValues([1, 2, 3]);
// Logs:
// Total: 6
// Rendering bar chart with new values
```
