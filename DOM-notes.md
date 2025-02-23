# How to create Nodes in your script:
1) create a variable
2) add that element a class name
3) add styles or text or anything
4) append that element to what you want, e.g. the webpage container

```
const text = document.createElement('h3');
text.classList.add('thirdheading');
thirdheading.textContent = 'hi xyz';
thirdheading.style.color = 'red';
container.appendChild(thirdheading);
```

# Events:
- 3 primary ways to do this: **event listeners are the most common**
1) You can specify function attributes directly on your HTML elements. This clutters the html section which is undesirable.
- Also, we can only set one “onclick” property per DOM element, so we’re unable to run multiple separate functions in response to a click event using this method
```
<button onclick="alert('Hello World')">Click Me</button>
```
2) You can set properties in the form of on <eventType>, such as onclick or onmousedown, on the DOM nodes in your JavaScript.
- same issue with 1 about one property for onclick
```
// the JavaScript file
const btn = document.querySelector("#btn");
btn.onclick = () => alert("Hello World");
```
3) You can attach event listeners to the DOM nodes in your JavaScript.
```
// the JavaScript file
const btn = document.querySelector("#btn");
btn.addEventListener("click", () => {
  alert("Hello World");
});
```

# Get info about event itself:
- can use a callback function to get info about the event:
```
btn.addEventListener("click", function (e) {
  console.log(e);
});
```