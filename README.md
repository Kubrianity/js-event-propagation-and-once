# JavaScript30 #25: js-event-propagation-and-once
This is a JavaScript practice, one of the JavaScript30 challenges by Wes Bos. </br>
This practice shows how event propagation including event capture and bubbling and once parameter are handled in JavaScript.

### 1. Event Bubbling 
When an event occurs on an element nested within other elements, the event runs on the innermost element first and then all the way up to parent elements one by one. </br>
If we want to stop that behaviour and apply our event only on the inner target element, we should use the following method inside our listener function.
```
 function logText(e) {
    console.log(this.classList.value);
    e.stopPropagation()
} 
 divs.forEach(div => div.addEventListener('click', logText)
```
### 2. Event Capturing
Event capturing can be seen as the opposite of event bubbling. In event capturing, an event propagates from the parent/outer element to the inner/target element. In order to enable this feature, we should pass **capture** parameter inside addEventListener() and set its value to true. Note that capture is false by default.
```
  divs.forEach(div => div.addEventListener('click', logText, {
    capture: true,
  }));
```
So, both event capturing and event bubbling are two ways of event propagation.
### 3. Once
If we want to our listener be invoked only once, we should pass **once** parameter inside addEventListener() method and set its value to true so that the listener would be removed when invoked.
```
  divs.forEach(div => div.addEventListener('click', logText, {
    once: true
  }));
  ```
