# What is Prettier?

Prettier is an opinionated code formatter with support for:

- JavaScript (including experimental features)
- [JSX](https://facebook.github.io/jsx/)
- [Angular](https://angular.dev/)
- [Vue](https://vuejs.org/)
- [Flow](https://flow.org/)
- [TypeScript](https://www.typescriptlang.org/)
- CSS, [Less](https://lesscss.org/), and [SCSS](https://sass-lang.com/)
- [HTML](https://en.wikipedia.org/wiki/HTML)
- [Ember/Handlebars](https://handlebarsjs.com/)
- [JSON](https://json.org/)
- [GraphQL](https://graphql.org/)
- [Markdown](https://commonmark.org/), including [GFM](https://github.github.com/gfm/) and [MDX v1](https://mdxjs.com/)
- [YAML](https://yaml.org/)

It removes all original styling[\*](https://prettier.io/docs/#footnotes) and ensures that all outputted code conforms to a consistent style.

### Installation

```bash
npm install --save-dev prettier
yarn add --dev --exact prettier
pnpm add --save-dev --save-exact prettier
bun add --dev --exact prettier
```

> **TIP:** Prettier will follow rules specified in .gitignore if it exists in the same directory from which it is run. You can also base your .prettierignore on .eslintignore (if you have one

> ** ANOTHER TIP:** If your project isn’t ready to format, say, HTML files yet, add \*.html.

Now, format all files with Prettier:

```bash
npx prettier . --write
yarn exec prettier . --write
pnpm exec prettier . --write
bunx prettier . --write
```

> **INFO:** What is `bunx` doing at the start? `bunx prettier` runs the locally installed version of Prettier. We’ll leave off the `bunx` part for brevity throughout the rest of this file!

> **WARNING:** If you forget to install **Prettier** first, `bunx` will temporarily download the latest version. That’s not a good idea when using Prettier, because we change how code is formatted in each release! It’s important to have a locked down version of Prettier in your `package.json`. And it’s faster, too.

`prettier --write .` is great for formatting everything, but for a big project it might take a little while. You may run `prettier --write app/` to format a certain directory, or `prettier --write app/components/Button.js` to format a certain file. Or use a glob like `prettier --write "app/\*_/_.test.js"` to format all tests in a directory (see fast-glob for supported glob syntax).

If you have a CI setup, run the following as part of it to make sure that everyone runs Prettier. This avoids merge conflicts and other collaboration issues!

```bash
npx prettier . --check
```

`--check` is like `--write`, but only checks that files are already formatted, rather than overwriting them. `prettier --write` and `prettier --check` are the most common ways to run Prettier.

See example configs in Templates:

- [[prettierrc.json]]
- [[prettierrc.yaml]]
- [[prettier.config.ts]]

## Prettier vs. Linters

Linters have two categories of rules:

**Formatting rules**: eg: max-len, no-mixed-spaces-and-tabs, keyword-spacing, comma-style…

Prettier alleviates the need for this whole category of rules! Prettier is going to reprint the entire program from scratch in a consistent way, so it’s not possible for the programmer to make a mistake there anymore :)

**Code-quality rules**: eg no-unused-vars, no-extra-bind, no-implicit-globals, prefer-promise-reject-errors…

Prettier does nothing to help with those kind of rules. They are also the most important ones provided by linters as they are likely to catch real bugs with your code!

In other words, use Prettier for formatting and linters for catching bugs!

> [!NOTE] NOTE
> When searching for both Prettier and your linter on the Internet you’ll probably find more related projects. These are generally **not recommended**, but can be useful in certain circumstances.

See [[05-eslint]] to learn about ESLint.
