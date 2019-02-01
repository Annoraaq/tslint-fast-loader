# tslint-fast-loader
Fast tslint loader for Webpack. This is a fork of tslint-loader but performs faster by an order of magnitude when typechecking is enabled.

## Installation

``` shell
npm install tslint tslint-fast-loader --save-dev
```

The package depends on Tslint 4.0+, no longer works with 3.* versions.

## Usage

Apply the tslint fast loader as preLoader in your webpack configuration.

### Webpack 4

```javascript
module.exports = {
    module: {
        rules: [
            {
                test: /\.ts$/,
                enforce: 'pre',
                use: [
                    {
                        loader: 'tslint-fast-loader',
                        options: { /* Loader options go here */ }
                    }
                ]
            }
        ]
    }
}
```

### Webpack 3

```javascript
module.exports = {
    module: {
        loaders: [
            {
                test: /\.ts$/,
                enforce: 'pre',
                loader: 'tslint-fast-loader',
                options: { /* Loader options go here */ }
            }
        ]
    }
}
```

### Webpack 2

```javascript
module.exports = {
    module: {
        rules: [
            {
                test: /\.ts$/,
                enforce: 'pre',
                loader: 'tslint-fast-loader',
                options: { /* Loader options go here */ }
            }
        ]
    }
}
```

### Webpack 1

```javascript
module.exports = {
    module: {
        preLoaders: [
            {
                test: /\.ts$/,
                loader: 'tslint-fast-loader'
            }
        ]
    },

    tslint: { /* Loader options go here */ }
}
```

### Loader options

```javascript
{
    configuration: {
        rules: {
            quotemark: [true, 'double']
        }
    },

    // can specify a custom config file relative to current directory or with absolute path
    // 'tslint-custom.json'
    configFile: false,

    // tslint errors are displayed by default as warnings
    // set emitErrors to true to display them as errors
    emitErrors: false,

    // tslint does not interrupt the compilation by default
    // if you want any file with tslint errors to fail
    // set failOnHint to true
    failOnHint: true,

    // enables type checked rules like 'for-in-array'
    // uses tsconfig.json from current working directory
    typeCheck: false,

    // automatically fix linting errors
    fix: false,

    // can specify a custom tsconfig file relative to current directory or with absolute path
    // to be used with type checked rules
    tsConfigFile: 'tsconfig.json',

    // name of your formatter (optional)
    formatter: 'yourformatter',

    // path to directory containing formatter (optional)
    formattersDirectory: 'node_modules/tslint-fast-loader/formatters/',

    // These options are useful if you want to save output to files
    // for your continuous integration server
    fileOutput: {
        // The directory where each file's report is saved
        dir: './foo/',

        // The extension to use for each report's filename. Defaults to 'txt'
        ext: 'xml',

        // If true, all files are removed from the report directory at the beginning of run
        clean: true,

        // A string to include at the top of every report file.
        // Useful for some report formats.
        header: '<?xml version="1.0" encoding="utf-8"?>\n<checkstyle version="5.7">',

        // A string to include at the bottom of every report file.
        // Useful for some report formats.
        footer: '</checkstyle>'
    }
}
```

## License

[MIT](http://www.opensource.org/licenses/mit-license.php)


