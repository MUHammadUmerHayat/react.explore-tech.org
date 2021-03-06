---
path: '/materials/react.animate'
type: 'GitHub'
img: './screenshot.png'
material:
  title: 'react.animate'
  url: 'https://github.com/pleasetrythisathome/react.animate'
  github_url: 'https://github.com/pleasetrythisathome/react.animate'
  subscribers_count: '6'
  stargazers_count: '171'
  tags: ['']
  subtitle: 'state animation plugin for react.js'
  clone_url: 'https://github.com/pleasetrythisathome/react.animate.git'
  ssh_url: 'git@github.com:pleasetrythisathome/react.animate.git'
  pushed_at: '2015-09-03T12:50:09Z'
  updated_at: '2018-09-25T02:33:12Z'
  author:
    name: 'pleasetrythisathome'
    avatar: 'https://avatars1.githubusercontent.com/u/1894358?v=4'
    github_url: 'https://github.com/pleasetrythisathome'
  latestRelease:
    tag_name: null
    name: null
    url: null
    created_at: null
---
React.Animate
=============

A simple state animation mixin for React.js

Philosophy
------------

React.Animate is a different approach to animate based on state rather than direct DOM mutation using $.animate or similar.

While it's great that you can use refs to get DOM nodes after render, the biggest benefit to using react is that there is always a direct, observable, and testable relationship between component props, state, and the rendered output.

Mutating the dom directly is an antipattern.

What we really want to animate is not the DOM, it's component state.

If you think about animation as a transition from one state value from another, you can just interpolate state over an interval, and your component can rerender precisely in response to the current component state at every step.

At it's most simple, React.Animate allows you to transition between one state and another over a set interval. The implementation supports the same syntax as $.animate.

you can pass either

```javascript
this.animate(properties [, duration ] [, easing ] [, complete ] );
```

or

```javascript
this.animate(key, value [, duration ] [, easing ] [, complete ] );
```

Example
------------

React.Animate can be included in any React class by adding it to the mixins array

By animating state instead of the DOM directly, we can define logic that acts during certain parts of our animations.

```javascript
var component = React.createClass({
  mixins: [React.Animate],
  getInitialState: function() {
    return {
      width: 100
    };
  },
  render: function() {
    var heightBounds = [50, 100];

    return React.DOM.div({
      style: {
        width: this.state.width,
        height: Math.min(heightBounds[1], Math.max(heightBounds[0], this.state.width / 2))
      },
      onClick: this.randomSize
    });
  },
  randomSize: function() {
    this.animate({
      width: _.random(20, 300)
    }, 500, function() {
      console.log('random size reached!');
    });
  }
});
```

view in [jsfiddle](http://jsfiddle.net/mWAnw/2/)


Installation
------------

React.Animate can be installed with [bower](http://bower.io/) using

```
bower install react.animate --save
```

React.Animate can be installed with [npm](https://www.npmjs.com/) using

```
npm install react.animate --save
```

Both will automatically pull the required React and Underscore dependencies.

to use React.Animate, include it in your page or build process after React and Underscore

Dependencies
------------

[easing functions](https://github.com/component/ease).
