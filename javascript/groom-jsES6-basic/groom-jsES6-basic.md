# JavaScript ES6 For Framework

[course](https://edu.goorm.io/learn/lecture/19879/프레임워크를-위한-javascript-es6) from groomedu

---

## Scope (200723)

There are two kinds of scopes. Global scopes and local scopes.

A variable declared in a global scope is a global variable.

A variable declared in a local scope is a local variable. (of course)

### Local Scopes

Local scopes are again devided into two scopes, block scopes and function scopes.

#### Block Scopes

Block scopes were implemented in ES6.

What is a block? 

    {
        // this is the active area for block scopes
    }

Block scopes are activated only using `let` and `const`.

When using `var`, the variable is considered as a global scope.

#### Function Scopes

Function scopes can only be used inside functions, as the name suggests. 

    function funcScope(){
        var num = 10;

        console.log(num);   // The variable num is recognized inside the function scope
    }
    console.log(num);   /* Outside the function, the variable is not recognized, 
                            resulting an Uncaught ReferenceError: num is not defined */

### Global Scopes

Global scopes can be used in all areas inside the code, when not confined by blocks and functions.

Block scopes not using `let` and `const` are also considered as a global scope.

    {
        var num = 10;
    }

    console.log(num)

    function numTest(){
        console.log(num);
    }
    
    numTest();

However, usage of global scopes are not recommended, and should not be used if possible.

When writing massive lines of code and functions, global scopes will become harder to track.

In this manner, global scopes are best used when it has a value that does not change.

### In Addition

- There are more kinds of scopes, these are just the fundamental kinds of scopes.

- Through Chrome's DevTools, one can see what kind of scope a variable is using, and where it is used.

