# React from the scratch

> In the end, this is not more than a boilerplate to start a project, the difference is here you are going to install and config every dependency in the future project. In a near future, you became a better developer, because you are the owner of your project, and you know exactly what is every dependency. You need to take control of the wild magic!

---

#### Courses that I have done before to write this guide:

##### React
- [Complete Intro to React](https://frontendmasters.com/courses/complete-react-v5) by [Brian Holt](https://twitter.com/holtbt)
- [Intermediate React](https://frontendmasters.com/courses/intermediate-react-v2/) by [Brian Holt](https://twitter.com/holtbt)

##### Webpack
- [Learn Using Webpack for the First Time – Webpack 4 Fundamentals](https://frontendmasters.com/courses/webpack-fundamentals/using-webpack-for-the-first-time/) by [Sean Larkin](https://twitter.com/thelarkinn)
- [Web Performance: Learn to Make Your Websites Load Fast with Webpack 4](https://frontendmasters.com/courses/performance-webpack/) by [Sean Larkin](https://twitter.com/thelarkinn)

##### Testing
- [JavaScript Testing Practices and Principles](https://frontendmasters.com/courses/testing-practices-principles/) by [Kent C. Dodds](https://twitter.com/kentcdodds)
- [Testing React Applications](https://frontendmasters.com/courses/testing-react/) by [Kent C. Dodds](https://twitter.com/kentcdodds)
- [Testing Javascript](https://testingjavascript.com/) by [Kent C. Dodds](https://twitter.com/kentcdodds)

---

## Version control

### Git

> 📖 **Git** is a **distributed version-control** system for tracking changes in **source code** during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows. [Wikipedia](https://en.wikipedia.org/wiki/Git)

### Github :octocat:

> 📖 GitHub is an American company that provides hosting for software development version control using Git [Wikipedia](https://en.wikipedia.org/wiki/GitHub)

1. Create a GitHub repository with an marvelous name, for example *marvelousName*!
   ![create a new github repository](https://raw.githubusercontent.com/pablovegau/fromTheScratch/master/tutorial/images/Create_a_new_github_repository.jpeg)
2. After clicking the *Create repository* button follow the instructions to push your first commit
   ![github instructions to push the first commit](https://raw.githubusercontent.com/pablovegau/fromTheScratch/master/tutorial/images/Intruccions_to_first_commit.jpeg)


## NPM

> 📖 **npm** is a **package manager** for the **JavaScript** programming language. It is the default package manager for the JavaScript runtime environment **Node.js**. It consists of a command line client, also called npm, and an **online database** of public and paid-for private packages, called the npm registry. [Wikipedia](https://en.wikipedia.org/wiki/Npm_(software))

- [About NPM](https://docs.npmjs.com/about-npm/)
- [NPM Home webpage](https://www.npmjs.com/)
- [NPM Docs](https://docs.npmjs.com/)

1. ▶️ Run `npm init` and answer the questions (or `npm init -y` to avoid the questions)

> Now you have a new file in your project root, named ***package.json***


## .gitignore

> 📖 A **gitignore** file specifies intentionally untracked files that Git should ignore

- [Git documentation about gitignore](https://git-scm.com/docs/gitignore)
- [gitignore.io -> Create useful .gitignore files for your project](https://www.gitignore.io/)

1. 📄 Create a new file named ***.gitignore*** in the project root

  ```
  vscode
  node_modules
  coverage
  dist
  ```


## ESLint

> 📖 **ESLint** is a **static code analysis** tool for identifying problematic patterns found in **JavaScript** code. Rules in ESLint are configurable, and customized rules can be defined and loaded. ESLint covers both **code quality** and coding style issues. ESLint supports current standards of ECMAScript, and experimental syntax from drafts for future standards. [Wikipedia](https://en.wikipedia.org/wiki/ESLint)

> *Note about ESLint definition: We are going to use Prettier for coding style issues. We are going to speak about Prettier in the next point.*

- [ESLint website](https://eslint.org/)
- [ESLint GitHub page](https://github.com/eslint/eslint)

1. 🔌 Install [eslint](https://www.npmjs.com/package/eslint) as a devDependency:

```
npm install --save-dev eslint
```

2. Now you can:
   - ▶️ Run into the command line `./node_modules/.bin/eslint --init` and follow the questions to config the initial ESLint file. When the installer ask about install ***eslint-plugin-react*** say yes.
   - Or 📄create a new file named ***.eslintrc*** in the root of your project, here belong the configurations related with **ESLint**. Then 🔌 install manually ***eslint-plugin-react*** as devDependency: `npm install --save-dev eslint-plugin-react`

> 📖 ***eslint-plugin-react*** add React specific linting rules for ESLint

Example of ***.eslintrc***
```json
{
    "extends": ["eslint:recommended"],
    "env": {
        "browser": true,
        "es6": true,
        "node": true
    },
    "parserOptions": {
        "ecmaFeatures": {
            "jsx": true
        },
        "ecmaVersion": 2018,
        "sourceType": "module"
    },
    "plugins": ["react"],
    "globals": {
        "React": true
    },
    "rules": {}
}
```

3. ✏️ Modify ***package.json*** adding ESLint scripts

```json
"scripts": {
  "lint": "eslint \"**/*.{js,jsx}\"",
  "validate": "npm run lint"
}
```

#### 🔰Check the progress 🔰

1. 📁Create a folder named ***src***.
2. Inside of *src* 📄create a file named ***wathevername.js***
3. Inside of ***wathevername.js*** add this code:

```javascript
const num1 = 5
const num2 = 7
const num3 = 10 // 'num3' is assigned a value but never used.eslint(no-unused-vars)
const text = "My cats Auri and Lyra are so cute" // 'text' is assigned a value but never used.eslint(no-unused-vars)

console.log(num1 + num2) // Unexpected console statement.eslint(no-console)
```

> If you see this errors is perfect 👌, now if you run ▶️ `"lint": "eslint \"**/*.{js,jsx}\""`  you can see the same errors in the console

#### 🆚VSCode users:

- 🔌Install ESLint plugin for VSCode.
- User configuration recommended:
```json
"eslint.autoFixOnSave": true,
"eslint.alwaysShowStatus": true
```

## Prettier

> 📖 Prettier is an opinionated code formatter. It removes all original styling and ensures that all outputted code conforms to a consistent style.

- [Prettier website](https://prettier.io/)
- [Prettier GitHub page](https://github.com/prettier/prettier)

1. 🔌Install [prettier](https://www.npmjs.com/package/prettier) as a devDependency:

```
npm install --save-dev prettier
```

2. 🔌 Install [eslint-config-prettier](https://www.npmjs.com/package/eslint-config-prettier) as a devDependency:

> 📖 Turns off all rules that are unnecessary or might conflict with Prettier

```
npm install --save-dev eslint-config-prettier
```

3. 🔌 Install [eslint-plugin-prettier](https://www.npmjs.com/package/eslint-plugin-prettier) as a devDependency

> 📖 Runs Prettier as an ESLint rule and reports differences as individual ESLint issues

```
npm install --save-dev eslint-plugin-prettier
```

> 📖 If you prefer 🔌 install all the packages at the same time

```
npm i -D prettier eslint-config-prettier eslint-plugin-prettier
```

2. 📄 Create in the root of your project a new file named ***.prettierrc***, here belong the configurations related with prettier.

   - [Options · Prettier](https://prettier.io/docs/en/options.html)
   - [Configuration File · Prettier](https://prettier.io/docs/en/configuration.html)

example of ***.prettierrc***
```json
{
  "useTabs": false,
  "printWidth": 120,
  "tabWidth": 2,
  "singleQuote": true,
  "trailingComma": "all",
  "jsxBracketSameLine": false,
  "semi": true,
  "bracketSpacing": true,
  "arrowParens": "avoid"
}
```

3. For a better development experience is better integrate prettier with eslint, ✏️modify your ***.eslintrc*** file adding prettier, plugin, extends and rules

  - [Integrating with ESLint · Prettier](https://prettier.io/docs/en/eslint.html)

```json
{
  "plugins": ["prettier"],
  "extends": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```

4. ✏️ Modify ***package.json*** adding Prettier scripts

```json
"scripts": {
  "format": "npm run prettier -- --write",
  "prettier": "prettier \"**/*.{js,jsx,css,json}\"",
  "validate": "npm run lint && npm run prettier -- --list-different"
}
```

5. If you need avoid some files, 📄 create a new file named ***.prettierignore*** in the root of your project, here belong the ignored files by prettier.

#### 🔰Check the progress 🔰

1. Now you can check the ***whateverfile.js*** and see a lot of errors related with the code formatting.

2. ▶️ Run `"npm run format"` and magic is done, prettier format your code.
    - If you have configured your editor, when you save the file, prettier format your code.

> If you like to play with prettier features, this is the perfect place [Prettier - playground](https://prettier.io/playground/)

#### 🆚 VSCode users:

- 🔌 Install Prettier plugin for VSCode.
- User configuration recommended:

```json
"editor.formatOnSave": true,
"prettier.requireConfig": true
```

## Husky

> 📖 Easy Git hooks control (git hooks are custom scripts, which can be run automatically when specific events occur)

- [Husky GitHub page](https://github.com/typicode/husky)

1. 🔌 Install [Husky](https://www.npmjs.com/package/husky) as a devDependency:

```
`npm install --save-dev husky`
```

2. ✏️ Modify ***package.json*** adding **Husky** config:

```json
"husky": {
  "hooks": {
    "pre-commit": "npm run validate",
    "pre-push": "npm run validate"
  }
}
```

> Now when we do a commit or a push, Husky is watching and execute the proper hook

#### 🔰Check the progress 🔰
1. ⏮Return the code to the previous point, before format the code with Prettier
2. With the errors in ***whateverfile.js*** try to commit the changes
3. If everything is fine the commit fails because the lint throw the 3 previous errors

> Don't fix the errors yet, we will fix it in the next section


## Lint staged

- [Lint-staged GitHub page](https://github.com/okonet/lint-staged)

1. 🔌 Install [lint-staged](https://www.npmjs.com/package/lint-staged) as a devDependency:

```
npm install --save-dev lint-staged
```

2. ✏️ Modify in the ***package.json*** the **Husky** configuration, now using **lint-staged**:

```json
"husky": {
  "hooks": {
    "pre-commit": "lint-staged",
    "pre-push": "lint-staged"
  }
}
```

3.  📄Create a new file, named ***.lintstagedrc***:

```json
{
  "linters": {
    "**/*.{js,jsx}": ["eslint"],
    "**/*.{js,jsx,css,json}": ["prettier --write", "git add"]
  }
}
```

#### 🔰 Check the progress 🔰

1. With the errors in ***whateverfile.js*** try to commit the changes.
2. If everything is fine the commit fails because the lint throw the 3 previous errors.
3. Now you can fix this errors and commit 😁


## Webpack

> 📖 At its core, webpack is a static module bundler for modern JavaScript applications. When webpack processes your application, it internally builds a dependency graph which maps every module your project needs and generates one or more bundles.

- [Webpack official site](https://webpack.js.org/)
- [Webpack · GitHub](https://github.com/webpack)
- [Webpack-contrib · GitHub](https://github.com/webpack-contrib)
- [Webpack NPM](https://www.npmjs.com/package/webpack)

---

#### Courses: (I highly recommend this two courses to deep into Webpack by [Sean Larkin](https://twitter.com/thelarkinn))

- [Learn Using Webpack for the First Time – Webpack 4 Fundamentals - by Sean Larkin](https://frontendmasters.com/courses/webpack-fundamentals/using-webpack-for-the-first-time/)
- [Web Performance: Learn to Make Your Websites Load Fast with Webpack 4 - by Sean Larkin](https://frontendmasters.com/courses/performance-webpack/)

---

1. 🔌 Install [webpack](https://www.npmjs.com/package/webpack) and [webpack-cli](https://www.npmjs.com/package/webpack-cli) as a devDependency:

```
npm install --save-dev webpack webpack-cli
```

2. 🔌 Install [html-webpack-plugin](https://www.npmjs.com/package/html-webpack-plugin) as a devDependency:

> 📖 **html-webpack-plugin** simplifies creation of HTML files to serve your bundles

````
npm install --save-dev html-webpack-plugin
````

3. 🔌 Install [webpack-dev-server](https://www.npmjs.com/package/webpack-dev-server) as a devDependency:

> 📖 Use webpack with a development server that provides live reloading. This should be used for development only

```
npm install --save-dev webpack-dev-server
```

4. 🔌 Install [webpack-merge](https://www.npmjs.com/package/webpack-merge) as a devDependency:

> 📖 **webpack-merge** provides a merge function that concatenates arrays and merges objects creating a new object

```
npm install --save-dev webpack-merge
```

> 📖 If you prefer 🔌 install all the packages at the same time

```
npm i -D webpack webpack-cli html-webpack-plugin webpack-dev-server webpack-merge
```

5. We need to create some files:

- root 📁
  - build-utils 📁
    - webpack.development.js 📄
    - webpack.production.js 📄
  - webpack.config.js 📄

*webpack.config.js*
```javascript
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpackMerge = require('webpack-merge');

const modeConfig = env => require(`./build-utils/webpack.${env}`)(env);

module.exports = ({ mode } = { mode: 'production' }) =>
  webpackMerge(
    {
      mode: mode,
      output: {
        filename: 'bundle.js',
      },
      plugins: [new HtmlWebpackPlugin(), new webpack.ProgressPlugin()],
    },
    modeConfig(mode),
  );
```

*webpack.development.js*
```javascript
module.exports = () => ({});
```

*webpack.production.js*
```javascript
module.exports = () => ({});
```

> Now we have the base configuration for webpack, and we can add independent features for each environment, it’s time to use a loader for css files and use the power of the environment splitting.

6. 🔌 Install [css-loader](https://www.npmjs.com/package/css-loader) and [style-loader](https://www.npmjs.com/package/style-loader) as a devDependency:

> 📖 **css-loader** interprets @import and url() like import/require() and will resolve them.

> 📖 **style-loader** adds CSS to the DOM by injecting a style tag.

```
npm install --save-dev css-loader style-loader
```

7. ✏️ Modify the ***webpack.development.js*** file

```javascript
module.exports = () => ({
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
});
```

8. 🔌 Install [mini-css-extract-plugin](https://www.npmjs.com/package/mini-css-extract-plugin) as a devDependency:

> 📖 **mini-css-extract-plugin** extracts CSS into separate files. It creates a CSS file per JS file which contains CSS

```
npm install --save-dev mini-css-extract-plugin
```

9. ✏️ Modify the ***webpack.production.js*** file

```javascript
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

module.exports = () => ({
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [MiniCssExtractPlugin.loader, 'css-loader'],
      },
    ],
  },
  plugins: [new MiniCssExtractPlugin()],
});
```

> In order to use images like *.jpg or *.png we need another loader

10. 🔌 Install [file-loader](https://www.npmjs.com/package/file-loader) and [url-loader](https://www.npmjs.com/package/url-loader) as a devDependency:

> 📖 ***file-loader*** resolves import/require() on a file into a url and emits the file into the output directory.

> 📖 ***url-loader*** is a loader for webpack which transforms files into base64 URIs.

```
npm install --save-dev file-loader url-loader
```

*webpack.config.js*
```javascript
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpackMerge = require('webpack-merge');

const modeConfig = env => require(`./build-utils/webpack.${env}`)(env);

module.exports = ({ mode } = { mode: 'production' }) =>
  webpackMerge(
    {
      mode: mode,
      module: {
        rules: [
          {
            test: /\.jpe?g$/,
            use: [
              {
                loader: 'url-loader',
                options: {
                  limit: 5000,
                },
              },
            ],
          },
        ],
      },
      output: {
        filename: 'bundle.js',
      },
      plugins: [new HtmlWebpackPlugin(), new webpack.ProgressPlugin()],
    },
    modeConfig(mode),
  );
```

11. 🔌 Install [clean-webpack-plugin](https://www.npmjs.com/package/clean-webpack-plugin) as a devDependency:

> 📖 **clean-webpack-plugin** is plugin to remove/clean your build folder(s).

```
npm install --save-dev clean-webpack-plugin
```

*webpack.config.js*
```javascript
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');
const webpackMerge = require('webpack-merge');

const modeConfig = env => require(`./build-utils/webpack.${env}`)(env);

const pathsToClean = { template: './dist' };

module.exports = ({ mode } = { mode: 'production' }) =>
  webpackMerge(
    {
      mode: mode,
      module: {
        rules: [
          {
            test: /\.jpe?g$/,
            use: [
              {
                loader: 'url-loader',
                options: {
                  limit: 5000,
                },
              },
            ],
          },
        ],
      },
      output: {
        filename: 'bundle.js',
      },
      plugins: [
        new HtmlWebpackPlugin(),
        new webpack.ProgressPlugin(),
        new { CleanWebpackPlugin }(pathsToClean)
      ],
    },
    modeConfig(mode),
  );
```

12. We need to create some files in order to use **presets**

- root 📁
  - build-utils 📁
      - presets 📁 **NEW**
        - webpack.analyze.js 📄 **NEW**
        - webpack.compress.js 📄 **NEW**
      - loadPresets.js 📄 **NEW**
      - webpack.development.js 📄
      - webpack.production.js 📄
- webpack.config.js 📄

*webpack.config.js*
```javascript
const webpack = require('webpack');
const webpackMerge = require('webpack-merge');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');
const modeConfig = env => require(`./build-utils/webpack.${env}`)(env);
const loadPresets = require('./build-utils/loadPresets');

const pathsToClean = { template: './dist' };

module.exports = ({ mode, presets } = { mode: 'production', presets: [] }) =>
  webpackMerge(
    {
      mode: mode,
      module: {
        rules: [
          {
            test: /\.jpe?g$/,
            use: [
              {
                loader: 'url-loader',
                options: {
                  limit: 5000,
                },
              },
            ],
          },
        ],
      },
      output: {
        filename: 'bundle.js',
      },
      plugins: [
        new HtmlWebpackPlugin(),
        new webpack.ProgressPlugin(),
        new { CleanWebpackPlugin }(pathsToClean)
      ],
    },
    modeConfig(mode),
    loadPresets({ mode, presets }),
  );
```

*loadPresets.js*
```javascript
const webpackMerge = require('webpack-merge');

const applyPresets = (env = { presets: [] }) => {
  const presets = env.presets || [];
  /** @type {string[]} */
  const mergedPresets = [].concat(...[presets]);
  const mergedConfigs = mergedPresets.map(presetName => require(`./presets/webpack.${presetName}`)(env));

  return webpackMerge({}, ...mergedConfigs);
};

module.exports = applyPresets;
```
13. 🔌 Install [webpack-bundle-analyzer](https://www.npmjs.com/package/webpack-bundle-analyzer) as a devDependency:

> 📖 **webpack-bundle-analyzer** visualize size of webpack output files with an interactive zoomable treemap.

```
npm install --save-dev webpack-bundle-analyzer
```

*webpack.analyze.js*
```javascript
const WebpackBundleAnalyzer = require('webpack-bundle-analyzer').BundleAnalyzerPlugin;

module.exports = () => ({
  plugins: [new WebpackBundleAnalyzer()],
});
```

14. 🔌 Install [compression-webpack-plugin](https://www.npmjs.com/package/compression-webpack-plugin) as a devDependency:

> 📖 **compression-webpack-plugin** prepare compressed versions of assets to serve them with Content-Encoding.

```
npm install --save-dev compression-webpack-plugin
```

*webpack.compress.js*
```javascript
const CompressionWebpackPlugin = require('compression-webpack-plugin');

module.exports = () => ({
  plugins: [new CompressionWebpackPlugin()],
});
```

15. ✏️ Modify ***package.json*** adding Webpack scripts

```javascript
"webpack": "webpack",
"webpack-dev-server": "webpack-dev-server",
"dev": "npm run webpack -- --env.mode development",
"prod": "npm run webpack -- --env.mode production",
"prod:analyze": "npm run prod -- --env.presets analyze",
"prod:compress": "npm run prod -- --env.presets compress",
"start": "npm run webpack-dev-server -- --env.mode development --watch --open --hot",
```

16. In order to enhance the debbuging process webpack bring us the [Devtool](https://webpack.js.org/configuration/devtool/) property. We use the default value for production environment. For development environment we are going to use the ‘inline-source-map’ value, with this value you can see in your devTools the code as you can see it in your code editor.

webpack.development.js
```javascript
module.exports = () => ({
  devtool: 'inline-source-map',
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
});
```

#### 🔰 Check the progress 🔰

1. In your *src* folder, 💣 delete all the files and 📄 create a file named ***index.js***:

```javascript
const num1 = 5;
const num2 = 5;

console.log(num1 + num2);
```

2. ▶️ Run in the console de `dev` script, if everything is correct, in the root of your project it has been created a *dist* folder, with two files: ***index.html*** and ***bundle.js***, and, of course in the console you don’t see an error!


## React

1. 🔌 Install [React](https://www.npmjs.com/package/react) as a dependency:

```
npm install --save react
```

2. 🔌 Install [React-dom](https://www.npmjs.com/package/react-dom) as a dependency:

> 📖 This package serves as the entry point to the DOM and server renderers for React. It is intended to be paired with the generic React package, which is shipped as react to npm.

```
npm install --save react-dom
```

3. Modify ***.eslintrc*** with the React extension:

*eslintrc*
```json
"extends": [
    "plugin:react/recommended"
]
```

## Babel

1. 🔌 Install [@babel/core](https://www.npmjs.com/package/@babel/core) as a devDependency:

> 📖 **@babel/core** transforms your ES6 code into ES5

```
npm install --save-dev @babel/core
```

2. 🔌 Install [@babel/preset-env](https://www.npmjs.com/package/@babel/preset-env) as a devDependency:

> 📖 **@babel/preset-env** determines which transformations/plugins to use and polyfills (provide modern functionality on older browsers that do not natively support it) based on the browser matrix you want to support

```
npm install --save-dev @babel/preset-env
```

3. 🔌 Install [@babel/preset-react](https://www.npmjs.com/package/@babel/preset-react) as a devDependency:

> 📖 **@babel/preset-react** babel preset for all React plugins, for example turning JSX into functions

```
npm install --save-dev @babel/preset-react
```

4. 🔌 Install [babel-loader](https://www.npmjs.com/package/babel-loader) as a devDependency:

> 📖 **babel-loader** webpack helper to transform your JavaScript dependencies (for example, when you import your components into other components) with Babel

```
npm install --save-dev babel-loader
```

5. 🔌 Install [@babel/plugin-proposal-class-properties](https://www.npmjs.com/package/@babel/plugin-proposal-class-properties) as a devDependency:

> 📖 **@babel/plugin-proposal-class-properties** this plugin transforms es2015 static class properties as well as properties declared with the es2016 property initializer syntax

```
npm install --save-dev @babel/plugin-proposal-class-properties
```

6. 🔌 Install [babel-eslint](https://www.npmjs.com/package/babel-eslint) as a devDependency:

> 📖 **babel-eslint** allows you to lint all valid Babel code with the fantastic ESLint

```
npm install --save-dev babel-eslint
```

> 📖 If you prefer 🔌 install all the packages at the same time

```
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader @babel/plugin-proposal-class-properties babel-eslint
```

> Temporary descriptions by https://reancode.wordpress.com/2018/05/21/why-using-babel-in-react-js/

2. ✏️ Modify the ***webpack.config.js*** to use **babel-loader** and change how to use the **html-webpack-plugin**:

```javascript
const webpack = require('webpack');
const webpackMerge = require('webpack-merge');
const HtmlWebPackPlugin = require('html-webpack-plugin');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');
const modeConfig = env => require(`./build-utils/webpack.${env}`)(env);
const loadPresets = require('./build-utils/loadPresets');

const pathsToClean = { template: './dist' };

const htmlPlugin = new HtmlWebPackPlugin({
  template: './src/index.html',
  filename: './index.html',
});

module.exports = ({ mode, presets } = { mode: 'production', presets: [] }) =>
  webpackMerge(
    {
      mode: mode,
      module: {
        rules: [
          {
            test: /\.jpe?g$/,
            use: [
              {
                loader: 'url-loader',
                options: {
                  limit: 5000,
                },
              },
            ],
          },
          {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
              loader: 'babel-loader',
            },
          },
        ],
      },
      output: {
        filename: 'bundle.js',
      },
      plugins: [htmlPlugin, new webpack.ProgressPlugin(), new { CleanWebpackPlugin }(pathsToClean)],
    },
    modeConfig(mode),
    loadPresets({ mode, presets }),
  );
```

3. ✏️ Modify ***.eslint*** to add the **babel-eslint** like a parser:

```javascript
{
  "extends": [
    "eslint:recommended",
    "prettier",
    "prettier/react",
    "plugin:react/recommended"
  ],
  "env": {
    "browser": true,
    "es6": true,
    "node": true
  },
  "parser": "babel-eslint", // ⬅️⬅️⬅️✅
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": 2018,
    "sourceType": "module"
  },
  "plugins": ["react", "prettier"],
  "globals": {
    "React": true
  },
  "rules": {
    "prettier/prettier": "error",
    "no-console": "off"
  }
}
```

4. 📄 Create a new file in the project root, named ***.babelrc***:

```javascript
{
  "presets": [
    "@babel/preset-react",
    [
      "@babel/preset-env",
      {
        "targets": {
          "browsers": ["last 2 versions"]
        }
      }
    ]
  ],
  "plugins": ["@babel/plugin-proposal-class-properties"],
  "sourceMaps": true,
  "retainLines": true
}
```

#### 🔰Check the progress 🔰

1. Into our **src** folder we are going to 📄 create 3 files: ***index.html***, ***index.js***, ***index.css***:

*index.html*
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Character selector</title>
</head>

<body>
  <section id="root"></section>
</body>

</html>
```

*index.css*
```css
.puurrProgramming {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 5rem;
}

.puurrProgramming img {
  width: 600px;
  padding-top: 1rem;
}
```

*index.js*
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';

function App() {
  return (
    <div className="puurrProgramming">
      At home doing puurr programming :D
      <img src="https://goo.gl/6ZvMCL" />
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

2. Now if everything is fine and you run in your console `npm start` it open your navigator and show a red Hello World!


## Testing


### Cypress

> 📖 Cypress is a platform for writing and automating UI tests.

1. 🔌 Install [cypress](https://www.npmjs.com/package/cypress) as a devDependency

```
npm install --save-dev cypress
```

2. 🔌 Install [eslint-plugin-cypress](https://www.npmjs.com/package/eslint-plugin-cypress) as a devDependency

> 📖 ***eslint-plugin-cypress*** is an ESLint plugin for Cypress tests

```
npm install --save-dev eslint-plugin-cypress
```

3. ▶️ Run cypress for first time, whit that we are going to 📁/ 📄 create all the necessary folders and files for work with Cypress

```
npx cypress open
```

> This command open cypress and create a bunch of examples and other folders, also create a *cypress.json* file in the project root

4. ✏️ Modify ***.eslintrc*** adding in the plugin array the ***eslint-plugin-cypress***

```json
{
  "plugins":[
      "cypress"
  ]
}
```

5. ✏️ Modify ***.eslintrc*** adding in the env array the **”cypress/globals”: true**

```javascript
{
  "env":[
      "cypress/globals": true
  ]
}
```

6. ✏️ Modify ***.gitignore*** file adding the cypress files to ignore

```
cypress/videos
cypress/screenshots
```

7. Now we can 💣 delete the examples folder
8. ✏️ Modify the *baseUrl* for our tests in ***cypress.json***

```json
{
  "baseUrl": "http://localhost:8080"  // 8080 or whatever port use your application
}
```

9. ✏️ Rename the **integration** folder for **e2e**
10. ✏️ Modify the *integrationFolder* in ***cypress.json***

```json
{
  "baseUrl": "http://localhost:8080",
  "integrationFolder": "cypress/e2e"
}
```

11. Also you can change the default viewport dimensions in ***cypress.json***

```json
{
  "baseUrl": "http://localhost:8080",
  "integrationFolder": "cypress/e2e",
  "viewportHeight": 600,  // 600 or whatever you prefer
  "viewportWidth": 1000  // 1000 or whatever you prefer
}
```

12. 🔌 Install [start-server-and-test](https://www.npmjs.com/package/start-server-and-test) as a devDependency

> 📖 ***start-server-and-test*** starts the server, waits for URL, then runs test command; when the tests end, shuts down the server

```
npm install --save-dev start-server-and-test
```

13. ✏️ Modify the ***package.json*** adding the **Cypress** scripts and ✏️ modify the *validate* script

```json
"cy:run": "cypress run",
"cy:open": "cypress open",
"pretest:e2e:run": "npm run prod",
"test:e2e:run": "start-server-and-test start http://localhost:8080/ cy:run",
"test:e2e:dev": "start-server-and-test start http://localhost:8080/ cy:open",
"validate": "npm run lint && npm run prettier -- --list-different && npm run test:e2e:run"
```

14. ✏️ Modify in ***package.json*** the *husky* configuration

```javascript
"husky": {
  "hooks": {
     "pre-commit": "lint-staged && test:e2e:run",
     "pre-push": "lint-staged && test:e2e:run"
  }
}
```

15. ✏️ Modify cypress/plugins/index.js

```javascript
// eslint-disable-next-line no-unused-vars
module.exports = (on, config) => {}
```

### Cypress-testing-library

> 📖 Simple and complete custom Cypress commands and utilities that encourage good testing practices

1. 🔌 Install [@testing-library/cypress](https://www.npmjs.com/package/@testing-library/cypress) as a devDependency

```
npm install —save-dev @testing-library/cypress
```

2. ✏️ Modify *cypress/support/index.js* and add the ***@testing-library/cypress*** extensions commands

```javascript
import '@testing-library/cypress/add-commands'
import './commands'
```

#### 🔰Check the progress 🔰

1. First of all is necessary to modify the ✏️ ***kitten.js*** file adding a data-tested in order to Cypress can find the node

```javascript
import React from 'react';

function kitten() {
  return (
    <div className="cuttiesKitten" data-testid="kitten">
      At home doing some puur programming :D
      <img src="https://goo.gl/6ZvMCL" alt="the cuttiest kitten programming" />
    </div>
  );
}

export default kitten;
```

2. After that we can create a new test named 📄 ***showMeTheKitten.e2e.js*** into the e2e test folder create before

```javascript
describe('Kitten app', () => {
  it('should a cute kitten when you click the button', () => {
    cy.visit('/')
      .getByText('Show')
      .click()
      .getByTestId('kitten')
      .should("have.text", "At home doing some puur programming :D")
  });
});
```

3. Finally you need to run `npm run cy:open`, if everything is fine we see all green in the navigator rised by Cypress

### Jest

> 📖 Jest is a JavaScript Testing Framework

1. 🔌 Install [jest](https://www.npmjs.com/package/jest) as a devDependency:

```
`npm install --save-dev jest`
```

2. 🔌 Install [react-test-renderer](https://www.npmjs.com/package/react-test-renderer) as a devDependency:

> 📖 react-test-renderer makes it easy to grab a snapshot of the "DOM tree" rendered by a React DOM component without using a browser or jsdom.
```
`npm install --save-dev react-test-renderer`
```

3. ✏️ Modify your ***.eslintrc*** adding jest as a environment

```javascript
"env": {
  "jest": true
}
```

4. ✏️ Modify ***package.json*** adding jest scripts

```json
"test": "jest",
"test:watch": "jest --watch",
"test:coverage": "jest --coverage",
"validate": "npm run lint && npm run prettier -- --list-different && npm test && npm run test:coverage && npm run test:e2e:run"
```

5. ✏️ Modify the **husky** configuration in the ***package.json***

```javascript
"husky": {
  "hooks": {
     "pre-commit": "lint-staged && && npm test && npm run test:coverage && npm run test:e2e:run",
     "pre-push": "lint-staged && && npm test && npm run test:coverage && npm run test:e2e:run"
  }
}
```


### React-testing-library

> 📖 Simple and complete custom React DOM testing utilities that encourage good testing practices

1. 🔌 Install [react-testing-library](https://www.npmjs.com/package/react-testing-library) as a devDependency

```
npm install --save-dev @testing-library/react
```

### Jest dom

> 📖 Custom jest matchers to test the state of the DOM

1. 🔌 Install [jest-dom](https://www.npmjs.com/package/jest-dom) as a devDependency

```
npm install --save-dev jest-dom
```

2. Into our test we use all the methods of jest-dom writing:

```
import 'jest-dom/extend-expect'
```

🔰**Check the progress** 🔰

1. Into the src folder 📁 create a new folder named `__test__`, inside of it 📄 a new test file, for example ***app.spec.js***

```javascript
import 'jest-dom/extend-expect'; // ⬅️⬅️⬅️ Jest-dom
import '@testing-library/react/cleanup-after-each'; // ⬅️⬅️⬅️ React-testing-library
import React from 'react';
import { render } from '@testing-library/react
';
import App from '../app';

test('should save the world', () => {
  const { getByText } = render(<App />);

  const app = getByText(/show/i);
  expect(app).toBeTruthy();
  expect(app).not.toHaveClass('horribleKitten');
});
```

2. ▶️ Run `npm t` in your command line, and if all is green, everything is right


### Jest axe

> 📖 **Axe** is an accessibility testing engine for websites and others HTML-based user interfaces

> 📖 Custom **Jest** matcher **aXe** for testing accessibility

1. 🔌 Install [jest-axe](https://www.npmjs.com/package/jest-axe) as a devDependency

`npm install --save-dev jest-axe`

🔰**Check the progress** 🔰

1. Let’s add some code to ***kitten.js*** and 📄 create a new test file for it (in the *__test__* folder, create a ***kitten.spec.js*** file)

*kitten.js*
```javascript
import React, { Fragment } from 'react';

function kitten() {
  return (
    <Fragment>
      <div className="cuttiesKitten" data-testid="kitten">
        At home doing some puur programming :D
        <img src="https://goo.gl/6ZvMCL" alt="the cuttiest kitten programming" />
      </div>
      <form>
        <input type="radio" value="pwaaa" />
        Pwaaa -something bad will happen if you select this…-
        <input type="radio" value="nice" />
        Nice -maybe this is not correct too, probably something wrong… you know…-
        <input type="radio" value="gorgeous" />
        Gorgeous -Yes, this it the correct answer-
      </form>
    </Fragment>
  );
}

export default kitten;
```
---

<!-- TODO: modify babel polyfill -->
Babel polyfill was deprecated, use this: https://babeljs.io/docs/en/next/babel-polyfill.html

In order to use async/await in our test, we need 🔌install [@babel/polyfill](https://www.npmjs.com/package/@babel/polyfill)

```
npm install --save-dev @babel/polyfill
```
> Then import it in each test that use this functionality

```
import '@babel/polyfill'
```
---

*kitten.spec.js*
```javascript
import '@babel/polyfill'; // ⬅️⬅️⬅️ we speak about that when we start speaking about Jest
import 'jest-dom/extend-expect';
import '@testing-library/react/cleanup-after-each';
import React from 'react';
import { render } from '@testing-library/react';
import { axe, toHaveNoViolations } from 'jest-axe';
import Kitten from '../kitten';

expect.extend(toHaveNoViolations);

test('should whatever', async () => {
  const { container } = render(<Kitten />);
  const axeResults = await axe(container.innerHTML);
  expect(axeResults).toHaveNoViolations();
});
```

2. ▶️ Run `npm t` and if everything is correct this test not pass 🔴, and that’s cool, if you see this error: "Form elements must have labels (label)”, now you know that you need a label for your form elements

<!-- TODO: Crear un archivo de configuración de jest con las cosas comunes -->

---

- Run -> :arrow_forward:
- Install -> :electric_plug:
- Create -> :pencil:
- Check the progress -> #### :beginner: Check the progress :beginner:
- VSCode -> #### :vs: VSCode users:


<!-- TODO: Babel polyfill -->
> If you need use async/await in your test 🔌 install [@babel/polyfill](https://www.npmjs.com/package/@babel/polyfill)

```
npm install --save-dev @babel/polyfill
```
> Then import it in each test that use this functionality

```
import '@babel/polyfill'
```


<!-- TODO: Jest working with dynamic import. Add with the dynamic import section -->
6. Jest don’t work properly with the dynamic imports, if you are using this feature, you need to install a new package [babel-plugin-transform-dynamic-import  -  npm](https://www.npmjs.com/package/babel-plugin-transform-dynamic-import)

```
`npm install --save-dev babel-plugin-transform-dynamic-import`
```

7. Add to *.babelrc* the plugin:

```json
"plugins": [
  "transform-dynamic-import"
],
```

*REVISAR SI FUNCIONA  *@babel/plugin-syntax-dynamic-import*
