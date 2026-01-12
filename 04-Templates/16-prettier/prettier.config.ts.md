#template #prettier

`prettier.config.ts`

```typescript
import type { Config } from "prettier";

const config: Config = {
  arrowParens: "avoid",
  bracketSpacing: true,
  endOfLine: "lf",
  printWidth: 80,
  semi: false,
  singleQuote: true,
  tabWidth: 2,
  trailingComma: "none",
  plugins: ["@ianvs/prettier-plugin-sort-imports"],
  importOrder: [
    "^react$",
    "<BUILTIN_MODULES>",
    "<THIRD_PARTY_MODULES>",
    "^types$",
    "^@types",
    "^@[a-zA-Z0-9-]+/",
    "^@/.*$",
    "^\\w+/",
    "^\\.\\.?.*$",
    "\\.css$",
  ],
};

export default config;
```

Related Reference:

- Prettier vs. Linters [[16-prettier]]
- `.prettierrc.json` configuration [[prettierrc.json]]
- `.prettierrc.yaml` or (yml) configuration [[prettierrc.yaml]]
