# RN Environment Setup

## Instructions

### Tools

* Flow
* ESLint
* Prettier
* VSCode

1.  Init **React Native** project

    ```sh
    $ react-native init HelloPGP
    $ cd HelloPGP/
    ```

2.  Init **git** repo

    ```sh
    $ git init
    $ git add --all && git commit -m "Initial commit"
    ```

3.  Install **Flow**

    Flow compiler

    ```sh
    $ brew install flow
    # Flow compiler
    $ yarn add --dev babel-cli babel-preset-flow
    ```

    Add "flow" to .babelrc presets. `.babelrc` should look like this:

    ```json
    {
      "presets": ["react-native", "flow"],
      "retainLines": true
    }
    ```

    Flow

    ```sh
    # Flow
    $ yarn add --dev flow-bin
    $ vim package.json
    ```

    Add the following flow entries to the package.json:

    ```json
    {
      "scripts": {
        "flow": "flow",
        "flow-stop": "flow stop"
      }
    }
    ```

4.  VSCode

    * Install extension [Flow Language Support](https://marketplace.visualstudio.com/items?itemName=flowtype.flow-for-vscode).

5.  **ESLint** with **Babel**-Parser

    We will use the **eslint-config-airbnb** Package. But first, we need to install its peer dependencies.

    ```sh
    (
      export PKG=eslint-config-airbnb-base;
      npm info "$PKG@latest" peerDependencies --json | command sed 's/[\{\},]//g ; s/: /@/g' | xargs yarn add --dev "$PKG@latest"
    )
    ```

    Install **babel-eslint**.

    ```sh
    $ yarn add --dev babel-eslint
    ```

    Create an `.eslintrc.json` file and copy the following configuration:

    ```json
    {
      "parser": "babel-eslint",

      "extends": "airbnb",

      "plugins": ["react", "jsx-a11y", "import"]
    }
    ```

6.  **Prettier**

    ```sh
    $ yarn add --dev prettier-eslint
    ```

7.  VSCode

    Add the following workspace settings:

    ```json
    {
      // Format a file on save. A formatter must be available, the file must not be auto-saved, and editor must not be shutting down.

      "editor.formatOnSave": true,

      // Support using flow through your node_modules folder, WARNING: Checking this box is a security risk. When you open a project we will immediately run code contained within it.

      "flow.useNPMPackagedFlow": true,

      // Enable/disable JavaScript validation. (For Flow)

      "javascript.validate.enable": false,

      // Enable/disable default JavaScript formatter (For Prettier)

      "javascript.format.enable": false,

      // Use 'prettier-eslint' instead of 'prettier'. Other settings will only be fallbacks in case they could not be inferred from eslint rules.

      "prettier.eslintIntegration": true
    }
    ```

## Attributions

This guide is based on:

* [React Native mit VSCode](https://hackernoon.com/configure-eslint-prettier-and-flow-in-vs-code-for-react-development-c9d95db07213)

* [VSCode Extensions für React](https://medium.com/react-native-training/vscode-for-react-native-526ec4a368ce)
