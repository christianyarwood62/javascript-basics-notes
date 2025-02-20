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
# add elements onto an array
- 3 methods:
    - use array.push('new item;)
    - or use array.length('new item')
    - index specifically, e.g. array[index] = 'new item'. This can creat undefined holes however, so indexes before the specified index

# Associative arrays
- many languages support arrays with named indexes, but javascript doesnt
- javascript always uses numbered indexes
    - **if you use named indexes, JavaScript will redefine the array to an object. After that, some array methods and properties will produce incorrect results.**

# When to use arrays or objects:
- You should use objects when you want the element names to be strings (text).
- You should use arrays when you want the element names to be numbers.

# how to check if you have an array
- use isArray(). e,g. 'array_name'.isArray()
- use instanceof(). e.g. ('array_name' instanceof() Array)

# Loops
- e.g.:
```
const cats = ["Leopard", "Serval", "Jaguar", "Tiger", "Caracal", "Lion"];

for (const cat of cats) {
  console.log(cat);
}
```
- maps and filters:
    - map() calls the function once for each item in the array, passing in the item. It then adds the return value from each function call to a new array, and finally returns the new array
    - filter() looks a lot like map(), except the function we pass in returns a boolean: if it returns true, then the item is included in the new array.
- to run a loop a set number of times:
```
for (initializer; condition; final-expression) {
  // code to run
}
```
    - An initializer — this is usually a variable set to a number, which is incremented to count the number of times the loop has run. It is also sometimes referred to as a counter variable.
    - A condition — this defines when the loop should stop looping. This is generally an expression featuring a comparison operator, a test to see if the exit condition has been met.
    - A final-expression — this is always evaluated (or run) each time the loop has gone through a full iteration. It usually serves to increment (or in some cases decrement) the counter variable, to bring it closer to the point where the condition is no longer true.

# While Loops:
- **Remember to add a final-expression (e,g. i++) because otherwise the loop will continue forever and break.
```
initializer
while (condition) {
  // code to run

  final-expression
}
```

# Do... While loop:
- The main difference between a do...while loop and a while loop is that the code inside a do...while loop **is always executed at least once.** So code in a while loop may never be executed
```
initializer
do {
  // code to run

  final-expression
} while (condition)
```

# Countdown Loop Example:
- https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Loops
```
const output = document.querySelector('.output');
output.textContent = "";

let i = 10;

while (i>=0) {
	const para = document.createElement('p');
	
	if (i === 10) {
		para.textContent = `Countdown ${i}`;
		
	} else {
		para.textContent = `${i}`;
	}

	output.appendChild(para);

	i--;
}
```

# Fillinf in Guest List Example
```

const people = ['Chris', 'Anne', 'Colin', 'Terri', 'Phil', 'Lola', 'Sam', 'Kay', 'Bruce'];

const admitted = document.querySelector('.admitted');
const refused = document.querySelector('.refused');

admitted.textContent = 'Admit: ';
refused.textContent = 'Refuse: ';

for (const person of people) {
  if (person === 'Phil' || person === 'Lola') {
    refused.textContent += `${person}, `;
  } else {
    admitted.textContent += `${person}, `;
  }
}

refused.textContent = refused.textContent.slice(0,refused.textContent.length-2) + '.';
admitted.textContent = admitted.textContent.slice(0,admitted.textContent.length-2) + '.';
```