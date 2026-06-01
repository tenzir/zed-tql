# Zed TQL Extension

This repository packages the Tenzir Query Language grammar for Zed.

## Grammar Synchronization

Do not add polling or scheduled upstream checks in this repository.

The source of truth is `tenzir/tree-sitter-tql`. That repository owns the
grammar, generated query files, and the workflow that propagates updates to
`tenzir/zed-tql` when upstream grammar assets change.

When syncing manually, update only these downstream artifacts:

- `extension.toml` `[grammars.tql].commit`
- `languages/tql/*.scm`

The checked-in query files under `languages/tql/` are generated in
`tenzir/tree-sitter-tql`; do not edit them by hand here.

## Releases

Publishing is tag-driven.

1. Ensure `extension.toml` has the intended extension version.
2. Create and push the matching `vX.Y.Z` tag.
3. `.github/workflows/release.yaml` publishes the Zed extension via
   `huacnlee/zed-extension-action`.

Do not replace this with a local changelog or `tenzir-ship` release flow unless
the repository's release model changes deliberately.
