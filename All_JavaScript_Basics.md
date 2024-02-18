# JavaScript Basics

## Data Types (most basic)

- `Numbers`
- `Strings`
- `Booleans`
- `null`
- `undefined`
- `Symbol`

### Variables

Hold the values of the simple data types and most complex data types. <br>
Using the keywords `let`, `const` and `var`.
--> `let` defines a **local scope** variable.
--> `const` defines a value that **cannot** be changed (unless it is redeclared)
--> `var` defines a **global scope** variable, pre-ES6

## Strings and its Methods

Only remeber that **ALL Primitive types are Immutable**. This means that, when using a method that returns something with a primitive type, the return is another string/number/etc, not the original, because they are immutable.

:arrow_right: strings hold text values. <br>
- String **concatenation**: `console.log("My name is " + "Matheus");`
- String **interpolation**: `console.log("My name is {name});")`
- String **Template**:  
```javascript
console.log(`My name is ${name}`);
```

:arrow_right: Useful Methods:
- `string.length` --> returns the length of the string (number)
- `string.toUpperCase()` --> returns the string all on UPPER CASE
- `string.toLowerCase()` -> returns the string on all lower case
- `string.substring(index_start, index_end)` --> returns the substring (a part of the original string) using an initial index and an ending index of the substring "slice"
- `string.split('')` --> returns an Array of strings, and the array is created by the separator indicated withing parentheses, for example, `string.split(',')` will return an array of strings where the new string is where there's the comma separating.


## Objects

Objects in JS are `key: value` pairs. Example below: 
```javascript
const person = {
    name: 'Matheus',
    walk = function {},
    talk = {}
}
```

As seen above, there is the **old** method for declaring a method (a function inside an object) in JS that is using the keyword `function`. But the **new** way to do that is simply naming the method and put the curly braces. <br>
To access the property/method in an object, we can use the knowm **dot notation** or the **bracket notation**.
- `this` :arrow_right: is a keyword that returns the reference to the current object. Its value can be different depending on the use. <br />
In JS, **functions are objects too**, therefore they have properties and methods, like other objects.
If we use by calling a method of an object, it references the object which we're dealing with. However, if we use it as a function call, or outside an object, it will return a `window` object in browsers. When running the browser in **strict mode**, the return of `this` will be `undefined`. To avoid that, we use the bind (a method to bind a function with an object) as in: `function.bind`.

Passing the object as the argument for the method `.bind()`, it returns an instance of the object passed as an argument. (As pointed above, functions are objects and objects have this method `bind()`).

`Arrow Functions` :arrow_right: they are functions but written in a simpler way.
- `const square (number) => {return number * number}` ---> used when we pass 1 parameter, the (number). We could also take away the parenteses from the parameter because we're passing only 1. If we had to pass more than 1 parameter, then we would have to use the parenteses.
- `const square = () => {return number * number}` ---> used when we **don't need to pass any parameters**
- `const square = (number) => number * number` ---> used when we have a single line in the body of the function, we could write it all in the same line. We don't need the curly braces nor the `return` keyword.

Arrow Functions DO NOT rebind `this`.

## Arrays

- `Array.map()` :arrow_right: 
Example: 
```javascript
const colors = ['red', 'green', 'blue'];
const items = colors.map(function (color) {
    return "<li?>" + color + "</li>";
});
```

The second Array, the `items` **does NOT modify** the original array. And the `.map()` method uses a callback function to perform an operation on each element of the array. Now, cleaning the code using arrow functions:
```javascript
const colors = ['red', 'green', 'blue'];
const items = colors.map(color => `<li>${color}</li>`);
```

In the code portion above, we used template literals to clean even more the code and be able to use a string and a portion that holds variables. <br>
The `.map()` method calls a function on every element of the array and provides a **new** array containing the results.

- `Array.filter()` :arrow:right:
Example: 
```javascript
const colors = ['dark red', 'light red', 'bright red', 'red', 'yellow', 'green', 'blue', 'orange'];
const red_colors = colors.filter(function (color) {
    return color.includes('red');
})
console.log(red_colors);
```

