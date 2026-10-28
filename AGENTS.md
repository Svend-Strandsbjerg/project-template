# Agent rules

Rules for coding agents working in repositories created from this template.

## Standard scripts

- `npm run typecheck`: `tsc --noEmit`. Run after every code change and
  before committing.
- `npm run lint`: `eslint .`. Run after every code change and before
  committing.
- `npm test`: `vitest run` (unit/integration tests). Run after changing code
  or tests and before committing.
- `npm run build`: `tsc -p tsconfig.build.json`, emits to `dist/`. Run before
  handing off or opening a PR.

Run `npm ci` first in a fresh checkout. CI runs all four scripts on every pull
request; a PR is not ready until they all pass.

## Bounded output

- Use quiet reporters (for example `npx vitest run --reporter=dot`).
- Redirect verbose output to a log file outside the repository and inspect
  only a bounded summary (`tail`, `grep ... | head`).
- Never print base64, `data:image/...` URLs, binary content, traces or huge
  JSON payloads to the console.
- Never write test assertions on full dataURLs, base64 strings or huge
  serialized JSON/DOM. Assert on hashes, lengths, dimensions or small
  structured summaries so a failure produces a short message.

## Logs and evidence

- Logs, screenshots, traces and other evidence are never committed.
- Never use `git add -A`, `git add .` or `git commit -a`. Stage explicit
  paths and check `git status --short` before every commit.

## Secrets and dependencies

- No secrets, tokens or credentials in code, config or commit history. Use
  environment variables (`.env*` files are git-ignored).
- Do not add new runtime dependencies unless the task genuinely needs them.
  Prefer the Node standard library.

## Scope

- Keep changes scoped to the task. Do not refactor, rename or reformat
  unrelated code.
