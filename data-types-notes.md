# DataTypes
1) number
2) bigInt
3) string
    - can use ", ', or `. both quotes are the same, backtick is extended functionality quotes, allow us to embed variable and expressions into strings by wrapping them in ${...}, e.g.:
    ```
    let name = "john"
        - alert(`Hello, ${name}!`) // Hello john!
    ```
4) boolean
5) undefined value
    - when a variable is undefined
    - bext practice to assign null to an empty or unknown value
6) objects
    - considered special, the first 6 are considered primitive
7) symbols
    - also considered special
8) typeof operator
    - returns the type of operand

# Notes:
- /n in a string will break line, but also respects breaks in the source code
- / before a character marks it as text, not part of the code, e.g. /' means it wont try and start a string, it will interpret it as an actual apostrophe

# Conditionals:
- lowercase is greater than uppercase, 'a' > 'A'
- true == 1, and false == 0
- a string will be converted to a number, so alert( '2' > 1)
- with strict equality, cant diffrentiate between 0 and false: (because operands are converted to numbers, so an empty string is zero)
    - alert( 0 == false); // true
    - alert( '' == false); / true
    - use '===' to return false for this because this wont do type conversion
- comparison with null and undefined:
    - alert( null === undefined); // false
    - alert( null == undefined); // true
    null becomes zero, undefined becomes NaN, when using these with maths comparisons (<,>, <=, >=)
- null vs 0
    - ( null > 0); // false
    - ( null == 0); // false
    - ( null >= 0); // true
    - with comparisons, null is converted to number zero.
    - with ==, its false
- incomparable undefined:
    - undefined gets converted to NaN for comparisons
    - undefined equals null, undefined, and no other value
    - ( undefined > 0); // false
    - ( undefined < 0>); // false
    - ( undefined == 0); // false
- **Avoid problems:**
    - **Treat any comparison with undefined/null except with === with excpetional care**
    - **Dont use comparisons with a variable which may be null/undefined. If a variable can have these values, check for them separately**

# Logical Operators:
- OR ||
- AND &&
- NOT !
- Nullish Coalescing &&

# OR (||)
- alert( true || false); // returns true
- finding the truthy value:
    - In other words, a chain of OR || returns the first truthy value or the last one if no truthy value is found.
    - alert( 1 || 0 ); // returns 1 (1 is truthy)
    - alert( undefined || null ||); // returns 0 (all falsy because returns last value)
- short circuit evaluation: (or oeprator stops evaluation immediately upon seeing true, so alert isnt run)
    - true || alert("not printed");
    - false || alert("printed");
- alerts return undefined. they will be executed but wont be truthy in an evaluation
    - i.e. alert( alert(1) || 2 || alert(3) ); // shows alert (but returns undefined so OR goes to second operand), then returns 2 because 2 is truthy.

# AND (&&)
- if all operands have been evaluated (i.e. all were truthy) then returns last operand
- so it returns first flasy value or last value if none were found
- precedence of AND (&&) is higher than OR (||)

# NOT (!)
- returns inverse
- a double not (!!), converts value into boolean:
    - i.e. alert( !!"not an empty string"); // returns true
- **precendance of NOT is highest of logical operators!**

# Switch statements:
- take a single value as an input and look through several choices until finding one that matches, thus executing that code.
```
switch (expression) {
  case choice1:
    // run this code
    break;

  case choice2:
    // run this code instead
    break;

  // include as many cases as you like

  default:
    // actually, just run this code
}
```
- cases can be grouped together like so:
```
case 3: // (*) grouped two cases
case 5:
    alert('Wrong!');
    alert("Why don't you take a math class?");
    break;
```
- type matters. For example, in a prompt, the answer would be a string, so if you write:
    case 3:
    alert("No!")
    - then the case wouldnt be executed because case 3 is a number, not a string and 3 isnt === '3'

# Ternary operator:
- tests a condition and returns one value if its true, and another if its false
- more useful than if..else statements if you have 2 choices that are chosen between via a true/flase condition (take up less code)
```
condition ? run this code : run this code instead. For example:
let result = condition ? value1 : value2;
```

# If statements:
- layout:
```
if (condition) {
  /* code to run if condition is true */
} else {
  /* run some other code instead */
}
```

# Random Notes:
- putting a + in front of a prompt converts a string into a number
    e.g. let a = +prompt('a?', '');
    - so when i enter a number (which it interprets as a string), it converts it to a number so I can compare using switch statements