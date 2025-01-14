Defines a way to represent and evaluate sentences in a language by using an abstract class for expressions, which concrete subclasses implement to interpret specific parts of the language's grammar.

## Components

```cs
// User input: “1 + 2 * 3”
IExpression expressionTree = new AdditionExpression(
    new MultiplicationExpression(
        new NumberExpression("2"),
        new NumberExpression("3")
    ),
    new NumberExpression("1")
);

expressionTree.Interpret()
```

- Abstract Expression: Establishes the interface for all expressions within the language.
- Terminal Expression: Represents the fundamental components of the language, such as numbers or variables. In the above example `NumberExpression` is a terminal expression, or “leaf” , that represents integers.
- Non-terminal Expression: Represents more complex expressions that are composed of other expressions using operators or functions. Above, `AdditionExpression` and `MultiplicationExpression` are non-terminal, or “composite” , expressions.
- Interpreter: Implements the logic for interpretation and determines how to evaluate different types of expressions.
