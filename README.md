# react-anything-sortable [![Build Status](https://travis-ci.org/jasonslyvia/react-anything-sortable.svg)](https://travis-ci.org/jasonslyvia/react-anything-sortable) [![npm version](https://badge.fury.io/js/react-anything-sortable.svg)](http://badge.fury.io/js/react-anything-sortable)

## Features

 - Sort any React element you like, images, composite components, etc.
 - No external dependencies but `React` itself
 - Touch event support (since 1.1.0)
 - Thoroughly tested

## Quick Demo

[Live Demo](http://jasonslyvia.github.io/react-anything-sortable/demo/index.html)

**Sort custom style children**

![react-anything-sortable](http://ww4.sinaimg.cn/large/831e9385gw1equswkpcfag209p02sgn5.gif)

**Sort images**

![react-anything-sortable](http://ww3.sinaimg.cn/mw690/831e9385gw1equstgvfmzg20a50360va.gif)

**Children with custom event handler**

![react-anything-sortable](http://ww4.sinaimg.cn/large/831e9385gw1eqy459cieqg20au02s0t4.gif)

## Installation

**If you're using React v0.13, please use `react-anything-sortable@0.3.2` instead, it's the latest compatible version.**

```
$ npm install --save react-anything-sortable

// if you're using React v0.13, try
$ npm install --save react-anything-sortable@0.3.2

// UMD build is provided as well, but please do consider use modern module bundlers like webpack or browserify.
```

## How to use

You can check the straight-forward demo by examining `demo` folder, or here's a brief example.

In `app.js`

````
var ReactDOM = require('react-dom');
var Sortable = require('react-anything-sortable');
var YourSortableItem = require('./YourItem');

ReactDOM.render(
<Sortable onSort={handleSort}>
  <YourItem sortData="1" />
  <YourItem sortData="2" />
</Sortable>
, document.body);
````

and in `YourItem.js`

ES 6 `import` is recommended

```
import React from 'react';
import {SortableItemMixin} from 'react-anything-sortable';

const YourItem = React.createClass({
  mixins: [SortableItemMixin],

  render() {
    return this.renderWithSortable(     // <= this.renderWithSortable is important
      <div>your item</div>
    );
  }
});
```

Or if you favor the old fashion way

````
var React = require('react');
var SortableItemMixin = require('react-anything-sortable').SortableItemMixin;

var YourItem = React.createClass({
  mixins: [SortableItemMixin],

  render: function(){
    return this.renderWithSortable(
      <div>your item</div>
    );
  }
});
````

## Notice

1. Specify your style for `Sortable` and `Sortable Items`, check `demo/style.css`, **it is NOT optional!**
2. Don't forget the `this.renderWithSortable` call in `YourItem.js`
3. Specify `sortData` in `YourItem.js` so that `Sortable` can return the sorted array
4. Add `onSort` props to `Sortable` to be noticed when a sort operation finished
5. Since we can't track any children modification in `Sortable`, you have to use `key` to force update `Sortable` when adding/removing children.


## Scripts

```
$ npm run test
$ npm run watch
$ npm run build
$ npm run demo
$ npm run demo-watch
```


## Contributors

1. [stayradiated](https://github.com/stayradiated)
2. [vizath](https://github.com/vizath)
