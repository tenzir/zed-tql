# Zed TQL Extension

A Zed extension providing TQL (Tenzir Query Language) syntax highlighting.

## Project Structure

- `extension.toml` - Extension manifest shipped to Zed
- `languages/tql/` - Syntactic scopes and highlighting queries
- `grammars/tql/` - Tree-sitter grammar submodule; `tql.wasm` is the compiled parser

## Development

Install the local extension for testing:

```bash
zed --dev install $(pwd)
```

## Style Guide

- IDs and paths: lowercase with hyphens (e.g., `tql`)
- Display names: Title Case (e.g., `TQL`)
- Tree-sitter queries: 2-space indentation, match existing predicate style
- Keep `extension.toml` and registry entries in sync; use semantic versioning

## Releases

- `extension.toml` is the ground truth for version numbers
- The workflow uses `huacnlee/zed-extension-action@v1` to update `tenzir/extensions`

**Credentials:** The `COMMITTER_TOKEN` secret needs a PAT with `repo` + `workflow` scopes, SSO-authorized for `tenzir`. The PAT owner (`tenzir-bot`) requires write access to the `tenzir/extensions` fork.
