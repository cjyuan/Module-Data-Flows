# Feedback to Improve the Code

## `index.html`

#### Check for syntax error in HTML and CSS
Have you validated the code in `index.html` using https://validator.w3.org/? (The original HTML have some errors)

#### Loading script as an ES module 
Suggestion: Consider loading `script.js` as an ES module to isolate its scope from the global context as:

`<script src="script.js" type="module"></script>`

This ensures that variables, functions, and imports in script.js don't leak into the global namespace, 
helps prevent naming conflicts, and enables the use of modern JavaScript features like import and export.

Note: With `type="module"`, `defer` is automatically enforced.

---
## `script.js`

#### Remove unnecessary code
On page load, a function is unnecessarily called twice.
Can you remove this unnecessary function call?

What kinds of code are considered unnecessary?
Are there any more unnecessary code that should also be removed?

#### Is the data stored in the proper data type?
Should "page count" be consistently represented as a string or a number in the app?

#### Meaningful variable names
```javascript
// The variable names do not clearly reflect that they store DOM nodes.
const title = document.getElementById("title");
const author = document.getElementById("author");
const pages = document.getElementById("pages");
const check = document.getElementById("check");
```
Using descriptive and consistent suffixes (like `El`, `Input`, `Btn`, `Form`, etc.) for variables that store DOM nodes can improve code readability and maintainability.

#### What is the data type of `.value`?
In `submit()`, do we need to check if `.value` is `null`?

#### Preprocessing input  
Before using input in an app, we should properly preprocess it:
  - **Input Validation** - Checking whether the input meets expected formats, types, or constraints
  - **Input Sanitization** - Cleaning input to exclude unwanted or potentially harmful data
  - **Input Normalization/Conversion** - Transforming input into the correct data type or a standardized, usable format

Questions to consider:
  - Should `title` and `author` be allowed to contain only space characters?
  - Should `title` and `author` be allowed to contain leading or trailing space characters?
  - What type of value should we use to store the page count?
  - What kinds of input values should be rejected?

#### Efficient approach to remove rows in `<table>`
In `render()`, instead of using a for loop to delete table rows one by one, we could possibly (with some tweak) delete all rows in one operation.

#### Differences among `.innerHTML`, `innerText`, and `textContent`
When setting the text content of an HTML element, there are subtle but important differences between using `.innerHTML`, `innerText`, and `textContent`.

In `render()`, are the text values assigned to the appropriate property of each DOM node?

#### Value of `id` attribute
In `render()`,
- Are the values assigned to the `id` attributes unique? 
- Is there any need to assign an `id` attribute to the buttons?

#### Naming consistency
The names given to the two buttons, `changeBut` and `delButton`, are not consistent.

#### Confirmation Message Timing Issue
In the callback function of the delete button, the alert message is shown before the book is actually deleted; the deletion only occurs after the alert dialog is dismissed. This introduces a risk that the operation may not complete (e.g., if the user closes the browser before dismissing the alert).

In general, it's better to display a confirmation message only after the associated operation has successfully completed.

