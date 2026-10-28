# `no-deprecated` hangs on a circular alias

Reproduction for a typescript-eslint bug: `@typescript-eslint/no-deprecated` never finishes when a file references an alias cycle that does not resolve to a declaration.

```sh
npm install
npm run lint   # does not finish
```

`a.ts` re-exports `x` from itself. `tsc` reports TS2303 (`Circular definition of import alias 'x'`) for this file.
