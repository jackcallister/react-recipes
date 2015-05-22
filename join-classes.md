### Joining user classes with inbuilt component classes.

Components which define their own `className` are frail to consumer overwriting.

```
var Component = React.createClass({

  render: function() {
    return (
      <div className='component' {...this.props}>Hello, World</div>
    );
  }
});

<Component className='myClass'>

// Renders =>
// <div class='myClass'>Hello, World</div>
```

Rather than overwriting the internal `className` use the `joinClasses` utility.

```
var joinClasses = require('react/lib/joinClasses');

var Component = React.createClass({

  render: function() {
    var classes = joinClasses(this.props.className, 'component');

    return (
      <div {...this.props} className={classes}>Hello, World</div>
    );
  }
});

<Component className='myClass'>

// Renders =>
// <div class='component myClass'>Hello, World</div>
```
