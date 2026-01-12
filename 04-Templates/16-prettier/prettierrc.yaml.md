#template #prettier

`.prettierrc.yaml (or yml)`

```yaml
arrowParens: avoid
bracketSpacing: true
endOfLine: lf
printWidth: 80
semi: false
singleQuote: true
tabWidth: 2
trailingComma: none
plugins:
  - "@ianvs/prettier-plugin-sort-imports"
importOrder:
  - "^react$"
  - "<BUILTIN_MODULES>"
  - "<THIRD_PARTY_MODULES>"
  - "^types$"
  - "^@types"
  - "^@[a-zA-Z0-9-]+/"
  - "^@/.*$"
  - "^\\w+/"
  - "^\\.\\.?.*$"
  - "\\.css$"
```

Related Reference:

- Prettier vs. Linters [[16-prettier]]
- `.prettierrc.json` configuration [[prettierrc.json]]
- `prettier.config.ts` configuration [[prettier.config.ts]]

