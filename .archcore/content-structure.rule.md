---
title: "Content Organization: 4-Section Structure"
status: accepted
---

## Rule

Every documentation page **must** belong to exactly one of 4 sidebar sections:

1. **Get Started** — Onboarding flow (introduction, quick start, comparison with flat files)
2. **Concepts** — Mental model and use cases (how it works, document types, documents & layout, relations, use cases)
3. **Agents & Tools** — Agent connectivity and CLI (supported agents, MCP server, CLI commands)
4. **Reference** — Lookup material and troubleshooting (MCP tools, configuration, document format, troubleshooting)

Every new page **must** be registered in the sidebar array in `astro.config.mjs`.

## Rationale

The 4-section structure maps to the user journey: **orient → understand → connect → look up**. The first section (Get Started) is action-oriented and serves new users. The remaining three (Concepts, Agents & Tools, Reference) serve users who want deeper understanding, agent setup, or are debugging issues.

This structure keeps navigation compact and scannable — 4 groups with 15 total pages instead of spreading thin across many sections.

## Section directories

| Section | Directory | Pages |
|---------|-----------|-------|
| Get Started | `start/` | `quick-start.mdx`, `vs-flat-files.md` |
| Get Started | root | `index.md` (Introduction) |
| Concepts | `concepts/` | `how-it-works.md`, `document-types.md`, `documents.md`, `relations.md`, `use-cases.md` |
| Agents & Tools | `agents/` | `supported-agents.md`, `mcp-server.md`, `cli.md` |
| Reference | `reference/` | `mcp-tools.md`, `configuration.md`, `document-format.md`, `troubleshooting.md` |

## Examples

### Good

- New page explaining a use case → **Concepts** (use cases are conceptual content)
- New page documenting an MCP tool → **Reference** (lookup material)
- New page explaining how relations work → **Concepts** (mental model)
- New page for agent setup → **Agents & Tools** (agent connectivity)
- New page walking through first setup → **Get Started** (onboarding)
- New page for a common error → **Reference** (troubleshooting is in Reference)

### Bad

- New concept explanation placed in Reference — Reference is for lookup, not learning
- New CLI command page placed in Concepts — commands are lookup material, belongs in Agents & Tools
- New use case placed in Get Started — use cases belong in Concepts
- New troubleshooting page placed in Agents & Tools — troubleshooting is in Reference

## Enforcement

- New pages require a sidebar entry in `astro.config.mjs`; the build will not surface unregistered pages in navigation
- During review, verify the page is in the correct section per the user journey mapping above