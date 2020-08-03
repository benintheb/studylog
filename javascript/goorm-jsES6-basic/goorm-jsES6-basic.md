# JavaScript ES6 For Framework

[course](https://edu.goorm.io/learn/lecture/19879/프레임워크를-위한-javascript-es6) from goormedu

---

## Interacting With Arrays

### Direct Addition: `.push`

`.push` is adding an element to arrays. The element is added to the end of the array. This directly adds the element to the array.

    const arr = [1, 2, 3, 4];
    arr.push(5);
    console.log(arr);
    // [1, 2, 3, 4, 5]

### Indirect Addition: `.concat`

When using frameworks in JavaScript, the matter of direct or indirect interaction with the array is important.  
`.concat` indirectly adds to the array by having to create another variable to contain the result.

    const arr = [1, 2, 3, 4];
    const arrAdd = arr.concat(5);
    console.log(arrAdd);
    // [1, 2, 3, 4, 5]

### Direct Subtraction: `.pop`

`pop` does the exact opposite of `push`. It deletes the last element in the array.

    const arr = [1, 2, 3, 4, 5];
    arr.pop(5);
    console.log(arr);
    // [1, 2, 3, 4]

### Looping in Arrays: `.forEach`, `.map`

For looping in arrays, using `for` would have been the original way.

    const names = ['ben', 'harry', 'mark'];

    for(var i = 0; i < names.length; i++){
        console.log(`My name is ${names[i]}.`);
    }
    // My name is ben.
    // My name is harry.
    // My name is mark.

This can be done in a more simple fashion, using the `.forEach`.

    const names = ['ben', 'harry', 'mark'];

    arr.forEach(name => console.log(`My name is ${name}.`));
    // My name is ben.
    // My name is harry.
    // My name is mark.

There is another simple way to loop arrays. That is the `.map`. `.map` is used frequently when using frameworks. The difference with `.forEach` is that `.map` stores the result of the function in a new array.

    const num = [1, 2, 3, 4];
 
    const newNum = num.map( n => n*2 );
    console.log(newNum);
    // [2, 4, 6, 8]

By creating a new variable and storing the result of the function, `.map` is open to a lot of useful tasks.

### Searching in Arrays: `.filter`

With `.filter`, a set of results can be searched and stored in another varible. 

    const num = [1, 3, 5, 7, 9];

    const fiveUp = num.filter(num => num >= 5);
    console.log(fiveUp);
    // [5, 7, 9]

`.filter` can be used to find complex keys and values in objects.

    const dateId = 
    [
        {"id":1, "date": "yesterday"}, {"id":2, "date": "yesterday"}, {"id":3, "date": "today"}
    ];

    const yesterday = dateId.filter(post => post.date === "yesterday");
    console.log(yesterday);
    // [{id: 1, date: "yesterday"}, {id: 2, date: "yesterday"}]

---

## JavaScript Arrays

Arrays in JavaScript are not acually arrays, but rather **objects** that pretend to be arrays.

    const arr = [1, 2, 3, 4];
    console.log(typeof arr);
    // object

### Length of Arrays: `.length`

The length of an array can be known with the method `.length`. Obviously, right?

    const arr = [1, 2, 3, 4];
    console.log(arr.length);
    // 4

In JavaScript however, the length of the array does not necessarily mean that there are that many elements.

    const arr = [];
    arr[2] = 3;
    console.log(arr.length);
    // 3

Even if there was only one element added to the array, the `.length` method counts the total length of the array.

- The length of the array and the number of elements in the array is different in JavaScript. 

___

## Arrow Function

Arrow function expressions are a lot less shorter than original function expressions. Arrow functions do not have its own bindings with `this`, `arguments`, `super`, or `new.target`.  
An arrow function is always anonymous and cannot be used as a constructor method.

    hello = () => {
        return "Hello World!";
    }

The blank parentheses in this example is where the parameters go in.

- If there is only one parameter, the parentheses can be excluded.
- If the code inside braces(curly brackets) can be expressed in one line, the braces can be excluded.
- If the braces are excluded, `return` is implicit.
```
    const square = num1 => num1 * num1;
    console.log(square(10));
    // 100
```

Codes can be very succinct with arrow functions.

    // if a number is larger than 0, print the number.
    // if a number is smaller than 0, print 0.

    const exam = num => num >= 0 ? num : 0;

Arrow functions massively increase the readability of callback functions.

    setTimeout( () => console.log("Hello!"), 3000);





---

## Template Literal

The existing string expressions have a certain inconvenience when it comes to coding. 

    const name = "Ben";
    console.log("Hi my name is " + name + ". Nice to meet you.");

To fit a variable inside a string, `+` signs have to be used. When needing to fit multiple variables, this can be very inconvenient.

Template literal is expressing string using backticks `` ` ``. This allows multiple lines be recognized, and there's no need for `+` to come in between. Also, conditional statements can be used.

```
console.log(`I'm tired of writing
these posts.`);
// I'm tired of writing
   these posts.

const name = "Ben";
console.log(`Hello my name is ${name}. Nice to meet you`);
// Hello my name is Ben. nice to meet you.

let hw = true;
console.log(`Oh my homework ${hw ? "is finished" : "is not done yet"}`);
// Oh my homework is finished
```

Variables can be accessed inside template literals with `${variable}`.

---

## `let` and `const`

### The Problem With `var`

- The usage of `var` inside a block is considered a global variable. One cannot use `var` for a block scope variable.  
The increase of global variables is never considered positive.

- `var` allows reusing of names. This causes the unintentional change of the values of variables.  
In this context, the distiction of variables containing flexible/non-flexible values cannot be made.
```
    var value = "value meant not to be changed";

    if(true){
        var value = "unintentional change";
    }

    console.log(value);   // value is changed.
```

### `let`

With `let`, the names of the variables cannot overlap. Also, `let` is considered to be in a block scope when used inside a block.

    if(true){
        let num = 3;
        console.log(num);
        //let num = 7;  // SyntaxError: Identifier 'num' has already been declared
        num = 7;
        console.log(num);   // 7 (other values can be stored)
    }
    //console.log(num); // ReferenceError: num is not defined

Inside the block, another variable `num` cannot be declared with `let`. However, the value can still be changed.

### `const`

`const` is all the same with `let` exept for one thing. The value of the variable declared with `const` **cannot** change.

    if(true){
        const num = 3;
        console.log(num);
        num = 7;    // TypeError: Assignment to constant variable
    }

<br>

`const` is commonly used to declare objects, for the structure of the object cannot be changed, but *the values of each keys **are** mutable*.

    const obj = {
        'key': 'value'
    }
    console.log(obj.key);   // value

    obj.key = 'value1';
    console.log(obj.key);   // value1

- Rather than the usage of `var`, `let` and `const` should be used if possible.

- If it is a value that is going to be reallocated, use `let`.  
If a value does not have to change, use `const` by default.

---

## Callback Function (200724)

### Synchronous and Asynchronous

Synchronous means to do one task at a time. The next task can start only after the previous task is finished.  
Asynchronous means to do multiple tasks at once. Without waiting for the neighboring tasks to finish, it starts all the tasks that it is given. 

<!-- ![sync_n_async](https://media.vlpt.us/images/cyongchoi/post/865ca482-fe2c-4444-9702-1d9701edf0c8/lpf0u9nbj7w41.jpg){: width="70%" height="100%"} -->
<img src="https://media.vlpt.us/images/cyongchoi/post/865ca482-fe2c-4444-9702-1d9701edf0c8/lpf0u9nbj7w41.jpg" alt="sync_n_async" width="70%"/>

- JavaScript naturally has a asynchronous behavior, that it does not wait for a code in calculation before moving on to the next code.

### Callback Function

There are instances where an order of execution needs to be guaranteed. The callback function is used in these instances.

    function a(){
        console.log("latter");
    }

    function b(callback){
        console.log("former");
        callback();
    }

    b(a);

    // former
    // latter

Function `b` receives function `a` as a factor and keeps it. Function `a` is executed only after function `b` does what it has to do.

### Callback Hell

There are instances where multiple executions need to be in an exact order.  
In an asynchronous environment, a large series of executions will result in callback after callback.

<!-- ![callback_hell](https://miro.medium.com/max/1400/1*sOy11ZsU1ijCSjZwx8ZzGQ.jpeg){: width="70%"} -->
<img src="https://miro.medium.com/max/1400/1*sOy11ZsU1ijCSjZwx8ZzGQ.jpeg" alt="callback_hell" width="70%"/>

This type of coding is called a callback hell. Callback hells are harder to read and are difficult to change logicwise.

- The solving of a callback hell was implemented in ES6, in `promise`, `async`, and `await`. They will be looked at another time.

---

## `this` Keyword (200723)

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

#### Block Scopes (implemented in ES6)

What is a block? 

    {
        // this is the active area for block scopes
    }

Block scopes are activated only using `let` and `const`. When using `var`, the variable is considered as a global scope.

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

However, usage of global scopes are not recommended, and should not be used if possible. When writing massive lines of code and functions, global scopes will become harder to track. In this manner, global scopes are best used when it has a value that does not change.

### In Addition

- There are more kinds of scopes, these are just the fundamental kinds of scopes.  
- Through the browser's developer tools menu, one can see what kind of scope a variable is using, and where it is used.
