#g5-component.js

Browserify Component Scaffold

[![NPM version](http://img.shields.io/npm/v/g5-component.svg?style=flat-square)](https://www.npmjs.org/package/g5-component) 
[![NPM license](http://img.shields.io/npm/l/g5-component.svg?style=flat-square)](https://www.npmjs.org/package/g5-component)

---

* event based
* scalable architecture
* completely self-contained
* clean, well documented
* consistent code and methodologies
* simple workflow
* environment agnostic code (UMD)
* can be used as a scaffold and a module
* ES6/ES2015 support via babel
* Tape unit tests
* Style guide (Airbnb) validation and test on commit
* Handlebars, LoDash, LESS
* Bootstrap, jQuery (available on component level)

---

###Architecture

The component, model, and viewModel all receive an instance of the EventEmitter.

The layers never communicate directly with each other, instead, an event tower mediates events between layers.


__[Component](https://github.com/MajorLeagueBaseball/g5-component/blob/master/src/scripts/g5-component.js)__ - contains an internal reference of the model, viewModel, and event layer

__[Model](https://github.com/MajorLeagueBaseball/g5-component/blob/master/src/scripts/model/master.js)__ - fetches data and passes it along to the component extender

__[Component Extender](https://github.com/MajorLeagueBaseball/g5-component/blob/master/src/scripts/component/extender.js)__ - module used for transforming data after it's received from the model

__[viewModel](https://github.com/MajorLeagueBaseball/g5-component/blob/master/src/scripts/viewModel/master.js)__ - bootstraps view and component, contains logic only related to the view

__[Component Master](https://github.com/MajorLeagueBaseball/g5-component/blob/master/src/scripts/component/master.js)__ - entry point for all component specific functionality

__[eventTower](https://github.com/MajorLeagueBaseball/g5-component/blob/master/src/scripts/events/master.js)__ - mediates events between layers

---

###Setup

> Install the package and use it as a module ([documentation](https://github.com/MajorLeagueBaseball/g5-component/blob/master/docs/usage-module.md))

```
npm i g5-component
```

> Or clone the package and use it as a scaffold ([documentation](https://github.com/MajorLeagueBaseball/g5-component/blob/master/docs/usage-scaffold.md))

```
git clone https://github.com/MajorLeagueBaseball/g5-component.git && cd g5-component
```

```
npm i less catw jscs http-server -g
```

```
npm i && npm run build
```

###Server / Development

> Server running on [http://localhost:9966](http://localhost:9966) with auto (split) builds [Ctrl+C] to kill server

```
npm run start-dev
```

###Server

> Server running on [http://localhost:9966](http://localhost:9966) with full build [Ctrl+C] to kill server

```
npm run start
```

###Commands

####Build

> Bundle build, without vendor dependencies

```
npm run build-js
```

####Build Vendor

> Vendor build

```
npm run build-js-vendor
```

####Build Full

> Full build, including vendor and bundle

```
npm run build-js-full
```

####Test

```
npm test
```

####JSHint

```
npm run lint
```

###Options

A single options Object shared between all Constructors

* `Element` __container__ - primary container
* `String` __css__ - classes
* `String` __i18n__ - localization
* `Number` __interval__ - polling interval (ms)
* `String` __path__ - data path (remote/local)
* `Boolean` __enablePolling__ - flag to enable/disable data polling

###Methods

```js
exampleComponent.init(); // initiates component
```

```js
exampleComponent.hasInstance(); // checks if container has an instance of g5-component
```

```js
exampleComponent.detachEvents(); // detaches all events
```

```js
exampleComponent.attachEvents(); // attaches all events
```

```js
exampleComponent.destroy(); // kills component instance
```

###Events

> Events must be attached before the component is initiated

```js
exampleComponent.on('ready', function(obj) {

    // console.log('component model and viewModel have been initiated', obj);

});

exampleComponent.on('data', function(data) {

    // console.log('component data from model', data);

});

exampleComponent.on('data-error', function(err) {

    // console.log('component model data error', err);

});

exampleComponent.on('destroy', function(obj) {

    // console.log('component instance killed', obj);

});
```

###Style Guide / Rules

* Style Guide - [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)
* Protect against `new` - constructors can be called with or without `new`
* Maintain chainability, methods return `this`

###Reference

* [Fetch](https://fetch.spec.whatwg.org/)
* [Simple Browserify Overview](https://github.com/yoshuawuyts/knowledge/blob/master/browserify.md)
* [Browserify Handbook](https://github.com/substack/browserify-handbook)
* [Browserify and UMD](http://dontkry.com/posts/code/browserify-and-the-universal-module-definition.html)
* [Task Automation with npm run](http://substack.net/task_automation_with_npm_run)
* [About Watchify](https://github.com/substack/watchify)
* [Tape Tests](https://github.com/substack/tape)
* [JSDoc](http://usejsdoc.org/)

###License

Copyright (c) 2015 [MLBAM](http://mlb.mlb.com/home)

Copyright (c) 2015 [Greg Babula](https://twitter.com/gregbabula)

Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
