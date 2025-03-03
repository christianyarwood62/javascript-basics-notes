# Objects
- e.g.:
``` 
let user = {
  name: "John",
  age: 30,
}
```
- 2 properties:
    - a key (name or identifier) before a colon then a value to the right of it
- you can add more values with putting a new key with a dot equalling a value
- can also remove with ```delete object.key```
- you can have multi word property keys, but they have to be quoted
- last property may end with a comma. This is called a 'trailing' or 'hanging' comma. Makes it easier to add/remove/move around properties because all lines are alike
- to access multiword properties, cant use dot notation, have to use square brackets, e.g.:
```
user['likes birds] = true;
```

## Computed properties:
- can use square brackets in an object literal when creating an object:
```
let fruit = prompt("Which fruit to buy?", "apple");

let bag = {
  [fruit]: 5, // the name of the property is taken from the variable fruit
};

alert( bag.apple ); // 5 if fruit="apple"
```
**Best practice - when property names are known and simple, dot notation is used. And if we need something more complec, we use square brackets**

## Property Value Shorthand:
- in real code, often to use existing variables as values for property names, e.g. name: name or age: age
    - but you can simply use a special ***property value shorthand***:
    ```
    function makeUser(name, age) {
        return {
            name, // same as name: name
            age,  // same as age: age
            // ...
        };
    }
    ```

## Property names limitations:
- there are none!
- variables cant use language reserved words like for, let, return, etc., but object properties can!
- numbers are converted to string. e.g.
```
let obj = {
  0: "test" // same as "0": "test"
};
```
- only exception if _proto_. We cant se this to a non object value

## Property existance test. 'in' operator
- it is possible to access any property in javascript. It will return undefined for a non-existing property
- special operator 'in' will return boolean if it exists or not:
```
let user = { name: "John", age: 30 };

alert( "age" in user ); // true, user.age exists
alert( "blabla" in user ); // false, user.blabla doesn't exist
```
    - **note that the property name is usually a quoted string

## For... in loop
- to loop over all keys of an object
```
for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // values for the keys
  alert( user[key] ); // John, 30, true
}
```

## Ordered like an object
- integer proeprties are sorted other appear in creation order, e.g. (USA is returned first because it has 1):
```
let codes = {
  "49": "Germany",
  "41": "Switzerland",
  "44": "Great Britain",
  // ..,
  "1": "USA"
};

for (let code in codes) {
  alert(code); // 1, 41, 44, 49
}
```
- **Note - integer properties are strings that can be converted between int and string without a change**

## object basics:
- you can also write functions into objects:
from: 
```
const person = {
  name: ["Bob", "Smith"],
  age: 32,
  bio: function () {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  introduceSelf: function () {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};
```
to:
```
const person = {
  name: ["Bob", "Smith"],
  age: 32,
  bio() {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  introduceSelf() {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};
```
- objects like this are referred to as object literals, different to objects instantiated from classes.

## What is 'this'
e.g. 
```
introduceSelf() {
  console.log(`Hi! I'm ${this.name[0]}.`);
}
```
- 'this' keyword refers to current object the code is being executed on


## Introducing constructors
- **constructors start with a capital letter and are named for the type of object they create**
- long winded to create multiple objects that look similar, e.g.:
```
const person1 = {
  name: "Chris",
  introduceSelf() {
    console.log(`Hi! I'm ${this.name}.`);
  },
};

const person2 = {
  name: "Deepti",
  introduceSelf() {
    console.log(`Hi! I'm ${this.name}.`);
  },
};
```
- we could write a function but **its easier to use constructors**,
    - function: 
    ```
    function createPerson(name) {
        const obj = {};
        obj.name = name;
        obj.introduceSelf = function () {
            console.log(`Hi! I'm ${this.name}.`);
        };
        return obj;
    }
    ```
    - **using constructors**:
    ```
    function Person(name) {
        this.name = name;
        this.introduceSelf = function () {
            console.log(`Hi! I'm ${this.name}.`);
        };
    }
    ```
    - to call Person() as a constructor, we use ***new***:
    ```
    const salva = new Person("Salva");
    salva.introduceSelf();
    // "Hi! I'm Salva."
    ```

## Map method:
- expects a callback function
- automatically iterates over an array so we dont have to use a for loop. e.g.:
```
function addOne(num) {
  return num + 1;
}
const arr = [1, 2, 3, 4, 5];
const mappedArr = arr.map(addOne);
console.log(mappedArr); // Outputs [2, 3, 4, 5, 6]
```

## Filter method:
- somewhat similar to map, as it still iterates through an array and applies a callback function, however instead of transforming the values in the array, it returns original values of the array, but ONLY IF the callback function returns true
```
function isOdd(num) {
  return num % 2 !== 0;
}
const arr = [1, 2, 3, 4, 5];
const oddNums = arr.filter(isOdd);
console.log(oddNums); // Outputs [1, 3, 5];
console.log(arr); // Outputs [1, 2, 3, 4, 5], original array is not affected
```

## Reduce method
- still iterates through an array
- still expects a callfunction, but takes 2 arguments instead of 1
- first argument is the accumulator
    - the current value of the result at that point in the loop
    - if no initialValue is set, then it will take the first value of the array
- second argument is the initialValue


## Splice Method:
- the delete method on an array will delete a key in an object but not the value so if you return the length of the new array, it will stay the same.
- you can use splice to delete element and shift to the freed place
- syntax is:
```
arr.splice(start[, deleteCount, elem1, ..., elemN])
```
- read this as "modify arr starting from start: and removes deleteCount number of elements and insers elem1,... elemN in their place. Returns the array of removed elements" e.g.:
```
let arr = ["I", "study", "JavaScript", "right", "now"];

