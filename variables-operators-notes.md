# Introduction
- "console.log" is the command to print something to the developer console in my browser
- to include javascript in your html, you can either:
    1) put the script directly into html file
    2) use an external script, e.g. "<script src="javascript.js"></script>. The name can be anything but remember .js

## Variables:
- declare variables using "let" command
- use "const" keyword to assign a constant variable that wont get reassigned, e.g. pi
- can also use "var" to declare a variable, but that was an old way thats not used anymore , but might come up still in history code
- can declare 2 variables at the same time:
'''
let admin, name;
name = "John"
admin = "name"
'''

- using "+" concatenates strings and numbers, but other operators will use typical maths, and javascript will convert strings to numbers if possible, e.g. "10" is a string but will be interpreted as a number
- javascript function isNaN() will give boolean if value is not a number. NaN is a number itself, proven by using function "typeof NaN" returns number. "Infinity" is also a number.
- Javascript interprets numeric constants as hexadecimal if theyre preceded by 0x, **Never write numbers with a leading zero, e.g. 07**

## Numbers:
- can use math logic to do calculations

## Naming:
- for multiple word declarations, use no spaces and make each first letter capitilised except first, e.g. myFirstVariablePercentage
- cant start with a number, no hyphens (use underscores instead)
- capital-named constants are only used as aliases for "hard coded" values, e.g. COLOR_RED = "#00F"