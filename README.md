# Repolex Knowledge Graph of ibis-project/talks

RDF knowledge graph data for [ibis-project/talks](https://github.com/ibis-project/talks), parsed by [repolex](https://repolex.ai).

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
rlex download ibis-project/talks
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 258cc49736dcf35e0073e0a137c07c08c07be1b4
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 258cc49736dcf35e0073e0a137c07c08c07be1b4
│           └── chunk-001.nq.gz
├── blob
│   ├── 21dadc10007064af9f41ea0e448b1b668bdc5bf6.nq.gz
│   ├── 73dd94a1a033cbac706d9afb4ca2d70e9e52572b.nq.gz
│   ├── 75e62cf72956b3feb04397483fdc418d69fdaf1f.nq.gz
│   └── a5b4e8ff687ce13534b518ca2b84a0b1276a6e1b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 258cc49736dcf35e0073e0a137c07c08c07be1b4.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 12 files
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

[ibis-project/talks](https://github.com/ibis-project/talks)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
