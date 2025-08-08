# Feedback to Improve the Code

### `index.html`
Have you validated the code in `index.html` using https://validator.w3.org/? (The original HTML have some errors)
 
---
### `script.js`

#### Calling `render()` twice on page load
On page load, `render()` is unnecessarily called twice; once in `populateStorage()` and once in the  `onload` event listener.

#### Page count is represented as a string
In `populateStorage()`, the `page` value passed to the `Book` constructor is represented as a string.

#### Meaningful variable names
```javascript
// These variable names do not quite indicate they store DOM nodes.
const title = document.getElementById("title");
const author = document.getElementById("author");
const pages = document.getElementById("pages");
const check = document.getElementById("check");
```
Using descriptive and consistent suffixes (like `El`, `Input`, `Btn`, `Form`, etc.) for variables that store DOM elements can improve code readability and maintainability.

#### What is the data type of `.value`?
In `submit()`, do we need to check if `.value` is `null`?

#### Preprocessing input  
Before using input in the app, we should properly preprocess it:
  - **Input Validation** - Checking whether the input meets expected formats, types, or constraints
  - **Input Sanitization** - Cleaning input to exclude unwanted or potentially harmful data
  - **Input Normalization/Conversion** - Transforming input into the correct data type or a standardized, usable format

Questions to consider:
  - Should `title` and `author` be allowed to contain only space characters?
  - Should `title` and `author` be allowed to contain leading or trailing space characters?
  - What type of value should we use to store the page count?
  - What kinds of input values should be rejected?

#### Efficient approach to remove rows in `<table>`
In `render()`, instead of using a for loop to delete table rows one by one, we could possibly (with some tweak) efficiently delete all rows in one operation.

#### Differences among `.innerHTML`, `innerText`, and `textContent`
When setting the text content of an HTML element, there are subtle but important differences between using `.innerHTML`, `innerText`, and `textContent`.

In `render()`, are the text values assigned to the appropriate property for each DOM node?

#### Value of `id` attribute
In `render()`,
- Are the values assigned to the `id` attributes unique? 
- Is there any need to assign an `id` attribute to the buttons?

#### Naming consistency
The names given to the two buttons, `changeBut` and `delButton`, are not consistent.

#### Confirmation Message Timing Issue
In the callback function of the delete button, the alert message is shown before the book is actually deleted; the deletion only occurs after the alert dialog is dismissed. This introduces a risk that the operation may not complete (e.g., if the user closes the browser before dismissing the alert).

In general, it’s better to display a confirmation message only after the associated operation has successfully completed.

