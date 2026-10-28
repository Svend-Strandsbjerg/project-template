# project-template

Minimal TypeScript/Node project template. Create new repositories from it with
GitHub's **Use this template** button.

## What the template contains

- `package.json` with the standard scripts (`build`, `typecheck`, `lint`,
  `test`) and dev dependencies only: TypeScript, Vitest, ESLint,
  typescript-eslint and `@types/node`. Requires Node 24 (`.nvmrc`).
- `tsconfig.json` (strict, ES2023, NodeNext) and `tsconfig.build.json`
  (emits to `dist/`, excludes tests).
- `eslint.config.js` (flat config, typescript-eslint recommended).
- `src/index.ts` with a sample function and `src/index.test.ts` with a Vitest
  test.
- `.github/workflows/ci.yml`: the `ci` job runs `npm ci`, typecheck, lint,
  test and build on pull requests and pushes to `main`.
- `.github/CODEOWNERS` and `.github/pull_request_template.md`.
- `AGENTS.md` (rules for coding agents) and `CLAUDE.md` (imports `AGENTS.md`).
- `.gitignore`, `.editorconfig`, `.nvmrc`.

## Usage

```sh
npm ci
npm run typecheck
npm run lint
npm test
npm run build
```

## New project checklist

Human steps when creating a new project from this template:

1. Use this template to create the repo.
2. Add the repo to the svend-agents GitHub App installation.
3. Create ruleset "Protect main" on the default branch:
   - require a pull request before merging
   - 1 required approval
   - require review from Code Owners
   - require approval of the most recent reviewable push
   - block force pushes
   - restrict deletions
   - require status check `ci`
   - empty bypass list
4. Create the Paperclip project with env
   `GH_CONFIG_DIR=/home/paperclip/agent-github/gh`.
