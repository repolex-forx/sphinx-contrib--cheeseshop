# Repolex Knowledge Graph of sphinx-contrib/cheeseshop

RDF knowledge graph data for [sphinx-contrib/cheeseshop](https://github.com/sphinx-contrib/cheeseshop), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download sphinx-contrib/cheeseshop
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 70b7023e8df78d1e9c3dc0119b885681bcbeff8e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 70b7023e8df78d1e9c3dc0119b885681bcbeff8e
│           └── chunk-001.nq.gz
├── blob
│   ├── 712d5e6cec772808f5154eb128de6309c82ead55.nq.gz
│   ├── 8846e947fa5239ce25a3d990060f65639a46570d.nq.gz
│   ├── 8ac5e390cd6725e7b2cdafd84299e736d7d082a6.nq.gz
│   ├── a0cacc5a423d1686cc538cf2737d62be50d8c577.nq.gz
│   ├── a4bdf594c072a9d5f0d33f9df753f41e939adac8.nq.gz
│   └── e25b012010e2ff4d8c7e22b50202634ecaf61c7a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 70b7023e8df78d1e9c3dc0119b885681bcbeff8e.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[sphinx-contrib/cheeseshop](https://github.com/sphinx-contrib/cheeseshop)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
