# Repolex Knowledge Graph of anysphere/bugbot-context

RDF knowledge graph data for [anysphere/bugbot-context](https://github.com/anysphere/bugbot-context), parsed by [repolex](https://repolex.ai).

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
rlex download anysphere/bugbot-context
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── aa2025ddc3cc22384f48b2d94e618c49302ae406
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── aa2025ddc3cc22384f48b2d94e618c49302ae406.nq.gz
│   └── repolex
│       └── aa2025ddc3cc22384f48b2d94e618c49302ae406
│           └── chunk-001.nq.gz
├── blob
│   ├── 2fb5b96ab151fb1881701b146f30bb8e3f1f0385.nq.gz
│   └── 995ba63b57ec1325f96bd2f0a39943ed507ef882.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── aa2025ddc3cc22384f48b2d94e618c49302ae406.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 9 files
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

[anysphere/bugbot-context](https://github.com/anysphere/bugbot-context)

---
*Parsed on 2026-10-04 by [repolex](https://repolex.ai)*
