# Zed TQL Extension

This repository packages the Tenzir Query Language grammar for Zed.

## Grammar Synchronization

The source of truth is `tenzir/tree-sitter-tql`. That repository owns the
grammar, generated query files, and the workflow that propagates updates to
`tenzir/zed-tql` when upstream grammar assets change. The upstream workflow also
bumps `extension.toml`'s version when it syncs a new grammar commit.
