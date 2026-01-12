> **NOTE**: This ESLint configuration is based on the rjleyva-rewrite monorepo and is intended for projects built with Astro, React, and TypeScript, using Supabase (PostgreSQL) as the backend.

```javascript
import astroPlugin from "eslint-plugin-astro";
import jsxA11yPlugin from "eslint-plugin-jsx-a11y";
import reactPlugin from "eslint-plugin-react";
import reactHooksPlugin from "eslint-plugin-react-hooks";
import tseslint from "@typescript-eslint/eslint-plugin";
import tsparser from "@typescript-eslint/parser";
import js from "@eslint/js";

export default [
	// Base configuration for all workspaces
	js.configs.recommended,
	{
		files: ["**/*.{js,mjs,cjs,ts,mts,cts}"],
		languageOptions: {
			parser: tsparser,
			parserOptions: {
				ecmaVersion: 2022,
				sourceType: "module",
				project: true,
			},
		},
		plugins: {
			"@typescript-eslint": tseslint,
		},
		rules: {
			...tseslint.configs.recommended.rules,
			"no-console": "warn",
			"@typescript-eslint/no-unused-vars": [
				"error",
				{
					argsIgnorePattern: "^_",
					varsIgnorePattern: "^_",
				},
			],
			"@typescript-eslint/explicit-function-return-type": "off",
			"@typescript-eslint/no-explicit-any": "warn",
			"prefer-const": "error",
			"no-var": "error",
		},
	},

	// Astro-specific configuration
	{
		files: ["apps/client/**/*.{astro,ts,tsx,js,jsx}"],
		...astroPlugin.configs.recommended,
		languageOptions: {
			parser: tsparser,
			parserOptions: {
				parser: "@typescript-eslint/parser",
				extraFileExtensions: [".astro"],
				project: "./apps/client/tsconfig.json",
			},
		},
		rules: {
			"astro/no-unused-css-selector": "error",
			"astro/prefer-class-list-directive": "error",
			"astro/no-set-html-directive": "error",
			"@typescript-eslint/no-unused-vars": "off",
		},
	},

	// React components (islands) in Astro
	{
		files: ["apps/client/**/*.{tsx,jsx}"],
		plugins: {
			react: reactPlugin,
			"react-hooks": reactHooksPlugin,
			"jsx-a11y": jsxA11yPlugin,
		},
		languageOptions: {
			parserOptions: {
				ecmaFeatures: {
					jsx: true,
				},
			},
		},
		rules: {
			...reactPlugin.configs.recommended.rules,
			...reactHooksPlugin.configs.recommended.rules,
			...jsxA11yPlugin.configs.recommended.rules,

			"react/react-in-jsx-scope": "off", // Not needed in Astro
			"react/prop-types": "off", // Using TypeScript
			"react-hooks/exhaustive-deps": "warn",

			// jsx-a11y customizations for blog/interactive content
			"jsx-a11y/anchor-is-valid": [
				"error",
				{
					components: ["Link"],
					specialLink: ["to"],
					aspects: ["noHref", "invalidHref", "preferButton"],
				},
			],
			"jsx-a11y/click-events-have-key-events": "warn", // Allow for some interactive elements
			"jsx-a11y/no-noninteractive-element-interactions": "warn",
		},
	},

	// Supabase Edge Functions
	{
		files: ["apps/server/**/*.{ts,js}"],
		languageOptions: {
			globals: {
				Deno: "readonly",
				console: "readonly",
			},
		},
		rules: {
			"no-console": "off",
			"@typescript-eslint/no-var-requires": "off",
		},
	},

	// Shared packages
	{
		files: ["packages/shared/**/*.{ts,js}"],
		rules: {
			"@typescript-eslint/explicit-function-return-type": "error",
			"@typescript-eslint/no-explicit-any": "error",
			"no-console": "error",
			"@typescript-eslint/prefer-readonly": "error",
		},
	},

	// Config and test files
	{
		files: [
			"*.config.{js,ts,mjs}",
			"eslint.config.js",
			"**/*.{test,spec}.{ts,tsx,js,jsx}",
		],
		rules: {
			"no-console": "off",
			"@typescript-eslint/no-var-requires": "off",
			"@typescript-eslint/no-explicit-any": "off",
		},
	},
];
```

Related Reference:

- [[05-eslint]]

