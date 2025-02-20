# Arrays
- arrays are variables that store multiple thingds (strings, numbers, etc.)
- common practice to declare arrays with 'const'
- declare an array with either: (use first option more - best practice)
```
const 'array name' = [item 1, item 2, etc.]
const 'array name' = new Array(item 1, item 2, etc.)
```
- arrays are objects (can check this with typef()). But its better to describe them as arrays, rather than objects.
    - this is because arrays use numbers to access its elements, objects use names to access theirs:
person[0] returns John
```
const person = ["John", "Doe", 46];
```
person.firstName returns john:
```
const person = {firstName:"John", lastName:"Doe", age:46};
```

# Loops
- use for loop to iterate:
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
let fLen = fruits.length;

let text = "<ul>";
for (let i = 0; i < fLen; i++) {
  text += "<li>" + fruits[i] + "</li>";
}
text += "</ul>";
```
- can also use Array.forEach()
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];

let text = "<ul>";
fruits.forEach(myFunction);
text += "</ul>";

function myFunction(value) {
  text += "<li>" + value + "</li>";
}
```