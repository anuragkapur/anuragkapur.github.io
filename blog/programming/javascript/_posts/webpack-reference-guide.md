# Introduction
* Webpack is module bundler
  * Lets you write JS in any module format (including mixed) and compiles them for the browser
* Setting up scripts when using webpack
    ```json
      "scripts": {
        "webpack-dev-server": "webpack-dev-server",
        "webpack": "webpack",
        "debug": "node --inspect --inspect-brk ./node_modules/webpack/bin/webpack.js",
        "prod": "npm run webpack -- --env.mode production",
        "dev": "npm run webpack-dev-server -- --env.mode development",
        "prod:debug": "npm run debug -- --env.mode production",
        "dev:debug": "npm run debug -- --env.mode development"
      }
    ```
* NPM Dependencies
    ```
    "webpack"
    "webpack-dev-server"
    "webpack-bundle-analyzer"
    "webpack-cli"
    "webpack-node-externals"
    "workbox-webpack-plugin"
    ```

# Webpack core concepts
* Config file: `webpack.config.js`
* [Entry points](https://webpack.js.org/concepts/entry-points/)
    ```javascript
    module.exports = {
      entry: './path/to/my/entry/file.js',
    };
    ```
* [Output](https://webpack.js.org/concepts/output/)
    ```javascript
    module.exports = {
      output: {
        path: './dist',
        filename: './bundle.js'
      }
    };
  
    // OR
  
    module.exports = () => {
      return {
        output: {
          path: './dist',
          filename: './bundle.js'
        }
      }
    };
    ```
* Passing env variables to the webpack config
  * package.json scripts
  ```json
    "scripts": {
      "prod": "npm run webpack -- --env.mode production"
    }  
  ```  
  * webpack.config.js
  ```javascript
    module.exports = (env) => {
      return {
        mode: env.mode,
        output: {
          path: './dist',
          filename: './bundle.js'
        }
      }
    };
  ```  
* [Loaders](https://webpack.js.org/concepts/loaders/)
  * Tells webpack how to modify files before its added to dependency graph
  * Loaders are also javascript modules (functions) that takes the source file and returns it in a [modified] state
  * Chaining loaders
    ```json
    rules: [
      {
        test: /\.less$/,
        use: ['style', 'css', 'less']
      }
    ]
    ```
    * Chained loaders are executed from right to left [style(css(less()))]
* [Plugins](https://webpack.js.org/concepts/plugins/)
  * Are JS objects (with an apply property)
  * Allow you to hook into the entire compilation lifecycle
  * Useful plugins
    * [HtmlWebpackPlugin](https://webpack.js.org/plugins/html-webpack-plugin/): generates index.html file with script 
    tags including our custom JS code
    * [ProgressPlugin](https://webpack.js.org/plugins/progress-plugin/)
* [Webpack dev server](https://github.com/webpack/webpack-dev-server)
  * Webpack generates the bundle in memory and server via an express server
* Splitting environment config files
  * Add NPM library `webpack-merge` to package.json
  * Update `webpack.config.js` to merge configs
    ```javascript
    const webpackMerge = require("webpack-merge");
    const modeConfig = env => require(`./build-utils/webpack.${env}`)(env);
    
    module.exports = ({ mode, presets } = { mode: "production", presets: [] }) => {
      return webpackMerge(
        {
          mode,
          output: {
            filename: "bundle.js"
          },
          plugins: [new HtmlWebpackPlugin(), new webpack.ProgressPlugin()]
        },
        modeConfig(mode)
      );
    };
    ```
  * Production config overrides
    ```javascript
    module.exports = () => ({
      output: {
        filename: "[chunkhash].js"
      }
    });
    ```

# References
* [Webpack 4 Fundamentals, Sean Larkin](https://frontendmasters.com/courses/webpack-fundamentals)
  * [Course Slides](https://docs.google.com/presentation/d/1hFtMCMo62DgOIc-9OwgaVwPZHwv1cgMELArHcMbXlSI/)