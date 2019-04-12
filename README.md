# From the scratch

> In the end, this is not more than a boilerplate to start a project, the difference is here you are going to install and config every dependency in the future project. In a near future, you became a better developer, because you are the owner of your project, and you know exactly what is every dependency. You need to take control of the wild magic!

## Github :octocat:

1. Create a GitHub repository with an marvelous name, for example *marvelousName*!
   ![create a new github repository](https://raw.githubusercontent.com/pablovegau/fromTheScratch/master/tutorial/images/Create_a_new_github_repository.jpeg)
2. After clicking the *Create repository* button follow the instructions to push your first commit
   ![github instructions to push the first commit](https://raw.githubusercontent.com/pablovegau/fromTheScratch/master/tutorial/images/Intruccions_to_first_commit.jpeg)


## NPM

- [About NPM](https://docs.npmjs.com/about-npm/)
- [NPM Home webpage](https://www.npmjs.com/)
- [NPM Docs](https://docs.npmjs.com/)

1. Run `npm init` and answer the questions (or `npm init -y` to avoid the questions)

> Now you have a new file in your project root, named package.json


## .gitignore

- [Git documentation about gitignore](https://git-scm.com/docs/gitignore)
- [gitignore.io -> Create useful .gitignore files for your project](https://www.gitignore.io/)

1. :pencil: Create a new file named *.gitignore*

  *.gitignore* example file:
  ```
  vscode
  node_modules
  coverage
  dist
  ```


## ESLint

- [ESLint website](https://eslint.org/)
- [ESLint GitHub page](https://github.com/eslint/eslint)

1. :electric_plug: Install [eslint](https://www.npmjs.com/package/eslint) as a devDependency:
```
npm install --save-dev eslint
```

2. Now you can:
   - :arrow_forward: Run into the command line `./node_modules/.bin/eslint --init` and follow the questions to config the initial ESLint file (.eslintrc).
   - Or :pencil: create in the root of your project a new file named *.eslintrc*, here belong the configurations related with eslint and install 'eslint-plugin-react' **DO THIS CORRECT**

example of *.eslintrc* for React
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

3. Add into the *package.json* the next scripts:

```json
"scripts": {
  "lint": "eslint \"**/*.{js,jsx}\"",
  "validate": "npm run lint"
}
```

#### :beginner: Check the progress :beginner:
1. Create a folder named **src**.
2. Inside of it create a file with **wathevername.js** and write some javascript code like this:
```javascript
const num1 = 5
const num2 = 7
const num3 = 10 // 'num3' is assigned a value but never used.eslint(no-unused-vars)
const text = "My cats Auri and Lyra are so cute" // 'text' is assigned a value but never used.eslint(no-unused-vars)

console.log(num1 + num2) // Unexpected console statement.eslint(no-console)
```

> If you see this errors is perfect :ok_hand:, now if you run :arrow_forward: `"lint": "eslint \"**/*.{js,jsx}\""`  you can see the same errors in the console

#### :vs: VSCode users:
- :electric_plug: Install ESLint plugin for VSCode.
- User configuration recommended:
```json
"eslint.autoFixOnSave": true,
"eslint.alwaysShowStatus": true
```

## Prettier

- [Prettier website](https://prettier.io/)
- [Prettier GitHub page](https://github.com/prettier/prettier)

1. :electric_plug: Install [prettier](https://www.npmjs.com/package/prettier), [eslint-config-prettier](https://www.npmjs.com/package/eslint-config-prettier), [eslint-plugin-prettier](https://www.npmjs.com/package/eslint-plugin-prettier) as a devDependency:

```
npm i -D prettier eslint-config-prettier eslint-plugin-prettier
```

2. :pencil: Create in the root of your project a new file named *.prettierrc*, here belong the configurations related with prettier.
   - [Options · Prettier](https://prettier.io/docs/en/options.html)
   - [Configuration File · Prettier](https://prettier.io/docs/en/configuration.html)

example of *.prettierrc*
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

3. For a better development experience is better integrate prettier with eslint, add this lines to your *.eslintrc* file.
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

4. Add into the *package.json* the next scripts:
```json
"scripts": {
  "format": "npm run prettier -- --write",
  "prettier": "prettier \"**/*.{js,jsx,css,json}\"",
  "validate": "npm run lint && npm run prettier -- --list-different"
}
```

5. :pencil: Create in the root of your project a new file named *.prettierignore*, here belong the ignored files by prettier.

#### :beginner: Check the progress :beginner:
1. Now you can check the **whateverfile.js**, you can see a lot of errors related with the code formatting.
2. :arrow_forward: Run `"npm run format"` and magic is done, prettier format your code.
    - If you have configured your editor, when you save the file, prettier format your code.

> If you like to play with prettier features, this is the perfect place [Prettier - playground](https://prettier.io/playground/)

#### :vs: VSCode users:
- :electric_plug: Install Prettier plugin for VSCode.
- User configuration recommended:
```json
"editor.formatOnSave": true,
"prettier.requireConfig": true
```


## Husky

- [Husky GitHub page](https://github.com/typicode/husky)

1. :electric_plug: Install [husky](https://www.npmjs.com/package/husky) as a devDependency:

```
`npm install --save-dev husky`
```

2. Add to the *package.json* the husky config:

```json
"husky": {
  "hooks": {
    "pre-commit": "npm run validate",
    "pre-push": "npm run validate"
  }
}
```

> Now when we do a commit or a push, husky is watching and execute the proper hook

#### :beginner: Check the progress :beginner:
1. Return the code to the previous point to format the code with Prettier
2. With the errors in **whateverfile.js** try to commit the changes
3. If everything is fine the commit fails because the lint throw the 3 previous errors

> Don't fix the errors yet, we will fix it in the next section


## Lint staged

- [Lint-staged GitHub page](https://github.com/okonet/lint-staged)

1. :electric_plug: Install [lint-staged](https://www.npmjs.com/package/lint-staged) as a devDependency:

```
npm install --save-dev lint-staged
```

2. Modify in the *package.json* the husky configuration using lint-staged:

```json
"husky": {
  "hooks": {
    "pre-commit": "lint-staged",
    "pre-push": "lint-staged"
  }
}
```

3. :pencil: Create a new file, named *.lintstagedrc*:

```json
{
  "linters": {
    "**/*.{js,jsx}": ["eslint"],
    "**/*.{js,jsx,css,json}": ["prettier --write", "git add"]
  }
}
```

#### :beginner: Check the progress :beginner:

1. With the errors in **whateverfile.js** try to commit the changes.
2. if everything is fine the commit fails because the lint throw the 3 previous errors.
3. Now you can fix this errors and commit 😁



---

- Run -> :arrow_forward:
- Install -> :electric_plug:
- Create -> :pencil:
- Check the progress -> #### :beginner: Check the progress :beginner:
- VSCode -> #### :vs: VSCode users:
