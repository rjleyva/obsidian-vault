# What is ESLint?

ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.

ESLint is completely pluggable. Every single rule is a plugin and you can add more at runtime. You can also add community plugins, configurations, and parsers to extend the functionality of ESLint.

> [!NOTE] Prerequisites
> To use ESLint, you must have Node.js (^18.18.0, ^20.9.0, or >=21.1.0) installed and built with SSL support. (If you are using an official Node.js distribution, SSL is always built in.)

## Installation

You can install and configure ESLint using this command:

```bash
npm init @eslint/config@latest
yarn create @eslint/config
pnpm create @eslint/config@latest
bun create @eslint/config@latest
```

If you want to use a specific shareable config that is hosted on npm, you can use the --config option and specify the package name:

> **NOTE** `npm init @eslint/config` assumes you have a `package.json` file already. If you don’t, make sure to run `npm init` or `yarn init` beforehand.

```bash
# use `eslint-config-xo` shared config - npm 7+
npm init @eslint/config@latest -- --config eslint-config-xo
yarn dlx eslint yourfile.js
pnpm dlx eslint yourfile.js
bunx eslint yourfile.js
```

See example configs in Templates:

- [[01-astro-eslint.config.js]]

See [[16-prettier]] to learn about Prettier vs Linters.
