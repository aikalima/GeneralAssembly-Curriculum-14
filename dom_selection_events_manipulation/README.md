#DOM Events in JavaScript

In order to make web pages more interactive, events are necessary to trigger actions on certain elements. A button click, mouse over, and tap are examples.

##Learning Objectives

- Apply proper principles to select DOM elements using JavaScript.
- Demonstrate ability to bind events to single and multiple DOM elements.
- Illustrate handling of events in static and dynamic documents.

##Selecting Elements

- In order to bind events to DOM elements, you need to select the elements first.
- The most common specific JS selector is `getElementById`.

`document.getElementById("myDiv")`

`<div id="myDiv"></div>`

- You can also search via a class name.

`document.getElementsByClassName("myDivs")`

`<div class="myDivs"></div>`

- You can search via tag name. This is very unspecific.

`document.getElementsByTagName("div")`

- You can use CSS selectors just like you would in a stylesheet to select elements.

`document.querySelector("div#myDiv")`

`document.querySelectorAll("div.myDivs")`

##Attaching Events

- Common Events:
	- change
	- click
	- mouseover
	- mouseout
	- keydown
	- keyup

#####"Shortcut" Method

```
document.getElementById("myDiv").onchange = function() { };

document.getElementById("myDiv").onclick = function() { };

document.getElementById("myDiv").onmouseover = function() { };
```

#####addEventListener

```
document.getElementById("myDiv").addEventListener("click", function() {
	//Your code here
}
```

- Events can only be attached to specific elements. Therefore, when you return a collection such as the result of `document.querySelectorAll` you CANNOT simply do this:

```
document.querySelectorAll(".paragraph").addEventListener("click", function() {
	alert("Click worked");
}
```

- We would need to loop through each element returned and attach a click handler:

```
var paragraphs = document.querySelectorAll(".paragraph");

for (var i = 0; i < paragraphs.length; i++) {
	paragraphs[i].addEventListener("click", function() {
		alert("Click worked");
	}
}
```

##Exercise 1

- Review the fiels in the ex_1 folder.
- Create your own app.js file and link it to the document using the `script` tag.
- Attach a click event to each paragraph, with an alert that pops up when clicked.
- Attach the same click handler to the entire nav. Hint: Use `getElementsByTagName`.
- Create a click handler for each footer link, and hijack the default action to make it show an alert rather than Google.com.

##DOM Manipulation with JavaScript

#####innerHTML Property

`innerHTML` can be a "getter" and a "setter":

`console.log(document.getElementById("footer").innerHTML);`

`document.getElementById("footer").innerHTML = "This is my new HTML";`

#####HTML Attributes

Shortcut Method:

`document.getElementById("footer").style.color = "red";`

Any attribute getter and setter:

`document.getElementById("footer").getAttribute("src");`

`document.getElementById("footer").setAttribute("src", "someimage.png");`

##Exercise 2

- Give ids to each paragraph in the previous example.
- Add buttons below each paragraph that when clicked:
	- Change the text in that particular paragraph only.
	- Change the background color of that paragraph.
	- Change the text color.

##Exercise 3

- Review the files in the ex_3 folder.
- Loop through each `li` element and attach a click handler that sets the class attribute to "selected".
- How do we know which item was clicked? This is set to the DOM element that received the event. Can you print it out to console?
- Change the image to reflect what was clicked.
- Add a "Reset" button that removes "selected" class from all list items.

##Binding Events to Dynamic Elements

- When elements come into the DOM dynamically, they didn't exist before, so you can't bind the event on page load.
- As a result, you have to bind the event at the time of load or to the document itself.

##Exercise 4

- Review the files in the ex_4 folder.
- Try to bind the click event to the paragraphs upon load of the AJAX.
- Extra Credit: Bind the click event to the document on page load so that it works when the DOM is loaded dynamically. Hint: Bind the click event to the document itself and console log the `event` object that is passed down into the callback function. This will give you the hint.

##Homework

- Check out the folder titled "contact_form_exercise".
- Follow the instructions in the readme.