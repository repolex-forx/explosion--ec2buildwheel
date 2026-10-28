# Repolex Knowledge Graph of explosion/ec2buildwheel

RDF knowledge graph data for [explosion/ec2buildwheel](https://github.com/explosion/ec2buildwheel), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/ec2buildwheel
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0d71d8d2e0f9d9ecd7063b5c13f4edbd2c70a3ba
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0d71d8d2e0f9d9ecd7063b5c13f4edbd2c70a3ba
│           └── chunk-001.nq.gz
├── blob
│   ├── 0e594ecd0048b34fababccf9924c28663639fd41.nq.gz
│   ├── 7513363277a75a302e1d9360d824c26c946433f8.nq.gz
│   ├── c494ba6d57dea531ef70689efe84d3d5ce0ec9b9.nq.gz
│   ├── cc0a6ae187877415b59038ece13b10746fca4b7c.nq.gz
│   └── f82a2d3b551b7759f5bf76dc29b18cfece300309.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0d71d8d2e0f9d9ecd7063b5c13f4edbd2c70a3ba.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 12 files
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

[explosion/ec2buildwheel](https://github.com/explosion/ec2buildwheel)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
