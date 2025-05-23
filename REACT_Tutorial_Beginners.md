# React tutorial for Beginners from Programming with Mosh

Tip from Mosh :arrow_right: use the VSCode extension Prettier and go on File-Preferences-Settings-Search for "format on save" and every time we save our file, it will be correctly formatted for us.


## Create React App VS Vite

The standard tool to create a React Application is to use the CLI command `create react app`. <br>
But Vite (Yuri Pereira said that he uses and a lot of international enterprises are using this too) is much faster and result in smaller bundle sizes for the application. <br>
:arrow_right: 
```javascript
npm  create vite@latest
```
This is to use the latest version of Vite OR instead of `@latest`, we can pass `@4.1.0` to use a specific version. <br>
Only follow the instructions presented at the screen after running the above command. <br>
:exclamation: **Attention to use TYPESCRIPT for react (standard as of now) and not Javascript.**


## Creating Component

Right click on the `src` folder, add File, named `Message.tsx`. The `.tsx` indicates a React Component using typescript, if we would write pure typescript the extension would be `.ts` (similar naming for javascript). <br>
There are 2 main ways of creating a React Component: **Class or Function approach**. We will use the FUNCTION APPROACH, because it's used more often nowadays and more concise. **OBS: on the previous React course of Programming with Mosh, there are videos showing react components with a Class Approach**. <br>


## How React Works

:exclamation: React builds a component tree (similar to the tree of HTML) and after translates this tree to a data structure in JavaScript, the **Virtual DOM**, that is an In-Memory representation of the Real DOM. React reads the nodes in the tree to see where it changed and ONLY updates the DOM updating the modified Node, without having to reload all DOM. <br>
For **actually displaying and modifying the DOM**, the library that does this job is `ReactDOM` and, for mobile, the other library is `React Native`, this means **we are able to build React applications and display them for Web or Smartphones just changing the Build Library**.

## STYLING

:esclamation: For Styling the application, we will install Bootstrap with the command `npm i bootstrap@versionNUmber` where versionNumber is the number that you'll use.

When using the HTML + CSS generated by bootstrap [Boostrap Documentation](https://getbootstrap.com/docs/5.3/components/list-group/), and using it inside a component in React, it throws errors at the reserved work `class` from the CSS. **To avoid those errors, rename ALL words 'class' for `className`**. <br>
:seedling: TIP: use the shortcut `Ctrl + D` to create many cursors and edit all words at once. <br>
:seedling: TIP 2: use `Prettier` as the code formatter and the shortcut `Ctrl Shift P` to open Command Pallete and search for "Format Document With" and select Prettier. <br> 
**Note that after the `ListGroup` component was formatted by Prettier, the extension added parenthesis automatically, because this is needed to brake multiple lines of HTML inside the component**.

In React, a component **CANNOT return more than 1 element**. To solve this, we can WRAP the whole set of elements inside a div, for example, but other elements are also allowed. <br>
:seedling: TIP 3: Select all the code that will be wrapped, hit `Ctrl Shift P`, opening Command Pallete, type `Wrap with abbreviation`, type `div` and it automatically wraps all the code selected by a div tag! <br>
:seedling: TIP 4: Instead of using the wrapping div, use `Fragments` by `import {Fragment} from 'react';`. To use it, select both the wrapping divs, and write `<Fragment>`. This wat, we are not adding an aditional component on the screen (and on the HTML Tree). <br>
:seedling: TIP 5: Instead of writing to import Fragments, we're able to use it without this much writing. Simply put **Angle Brackets (`<>` and  `</>`) to denote that we're using Fragments**. This eliminates the need to import at the top of our file.

OK, BUT, the idea of render a list on the screen is that this list would be rendered dynamically, having as much elements as they're needed.

Now, let's start using some JS mixed with JSX and programming logic. By creating an Array (itens) and using the map() method, we can add, delete, etc using Arrays. And by addingthe code inside the JSX markup we are able to insert a list that is dynamic.

## Conditional Rendering

Sometimes, we want to render things on the screen based on some condition, a good approach is to use a logical expression as: 
```javascript
{items.length === 0 && <p>No item found</p>}
```
:seedling: Common way of React Developers to render things conditionally.
Using this inside our ListGroup Component, we are rendering the message only if the length is 0, because if length is 0 (True), anything true && something is the something. So, if the first part, the length is True, the `<p>` message will be rendered. 


## Handling Events


After applying Bootstrap Class to the `<li>` tags, the idea is to show something in the console when clicking on some item on the list. <br>
Similar to HTML, the React element has a property (or a **prop**), called `onClick={}`. Inside this braces, we write an arrow funtion to handle the click event. <br>
In the first examples, we displayed the `item` and the `index` property (position) in the array. That was a one-liner expression. BUT, if we wanted to display a more complex logic, we would create a function in the upper area of the component, and that function would be responsible for handling that event. In the example, the instructor used a **`type annotation` available in Typescript**.

## Managing State

When clicking on a list item, we want to highlight it, and we'll be doing that by using the **CSS `active` class**. <br>
To inform React that the data passed dynamically, we have to use a built-in function called **`useState`**. <br>
**This is a `React Hook`, that is, a function that allows us to tap into built-in features of React**. Using this Hook, we are informing React that this component will have DATA that will CHANGE OVER TIME. ALWAYS, `useState` returns an ARRAY. <br>
In the example of the course, he uses a `selectedIndex` variable to hold the data of the list item selected. **Following a React Best Practice**, he declares the second element being a function called `setSelectedIndex`, indicating with the keyword `set` that this is a function that will handle the changing of state of the component. <br>
NOTE that in React, **each component has its own state**, meaning that if we add another `<ListGroup>` component, it will have its own and separated state. As an example, add another listgroup and see that we can select any element in the first list that this change won't impact the second list.


## Passing Data with Props

We pass data through the components using the props, making them reusable. <br>
We pass the values of the props like HTML property values.

## Passing Functions via Props

In real life,  in the majority of times, we want that something happens **after** an item is selected, as filtering an object, redirect to another page, etc. <br>
Thinking in how to add the logic **without** interfering with the component (having in mind the components should be reusable), we would have the parent element (in our case, the `app` component) to inform its children components of changings in the state, and those changes in the state would make the children components respond as needed. <br>
We are going to create a property in the interface, that is a function, that **do not return anything**. The name will be `onSomething`, like the `onClick` known property of HTML. <br>


## States vs Props

- `Props` :arrow_right: are the **inputs** passed to the component. They should be treat as **immtable**, or read-only.
- `State` :arrow_right: is the **internal data** managed by the component that can **change over time**, they are similar to local variables inside a function. They are (and should be) **mutable**, since we want to capture their changes over time. <br>
:exclamation: OBS: Both have one thing in common: any time they change, React will re-render our component and modify the DOM accordingly.


## Passing Children

How to create a component that has children. <br>
On the `components` folder, add a New File, called `Alert.tsx`. Instal the extension by searching for "ES7+", that provides shortcuts, as we will use some of them right now, instead of defining a function and exporting it by default, we will going to use the shortcut: `rafce`, that will create an React Arrow Function Export Component and we have our code snippet just created. <br>

