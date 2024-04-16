# Lexical Scoping 
- Scope Hierarchy: Lexical scoping establishes a hierarchy of scopes based on the structure of the code. Each function in JavaScript creates its own scope, and nested functions have access to variables defined in their containing (lexical) scope.

- Scope Chain: When a variable is referenced within a function, JavaScript first looks for that variable's value within the function's own scope. If the variable is not found, JavaScript continues to search in the outer (lexical) scopes, following the chain of nested functions until it either finds the variable or reaches the global scope.

- Closure: Closures, which are functions that have access to variables from their containing scope even after the parent function has finished executing, rely on lexical scoping. The inner function maintains a reference to its lexical environment, allowing it to access variables from the outer scope even when it's executed outside of that scope.

- Static Binding: Lexical scoping is also known as static scoping or static binding because the scope of a variable is determined at the time the code is written and remains fixed throughout the execution of the program. This contrasts with dynamic scoping, where the scope of a variable is determined dynamically at runtime.

```JS
function outerFunction() {
  var outerVariable = 'I am outer';

  function innerFunction() {
    console.log(outerVariable); // Access outerVariable from outerFunction's scope
  }

  innerFunction();
}

outerFunction(); // Output: "I am outer"
```
> In this example, innerFunction has access to the outerVariable defined in its containing scope (outerFunction), even though innerFunction is executed outside of outerFunction's scope. This is possible due to lexical scoping, which allows nested functions to access variables from their parent functions' scopes.