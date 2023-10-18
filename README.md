<div align=center>

# [BASE TS TEMPLATE]

[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
[![semantic-release: angular](https://img.shields.io/badge/semantic--release-angular-e10079?logo=semantic-release)](https://github.com/semantic-release/semantic-release)
[![build](https://github.com/d3p1/base-ts-template/actions/workflows/build.yml/badge.svg)](https://github.com/d3p1/base-ts-template/actions/workflows/build.yml)
[![release](https://github.com/d3p1/base-ts-template/actions/workflows/release.yml/badge.svg)](https://github.com/d3p1/base-ts-template/actions/workflows/release.yml)

</div>

## Introduction

A [repository aimed at serving as a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) to implement projects using [TypeScript](https://www.typescriptlang.org/), providing basic configurations for using [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/), [Prettier](https://prettier.io/), [ESLint](https://eslint.org/), and [Jest](https://jestjs.io/). It also includes a setup for use within a [Dev Container](https://code.visualstudio.com/docs/devcontainers/containers), featuring optimized [VSCode](https://code.visualstudio.com/) configurations for working with these technologies. Lastly, it incorporates [GitHub Actions](https://github.com/features/actions) that automate the project [build](./.github/workflows/build.yml) and [release](./.github/workflows/release.yml).

## Usage

This [template repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) is not ready for immediate use. This is because it merely adds basic configurations for the various technologies, but both [ESLint](https://eslint.org/) and [Jest](https://jestjs.io/) need to be set up to work on either the server-side or client-side.

## Brief technical overview

We will proceed with detailed information about the various technologies used:

[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/): This repository comes with [`commitlint`](https://commitlint.js.org/) and [`husky`](https://typicode.github.io/husky/) installed, along with the [`@d3p1/commitlint-config` configuration](https://github.com/d3p1/commitlint-config), to enforce commits to follow the format: `<type>(<scope>): <description> [<issue-number>]`

[Prettier](https://prettier.io/) & [ESLint](https://eslint.org/): This repository includes `prettier` and `eslint` for maintaining code with a consistent style, free of errors, and following best practices. The [`eslint` configuration](./.eslintrc.json) uses [`eslint-config-prettier`](https://github.com/prettier/eslint-config-prettier) to disable rules that may conflict with `prettier`. Additionally, the idea is to always run `prettier` before `eslint` (see the [`refactor` script in `package.json`](./package.json)), which is why the [Dev Container configuration](.devcontainer/devcontainer.json) includes the [Format Code Action extension (and its corresponding setup) so that VSCode runs `prettier` first and then `eslint` upon saving a file](https://marketplace.visualstudio.com/items?itemName=rohit-gohri.format-code-action).

[TypeScript](https://www.typescriptlang.org/) & [Jest](https://jestjs.io/): Both [TypeScript](https://www.typescriptlang.org/) and [Jest](https://jestjs.io/) are set up to work with code within `./src` (note the template files in `./src/index.ts` and `.src/index.test.ts`). See the `rootDir` and `include` options in [`tsconfig.json`](./tsconfig.json), as well as the `roots` option in [`jest.config.json`](./jest.config.json).

[GitHub Actions](https://github.com/features/actions): The [`release` workflow](.github/workflows/release.yml) uses [Semantic Release](https://github.com/semantic-release/semantic-release) (in reality, it uses the [`d3p1/semantic-releasify@v1` action](https://github.com/d3p1/semantic-releasify) to facilitate its use). This will only trigger if the [`build` workflow](.github/workflows/build.yml) runs successfully. Please review the `workflow_run` event in [`release.yml`](.github/workflows/release.yml) and the condition used in its `release` job. Since the [Semantic Release](https://github.com/semantic-release/semantic-release) bot creates a tag for each release, updates the `CHANGELOG.md`, and generates a release, it's necessary for the branch to not be protected so that the bot can add its changes without issues. As this repository is intended to serve as a template for personal repositories, this isn't a major concern, as non-contributors (and in personal repositories, typically, the only contributor is the repository owner) won't be able to `push` directly to the default branch or approve PRs from forks made to submit changes.

## Changelog

Detailed changes for each release are documented in [`CHANGELOG.md`](./CHANGELOG.md).

## License

This work is published under [MIT License](./LICENSE).

## Author

Always happy to receive a greeting on:

- [LinkedIn](https://www.linkedin.com/in/cristian-marcelo-de-picciotto/)
- [Web](https://d3p1.dev/)
