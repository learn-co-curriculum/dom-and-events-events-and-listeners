# Events and listening to DOM nodes

## Objectives

1. Add an event listener to a DOM node
2. Accessing the event object
3. Altering HTML after events occur

## Bringing it together

So far we've seen that we can easily manipulate nodes in the DOM, and even create and remove elements (we are using the words DOM nodes and elements interchangeably) at will. But what triggers these changes?  How do real websites change elements?  Well, their code listens for events, and then alters the HTML accordingly.

Events occur inside a browser window and are attached to the DOM element from where the event originated.  For example, we can say that a user clicked on the paragraph.  The clicking would be an event.  This is another one of those concepts that comes through practice, so let's dive in.

## Listening for events

There are lots of events that we can listen for in the browser.  Really every movement of the mouse or keyboard is an event.  So to take action upon a specific event, like a mouse click occurring we first need to tell JavaScript to listen for it by adding an event listener.   

Adding an event listener to a DOM node is easy — we just call `addEventListener()` on the node. `addEventListener()` takes two arguments: the name of the event, and a function to handle the event.

Let's start by adding a listener for `click` events to the `main#main` element in `index.html`. Once you've opened `index.html` in the browser, enter the following in the browser's JS console:

```js
const main = document.getElementById('main')

main.addEventListener('click', function(event) {
  alert('I was clicked!')
})
```

Now if you click on the `main` element (you can click its text, "My ID is 'main'!"), you should see an alert: `'I was clicked!'`. What's going on here?

Well when you typed in the above code, you added an event listener to listen for a click event from anywhere in the `main` element.  You did this by calling the `addEventListener` on the `main` element.  Then you passed the `'click'` as the first argument to this method to specify the name of the event we're listening for.  

The second argument is a callback function that specifies what to do upon the event occurring. In this case, when the callback function is called it calls an alert.   

### Accessing the event object

Let's change the code in the callback function.  You can refresh the page to clear our the previous event listener you added through the console.  Then add in the following code.  

```js
const main = document.getElementById('main')

main.addEventListener('click', function(event) {
  console.log(event)
})

```

When you click, you will see the following:

```js
MouseEvent {isTrusted: true, screenX: 358, screenY: 233, clientX: 358, clientY: 112, …}
```

Pretty cool, eh?  Our callback function is now saying to log the event that occurs.  When we click, we see the event show up in the console.  You can take a look at all of the attributes that we have access to for each event.  An  event has a number of useful properties on it.

Let's take a look at another event, the `keydown` event.  For example, the keypress, keydown, and keyup events have a `which` property that tells us which key was pressed. Let's add an event listener to the `input` element to get a feel for this.

```js
const input = document.querySelector('input')

input.addEventListener('keydown', function(e) {
  console.log(e.which)
})
```

You'll notice that, for example, pressing "enter" prints `13` in console; pressing "a" prints `65`; etc.

### Combining Event Listeners With Altering HTML

Ok, now that we have seen how to listen to specific events on specific elements.  Let's make our webpage move.  For now, we'll simply change the `visibility` attribute.  So when we click on the `main` element, we can show and hide the `h1` saying "Ada Lovelace".  Here we go.  

```js
const main = document.getElementById('main')
const ada = document.querySelector('h1')

main.addEventListener('click', function(event) {
  if(ada.style.visibility === "hidden"){
    ada.style.visibility = "visible"
  } else {
    ada.style.visibility = "hidden"
  }
})
```

Ah yes, that never gets old.  Notice that our `h1` only shows or hides if you click inside the `main` element.  Click outside of it, and it's almost as if our code wasn't listening to that event at all (it wasn't).    

### Summary

In this lesson we learned that we can trigger manipulations of our DOM through events that occur in the browser.  We saw how we can listen for specific events by using the `addEventListener` method.  Then we saw how we can manipulate our DOM by passing a callback function to take action upon a specific event.  Finally, we saw how we can access the `event` object through the argument passed to our callback function.  We put these lessons together with the last piece of code.   


## Resources

- [MDN - Web Events](https://developer.mozilla.org/en-US/docs/Web/Events)
- [QuirksMode - Event order](http://www.quirksmode.org/js/events_order.html)

<p class='util--hide'>View <a href='https://learn.co/lessons/events-and-eventListeners'>Listening To Nodes</a> on Learn.co and start learning to code for free.</p>
