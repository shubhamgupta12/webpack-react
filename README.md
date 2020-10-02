
#   Setup React project using Webpack 4.44.2 and Babel 6.26.3 : 

#### 1. Install these as devDependencies:
`webpack`
`webpack-dev-server`
`webpack-cli`

#### 2. Enter the command in package.json 

```
webpack-dev-server --config ./webpack.config.js --mode development
```

#### 3. Basic config:
```
module.exports = {
    entry: [
        './src/index.js'
    ],
    output: {
        path: __dirname + '/dist',
        publicPath: '/',         // Relative to the path where index.html is
        filename: 'bundle.js'
    },
    devServer: {
        contentBase: './dist'
    }
}
```

#### 4. Install Babel as devDependencies
`@babel/core` - main babel pkg
`babel-loader` - compiles js code in webpack
`@babel/preset-env` - understands browser support for specific js code and converts that
`@babel/preset-react` - for React - jsx to js

#### 5. Add this to package.json or to a new `.babelrc` file
```
"babel": {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react"
    ]
}
```

#### 6. Add `module` and `resolve` to webpack config:
This is to identify all js/jsx files and transpile those using `babel-loader`. 
`resolve` allows to omit writing extensions while importing files.
```
  module: {
    rules: [
      {
		test: /\.(js|jsx)$/,
		exclude: /node_modules/,
		use: ['babel-loader']
      }
    ]
  },
  resolve: {
	  extensions: ['.js', '.jsx']
  }
  ```
  
 #### 7. Install `react` and `react-dom`
 #### 8. Install `eslint` and `eslint-loader` 
 #### 9. Add `eslint` config in webpack rules:
 ```
    {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ["eslint-loader"]
    }
```
#### 10. Add `babel-eslint`
so that eslint can run on ES6+

#### 11. More eslint dependencies
    "eslint-config-airbnb"  ==> For airbnb styleguide
    "eslint-plugin-jsx-a11y" ==> For accessibility
    "eslint-plugin-import"  ===> For import/export
    
#### 12. `.eslintrc.json` file
    {
      "parser": "babel-eslint",
      "rules": {
        "no-console": "warn"
      },
      "extends": ["airbnb-base"]
    }
