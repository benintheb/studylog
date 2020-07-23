# JavaScript ES6 For Framework

[course](https://edu.goorm.io/learn/lecture/19879/프레임워크를-위한-javascript-es6) from groomedu

---

## this Keyword (200723)

### Binding

The term *binding* can be used to describe the `this` keyword.

    var obj1 = {
        name: 'harry',
        nameOut: function(){
            console.log(this.name);
        }
    }

    var obj2 = {
        name: 'ben'
    }

    obj2.nameOut = obj1.nameOut;

    obj1.nameOut(); // harry
    obj2.nameOut(); // ben

As seen in the code, `obj2`'s nameOut function was created and given the same `nameOut` function as `obj1`.  
However, `obj1` and `obj2`'s nameOut function both give different printouts, for each `nameOut` function is *binded* onto different objects.

*Binding* is matching the right methods to the right objects.

### The Window Object

The window object, or the Browser Object Model(BOM) is a way to "talk to" a browser.  
All global objects, functions, and variables become members of the window object, including the document object(DOM).


For JavaScript running in a browser, it is the **window object**.  
For JavaScript running in server side(node.js), it is the **global object**.  

### Binding of this In a General Method

When calling a function, the usage of `this` binds to the window object.  

    var name = "harry";
    console.log(window.name);   // harry

    var nameOut = function(){
        var name = "ben";
        console.log(this.name); //harry
    }

    nameOut();

Both log functions print out harry, for both are calling for the variable `name` of the window object.

### Binding of this In a Object Method

`this` in a object method binds to whichever object it is called in.

    var obj1 = {
        name: 'harry',
        nameOut: function(){
            console.log(this.name);
        }
    }

    var obj2 = {
        name: 'ben'
    }

    obj2.nameOut = obj1.nameOut;

    obj1.nameOut(); // harry
    obj2.nameOut(); // ben

Both objects are calling `this.name`, but each method is binded with a different `name`: the `name` that is declared in each of it's own object.

### Binding of this In a Constructor Method

`this` in a constructor method binds to the object that is constructed by the method.

    var person = function(name){
        this.name = name;
    }

    var a = new person("harry");
    console.log(a.name);    // harry

    var b = new person("ben");
    console.log(b.name);    // ben

`this` is called in the constructor method `person`, but is binded to objects `a` and `b` that are constructed by `person`.  

- The difference between a general method and a constructor method is that the constructor method makes new objects with the usage of `new`.

### Binding of this In a Inner Method

`this` in an inner method **always** binds to the window object.

    var value = 100;

    var obj = {
        value: 1,
        func: function(){
            console.log("func's value: ", this.value);
            function innerFunc(){
                console.log("innerFunc's value: ", this.value);
            }
            innerFunc();    // innerFunc's value: 100
        }
    };
    obj.func(); // func's value: 1

Method `func`'s `this.value` is binded with `value` of `obj` which is 1, but the inner method `innerFunc`'s `this.value` is binded with `value` of the window object which is 100.  

- This phenomena shows one of the flaws of the JavaScript language.  
- There are methods such as `apply`, `call`, and `bind` to address this flaw, but will be looked at another time.

---

## Scopes (200723)

There are two kinds of scopes. Global scopes and local scopes.

A variable declared in a global scope is a global variable.  
A variable declared in a local scope is a local variable. (of course)

### Local Scopes

Local scopes are again devided into two scopes, block scopes and function scopes.

- #### Block Scopes (implemented in ES6)

What is a block? 

    {
        // this is the active area for block scopes
    }

Block scopes are activated only using `let` and `const`. When using `var`, the variable is considered as a global scope.

- #### Function Scopes

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

However, usage of global scopes are not recommended, and should not be used if possible. When writing massive lines of code and functions, global scopes will become harder to track. In this manner, global scopes are best used when it has a value that does not change.

### In Addition

- There are more kinds of scopes, these are just the fundamental kinds of scopes.  
- Through Chrome's DevTools, one can see what kind of scope a variable is using, and where it is used.
