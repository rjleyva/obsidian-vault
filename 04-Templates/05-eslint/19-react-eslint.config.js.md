# ESLint - JavaScript config

This is a strict ESLint configuration for a Vite + React + TypeScript project.
You should adjust it according to your project’s specific requirements.

```javascript
import jsxA11y from "eslint-plugin-jsx-a11y";
import reactPlugin from "eslint-plugin-react";
import reactHooks from "eslint-plugin-react-hooks";
import reactRefresh from "eslint-plugin-react-refresh";
import globals from "globals";
import tseslint from "typescript-eslint";
import js from "@eslint/js";

export default [
  // Core ESLint recommended rules
  js.configs.recommended,
  // Strict type-checked rules
  ...tseslint.configs.recommended,
  // React flat config
  reactPlugin.configs.flat.recommended,
  // JSX A11y flat config
  jsxA11y.flatConfigs.recommended,
  // Custom configuration for TSX/JSX files
  {
    name: "source-typescript-and-jsx-files",
    files: ["**/*.{ts,tsx,js,jsx}"],
    languageOptions: {
      parser: tseslint.parser,
      parserOptions: {
        ecmaVersion: "latest",
        sourceType: "module",
        ecmaFeatures: {
          jsx: true,
        },
      },
      globals: globals.browser,
    },
    plugins: {
      react: reactPlugin,
      "react-hooks": reactHooks,
      "react-refresh": reactRefresh,
    },
    rules: {
      // Custom TS rules
      "react/react-in-jsx-scope": "off", // no longer required in React 17+
      "@typescript-eslint/no-explicit-any": "error",
      "@typescript-eslint/no-unused-vars": [
        "error",
        {
          argsIgnorePattern: "^_",
          varsIgnorePattern: "^_",
        },
      ],
      // React Hooks rules
      ...reactHooks.configs.recommended.rules,
      // React Refresh rule
      "react-refresh/only-export-components": [
        "error",
        { allowConstantExport: true },
      ],
    },
    settings: {
      react: {
        version: "detect",
      },
    },
  },
];
```

Related Reference:

- [[05-eslint]]
- [[01-astro-eslint.config.js]]
