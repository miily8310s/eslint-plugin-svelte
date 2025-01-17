# User Guide

## :cd: Installation

```bash
npm install --save-dev eslint @ota-meshi/eslint-plugin-svelte svelte
```

::: tip Requirements

- ESLint v7.0.0 and above
- Node.js v10.13.0 and above

:::

## :book: Usage

<!--USAGE_GUIDE_START-->

### Configuration

Use `.eslintrc.*` file to configure rules. See also: [https://eslint.org/docs/user-guide/configuring](https://eslint.org/docs/user-guide/configuring).

Example **.eslintrc.js**:

```js
module.exports = {
  extends: [
    // add more generic rule sets here, such as:
    // 'eslint:recommended',
    "plugin:@ota-meshi/svelte/recommended",
  ],
  rules: {
    // override/add rules settings here, such as:
    // '@ota-meshi/svelte/rule-name': 'error'
  },
}
```

This plugin provides configs:

- `plugin:@ota-meshi/svelte/base` ... Configuration to enable correct Svelte parsing.
- `plugin:@ota-meshi/svelte/recommended` ... Above, plus rules to prevent errors or unintended behavior.

See [the rule list](../rules/README.md) to get the `rules` that this plugin provides.

::: warning ❗ Attention

The `@ota-meshi/eslint-plugin-svelte` can not be used with the [eslint-plugin-svelte3].
If you are using [eslint-plugin-svelte3] you need to remove it.

```diff
  "plugins": [
-   "svelte3"
  ]
```

:::

#### settings["@ota-meshi/svelte"]

You can change the behavior of this plugin with some settings.

- `ignoreWarnings` (optional) ... Specifies an array of rules that ignore reports in the template.  
  For example, set rules on the template that cannot avoid false positives.

e.g.

```js
module.exports = {
  // ...
  settings: {
    "@ota-meshi/svelte": {
      ignoreWarnings: [
        "@typescript-eslint/no-unsafe-assignment",
        "@typescript-eslint/no-unsafe-member-access",
      ],
    },
  },
  // ...
}
```

### Running ESLint from the command line

If you want to run `eslint` from the command line, make sure you include the `.svelte` extension using [the `--ext` option](https://eslint.org/docs/user-guide/configuring#specifying-file-extensions-to-lint) or a glob pattern, because ESLint targets only `.js` files by default.

Examples:

```bash
eslint --ext .js,.svelte src
eslint "src/**/*.{js,svelte}"
```

### Used in combination with TypeScript

When using a Svelte file written in TypeScript, the following settings are additionally required in `.eslintrc. *`.

Example **.eslintrc.js**:

```js
module.exports = {
  // ...
  overrides: [
    {
        "files": ["*.svelte"],
        "parser": "svelte-eslint-parser",
        "parserOptions": {
           "parser": "@typescript-eslint/parser"
        }
    }
  ]
  // ...
}
```

## :computer: Editor Integrations

### Visual Studio Code

Use the [dbaeumer.vscode-eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) extension that Microsoft provides officially.

You have to configure the `eslint.validate` option of the extension to check `.svelte` files, because the extension targets only `*.js` or `*.jsx` files by default.

Example **.vscode/settings.json**:

```json
{
  "eslint.validate": ["javascript", "javascriptreact", "svelte"]
}
```

<!--USAGE_GUIDE_END-->

## :question: FAQ

- TODO

[eslint-plugin-svelte3]: https://github.com/sveltejs/eslint-plugin-svelte3
