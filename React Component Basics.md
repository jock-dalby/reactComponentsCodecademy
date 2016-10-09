React applications are made out of components.

What's a component?

A component is a small, reusable chunk of code that is responsible for one job. That job is often to render some HTML.

The terms "component," "React component," and "component instance" all refer to the same thing.

Take a look at the code below. This code will create and render a new React component:
```js
var React = require('react');
var ReactDOM = require('react-dom');

var MyComponentClass = React.createClass({
  render: function () {
    return <h1>Hello world</h1>;
  }
});

ReactDOM.render(
  <MyComponentClass />,
  document.getElementById('app')
);
```
------ Import React & ReactDOM ------

var React = require('react') returns a JavaScript object. This object contains the React library.

require('react-dom') contains React-related methods for interacting with the DOM.

The methods returned by require('react') don't deal with the DOM at all. They don't engage directly with anything that isn't part of React. They are for pure React purposes, such as creating components or writing JSX elements.

------ Create a Component Class ------

Every component must come from a component class.

A component class is like a factory that creates components. If you have a component class, then you can use that class to produce as many components as you want.

To make a component class, you use one of the methods in the React library: React.createClass.

When you make a new component class, you should store it in a variable so that you can use it later. Component class variable names must begin with capital letters to adhere to the naming convention in which class names are written in UpperCamelCase.

------ Component Class Instructions ------

React.createClass takes one argument. That argument must be a JavaScript object. This object will act as a set of instructions, explaining to your component class how to build a React component.

Here's what your "instructions object" would look like on its own.
```js
{
  render: function () {
    return <h1>Hello world</h1>;
  }
}
```

There is only one property that you have to include in this object: a render function. A render function must have a return statement. Usually, this return statement returns a JSX expression:

```js
var React = require('react');
var ReactDOM = require('react-dom');


var componentBlueprint = {
  render: function () {
    return <h1>Hello world</h1>
  }
};

var MyComponentClass = React.createClass(componentBlueprint);
```
Saving the instructions object in a variable (as above) is a nice way to illustrate how it works, but it basically never happens in practice. It's much more common to see something like this:

```js
var React = require('react');
var ReactDOM = require('react-dom');

var MyComponentClass = React.createClass({
  render: function () {
    return <h1>Hello world</h1>;
  }
});
```
MyComponentClass is now a working component class! It's ready to follow its instructions object and make some React components.

So, let's make a React component! It only takes one more line:
```js
<MyComponentClass />
```
To make a React component, you write a JSX element. Instead of naming your JSX element something like h1 or div like you've done before, give it the same name as a component class. Voilà, there's your component instance!

JSX elements can be either HTML-like, or component instances. JSX uses capitalization to distinguish between the two! That is why component class names must begin with capital letters. In a JSX element, that capitalized first letter says, "I will be a component instance and not an HTML tag."
