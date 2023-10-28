# JavaScript Scope Examples
Quick guide for JavaScript Scopes. Created by [Devpebe](https://devpebe.com)

## Scope types
- Global scope
- Module scope
- Function scope
- Block scope

### Global scope
#### Short definition
Global is default scope for all the code running in script. It means all the code has access to values (variables, functions, etc.) in this scope.

#### Global scope examples
```js
// GLOBAL SCOPE
const test = 'example'; // Global scope variable

function testFunction () {
  console.log(test); // This function has access to global scope variable
}
```

### Module scope
#### Short definition
Module scope means the code is in a separate JavaScript file and scope of this file is a module. To use the code from a module you need to export functions, variables.

#### Module scope examples
`module.js`
```js
// module.js content
// MODULE SCOPE
const moduleVariable = 'moduleValue';
```

`index.html`
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Module scope example</title>
    </head>
    <body>
        <script>
          // GLOBAL SCOPE
          const test = 'example'; // Global scope variable
          
          function testFunction () {
            // FUNCTION SCOPE
            console.log(test); // This function has access to global scope variable
          }
        </script>
        <script src="module.js" type="module"></script>
    </body>
</html>
```

### Function scope
#### Short definition
Function scope is created with function. Function scope has access to parent scopes. Parent scope doesn't have access to child scopes.

#### Function scope examples
```js
function testFunction () {
  // FUNCTION SCOPE (testFunction)
  const testVariable = 'test'

  function example () {
    // FUNCTION SCOPE (example)
    const exampleVariable = 'example';
    console.log(testVariable) // prints 'test'
  }

  console.log(testVariable); // ReferenceError: testVariable is not defined
}

console.log(testVariable) // ReferenceError: testVariable is not defined
console.log(exampleVariable) // ReferenceError: testVariable is not defined
```

### Block scope
#### Short definition
Block scope is created with `let` and `const` keyword. Whenever you create a variable in `if` statement or any other you can access this variable only inside this block. `var` is not included here!

#### Block scope examples 
```js
function example () {
  const exampleVariable = 'example';

  if (exampleVariable) {
    const blockVariable = 'blockVariable';

    console.log(blockVariable); // prints 'blockVariable'
  }

  // FUNCTION example scope
  console.log(blockVariable) // ReferenceError: blockVariable is not defined
}
