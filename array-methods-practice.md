https://javascript.info/array-methods#transform-an-array

## Task 1: Translate border-left-width to borderLeftWidth
Write the function camelize(str) that changes dash-separated words like “my-short-string” into camel-cased “myShortString”.
That is: removes all dashes, each word after dash becomes uppercased.
### Examples:
```
    camelize("background-color") == 'backgroundColor';
    camelize("list-style-image") == 'listStyleImage';
    camelize("-webkit-transition") == 'WebkitTransition';
```
### Answer
```
function camelize(str) {
  return str
    .split('-') // splits 'my-long-word' into array ['my', 'long', 'word']
    .map(
      // capitalizes first letters of all array items except the first one
      // converts ['my', 'long', 'word'] into ['my', 'Long', 'Word']
      (word, index) => index == 0 ? word : word[0].toUpperCase() + word.slice(1)
    )
    .join(''); // joins ['my', 'Long', 'Word'] into 'myLongWord'
}
```
## Task 2: Filter a range
Write a function filterRange(arr, a, b) that gets an array arr, looks for elements with values higher or equal to a and lower or equal to b and return a result as an array.
The function should not modify the array. It should return the new array.
### Example:
```
    let arr = [5, 3, 8, 1];
    let filtered = filterRange(arr, 1, 4);
    alert( filtered ); // 3,1 (matching values)
    alert( arr ); // 5,3,8,1 (not modified)
```
### Answer
```
function filterRange(arr, a, b) {
  // added brackets around the expression for better readability
  return arr.filter(item => (a <= item && item <= b));
}

let arr = [5, 3, 8, 1];
let filtered = filterRange(arr, 1, 4);
alert( filtered ); // 3,1 (matching values)
alert( arr ); // 5,3,8,1 (not modified)
```
## Task 3: Filter range "in place"
Write a function filterRangeInPlace(arr, a, b) that gets an array arr and removes from it all values except those that are between a and b. The test is: a ≤ arr[i] ≤ b.
The function should only modify the array. It should not return anything.
### Example:
```
    let arr = [5, 3, 8, 1];
    filterRangeInPlace(arr, 1, 4); // removed the numbers except from 1 to 4
    alert( arr ); // [3, 1]
```
### Answer:
```
function filterRangeInPlace(arr, a, b) {
  for (let i = 0; i < arr.length; i++) {
    let val = arr[i];
    // remove if outside of the interval
    if (val < a || val > b) {
      arr.splice(i, 1);
      i--;
    }
  }
}

let arr = [5, 3, 8, 1];
filterRangeInPlace(arr, 1, 4); // removed the numbers except from 1 to 4
alert( arr ); // [3, 1]
```
## Task 4: Sort in decreasing order
### Example:
```
    let arr = [5, 2, 1, -10, 8];
    // ... your code to sort it in decreasing order
    alert( arr ); // 8, 5, 2, 1, -10
```
### Answer:
```
    let arr = [5, 2, 1, -10, 8];
    arr.sort((a, b) => b - a);
    alert( arr );
```
## Task 5: Copy and sort array
We have an array of strings arr. We’d like to have a sorted copy of it, but keep arr unmodified.
Create a function copySorted(arr) that returns such a copy.
### Examples:
```
    let arr = ["HTML", "JavaScript", "CSS"];
    let sorted = copySorted(arr);
    alert( sorted ); // CSS, HTML, JavaScript
    alert( arr ); // HTML, JavaScript, CSS (no changes)
```
### Answer:
```
function copySorted(arr) {
  return arr.slice().sort();
}
let arr = ["HTML", "JavaScript", "CSS"];
let sorted = copySorted(arr);
alert( sorted );
alert( arr );
```
## Task 6: Map to names
You have an array of user objects, each one has user.name. Write the code that converts it into an array of names.
### Examples:
```
    let john = { name: "John", age: 25 };
    let pete = { name: "Pete", age: 30 };
    let mary = { name: "Mary", age: 28 };
    let users = [ john, pete, mary ];
    let names = /* ... your code */
    alert( names ); // John, Pete, Mary
```
### Answer:
```
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 28 };
let users = [ john, pete, mary ];
let names = users.map(item => item.name);
alert( names ); // John, Pete, Mary
```
## Task 7: Map to Objects
You have an array of user objects, each one has name, surname and id.
Write the code to create another array from it, of objects with id and fullName, where fullName is generated from name and surname.
### Examples:
```
    let john = { name: "John", surname: "Smith", id: 1 };
    let pete = { name: "Pete", surname: "Hunt", id: 2 };
    let mary = { name: "Mary", surname: "Key", id: 3 };
    let users = [ john, pete, mary ];
    let usersMapped = /* ... your code ... */

    /*
    usersMapped = [
    { fullName: "John Smith", id: 1 },
    { fullName: "Pete Hunt", id: 2 },
    { fullName: "Mary Key", id: 3 }
    ]
    */

    alert( usersMapped[0].id ) // 1
    alert( usersMapped[0].fullName ) // John Smith
```
### Answer:
```
let john = { name: "John", surname: "Smith", id: 1 };
let pete = { name: "Pete", surname: "Hunt", id: 2 };
let mary = { name: "Mary", surname: "Key", id: 3 };

let users = [ john, pete, mary ];

let usersMapped = users.map(user => ({
  fullName: `${user.name} ${user.surname}`,
  id: user.id
}));

/*
usersMapped = [
  { fullName: "John Smith", id: 1 },
  { fullName: "Pete Hunt", id: 2 },
  { fullName: "Mary Key", id: 3 }
]
*/

alert( usersMapped[0].id ); // 1
alert( usersMapped[0].fullName ); // John Smith
```
## Task 8: Sort users by age
Write the function sortByAge(users) that gets an array of objects with the age property and sorts them by age.
### Examples:
```
    let john = { name: "John", age: 25 };
    let pete = { name: "Pete", age: 30 };
    let mary = { name: "Mary", age: 28 };

    let arr = [ pete, john, mary ];

    sortByAge(arr);

    // now: [john, mary, pete]
    alert(arr[0].name); // John
    alert(arr[1].name); // Mary
    alert(arr[2].name); // Pete
```
### Answer: 
```
function sortByAge(arr) {
  arr.sort((a, b) => a.age - b.age);
}

let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 28 };

let arr = [ pete, john, mary ];

sortByAge(arr);

// now sorted is: [john, mary, pete]
alert(arr[0].name); // John
alert(arr[1].name); // Mary
alert(arr[2].name); // Pete
```
## Task 9: Shuffle an array
Write the function shuffle(array) that shuffles (randomly reorders) elements of the array.
Multiple runs of shuffle may lead to different orders of elements.
### Example:
```
    let arr = [1, 2, 3];

    shuffle(arr);
    // arr = [3, 2, 1]

    shuffle(arr);
    // arr = [2, 1, 3]

    shuffle(arr);
    // arr = [3, 1, 2]
```
### Answer:
```
function shuffle(array) {
  for (let i = array.length - 1; i > 0; i--) {
    let j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
}

// counts of appearances for all possible permutations
let count = {
  '123': 0,
  '132': 0,
  '213': 0,
  '231': 0,
  '321': 0,
  '312': 0
};

for (let i = 0; i < 1000000; i++) {
  let array = [1, 2, 3];
  shuffle(array);
  count[array.join('')]++;
}

// show counts of all possible permutations
for (let key in count) {
  alert(`${key}: ${count[key]}`);
}

123: 166693
132: 166647
213: 166628
231: 167517
312: 166199
321: 166316
```
## Task 10: Get average age
Write the function getAverageAge(users) that gets an array of objects with property age and returns the average age.
The formula for the average is (age1 + age2 + ... + ageN) / N.
### Example:
```
    let john = { name: "John", age: 25 };
    let pete = { name: "Pete", age: 30 };
    let mary = { name: "Mary", age: 29 };

    let arr = [ john, pete, mary ];

    alert( getAverageAge(arr) ); // (25 + 30 + 29) / 3 = 28
```
### Answer:
```
function getAverageAge(users) {
  return users.reduce((prev, user) => prev + user.age, 0) / users.length;
}

let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 29 };

let arr = [ john, pete, mary ];

alert( getAverageAge(arr) ); // 28
```
## Task 11: Filter unique array members
Let arr be an array.
Create a function unique(arr) that should return an array with unique items of arr.
### Example:
```
    function unique(arr) {
        /* your code */
    }

    let strings = ["Hare", "Krishna", "Hare", "Krishna",
        "Krishna", "Krishna", "Hare", "Hare", ":-O"
    ];

    alert( unique(strings) ); // Hare, Krishna, :-O
```
### Answer:
```
function unique(arr) {
    let result = []

    for (let string of arr) {
        if (!result.includes(string)) {
            result.push(string);
        }
    }

    return result;
}
```
## Task 12: Create keyed object from array
Let’s say we received an array of users in the form {id:..., name:..., age:... }.
Create a function groupById(arr) that creates an object from it, with id as the key, and array items as values.
### Example
```
    let users = [
        {id: 'john', name: "John Smith", age: 20},
        {id: 'ann', name: "Ann Smith", age: 24},
        {id: 'pete', name: "Pete Peterson", age: 31},
    ];

    let usersById = groupById(users);

    /*
    // after the call we should have:

    usersById = {
        john: {id: 'john', name: "John Smith", age: 20},
        ann: {id: 'ann', name: "Ann Smith", age: 24},
        pete: {id: 'pete', name: "Pete Peterson", age: 31},
    }
    */
```
### Answer
```
function groupByID(users) {
    return users.reduce((obj, value) => {
        obj[value.id] = value;
        return obj;
    }, {})
}
```

