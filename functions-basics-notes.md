# Function expression vs function declaration:
- Function Declaration: a function, declared as a separate statement, in the main code flow:
```
// Function Declaration
function sum(a, b) {
  return a + b;
}
```
- Function Expression: a function, created inside an expression or inside another syntax construct. Here, the function is created on the right side of the “assignment expression”. these dont have to have a name following 'function'
```
// Function Expression
let sum = function(a, b) {
  return a + b;
};
```
- functional declarations can be called anywhere in the script (i.e. theyre at the end, but I can call them from the start). Functional expressions can only usable from the moment its executed (i.e. put them at the start of the script if i want to call them down the line)

# Function Notes:
- functions are values,. they can be assigned, copied, or declared
- function declarations are preferred over function expressions

# Call stack:
- keeps track of function calls
- also manages execution contexts
- works on last-in-first-out principle
- steps:
    1) javascript executes the script
    2) it places the global execution context (denoted by main()), and gets put on the call stack first
    3) then the last function in the script gets called first and put on top of main() in the call stack
    4) starts executing that function
    5) more functions get put on top 
    6) when function is executed, it gets removed from the call stack one by one
- stacks have limited size (depending on the host environemtn), so if  the number of execution contexts exceed the size of the stack, a stack overlow error will occur. JavaScript only has one call stack, so can only do one thing at a time

# Arrow Functions:
- simple syntax to create functionds, often better than function expressions
```
let func = (arg1, arg2, ..., argN) => expression;
```
- e.g. a simpler version than:
```
let func = function(arg1, arg2, ..., argN) {
  return expression;
};
```
- multiline arrow functions:
    - enclose these with curly brackets
    - require a return within them to return a value
```
let sum = (a, b) => {  // the curly brace opens a multiline function
  let result = a + b;
  return result; // if we use curly braces, then we need an explicit "return"
};

alert( sum(1, 2) ); // 3
```