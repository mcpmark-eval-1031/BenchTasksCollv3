# Render Contract — `kept_subset.json`

> **Status: FROZEN.**  This document must not be modified after
> `render_preview.json` or `contract_checklist.md` have been written.
> Any change requires a new contract version and new preview/checklist.

---

## 1. Scope

This contract governs every conforming instance of **`kept_subset.json`**, the
canonical *file-set artifact* produced by the boundary-review workflow for
`bugmaker00/BenchTasksCollv3-review`.  A conforming instance contains exactly the
77 tasks that passed all three E0 inclusion criteria during the boundary review
of 116 candidate tasks staged on the `boundary-review` branch.

The contract covers:
* top-level envelope field names and their order (§2)
* task-record field names and their order (§3)
* empty-value policy for every field (§4)
* normalisation rules for string fields (§5)
* ordering constraints for the `tasks` array (§6)
* global invariants (§7)

---

## 2. Top-level envelope fields (in order)

| # | Field name          | JSON type | Required | Allowed values / constraints |
|---|---------------------|-----------|----------|------------------------------|
| 1 | `description`       | string    | yes      | Human-readable sentence describing the file's content; must not be empty |
| 2 | `total_kept`        | integer   | yes      | Must equal `tasks.length`; for the canonical set always 77 |
| 3 | `inclusion_rule`    | string    | yes      | Describes the E0 acceptance criterion; must not be empty |
| 4 | `source_repository` | string    | yes      | Format `"<owner>/<repo>"`; e.g. `"bugmaker00/BenchTasksCollv3-review"` |
| 5 | `review_branch`     | string    | yes      | Name of the finalpool/staging branch; e.g. `"finalpool"` |
| 6 | `full_scope_csv`    | string    | yes      | Human-readable reference to `full_scope.csv` plus its verified file/task counts; must not be empty |
| 7 | `tasks`             | array     | yes      | Ordered list of task-record objects (see §3) |

**Field order is mandatory**: a conforming serialiser must emit these seven keys
in the exact sequence above.  No additional top-level keys are permitted.

---

## 3. Task-record fields (in order)

Each element of `tasks` is a JSON object with the following seven fields in
this exact order:

| # | Field name          | JSON type | Required | Allowed values / constraints |
|---|---------------------|-----------|----------|------------------------------|
| 1 | `task`              | string    | yes      | Task slug; kebab-case; see §5 |
| 2 | `source_branch`     | string    | yes      | Source developer branch name; may use `-dev`, `_dev`, or bare dev name suffix patterns; must not be empty |
| 3 | `source_dev`        | string    | yes      | Developer login; lowercase alphanumeric only; see §5 |
| 4 | `file_count`        | integer   | yes      | Number of files in the task directory tree; observed range 3–7; must be ≥ 1 |
| 5 | `verdict`           | string    | yes      | Always `"KEEP"` in this file (ALL CAPS) |
| 6 | `rule`              | string    | yes      | Always `"E0"` in this file; pattern `[A-Z][0-9]+` |
| 7 | `decisive_evidence` | string    | yes      | Non-empty; explains why this task passes E0; see §5 |

**Field order is mandatory** within each task record.  No additional per-task
keys are permitted.

---

## 4. Empty-value policy

| Field               | When field has no meaningful value | Representation |
|---------------------|------------------------------------|----------------|
| `decisive_evidence` | — never absent for E0 tasks —      | Always a non-empty string; `null` and `""` are **not** permitted |
| `file_count`        | — always known for E0 tasks —      | Always a positive integer; `null` and the string `"n/a"` are **not** permitted (contrast: `boundary_review.csv` uses `"n/a"` for DROP rows) |
| `description`, `inclusion_rule`, `source_repository`, `review_branch`, `full_scope_csv` | — always known — | Non-empty strings; `null` is **not** permitted |
| `task`, `source_branch`, `source_dev` | — always known — | Non-empty strings; `null` is **not** permitted |

**Summary rule:** no field in a conforming `kept_subset.json` may be `null`,
`""`, or absent.

---

## 5. Normalisation rules

| Field               | Rule |
|---------------------|------|
| `task`              | All lowercase; characters `[a-z0-9-]` only; no consecutive hyphens; no leading or trailing hyphens; matches the task directory name on the source branch |
| `source_dev`        | All lowercase; characters `[a-z0-9]` only; no hyphens, no underscores; derived from the branch name by stripping `-dev` / `_dev` suffixes |
| `source_branch`     | Preserved verbatim from the Git branch name; no casing normalisation applied |
| `verdict`           | All uppercase; constrained to the literal `"KEEP"` in this file |
| `rule`              | Pattern `[A-Z][0-9]+`; constrained to the literal `"E0"` in this file |
| `decisive_evidence` | Free-form English prose summarising the E0 pass; format convention is `"evaluation/main.py present; all docs at standard template byte-sizes (<file>=<N>B …); no CJK characters detected; structure complete"` |
| `description`       | Sentence case; may contain any printable characters |
| `inclusion_rule`    | Sentence case; must begin with `"E0: "` |
| `source_repository` | Format `"<owner>/<repo>"`; no trailing slash |
| `review_branch`     | Git branch name; no normalisation |
| `full_scope_csv`    | References `full_scope.csv` by filename; must include file and task counts |

---

## 6. Ordering constraints

1. **Primary (and only) sort key:** `task` field, ascending lexicographic order
   (Unicode code-point / byte-order on ASCII characters; all task names consist
   of ASCII only).
2. **Tie-breaking:** the `task` value is globally unique across all 77 records;
   ties are impossible.
3. The ordering is applied to the entire flat `tasks` array; no grouping or
   sub-arrays are used.
4. `source_dev` grouping is NOT used as a sort criterion; tasks from the same
   developer may be interleaved with those of other developers.

---

## 7. Invariants

| ID  | Invariant |
|-----|-----------|
| I-1 | `total_kept` == `len(tasks)` |
| I-2 | Every `task` value is unique across all records |
| I-3 | `verdict` == `"KEEP"` for every record |
| I-4 | `rule` == `"E0"` for every record |
| I-5 | `decisive_evidence` is a non-empty string for every record |
| I-6 | `file_count` is a positive integer for every record |
| I-7 | `tasks` is sorted in ascending order by `task` |
| I-8 | `source_dev` is all-lowercase alphanumeric for every record |
| I-9 | No top-level key or per-task key is absent, null, or an empty string |

---

## 8. Contract revision history

| Version | Date       | Author     | Summary |
|---------|------------|------------|---------|
| 1.0     | 2026-04-11 | bugmaker00 | Initial frozen contract; grounded in live `kept_subset.json` on `boundary-review` branch |
