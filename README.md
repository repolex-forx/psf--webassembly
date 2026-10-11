# Repolex Knowledge Graph of psf/webassembly

RDF knowledge graph data for [psf/webassembly](https://github.com/psf/webassembly), parsed by [repolex](https://repolex.ai).

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
rlex download psf/webassembly
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 60cd7a66728eb6ffdb658653dd19384cdd1bb4ee
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 60cd7a66728eb6ffdb658653dd19384cdd1bb4ee
│           └── chunk-001.nq.gz
├── blob
│   ├── 3b82e07e7c2c1d7510d2376806d04f0f4bde9d08.nq.gz
│   ├── 654a225cc8d1a90f53172c0ee7c6e1167ea5764c.nq.gz
│   ├── 6d2a1dab6e8ef8cc2ec8c7c6dced662b2b0fce11.nq.gz
│   ├── 922cbea670c96b4e6fee9975848ceb5bdfbd362c.nq.gz
│   ├── b6e47617de110dea7ca47e087ff1347cc2646eda.nq.gz
│   ├── e002665db1b684bf9f595441cbfbc9b56b299108.nq.gz
│   └── f712fdb654f2b24802b100aea9a18816f22e0f68.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 60cd7a66728eb6ffdb658653dd19384cdd1bb4ee.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 15 files
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

[psf/webassembly](https://github.com/psf/webassembly)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
