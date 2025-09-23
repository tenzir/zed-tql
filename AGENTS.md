# Repository Guidelines

## Project Structure & Module Organization

- `extension.toml` defines the TQL extension manifest shipped to Zed.
- `languages/tql/` contains syntactic scopes and highlighting queries.
- `grammars/tql/` tracks the Tree-sitter grammar submodule; `tql.wasm` is the compiled parser artifact consumed by Zed.

## Build, Test, and Development Commands

- `zed --dev install $(pwd)` installs the local extension into your Zed profile for manual testing.
- `pnpm sort-extensions` (run inside the `tenzir/extensions` fork) keeps registry manifests sorted before opening upstream PRs.
- `pnpm install` in that fork bootstraps tooling required by `sort-extensions`.

## Coding Style & Naming Conventions

- Follow the casing already used: IDs and paths stay lowercase with hyphens (e.g., `tql`), while display names use Title Case (`TQL`).
- Keep Tree-sitter query files indented with two spaces; ensure new highlights mirror existing predicate style.
- Update `extension.toml` and matching registry entries together and prefer semantic version bumps (e.g., `0.1.0`).

## Commit & Pull Request Guidelines

- Follow short, sentence-case commit subjects (recent examples: “Sync Tree-sitter grammar”). Group related edits per commit.
- For releases, tag `v*` (e.g., `v0.1.0`) only after `extension.toml` is final; the Release workflow pushes registry updates via `tenzir/extensions`.

## Release Automation

- Pushing a tag matching `v*` triggers `.github/workflows/release.yaml`, which runs `huacnlee/zed-extension-action@v1` to bump `tenzir/extensions` via our fork.
- The workflow authenticates with the `COMMITTER_TOKEN` secret; back it with a PAT that has `repo` and `workflow` scopes and is SSO-authorized for the `tenzir` org.
- The PAT owner (currently `tenzir-bot`) needs write access to the `tenzir/extensions` fork so the action can call `mergeUpstream`, create branches, and push commits.
- If the job fails, fix credentials/permissions and re-run the existing workflow for the release tag (`gh run rerun <run-id>`); no new tag is required.
