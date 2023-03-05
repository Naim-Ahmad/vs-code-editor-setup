
 # vs-code-editor-setup
vs code editor setup for react project. You can use any editor but as I personally prefer VS Code. I will give some instructions about how I prefer VS code to be setup for React applications.

<h2> Plugin </h2>
<p>You need to install the below plugins:</p>
<ul>

  <li>ESLint by Dirk Baeumer</li>
  <li>Prettier - Code formatter by Prettier</li>
</ul>
  
  <h2>Settings</h2>
  <p>Follow the below settings for VS Code -
</p>
  
<ol>
  <li>Create a new folder called ".vscode" inside the project root folder
</li>
  <li>Create a new file called "settings.json" inside that folder.</li>
  <li>Paste the below json in the newly created settings.json file and save the file.</li>
</ol>

```
{

  // config related to code formatting
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[javascript]": {
    "editor.formatOnSave": false,
    "editor.defaultFormatter": null
  },
  "[javascriptreact]": {
    "editor.formatOnSave": false,
    "editor.defaultFormatter": null
  },
  "javascript.validate.enable": false, //disable all built-in syntax checking
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.fixAll.tslint": true,
    "source.organizeImports": true
  },
  "eslint.alwaysShowStatus": true,
  // emmet
  "emmet.triggerExpansionOnTab": true,
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  }
}
```

<h2>Set Line Breaks</h2>
<p> Make sure in your VS Code Editor, "LF" is selected as line feed instead of CRLF (Carriage return and line feed). To do that, just click LF/CRLF in bottom right corner of editor, click it and change it to "LF". If you dont do that, you will get errors in my setup.</p>

<h2>Linting Setup</h2>
<p>In order to lint and format your React project automatically according to popular airbnb style guide, I recommend you to follow the instructions below.
</p>

<h3>Install Dev Dependencies</h3>
```
yarn add -D prettier
yarn add -D babel-eslint
npx install-peerdeps --dev eslint-config-airbnb
yarn add -D eslint-config-prettier eslint-plugin-prettier
```

<p>or You can also add a new script in the scripts section like below to install everything with a single command:</p>

```
scripts: {
    "lint": "yarn add -D prettier && yarn add -D babel-eslint && npx install-peerdeps --dev eslint-config-airbnb && yarn add -D eslint-config-prettier eslint-plugin-prettier"
}
```
 <p>and then simply run the below command in the terminal -</p>
 
 ```
 yarn lint #or 'npm run lint'
 ```
 
 <h3>Create Linting Configuration file manually</h3>
 
 <p>Create a .eslintrc file in the project root and enter the below contents:</p>
 
 ```
 {
  "extends": [
    "airbnb",
    "airbnb/hooks",
    "eslint:recommended",
    "prettier",
    "plugin:jsx-a11y/recommended"
  ],
  "parser": "@babel/eslint-parser",
  "parserOptions": {
    "ecmaVersion": 8,
    "requireConfigFile": false,
    "babelOptions": {
      "presets": ["@babel/preset-react"]
    }
  },
  "env": {
    "browser": true,
    "node": true,
    "es6": true,
    "jest": true
  },
  "rules": {
    "react/react-in-jsx-scope": 0,
    "react-hooks/rules-of-hooks": "error",
    "no-console": 0,
    "react/state-in-constructor": 0,
    "indent": 0,
    "linebreak-style": 0,
    "react/prop-types": 0,
    "jsx-a11y/click-events-have-key-events": 0,
    "import/no-extraneous-dependencies": 0,
    "react/jsx-filename-extension": [
      1,
      {
        "extensions": [".js", ".jsx"]
      }
    ],
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "es5",
        "singleQuote": true,
        "printWidth": 100,
        "tabWidth": 4,
        "semi": true,
        "endOfLine": "auto"
      }
    ]
  },
  "plugins": ["prettier", "react", "react-hooks"]
}

 ```
 
