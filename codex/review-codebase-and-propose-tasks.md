# Codebase Review and Proposed Task Backlog

Date: 2026-05-25

## Scope reviewed

- Repository structure and documentation entry points (`README.md`, `powerquery-docs/index.yml`, `powerquery-docs/toc.yml`).
- Open placeholders and known unfinished sections (`TODO`, `TBD`, `FIXME`) across markdown and yaml files.

## Key findings

1. **ODBC docs contain multiple unresolved TODO markers** and a checklist placeholder, suggesting incomplete guidance in an otherwise technical article used by connector authors.
2. **ODBC troubleshooting has at least one TODO section**, which may cause dead-ends for users seeking debugging steps.
3. **Custom connector FAQ sample code includes an inline TODO**, indicating a missing protocol-version validation example.

## Proposed tasks (prioritized)

### P0 — Complete ODBC parameter documentation placeholders

**Why now**
- This file has the highest concentration of TODO placeholders in the docs set.
- It likely impacts developers implementing ODBC-based connectors.

**Definition of done**
- Replace every TODO/checklist placeholder in `powerquery-docs/odbc-parameters.md` with complete, tested guidance.
- Ensure examples and checklist items are actionable and consistent with current connector SDK behavior.

### P1 — Fill missing troubleshooting content in ODBC troubleshooting guide

**Why now**
- Troubleshooting docs are often visited under urgency; placeholders directly reduce resolution speed.

**Definition of done**
- Replace TODO sections in `powerquery-docs/odbc-troubleshooting.md` with concrete issue patterns, diagnostics, and remediations.
- Add at least one end-to-end troubleshooting flow.

### P1 — Finalize protocol-version check guidance in custom connector FAQ

**Why now**
- Sample code snippets are commonly copied; leaving TODOs in code paths can propagate weak validation patterns.

**Definition of done**
- Update `powerquery-docs/custom-connector-development-faq.yml` sample to include protocol version validation guidance.
- Confirm snippet readability and consistency with existing FAQ style.

### P2 — Add repository maintenance check for unresolved placeholders

**Why now**
- Prevents future placeholder regressions and keeps docs production-ready.

**Definition of done**
- Add a lightweight CI check (or local lint script) that fails on unresolved `TODO/TBD/FIXME` markers in public docs paths.
- Document exceptions (if any) in contributor guidance.

## Suggested execution order

1. `powerquery-docs/odbc-parameters.md` placeholder completion.
2. `powerquery-docs/odbc-troubleshooting.md` completion.
3. FAQ sample-code TODO cleanup.
4. Placeholder regression guardrail in CI.

## Notes

- This backlog is intentionally scoped to high-signal gaps detected quickly from content placeholders and entry-point review.
- A deeper follow-up pass could score docs by traffic/impact and then prioritize refresh work accordingly.