// remove 3 first elements and replace them with another
arr.splice(0, 3, "Let's", "dance");

alert( arr ) // now ["Let's", "dance", "right", "now"]
```
- splice method also works with negative numbers if we set deleteCount to 0
- also allows for negative indexes

## Slice method:
- Syntax:
```
arr.slice([start], [end])
```
- copies an item at start and moves it to end
- can also copy arr if you call no arguments
- no second argument moves it to the end

## Concat:
- creates a new array that includes values from other arrays and additional items
```
arr.concat(arg1, arg2...)
```
- Normally, it only copies elements from arrays. Other objects, even if they look like arrays, are added as a whole:
    - …But if an array-like object has a special Symbol.isConcatSpreadable property, then it’s treated as an array by concat: its elements are added instead: 
    ```
    let arr = [1, 2];

    let arrayLike = {
        0: "something",
        1: "else",
        [Symbol.isConcatSpreadable]: true,
        length: 2
    };

    alert( arr.concat(arrayLike) ); // 1,2,something,else
    ```

## Iterate: forEach:
- allows to run a function for every element of an array
- syntax:
```
arr.forEach(function(item, index, array) {
  // ... do something with an item
});
```
- any returns are thrown away and ignored

## Searching in an array:
### indexOf/lastIndexOf and includes
- arr.indexOf(item, from) - looks for item starting from index from and returns index where it was found, otherwise -1.
- arr.includes(item, from) - looks for item from index from, and returns true if found
- **Usually these methods are used with one argument and starting from beginning as default
- **indexOf uses strict equality ===
- lastIndexOf is the same as indexOf but looks from right to left and returns first instance if it repeats (same nature as indexOf)
- **includes method handles NaN correctly, unlike indexOf**
    ```
    let fruits = ['Apple', 'Orange', 'Apple']

    alert( fruits.indexOf('Apple') ); // 0 (first Apple)
    alert( fruits.lastIndexOf('Apple') ); // 2 (last Apple)
    ```
### find and findIndex/findLastIndex
- syntax:
```
let result = arr.find(function(item, index, array) {
  // if true is returned, item is returned and iteration is stopped
  // for falsy scenario returns undefined
});
```
e.g.: (typical to find the function with one argument, other arguments typically not used)
```
let users = [
  {id: 1, name: "John"},
  {id: 2, name: "Pete"},
  {id: 3, name: "Mary"}
];

let user = users.find(item => item.id == 1);

alert(user.name); // John
```

- arr.findIndex has same syntac but returns index where element was found instead of element itself. value of -1 is return is nothing found.
    - arr.findLastIndex works from right to left

### filter
- find method looks for the first instance of an element and returns true
- arr.filter(fn) returns an array of all matching elements
- syntax:
```
let results = arr.filter(function(item, index, array) {
  // if true item is pushed to results and the iteration continues
  // returns empty array if nothing found
});
```

## Transform an array
Methods that transform and reorder arrays

### map
- arr.map is **extremely and often** used
- syntax: 
```
let result = arr.map(function(item, index, array) {
  // returns the new value instead of item
});
```

### sort(fn)
- sorts the array ***in place*** changing its element order
- **items are sorted as strings by default** so sorting numbers with sort with no function wouldnt work. we have to write a compare function, e.g.:
```
function compareNumeric(a, b) {
  if (a > b) return 1;
  if (a == b) return 0;
  if (a < b) return -1;
}

let arr = [ 1, 2, 15 ];

arr.sort(compareNumeric);

alert(arr);  // 1, 2, 15
```
- sort(fn) runs a generic sorting algorithm so we dont care the a and b it compares. So basically give 2 arguments (a and b) in the function to allow it to compare.
- but an array can have strings and numbers, so we need an ***ordering function*** to know how to compare elements as default is string order.
- you can use a comparison function to return a positive number to say "greater" and a negative number to say "less" (and also use an arrow function):
```
arr.sort( (a, b) => a - b );
```

- better to use str.localeCompare method to sort letter because it compares other language letters

### reverse
- arr.reverse() reverse order of array

### split and join
- str.split(delim)
- put the delim in quotes and it splits it by that deliminater
- **rarely used** - also has second argument str.split(delim, limit). This limits how many of the first elements it splits
- putting an empty delim would split stringh into array of letters
- str.join(glue) - would join an array with specified glue

### reduce/reduceRight
- when we need to iterate through an array, we can use forEach, for, or fot...of loops
- when we need to iterate through and return data for each element, we can use map
- reduce and reduceRight are used to calculate a single value based on the array
- syntax: 
```
let value = arr.reduce(function(accumulator, item, index, array) {
  // ...
}, [initial]);
```
- arguments:
    - accumulator is the result of the previous function call, equals initial the first time
    - item is the current array item
    - index is its position
    - array is the array
- as the fn is applies, the result of the previous fn call is passed to the next one as the first argument
- if no initial value is given then the first element is given as initial value. however **caution** if the array is empty then if there is no initial value given it will return error

## Array.isArray
- typeof for arrays and objects both return object
- however can use Array.isArray()

## Most methods support "thisArg"
- almost all array methods that call functions (find, filter, map, etc.) accept an optinal additional parameter thisArg

