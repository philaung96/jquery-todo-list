# Advanced jQuery

## Event Delegation

Let's look at a click event that we have seen before.

```html
<ul>
    <li>Riyadh</li>
    <li>Boston</li>
    <li>Jeddah</li>
</ul>
```

```js
$("li").on("click", function(event){
    $(event.target).css("color", "red")
})

```

When we `click` on an `li` then the css font color fo that `li` changes to red.

However when we add a new `li` dynamically, the click event does not work on that `li`.

```html
<ul>
    <li>Riyadh</li>
    <li>Boston</li>
    <li>Jeddah</li>
</ul>
```

```js
$("li").on("click", function(event){
    $(event.target).css("color", "red")
})

// could also be added by a user submitting a form
$("ul").append("<li>New York</li>");
```

The click event works on the `li` for `Riyadh`, `Boston`, and `Jeddah` but not on `New York`.  This is because the click event was added BEFORE the `New York` `<li>` was appended to the DOM.

We can fix this by using **event delegation**.

```js
$("ul").on("click", "li", function(event){
    $(event.target).css("color", "red")
})

// could also be added by a user submitting a form
$("ul").append("<li>New York</li>");
```

Notice how we select a parent element that IS on the page when the page originally loads and we tell it to listen for a click even on its children that are an `li`.

### Lab

- Open the [event-delegation/index.html](event-delegation/index.html]) file in the browser. 
- Add a new `li` by submitting the form
- Notice how the click event works on the other `li`s but not the new one
- Use event delegation in [event-delegation/main.html](event-delegation/main.js]) to fix the problem so that the click event works on even dynamically added `li`s.

## Group Project

With your group, you are going to build a fully functioning To Do List application using jQuery.  The HTML and CSS has already been completed for you.  It is up to you and your team to write the jQuery and Javascript to make the To Do List function.  Every team member should be coding along together and have their own copy of the code.  Work together and make sure every team member understands the code.

- The [pseudo code is here](to-do-list/pseudocode_suggestions.md)
- Your [starter code is here](to-do-list)

**Goals**

1.  Add a submit event to "Add to List"
2.  Add a click even to "Clear List"
3.  Add a remove button and click event to "Remove" an item from the list (you will need event delegation)
4.  Add a click event on the item to cross off the item to "Complete" the to do item (you will need event delegation)
5.  Add a click event to "Clear Completed" items

**Bonus Features**

6.  Add a count of all items that are not "Complete"
7.  Add an edit button and click event to change the html of the `li` for that item to a `form` and `input` so they can edit the to do item (you will need event delegation)
8.  Add a submit event to the `form` so they can save the edited to do item and change the html of the `li` to be the updated item (you will need event delegation)