In the example above, we also used the `includes()` method, that takes at least one argument and returns an array where it evaluates `True`. In our case, we wanted to filter an array of colors and return every type of red color. We passed a function using the includes() method and filtered all elements that included 'red' in its content.

- `Array.reduce()` :arrow_right:
The reduce() method, as the name says, reduces an array, by computing the values (like a For Loop) and returning an array with only the computed values.


## Constructor Functions and ES6 Classes
Is a function that will take parameters (that will be the object properties) and build all in an Object. Example:
```javascript
function Person(firstName, lastName, birthDate) {
    this.firstName = firstName,
    this.lastName = lastName,
    this.birthDate = birthDate
};
const Joe = Person('Joe','Race','12-2-2000');
const Lilly = Person('Lilly', 'Roberts','5-20-1998');
console.log(Joe);
console.log(Lilly);
```

## Object Destructuring

Example: 
```javascript
const address = {
    street: '',
    city: '',
    country: ''
};
//const street = address.street;
//const city = address.city;
//instead of having 3 variable declaration, use DESTRUCTURING:
const {street, city, country} = address;
console.log(street);
```

Instead of declaring all variables using the dot notation, we simply declare the variables we want using a object-like notation and we will have the variables we want without having to write as much code. Also, we can use an **alias** when addressing the new variables:
```javascript
const {street: st} = address;
```
In this case, we are declaring the `st` variable that receibes the value from the street property from the object address.

## Spread and Rest Operators

```javascript
const array1 = [1,2,3];
const array2 = [4,5,6];
const combinedV1 = array1.concat(array2);
//better way, using spread
const combinedTurbo = [...array1, ...array2];
```
In addition, using the **spread operator**, we are able to inser things like a new element or a property inside the array or object, things that are not possible using the concat() method.

## Classes

Before, if we wanted to create another object similar to the first, we had to copy the object 1 and rename it to object2, for example. BUT, if we have a method that contains a bug, we are spreading this bug to other objects (that were copied), and we´re also duplicating code. <br>
For this we have classes, a blueprint of the objects we want to have. Example:
```javascript
const Person {
    constructor(name) {
        this.name = name;
    }
    walk() {
        console.log("walk");
    }
    greet() {
        console.log("Hi!");
    }
}

const Joe = new Person('Joe');
```

## Inheritance

Using the previous code example (`classesExample.js`), we created the class Teacher. But if we wanted to have a `walk()` method just like Person class has. If we had to copy that method, we would be duplicating code. By making the Teacher Class to inherit from the Person Class, we can **inherit all the methods that Person has, including the constructor()**. We do this by using the keyword `extends`, as in the example:
```javascript
class Teacher extends Person {
    tech() {
        console.log("Time to Teach!");
    }
}
```

It is related to Python, because in this process, we are inheriting all the methods including the constructor. But, if we want to implement a customized constructor for the Teacher Class, we could create one. However, since this is an inherited Class, it will use the constructor of the parent class. To be able to modify the Person Class and add some itens to our Teacher Class, we have to use the keyword `super()`, for enabling the use of the constructor of the parent class. EXample:
```javascript
class Teacher extends Person {
    constructor(name, degree) {
        super(name) = name;
        this.degree = degree;
    }
    teach() {
        console.log("Teach hour");
    }
}
```
This way, we initialized properly the name property and the degree (that does not exist in Person Constructor). In React, we **extend** the base components that are within it, adding our custom properties, fields, etc.


## Modules

Modules in JS are like the modules in Python, with the purpose of splitting the code, adding modularity to our programs. The separated files (modules, with their Classes) **are NOT visible to any other files**. If we want to use these classes in another program, we MUST export and import then, using the keywords `export` and `import`. Example:
```javascript
export class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
}

// in the index.js file, import the Person Class
import {Person} from './classPerson';
```

I was geting some errors by using `node index.js` trying to execute the index.js file that imports the Person and Teacher files/Classes. It throws an error of `Cannot use import statement outside a module`. I think this is because i did not initialized a node project (as seen in the video tutorial (Mosh ES6 Tutorial)). <br>
**NAMED IMPORTS: `import {XYZ} from './XYZ';`** <br>
**DEFAULT IMPORTS: `import XYZ from 'XYZ';`**