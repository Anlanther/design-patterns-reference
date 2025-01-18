Ensures a class has only one instance and provides a global point of access to that instance. The single instance is commonly used for managing shared resources, configuration settings, or logging functionality within an application.

## Pros

1. Resource Efficiency: Database connections and resources are typically limited and can be expensive to establish. By using a single instance of a database object, you minimize the overhead of creating and managing multiple connections, optimizing resource utilization.
2. Consistency and State Management: Having a single database instance ensures consistent state management and transaction handling across different parts of the application. Changes made to the database state are visible universally within the application, avoiding inconsistencies that could arise from multiple database instances.
3. Simplified Configuration and Management: With a singleton database instance, configuration settings such as connection parameters, credentials, and initialization logic are centralized and managed in one place. This simplifies application setup and maintenance.
4. Performance Optimization: By reusing a single database instance, you can optimize database query performance and reduce latency associated with establishing new connections or reinitializing database resources.

## In Practice

### Bad Example

```cs
// Configure the app settings
var settings = new AppSettings();
settings.Set("app_name", "Design Pattern Mastery");
settings.Set("app_creator", "Danny");
System.Console.WriteLine(settings.Get("app_name")); // Design
Pattern Mastery

// Accessing settings somewhere else in the app (i.e. in another class)...
var test = new Test();
test.Run();
```

### Good Example

```cs
var settings = AppSettings.GetInstance();
settings.Set("app_name", "Design Pattern Mastery");
settings.Set("app_creator", "Danny");
System.Console.WriteLine(settings.Get("app_name")); // Design Pattern Mastery

// Accessing settings somewhere else in the app (i.e. in another class)...
var test = new Test();
test.Run();
```
