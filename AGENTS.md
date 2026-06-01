# Zed TQL Extension

This repository packages the Tenzir Query Language grammar for Zed.

## Grammar Synchronization

The source of truth is `tenzir/tree-sitter-tql`. That repository owns the
grammar, generated query files, and the workflow that propagates updates to
`tenzir/zed-tql` when upstream grammar assets change. The upstream workflow also
bumps `extension.toml`'s version when it syncs a new grammar commit.

## Releases

Publishing is tag-driven.

1. Ensure `extension.toml` has the intended extension version.
2. Create and push the matching `vX.Y.Z` tag.
3. `.github/workflows/release.yaml` publishes the Zed extension via
   `huacnlee/zed-extension-action`.

Do not replace this with a local changelog or `tenzir-ship` release flow unless
the repository's release model changes deliberately.
