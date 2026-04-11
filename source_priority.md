# Source Priority Rule

## Authoritative Source Order

1. **Canonical finalpool** (`bugmaker00/BenchTasksCollv3-review@finalpool`, PR \#1, snapshot 2026-04-09) — **PRIMARY / WINS ALL CONFLICTS**
2. **Developer branches** (`mcpmark-eval-1031/BenchTasksCollv3@{dev_branch}`) — secondary; provides live per-developer task lists and current file content used by the canonical review
3. **Intermediate finalpool** (`mcpmark-eval-1031/BenchTasksCollv3@finalpool`, snapshot 2026-03-23, README states 67 tasks) — tertiary; provides evidence of pre-CJK file states and earliest structural baseline

## Rationale

The canonical finalpool (source 1) is the chronologically later, editorially complete snapshot used for the official boundary review. It captures all 14 developer branches as of 2026-04-09 (116 candidates total) and carries the definitive verdict (E0 KEEP / E1 / E2 / E3 DROP) for every task.

The developer branches (source 2) are the live working trees from which source 1 was compiled. Where the canonical PR description references specific file sizes or task identities, those measurements are taken from source 2 at the 2026-04-09 cut-off.

The intermediate finalpool (source 3) is a partial, incomplete snapshot from 2026-03-23 with only 67 of the eventual 116 candidates. It pre-dates several developer commits, including CJK additions (e.g., `jl/monthly-sales-analysis/docs/task.md` measured 103 B in source 3 but 172 B in source 2 at review time) and numerous new task submissions across lv, ruige, junteng, xiaochen, yuxuan, yuzhen, and zhaochen branches.

## Application Rules

- **Any numerical aggregate** (task count, file size, verdict, rule code) resolves to source 1 when sources disagree.
- **Task verdicts** (KEEP/DROP, rule code E0–E3) always derive from source 1.
- **File content conflicts** resolve to source 2 (canonical developer branch state at 2026-04-09), which is the state source 1 reviewed.
- **Source 3 values are preserved in `conflict_resolution.csv`** as the `source_a_value` column; they are never written to `resolved_values.json`.
- When source 1 is silent on a sub-field (e.g., exact task-level file sizes for non-example tasks), source 2 is used to fill the gap.
