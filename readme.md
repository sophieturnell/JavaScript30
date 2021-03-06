﻿![](https://javascript30.com/images/JS3-social-share.png)

# JavaScript30
A 30 day JavaScript challenge with no jQuery, no pre-processors and no frameworks.  

## Contents
[Day 1 - JavaScript Drum Kit](#day-1---javascript-drum-kit)  
[Day 2 - CSS & JS Clock](#day-2---css-&-js-clock)  
[Day 3 - Playing with CSS Variables & JS](#day-3---playing-with-css-variables-&-js)  
[Day 4 - Array Cardio Day 1](#day-4---array-cardio-day-1)  
[Day 5 - Flex Panels Image Gallery](#day-5---flex-panels-image-gallery)  
[Day 6 - Ajax Type Ahead](#day-6---ajax-type-ahead)
[Day 7 - Array Cardio Day 2](#day-7---array-cardio-day-2)
[Day 8 - Fun with HTML5 Canvas](#day-8---fun-with-html5-canvas)
[Day 9 - 14 Must Know Dev Tools Tricks](#day-9---14-must-know-dev-tools-tricks)
[Day 10 - Hold Shift to Check Multiple Checkboxes](#day-10---hold-shift-to-check-multiple-checkboxes)
[Day 11 - Custom HTML5 Video Player](#day-11---custom-html5-video-player)
[Day 12 - Key Sequence Detection (KONAMI CODE)](#day-12---key-sequence-detection---KONAMI-CODE)
[Day 13 - Slide in on Scroll](#day-13---slide-in-on-scroll)
[Day 14 - Object & Arrays - JS Reference VS Copy](#day-14---object-&-arrays---JS-reference-vs-copy)
[Day 15 - Local Storage & Event Delegation](#-day-15---local-storage-&-event-delegation)
[Day 16 - CSS Text Shadow Mouse Move Effect](#-day-16---CSS-text-shadow-mouse-move-effect)
[Day 17 - Sorting Band Names without Articles](#-day-17---sorting-band-names-without-articles)
[Day 18 - Tally String Times with Reduce](#-day-18---tally-string-times-with-reduce)
[Day 19 - Unreal Webcam Fun](#-day-19---unreal-webcam-fun)
[Day 20 - Native Speech Recognition](#-day-20---native-speech-recognition)
[Day 21 - Geolocation based Speedometer and Compass](#-day-21---geolocation-based-speedometer-and-compass)
[Day 22 - Follow Along Link Highlighter](#-day-22---follow-along-link-highlighter)
[Day 23 - Speech Synthesis](#-day-23---speech-synthesis)
[Day 24 - Sticky Nav](#-day-24---sticky-nav)
[Day 26 - Stripe Follow Along Dropdown - Stripe Part 2](#-day-26---stripe-follow-along-dropdown---stripe-part-2)
[Day 27 - Click and Drag to Scroll](#-day-27---click-and-drag-to-scroll)
[Day 28 - Video Speed Controller UI](#-day-28---video-speed-controller-UI)
[Day 29 - Countdown Timer](#-day-29---countdown-timer)



## Deployment
Use the "clone or download" button and open the relevant "Starter" HTML file in your browser.


## Technologies & Methodologies Used
- HTML5
- CSS3
- Vanilla JavaScript (ES6)
- Flexbox Layout Module


## Diary Notes

## Day 1 - JavaScript Drum Kit
I used the Document Object Model (DOM) event listeners to play audio file clips when each drum is hit. When the keys are pressed the buttons transition to grow larger and glow gold.

![](https://imgur.com/J2it9MT.jpeg)

Introduced the below:
- **`data-...` attributes** embed bespoke attributes on HTML elements. The stored (custom) data can then be used in the page's JavaScript to create a more engaging user experience (without any AJAX calls or server-side database queries).

- **`transitionend` events**  use in built `transitionend` (small 'e') and occur when a CSS transition has completed.

- **http://keycode.info/** for the number of each key.  

- **`<kbd>`** defines keyboard input.

---


## Day 2 - CSS & JS Clock
Takes the current time from JavaScript and updates the clock face hands as the time changes.

![](https://imgur.com/nfJdkqq.jpeg)

- Good practice rotating elements and using JavaScript dates rather than Moments.

- Introduced me to using the **`transition-timing-function:Cubic-bezier;`** demo in Chrome dev tools.

---


## Day 3 - Playing with CSS Variables & JS
CSS Variables allow you to update the entire app using one input point. This example includes image blur and colouring and resizing the width of the image border. 

![](https://imgur.com/jdWbd3N.jpeg)

- Introduced me to using CSS variables. Helpful as when using SASS, the preprocessor variable values become fixed values, whereas CSS allows you to change the value of variables throughout the lifecycle of your program.

- Practiced using `data-...` attributes and learnt that you can call all `data-...` attributes using **`this.datset`**.

1. Assign variables and default values to the root:

    ```css
    :root { /* Highest level - define default values for variables here */
      --base: #ffc600;
      --spacing: 10px;
      --blur: 10px;
    }
    ```

2. Add variables to styles:

    ```css
    img {
      padding: var(--spacing);
      background: var(--base);
      filter: blur(var(--blur));
    }
    ```
 
3. Access variables in JavaScript:

    ```javascript
     // SELECT ALL INPUTS ON PAGE
    const inputs = document.querySelectorAll('.controls input') //returns a node list (not an array) 

    function handleUpdate() {
      const suffix = this.dataset.sizing || '' //or nothing if there is no suffix e.g. px
      document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix) //updates the element with new style
    }

    // CREATES EVENT LISTENERS FOR EACH INPUT
    inputs.forEach(input => input.addEventListener('change', handleUpdate))
    inputs.forEach(input => input.addEventListener('mousemove', handleUpdate))
    ```
 
**NOTE**: In calling `.querySelector()` or `.querySelectorAll()` we receive a data structure that looks like an _Array_ but is actually a _Node List_. 
The _"listNode"_ object that we obtain (can be viewed in the console under _proto_) has a reduced API.  

To convert it to an array:
 
```javascript
const inputs = document.querySelectorAll('.controls input')
const inputsArr1 = Array.from(inputs)

//OR

const inputsArr2 = [...inputs]
```

---


## Day 4 - Array Cardio Day 1

An exercise focusing on array methods including **sort, filter, map, reduce, includes, split and Array.from**.


Console view:
![](https://imgur.com/AVAn33q.jpeg)


- I was introduced to **`console.table()`** that shows a table of the data returned.

- I added an age column to make it easier to check if my methods had been successful.

	```javascript
	inventors.forEach(obj => obj.age = obj.passed - obj.year)
	
	//OR
	
	inventors.forEach(obj => obj["age"] = obj.passed - obj.year)
	
	//OR
	
	inventors = inventor.map(p => ({ ...p, lifetime: p.passed - p.year })
	```

- I calculated a different answer for aggregate age in question 4. When I accumulate the ages mine seems correct. Am I misinterpreting the question?

- Questions 6 - 8 were more challenging.  

I found question 6 particularly helpful for familiarising myself with running code in the console. For this question I accessed the console at https://en.wikipedia.org/wiki/Category:Boulevards_in_Paris. I used the Chrome Dev Tools to find the div/class containing the list of names and selected it below.



Q.6 _Create a list of Boulevards in Paris that contain 'de' anywhere in the name  
  https://en.wikipedia.org/wiki/Category:Boulevards_in_Paris_

  1 - Inspect page and select dom elements. Boulevards are saved to the class `mw-category` so select this.

  ```javascript
  const category = document.querySelector('.mw-category')
  ```

  2 - Searches category list for a list of links (anchor tags).

  ```javascript
  const links = document.querySelectorAll('a')
  ```

  3 - Convert from Node List into an Array so you can map over each link and display the name (2 options below). Note that both happen from within the category.

  ```javascript
  const links = Array.from(category.querySelectorAll('a'))
    // OR - spread every item into the array (below)
  const links = [...category.querySelectorAll('a')]
  ```

  4 - Map through all of the links returning the link text for each element, then filter the Array to only display names containing "de".

  ```javascript
  const de = links
                .map(link => link.textContent)
                .filter(streetName => streetName.includes('de'))
  ```


  Refactored: 

  ```javascript
  const categoryLinks = Array.from(document.querySelectorAll('.mw-category a')) // Creates an array of anchor tags in the class in one step
    const de = categoryLinks
        .map(link => link.textContent)
        .filter(boulevardName => boulevardName.includes('de'))
  ```


I ran the below code by typing it directly into the browser console.

![](https://imgur.com/zMIot6S.jpeg)

---

## Day 5 - Flex Panels Image Gallery

An interactive image gallery using classess and transitions to update elements.

![](https://imgur.com/x4VuoPc.jpeg)

Here I used 2 events listeners:  
1. `click` to toggle the `.open` class, increasing the panel size and font size.
2. `transitionend` which runs once `.open` CSS transition has run if the event property includes `flex(-grow)`. We specifiy this as the key property we are waiting for before adding the text is the enlargement of the image panel. `transitionend` toggles `.open-active` and translates the text along the y axis into the page.

```javascript
    function toggleActive(e) {
      // console.log(e.propertyName) //shows "open" class properties
      if (e.propertyName.includes('flex')) {
        this.classList.toggle('open-active')
      }
    }
```
Ordinarily you can use `(e.propertyName === 'flex-grow')` for the if condition, but `.includes` is more explicit and helps with browser compatibility here.

Notes:
- **flex-grow**, **flex-shrink** and **flex-basis** e.g. `flex: 1 0 auto;`
- **CSS Selectors** e.g.`.panel > *:first-child` selects the first child element in the panel class. https://www.w3schools.com/cssref/css_selectors.asp
- **classLists** - toggling classes on and off https://www.w3schools.com/jsref/prop_element_classlist.asp
- **e.propertyName** - returns the CSS properties of an event.

---

## Day 6 - Ajax Type Ahead

A simple search bar using **Regular Expressions** to filter and return matching states and cities. 

![](https://imgur.com/pufmTP9.jpeg)

- Used fetch to return data from the endpoint.
- Used a Regular Expressions to match the word inputted to the data fetched.  Added variables to RegExp so that you can match whatever is input, rather than a set place. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions
- `change` only fires when you submit so listen for `keyup` event.
- Googled function for adding commas to the population number. Check how it works.

---

## Day 7 - Array Cardio Day 2

Covers **`some()`, `every()`, `find()`, `findIndex()`, `splice()`, and `slice()`,** including revision of Dates and `getFullYear()`.

![](https://imgur.com/PriPLat.jpeg)

- console.log({isAdult}) -  shows name of the variable and the value so - `isadult: true`, rather than just `true` in the console.
- Deleting an item from an array using splice and slice:

```javascript
comments.splice(findCommentIndex, 1) 
```

Splice ammends original array.  
findCommentIndex is the start point, 1 is the number of elements to remove from the start point, (a third value would represent what is to be inserted).

```javascript
const newComments = [
  ...comments.slice(0, findCommentIndex),
  ...comments.slice(findCommentIndex + 1)
]
```

Slice creates a new array - here called `newComments`.  
`0` is the starting point and the array is cut off before `findCommentIndex` for the first part of the array.  
`findCommentIndex + 1` is the start point for the rest of the array, no cut off value is given.  
This extracts the `findCommentIndex` from the array.  
The Spread Operator, `...`, extracts the nested elements to display them in the `newComments` array.  

- Look at how negative starting points work in splice and slice.

---

## Day 8 - Fun with HTML5 Canvas

Creates a paint-esk canvas that draws rainbow coloured lines in oscilating pen sizes.

![](https://imgur.com/vGJ7ibg.jpeg)

- A good introduction to canvas and context. All context attributes were new to me e.g. `linejoin`, `linecap`.
- Don't draw on the canvas directly, draw on the context which can be 2d or 3d (used for video games).
- I stuggled to get the Destructuring an Array syntax to work for some reason. Commented out on line 41.
- `mouseout` - mouse moves out of the screen.
- Select hue range from mothereffing hsl https://mothereffinghsl.com/
- Look at blend modes `ctx.globalCompositeOperation = 'multiply'` - the effect when you layer your drawing.

---

## Day 9 - 14 Must Know Dev Tools Tricks

Checking out console methods including **interpolating and styling `console.log`**, and using **console. `warn`, `error`, `info`, `assert`, `dir`, `clear`, `groupCollapsed`, `groupEnd`, `count`, `time` and `table`**.
All bar `console.log` and `console.table` were new to me so this was really insightful.

![](https://imgur.com/WQ77DWB.jpeg)

- To find where javascript of an element is in your code - select the element, then below option to takes you to the line of code causing that attribute.

![](https://imgur.com/ogrppHV.jpeg)

---

## Day 10 - Hold Shift to Check Multiple Checkboxes 

A checklist allowing you to select all items between 2 selected list items.

![](https://imgur.com/11AU3no.jpeg)

- When the first box is checked it is put into a variable.
- `e.shiftKey` checks if shift key has been pressed and `this.checked` that the lastChecked box is ticked.
- If this is the case I loop through all checkboxes looking for the initial box ticked, then tick all boxes unitl I reach the most recently ticked box.
- `inBetween` is set to true when inbetween last 2 list items and currentlly not ticked or `!inBetween` when ticked to start and we want to deselect.
- Work out how to prevent unticking a box, then selecting a box with shift, checking all boxes inbetween.

---

## Day 11 - Custom HTML5 Video Player

Building video interface. My first time using video `paused`, `currentTime`, `duration`, `timeupdate` similar to `progress`. Revised `e.offsetX`and used flag variables.

![](https://imgur.com/lx1Llfl.jpeg)

Key learnings:
- `paused` is a property on video (there is not a playing property).
- Revision of `data-...` called by `this.dataset` from lesson on day 3.
- Creating flag variables:

```javascript
// SCRUB - CLICK TO POSITION TO PLAY FROM
function scrub(e) {
  console.log(e)
  const scrubTime = (e.offsetX / progress.offsetWidth) * video.duration 
  // (point clicked/bar width - to give %) * length of video
  video.currentTime = scrubTime // updates the time of video showing
}

// CREATE A FLAG VARIABLE
// Set it to false, then when you click it becomes true
let mousedown = false
progress.addEventListener('click', scrub)
progress.addEventListener('mousemove', (e) => mousedown && scrub(e)) // ALLOWS CLICK & DRAG OF PROGRESS BAR
// checks mousedown variable and if true runs scrub (works like an inline if statment). If mousedown is false, line will return false.
// requires e - data from event to be passed in so we know the location of the mousemove.
progress.addEventListener('mousedown', () => mousedown = true)
progress.addEventListener('mouseup', () => mousedown = false)
```

- Added Full Screen toggle button.
- Other ideas to extend here: https://freshman.tech/custom-html5-video/ 

---

## Day 12 - Key Sequence Detection - KONAMI CODE

The secret handshake of the internet!
https://www.howtogeek.com/659611/what-is-the-konami-code-and-how-do-you-use-it/
App displays unicorns and rainbows when secretCode is input using https://www.cornify.com/

![](https://imgur.com/9tbOAVW.jpeg)

- Helped understand negative splice arguments in array methods.

---

## Day 13 - Slide in on Scroll

Animating images to slide into an app when you scroll the page.

![](https://imgur.com/9kf54Rb.jpeg)

Key learnings:
- **Debounce** functions to aid performance. Can find in Lodash JS library.
- Window methods `scrollY` and `innerHeight` and formatting using `offsetTop`.
- I initially confused changing the positioning of image, with the timing of the image sliding in but resolved this quickly using the Chrome Dev Tools.
- Revised `classList.add` and `classList.remove`.

---

## Day 14 - Object & Arrays - JS Reference VS Copy

Focus on the difference between reference and copy with primitive tyoes, arrays and objects. These are especially important when it comes to nested data.

![](https://imgur.com/UnPW0z0.jpeg)

- Refreshed: `slice()`, `concat()`, spread operator and `Array.from()`.
- New: `Object.assign()` and using deep cloning to access anything deeper than one level. https://lodash.com/docs/#cloneDeep
- Spend some time looking at Lodash library.

---

## Day 15 - Local Storage & Event Delegation

**Persisting state with local storage** and **Event Delegation** (adding an event listener on something that doesn't exist).

![](https://imgur.com/DjaVKY3.jpeg)

Key Learnings:
- Listen for `submit` event when a button is clicked or enter pressed rather than a `click` event.
- Use settings cog symbol in the console to select "preserve log". This shows logs previous to refreshing the page.
- Shows "Navigated to:" which shows our page is refereshing. Use `e.preventDefault` to stop reloading. By default submitting form sends the data to an external source (server side) and reloads but here we do all work on the client side (locally).
- `data-index`, `id` and `for` link the items.
- Can't write `checked=false` as any existence of the attribute "checked" will make it display as checked.
- CSS lines 58 to 70 add emoji to checkboxes when selected.

**Local Storage**
- Object in browser called `localStorage` able to save text to the browser. Dev Tools > Application > Local Storage > file://
- localStorage methods for making data persistent when refreshing the browser: 
    `localStorage.getItem(key)`
    `localStorage.setItem(key, value)`
    `localStorage.removeItem(key)`
- Can only save strings to local storage. Use `JSON.stringify()` to convert value to a string (may look like an array in Application, but actually a string).
- On page load, convert string back to array of objects using `JSON.parse()`.

**Event Delegation**
-  When an event happens on the "responsible" parent, this is passed on to the children (which may or may not exist yet).
- `e.target` revision

---

## Day 16 - CSS Text Shadow Mouse Move Effect

Using offset to help find the cursor and move the shadows depending on the location.

![](https://imgur.com/lcSbzlf.jpeg)

- `contenteditable` Allows content to be edited. If not used as an attribute, content will be inherited from the parent. https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Editable_content
- Deconstructing:
```javascript
    const width = hero.offsetWidth
    const height = hero.offsetHeight
    const { offsetWidth: width, offsetHeight: height } = hero // Above 2 lines in 1 
```
- Revision of `offsetWidth`, `offsetHeight`, `offsetX`, `offsetY`
- **textShadow** `object.style.textShadow = "none|h-shadow v-shadow blur color|initial|inherit"` https://www.w3schools.com/jsref/prop_style_textshadow.asp

---

## Day 17 - Sorting Band Names without Articles

Sorts an array of bands alphabetically, ignoring "The", "A" or "An" at the start.

![](https://imgur.com/xaZDy1u.jpeg)

- Practice using `sort()`, `replace()`, `trim()` removes whitespace either side of a string.
- I'm quite new to Regular Expressions but these look really useful, try to work with these more. `^` - starts with, `|` or, `i` insensitive (upper or lower case). Stripping a word of "a ", "the " and "an " below.
```javascript
function strip(bandName) {
        return bandName.replace(/^(a |the |an )/i, '').trim()
    }
```
- Mapping an array to create a list of strings.

```javascript
const sortedBands = bands.sort((a, b) => strip(a) > strip(b) ? 1 : -1)

document.querySelector('#bands').innerHTML = sortedBands.map(band => `<li>${band}</li>`).join('')
```

## Day 18 - Tally String Times with Reduce

Calculating the aggregate time needed for all videos to play.

![](https://imgur.com/3azGN3I.jpeg)

- Remember `data-time` is an attribute so selected like this `[data-time]`.
- **ES6 destructuring** - this wasn't showing in my browser so spent a long time thinking about this, trying to work out why this wouldn't work in Chrome and  how to access the values without using the destructor etc. In the end I realised my `console.log` was in the wrong place. It should have been inside the brackets.
- Good practise converting dataTypes, accessing nested values using `map` and `reduce`.

---

## Day 19 - Unreal Webcam Fun

![](https://imgur.com/GEzyq5p.jpeg)

## Deployment
- Requires a secure origin to access camera (https or local host). Run server using Node: `npm install`, `npm start`.
- `"browser-sync": "^2.12.5 <2.23.2"` - allows you to open website and start a server with live reloading. Local server = 3001

- New learnings `srcObject`,`ctx.drawImage()`, `ctx.getImageData()`, `ctx.putImageData()`, `toDataURL`, `insertBefore()`
- Revision of promises, `createElement()`, `setAttribute()`, `innerHTML` vs. `textContent` and `forEach()`

- First time accessing the camera. Used `navigator.mediaDevices.getUserMedia({ video: true, audio: false })`to return the promise.
- `canplay` fired when the user agent can play the media, but estimates that not enough data has been loaded to play the media up to its end without having to stop for further buffering of content.
- Base64 - text representation containing all the attributes of an image.
- `debugger` is a keyword stops the execution of JavaScript, and calls (if available) the debugging function. This has the same function as setting a breakpoint in the debugger. Used here to pause the code so we can dig into the pixel ImageData in the console. `ImageData.data` is contains arrays of rgba colour codes: 
0: 135 - red
1: 124 - green
2: 111 - blue
3: 255 - alpha
4: 112 - red...
For every pixel in image, there are 4 elements in the array.

## Day 20 - Native Speech Recognition

- Creating list using the microphone only. Siri style!

![](https://imgur.com/VY4CDKV.jpeg)

## Deployment
- Requires a secure origin to access microphone (https or local host). Run server using Node: `npm install`, `npm start`. Then click the "index-START" file in the browser. Make sure other tabs using the microphone are closed if not working.

First time using speech recognition and some good practise retrieving nested data. 
https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API
https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition

New learnings:
- `SpeechRecognition` is a global variable that lives in the browser on top of the window.
- `interimResults`
- Event data contains transcript and confidence rating as %.
- Event listeners `result` and `end`.
- `e.results[0].isFinal` boolean which tells you if the user stopped talking to start in a new paragraph.

---

## Day 21 - Geolocation based Speedometer and Compass

![](https://imgur.com/fgQG9iA.jpeg)

- Uses co-ordinates, heading and speed.
- Heading is direction - how many degrees north you are facing.
- Can fake co-ordinates but not heading or speed.

- Good instructions of how to pass warning messages when opening.

- Use iOS simulator in xCode. xCode > Open Developer Tools > Simulator.

- STILL STRUGGLING WITH xCode - my first time using and the menus seem to be different from the versions when I google.
- Debug menu no longer has a Location option - haven't found the new way to change this yet.

- `navigator.geolocation.watchPosition()` - gives position changing over time.
- `navigator.geolocation.getCurrentPosition()` - gives position once`
- accuracy given in number of meters
- heading - direction in degrees relative to north
- speed in kph

- **Success Callback** when user allows something, the callback will run.

---

## Day 22 - Follow Along Link Highlighter - Stripe Part 1

Build a link higlighter which will transtition from one link to another with a smooth effect by adding a class to the link. Part 1 of building a replica of the navigation bar from Stripe.

![](https://imgur.com/4qwNDu9.jpeg)

New Learnings:
- Differences between `mouseover`, `mouseenter` and `onmousemove`:
  - The `mouseover` event triggers when the mouse pointer enters the div element, and its child elements.
  - The `mouseenter` event is only triggered when the mouse pointer enters the div element.
  - The `onmousemove` event triggers every time the mouse pointer is moved over the div element.

- `getBoundingClientRect()` method returns the size of an element and its position relative to the viewport.
The element's size is equal to its width/height + padding in the case that the standard box model is being used, or width/height only if `box-sizing: border-box` has been set on it. https://developer.mozilla.org/en-US/docs/Web/API/Element/getBoundingClientRect

---

## Day 23 - Speech Synthesis

Playing typed text.

![](https://imgur.com/eLNIdck.jpeg)

- `SpeechSynthesisUtterance()` used when one person speaking. https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance
-  speechSynthesis is a global variable that can be used to retrieve information about the synthesis voices, start, pause speech etc. e.g. `speechSynthesis.speak(msg)` which plays the msg. https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis
- Event listener `voiceschanged`
- `speechSynthesis.getVoices()` returns Mac's inbuilt array of different voices.
- Emojis spoken in native language, text in English.
- Passing and argument to a function through an event listener.
Both create another function:

```javascript
  stopButton.addEventListener('click', () => toggle(false))
  stopButton.addEventListener('click', toggle.bind(null, false))
```

## Day 24 - Sticky Nav

Fixing a navigation bar to the top of the scrolled screen. Shows logo and body grows when nav at top of page. Useful for slideovers.

![](https://imgur.com/reUwL0X.jpeg)

- Revision of `offsetTop`, `offsetHeight`, `window.scrollY`, `classList`,
- Add classlist to the body to make it more accessible.
- WHen you make an element fixed - it no longer takes up space in the document so content jumps up the page. Add pixels to the body to solve.
- Cannot animate from 0 to auto. Use max width here for the logo.
- Practice using classes to make transitions in CSS. 

---

## Day 25 - Event Capture, Propagation, Bubbling & Once

Event bubbling and capturing are two ways of event propagation in the HTML DOM API.

When an event is fired on an element that has parent elements, modern browsers run these two different phases — the **capturing** phase and the **bubbling** phase.

![](https://imgur.com/4JJzjWg.jpeg)

- **Bubbilng** - When an event happens on an element, it first runs the handlers on the element, then on its parent, then all the way up on other ancestors. The process is called “bubbling”, because events “bubble” from the inner element up through parents like a bubble in the water. Bubbling is the default.

- **event.target** - The most deeply nested element that caused the event is called a target element, accessible as event.target.

- **Capture** - the event is first captured by the outermost element and propagated to the inner elements, from the top down, (ancestors to child).
- **Bubbles** - the event is first captured and handled by the innermost element and then propagated to outer elements, from the bottom up (child to ancestors).

- `{capture: true}` below - runs the funtion on the way down, rather than on the way back up. By deefaul this is false.

```javascript
divs.forEach(div => div.addEventListener('click', logText, {capture: true}))
```

- **Stop Propagation** - Stops bubbling up (I clicked the exact element I required)
- **Once** - `{once: true}` - listens for a click and then unbinds itself, so will only run once. Useful in shop checkouts where you only want data to be submitted once. (same as `removeEventListener`).

---

## Day 26 - Stripe Follow Along Dropdown - Stripe Part 2

Transforming one dropdown box in the navigation bar to be used for all nav dropdowns. This time the background element is a child of the navigation element rather than the body (in day 24) which affects the way we calculate the coordinates of the background.

![](https://imgur.com/Wf1LMYs.jpeg)

- Hover parent `<li>`
- `.cool > li` all direct <li> descendents of cool class.
- When entering into a **named functions** the value of `this` changes, when entering into an **arrow function** this is inherited from the parents.

---

## Day 27 - Click and Drag to Scroll

Horiztonally scrolling divs.

![](https://imgur.com/pkVd3Mz.jpeg)

- `e.pageX` - finding the location on page excluding margin (x co-ordinates)
- `scrollLeft` practice.

---

## Day 28 - Video Speed Controller UI

Changing the playback rate of a video using a controller.

![](https://imgur.com/HrKw0uT.jpeg)

- Similar to the fundraising bar exercise but good practice with finding the location on the page.

---

## Day 29 - Countdown Timer

Creating a countdown timer with preset buttons and a "Enter minutes" field.

![](https://imgur.com/EndJAHI.jpeg)

- This activity is one of the more substatial tasks.

- Running order:
  - The event listeners detect a click or submit event.
  - The `startTimerButton` or `startTimerInput` function is run.
  - `startTimerButton` parses the minutes (string) entered from the dataset attribute and passes this to the `timer` function. (`startTimerInput` also runs the `timer` function).
  - The `timer` function:
    - Clears any previously running timers.
    - Finds the start and finish time .
    - Runs the `displayTimeLeft` and `displayEndTime` functions which calculate the times a display them in the correct format.
    - Sets the intervals to refresh the time.
  
Notes:
- Good refresher on time. `setInterval()`, `clearInterval()`, `data-...` called with `this.dataset`.
- `setInterval()` doesn't run immediately, (runs after first second) so run `displayTimeLeft` on line 14 before the interval timer starts running.
- `new Date()` converts to current date "timestamp".
- Put this into a variable(e.g. `x`) to call `x.getDate()`, `x.getDay()`, `x.getMonth()`.
- `Date.now()` new syntax to give current time (returns number of milliseconds since Jan 1st 1970).

- This will pause when you scroll in some browsers so use the code in the solution instead.

```JavaScript
function timer(seconds) {
  setInterval(function() { // Pauses when you scroll
    seconds --
  }, 1000)
}
```

- If there is an attribute of `name="..."` on a div, it can be called using the value of name only as below.

![](https://imgur.com/BkTaeYX.jpeg)

This works for nested values too. You can select the input like this: `document.customform.minutes`
```JavaScript
<form name="customForm" id="custom">
        <input type="text" name="minutes" placeholder="Enter Minutes">
      </form>
```

- Changing title of browser tab using `document.title`.

---

## Day 30 - Whack A Mole Game

![](https://imgur.com/5MWDR4Q.jpeg)

- Revision of `Math.random()`, `Math.floor()`, `Math.round`, `setInterval()`,`setTimeout()`
- `isTrusted` lives inside the event attributes. The click event can be simulated but if it is this will show as `isTrusted: false`, a true click will show `isTrusted: true`.

- Further improvements: high score board, expert levels (reduced time), 