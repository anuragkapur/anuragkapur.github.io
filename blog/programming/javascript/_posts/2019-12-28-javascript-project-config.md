---
layout: post
title:  "JavaScript Project Reference Configuration"
date:   2019-12-28 00:00:00 +0000   
categories: programming javascript
tags: programming
teaser: My default reference project configuration (prettier, eslint etc) for JS projects 
img-url: /assets/blog/programming/js-project-config.jpg
permalink: /blog/js-project-reference-config
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Prettier](#prettier)
  - [Install](#install)
  - [package.json script](#packagejson-script)
  - [.prettierrc](#prettierrc)
  - [Webstorm IDE setup](#webstorm-ide-setup)
- [ESLint](#eslint)
  - [Install](#install-1)
  - [package.json script](#packagejson-script-1)
  - [.eslintrc.json](#eslintrcjson)
  - [ESLint + React](#eslint--react)
  - [Webstorm IDE setup](#webstorm-ide-setup-1)
- [Parcel](#parcel)
  - [Install](#install-2)
  - [package.json script](#packagejson-script-2)
- [Babel](#babel)
  - [Install](#install-3)
  - [.babelrc](#babelrc)
  - [Update to .eslinstrc.json](#update-to-eslinstrcjson)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Prettier
A code styling / pretty printing utility.

## Install
* Global install on dev machine
    ```shell
    npm install --global prettier
    ```
* Local project install
    ```shell
    npm install --save-dev prettier
    ```  

## package.json script
```json
"scripts": {
    "format": "prettier --write \"src/**/*.{js,jsx}\"",
},
```

## .prettierrc
```json
{}
```  

## Webstorm IDE setup
* Install prettier plugin
* Setup File Watcher
  * Set scope to `Open Files` instead of `Project Files`    
[https://prettier.io/docs/en/webstorm.html](https://prettier.io/docs/en/webstorm.html)

# ESLint
A static code analysis / linting tool.

## Install
* Local project install
    ```shell
    npm install --save-dev eslint eslint-config-prettier
    ```  
  
## package.json script  
```json
"scripts": {
    "lint": "eslint \"src/**/*.{js,jsx}\" --quiet",
},
```

## .eslintrc.json
```json
{
  "extends": ["eslint:recommended", "prettier", "prettier/react"],
  "plugins": [],
  "parserOptions": {
    "ecmaVersion": 2018,
    "sourceType": "module",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "env": {
    "es6": true,
    "browser": true,
    "node": true,
    "jest": true  
  }
}
```

## ESLint + React
* Getting ESLint to recognise React
    ```shell
    npm install -D babel-eslint eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-react-hooks
    ```
* Updated .eslintrc.json
    ```json
    {
      "extends": [
        "eslint:recommended",
        "plugin:import/errors",
        "plugin:react/recommended",
        "plugin:jsx-a11y/recommended",
        "prettier",
        "prettier/react"
      ],
      "rules": {
        "react/prop-types": 0,
        "no-console": 1,
        "react-hooks/rules-of-hooks": 2,
        "react-hooks/exhaustive-deps": 1
      },
      "plugins": ["react", "import", "jsx-a11y", "react-hooks"],
      "parserOptions": {
        "ecmaVersion": 2018,
        "sourceType": "module",
        "ecmaFeatures": {
          "jsx": true
        }
      },
      "env": {
        "es6": true,
        "browser": true,
        "node": true
      },
      "settings": {
        "react": {
          "version": "detect"
        }
      }
    }
    ```   

## Webstorm IDE setup
Reference: [https://www.jetbrains.com/help/webstorm/eslint.html](https://www.jetbrains.com/help/webstorm/eslint.html)

# Parcel
Bundler for JavaScript projects.    
* Zero-config
* Includes babel for transpilation
* Supports hot module replacement to speed up development

## Install
* Local project install
    ```shell
    npm install --save-dev parcel-bundler
    ```
  
## package.json script
```json
"scripts": {
  "dev": "parcel src/index.html",
  "production-build": "parcel build --public-url ./dist/ src/index.html",
}
```

# Babel
Javascript transpiler    
(use if not using parcel for handling babel with parcel's default config)

## Install
```shell
npm install -D babel-eslint @babel/core @babel/preset-env @babel/plugin-proposal-class-properties @babel/preset-react
```

## .babelrc
```json
{
  "presets": ["@babel/preset-react", "@babel/preset-env"],
  "plugins": ["@babel/plugin-proposal-class-properties"]
}
```

## Update to .eslinstrc.json
```json
{
  "parser": "babel-eslint",
}
```

# TypeScript

## Install
```shell
npm install -D typescript
```

## Generate `tsconfig.json`
```shell
npx tsc --init. npx
```

## package.json script
```json
"scripts": {
  "typecheck": "tsc --noEmit"
}
```