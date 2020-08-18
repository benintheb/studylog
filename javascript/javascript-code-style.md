## JavaScript Style Guide  
#### article from [this course](https://edu.goorm.io/learn/lecture/19879/프레임워크를-위한-javascript-es6/lesson/985691/쉬어가기2-코드-스타일)

A code style is needed for the consistency of the code in a big projects, and for useful communications between developers.  
Code styles are not required or forced, but is a implicit rule that programmers follow.  

- This article references the [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript), and the [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html).  
All of the topics will not be dealt with, just a few of the most commonly used ones.

---

### Naming

1. Reserved words are not used as variable names.
1. Abbreviations are all upper or all lower case letters.
1. File names are all lower case letters.
1. Variables, functions, parameters, object names, and package names follow the camelCase naming convention.
1. Class names, and constructor methods follow the PascalCase naming convention.

### Indentations

Indentations are two spaces with the space bar.

### Variables

1. Variables are fundamentally made with `const`.
1. Use `let` exceptionally when it is a changing value.

### Functions

1. If a name is needed, use `const`.
1. Preferably use arrow functions.
1. If the body of the arrow function is a line of code, the curly brackets and the `return` statement can be omitted. If curly brackets are not omitted, a `return` statement is required.

### Curly Brackets

1. Open the curly brackets and change the line.
1. Change the line and close the curly brackets.
```
function sayHello(name)
{
    console.log(`Hello, my name is ${name}.`);
}
```
1. Open and close in one line with `{}` only when empty. (Except for `if`-`else`, `try`-`catch`-`finally`)
```
const foo = () => {};
```

- This type of indentation style is called the The K&R style (Kernighan & Ritchie Style).

### Arrays

1. When allocated multiple values from one array, use deconstructing.
1. Use the spread operator(`...`) when copying an array.
1. Use `push` when adding to an array.

### Objects

Use double quotation marks when addressing the key.

### Operators

Use the identity operator/nonidentity operator(`===`, `!==`) instead of the equality operator/inequality operator(`==`, `!=`).


    


