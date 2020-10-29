# A template for a npm package with typescript and jest

## Initial steps

1. make new folder: `mrdir project-folder && cd project-folder`
1. create `README.md` file: `echo "# My Awesome Project" >> README.md`
1. init git repository: `git init`
1. commit `README.md` file: `git add README.md && git commit -m "initial commit"`
1. create `package.json`: `npm init -y`

## Create basic configuration files:

### Install some essential packages

```bash
yarn add -D @types/jest \
            @typescript-eslint/eslint-plugin \
            @typescript-eslint/parser \
            eslint \
            eslint-config-prettier \
            eslint-plugin-prettier \
            eslint-plugin-simple-import-sort \
            jest \
            nodemon \
            prettier \
            ts-jest \
            typescript
```

### Config for typescript

[tsconfig.json](./tsconfig.json)

### ESLint Config for typescript

[tsconfig.eslint.json](./tsconfig.eslint.json)

### Prettier config

[.prettierrc](./.prettierrc)

### ESLint config

[.eslintrc.js](./.eslintrc.js)

### Create `.gitignore` file

[.gitignore](./.gitignore)

## Create new scripts in the `package.json`

`"scripts":`

```json
{
  "build": "tsc",
  "test": "jest",
  "test:coverage": "jest --coverage --verbose",
  "watch": "nodemon --watch src --exec yarn build",
  "lint": "eslint --fix --ignore-path .gitignore src && prettier --write --ignore-path .gitignore \"./**/*.json\"",
  "prepare": "yarn build",
  "prepublishOnly": "yarn lint && yarn test",
  "preversion": "yarn lint",
  "version": "git add -A",
  "postversion": "git push && git push --tags"
}
```
