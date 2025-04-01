# SecretLint <!-- omit in toc -->

[![Dependabot Updates](https://github.com/tyler36/secretlint-demo/actions/workflows/dependabot/dependabot-updates/badge.svg)](https://github.com/tyler36/secretlint-demo/actions/workflows/dependabot/dependabot-updates)

## Overview

Secretlint is a linting tool to prevent committing credentials.

Homepage: <https://github.com/secretlint/secretlint>
Playground: <https://secretlint.github.io/>

## Install

1. Install

```shell
npm install secretlint @secretlint/secretlint-rule-preset-recommend --save-dev
```

## Usage

### Docker

Check files in the current directory with Docker

```shell
docker run -v `pwd`:`pwd` -w `pwd` --rm -it secretlint/secretlint secretlint "**/*"
```

### With node installed

```shell
npx @secretlint/quick-start "**/*"
```

### NPM help

```json
  "scripts": {
    "lint:secrets": "secretlint **/*"
  },
```

## Use cases

### Hide secrets in files

One good usage is to find and mask secrets from your CLI history.
The following line scans your `.zsh_history` and replaces all secrets with a mask.

```shell
secretlint .zsh_history --format=mask-result --output=.zsh_history
```

### Ignoring

#### Ignoring lists

By default, secretlint ignores the following globs:

- `**/.git/**`,
- `**/node_modules/**`,
- `**/.secretlintrc/**`,
- `**/.secretlintrc.{json,yaml,yml,js}/**`,
- `**/.secretlintignore*/**`

Use `.secretlintignore` file with globs.

#### Ignoring with comments

[@secretlint/secretlint-rule-filter-comments](https://www.npmjs.com/package/@secretlint/secretlint-rule-filter-comments) supports using comment to disable/enable secretlint.

```php
secret='password' // secretlint-disable-line
// secretlint-disable-next-line
secret='password'
```

```php
// secretlint-disable
secret='password'
// secretlint-enable
```

## Configuration

Create a configuration file with the following line:

```shell
npx secretlint --init
```

Secretlint has a configuration file `.secretlintrc.{json,yml,js}`.

### Masking secrets

Use `--maskSecrets` to prevent secrets from displaying in logs and outputs.

### Locale

Use `--locale` with a valid language to translate messages. For example: `secretlint **/* --locale ja`
