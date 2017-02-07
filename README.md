# grunt-webpack [![Build Status](https://travis-ci.org/webpack-contrib/grunt-webpack.svg?branch=master)](https://travis-ci.org/webpack-contrib/grunt-webpack) [![codecov](https://codecov.io/gh/webpack-contrib/grunt-webpack/branch/master/graph/badge.svg)](https://codecov.io/gh/webpack-contrib/grunt-webpack)

Use [webpack](https://github.com/webpack/webpack) with grunt.

**This is the readme for version 2.0. For the 1.0 readme visit [here](https://github.com/webpack-contrib/grunt-webpack/tree/1.0).** 

## Getting Started

Install this grunt plugin next to your project's [Gruntfile.js](http://gruntjs.com/getting-started). You also need to install webpack yourself, this grunt plugin does not install webpack itself.

```bash
yarn add webpack grunt-webpack
```

If you also want to use the webpack-dev-server task you also need to install `webpack-dev-server`

```bash
yarn add webpack-dev-server
```

Then add this line to your project's `Gruntfile.js` gruntfile:

```javascript
module.exports = function(grunt) {

  // Project configuration.
  grunt.initConfig({ ... });

  grunt.loadNpmTasks('grunt-webpack');
};
```

## Configuration

`webpack-grunt` offers two different tasks `webpack` and `webpack-dev-server`. Both support all webpack options as 
can be seen in the [webpack documentation][3]. For exceptions and additions see this list.

### Both Tasks

#### progress
Type: `bool`
Default: `true` (`false` if no TTY present)

Activates or deactivates the progress output of webpack.

#### keepalive
Type: `bool`
Default: `false` (`true` if watch mode is used and for webpack-dev-server)

Activates or deactivates the progress output of webpack.

### Webpack Task

#### failOnError
Type: `bool`
Default: `true` (`false` if watch mode is used)

> TODO this is not true currently, it is not disabled when watchmode used

Terminate the grunt process when an error happens if set to `true`. If set to `false` the grunt process will not be immediately terminated on error and instead still run tasks scheduled to run after the webpack task.

#### storeStatsTo
Type: `string`
Default: `null`

When set the stats from webpack will be written to a variable with the name provided in this option. The variable can later be used inside of other grunt tasks with template tags `<%= %>`.

```js
...
storeStatsTo: "webpackStats"

...

<%= webpackStats.hash %>
...
```

> For more information about grunt template tags have a look at the [grunt docs][2].

### Webpack-dev-server Task

The webpack-dev-server options [`host`][5], [`hotOnly`][6], [`inline`][1], [`port`][4] and [`public`][7] which are usually only available in the CLI can also be used in this grunt-plugin.

## Examples

### old

``` javascript
webpack: {
  someName: {
	// webpack options
	entry: "./client/lib/index.js",
	output: {
		path: "asserts/",
		filename: "[hash].js",
	},

	stats: {
		// Configure the console output
		colors: false,
		modules: true,
		reasons: true
	},
	// stats: false disables the stats output

	storeStatsTo: "xyz", // writes the status to a variable named xyz
	// you may use it later in grunt i.e. <%= xyz.hash %>

	progress: false, // Don't show progress
	// Defaults to true

	failOnError: false, // don't report error to grunt if webpack find errors
	// Use this if webpack errors are tolerable and grunt should continue

	watch: true, // use webpacks watcher
	// You need to keep the grunt process alive

	watchOptions: {
		aggregateTimeout: 500,
		poll: true
	},
	// Use this when you need to fallback to poll based watching (webpack 1.9.1+ only)

	keepalive: true, // don't finish the grunt task
	// defaults to true for watch and dev-server otherwise false

	inline: true,  // embed the webpack-dev-server runtime into the bundle
	// Defaults to false

	hot: true, // adds the HotModuleReplacementPlugin and switch the server to hot mode
	// Use this in combination with the inline option

  },
  anotherName: {...}
}
```

`grunt-webpack` uses the [webpack options](http://webpack.github.io/docs/configuration.html).


## License

Copyright (c) JS Foundation

MIT (http://opensource.org/licenses/mit-license.php)

[1]: https://webpack.js.org/configuration/dev-server/#devserver-inline-cli-only
[2]: http://gruntjs.com/api/grunt.template
[3]: https://webpack.js.org/configuration/
[4]: https://webpack.js.org/configuration/dev-server/#devserver-port-cli-only
[5]: https://webpack.js.org/configuration/dev-server/#devserver-host-cli-only
[6]: https://webpack.js.org/configuration/dev-server/#devserver-hotonly-cli-only
[7]: https://webpack.js.org/configuration/dev-server/#devserver-public-cli-only
