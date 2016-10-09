----- Use multiline JSX in a component -----
```js
var React = require('react');
var ReactDOM = require('react-dom');

var QuoteMaker = React.createClass({
  render: function () {
    return (
      <blockquote>
        <p>
          The world is full of objects, more or less interesting; I do not wish to add any more.
        </p>
        <cite>
          <a target="_blank"
            href="http://bit.ly/1WGzM4G">
            Douglas Huebler
          </a>
        </cite>
      </blockquote>
    );
  }
});

ReactDOM.render(
  <QuoteMaker />,
  document.getElementById('app')
);
```

The key thing to notice in the above code is the parentheses in the return statement. A multi-line JSX expression should always be wrapped in parentheses! That is why QuoteMaker's return statement has parentheses around it.
```js
var React = require('react');
var ReactDOM = require('react-dom');

var owl = {
  title: "Excellent Owl",
  src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-owl.jpg"
};

// Component class starts here:
var Owl = React.createClass({
  render: function() {
    return (
    	<div>
        <h1>{owl.title}</h1>
        <img src={owl.src} alt={owl.title} />
      </div>
      )
  }
})

ReactDOM.render(<Owl />, document.getElementById('app'));
```

----- Put Logic in a Render Function -----

A render function must have a return statement. However, that isn't all that it can have.

A render function can also be a fine place to put simple calculations that need to happen right before a component renders. Here's an example of some calculations inside of a render function:
```js
var Random = React.createClass({
  render: function () {

    // First, some logic that must happen
    // before rendering:
    var n = Math.floor(Math.random()*10+1);

    // Next, a return statement
    // using that logic:
    return <h1>The number is {n}!</h1>;
  }
});
```
Watch out for this common mistake:
```js
var Random = React.createClass({

  // This should be in the render function:
  var n = Math.floor(Math.random()*10+1);

  render: function () {
    return <h1>The number is {n}!</h1>;
  }
});
```

Example 2

```js
var React = require('react');
var ReactDOM = require('react-dom');

var friends = [
  {
    title: "Yummmmmmm",
    src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-monkeyweirdo.jpg"
  },
  {
    title: "Hey Guys!  Wait Up!",
    src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-earnestfrog.jpg"
  },
  {
    title: "Yikes",
    src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-alpaca.jpg"
  }
];

// New component class starts here:
var Friend = React.createClass({
  render: function () {
    var friend = friends[2];
    return (
      <div>
        <h1>{friend.title}</h1>
        <img src={friend.src} />
      </div>
    );
  }
});

ReactDOM.render(
  <Friend />,
  document.getElementById('app')
);
```

----- Use a conditional in a Render Function -----

```js
var React = require('react');
var ReactDOM = require('react-dom');

var TodaysPlan = React.createClass({
  render: function () {
    var task;
    if (!apocalypse) {
      task = "learn React.js"
    } else {
      task = "run around"
    }

    return <h1>Today I am going to {task}!</h1>;
  }
});

ReactDOM.render(
	<TodaysPlan />,
	document.getElementById('app')
);
```
Notice that the if statement is located inside of the render function, but before the return statement. This is pretty much the only way that you will ever see an if statement used in a render function.

----- Use this in a React Component -----

The word this gets used in React a lot!

You are especially likely to see this inside of an object that is being passed to React.createClass. Here is an example:
```js
var IceCreamGuy = React.createClass({
  food: 'ice cream',

  render: function () {
    return <h1>I like {this.food}.</h1>;
  }
});
```

this refers to the instructions object being passed to React.createClass.

this has two properties: food, and render. this.food will evaluate to "ice cream."

There's nothing React-specific about this behaving in this way! However, in React you will see this used in this way almost constantly.

If you aren't totally comfortable with this in JavaScript, here is a good resource.

http://www.digital-web.com/articles/scope_in_javascript/

----- Use an Event Listener in a Component -----

Render functions often contain event listeners. Here's an example of an event listener in a render function:
```js
render: function () {
  return (
    <div onHover={myFunc}>
    </div>
  );
}
```
Recall that an event handler is a function that gets called in response to an event. In the above example, the event handler is myFunc.

In React, you define event handlers as property values on the instructions object. Like this:
```js
React.createClass({
  myFunc: function () {
    alert('Stop it.  Stop hovering.');
  },

  render: function () {
    return (
      <div onHover={this.myFunc}>
      </div>;
    );
  }
});
```
Notice that the object being passed to React.createClass has two properties: myFunc and render. myFunc is being used as an event handler. myFunc will be called any time that a user hovers over the rendered <div></div>.
