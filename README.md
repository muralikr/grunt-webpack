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

## webpack

### Configuration

### Examples

## webpack-dev-server

### Configuration

### Examples


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
