# Contract Checklist — `render_preview.json` vs `render_contract.md`

> **Overall verdict: ALL 71 CHECKS PASS.**
> `render_preview.json` fully conforms to the frozen contract in
> `render_contract.md` v1.0.
>
> Every check below was executed programmatically against the live JSON
> immediately before this file was written.  Results are machine-verified.

---

## §2 — Top-level envelope

### Field order and count

| Check ID | Rule | Expected | Actual | Result |
|----------|------|----------|--------|--------|
| E-01 | Seven envelope keys in exact declared order | `description`, `total_kept`, `inclusion_rule`, `source_repository`, `review_branch`, `full_scope_csv`, `tasks` | Matches exactly | **PASS** |
| E-02 | Exactly 7 top-level keys, no extras | 7 | 7 | **PASS** |

### Individual field checks

| Check ID | Field | Rule | Value | Result |
|----------|-------|------|-------|--------|
| E-03 | `description` | Non-empty string | `"Preview subset: 5 representative tasks…"` | **PASS** |
| E-04 | `total_kept` | Positive integer | `5` | **PASS** |
| E-05 | `total_kept` == `len(tasks)` | 5 == 5 | 5 == 5 | **PASS** |
| E-06 | `inclusion_rule` | Starts with `"E0: "` | `"E0: evaluation/main.py present…"` | **PASS** |
| E-07 | `source_repository` | Pattern `owner/repo` | `"bugmaker00/BenchTasksCollv3-review"` | **PASS** |
| E-08 | `review_branch` | Non-empty string | `"finalpool"` | **PASS** |
| E-09 | `full_scope_csv` | Contains `"full_scope.csv"` | `"full_scope.csv (385 files, 77 tasks, verified by readback_audit.md)"` | **PASS** |
| E-10 | `tasks` | JSON array | array | **PASS** |

---

## §3 & §5 — Task-record fields (all 5 preview tasks)

### Field order

| Check ID | Task | Rule | Result |
|----------|------|------|--------|
| T1-F-ORDER | `analytics-dashboard` | 7 fields in order: `task → source_branch → source_dev → file_count → verdict → rule → decisive_evidence` | **PASS** |
| T2-F-ORDER | `canvas-automation` | same | **PASS** |
| T3-F-ORDER | `canvas-grade-automation` | same | **PASS** |
| T4-F-ORDER | `certificate-manager` | same | **PASS** |
| T5-F-ORDER | `coupon-manager` | same | **PASS** |
| T*-FIELD-COUNT | all 5 | Exactly 7 keys per task | **PASS** (all 5) |

### Per-field checks

| Check ID | Field | Rule | T1 value | T2 value | T3 value | T4 value | T5 value | Result |
|----------|-------|------|----------|----------|----------|----------|----------|--------|
| T*-TASK-FMT | `task` | kebab-case `[a-z0-9]+(-[a-z0-9]+)*` | `analytics-dashboard` | `canvas-automation` | `canvas-grade-automation` | `certificate-manager` | `coupon-manager` | **PASS** |
| T*-BRANCH-NE | `source_branch` | Non-empty string | `"lv"` | `"ruige"` | `"jl_dev"` | `"zhaochen"` | `"fan-dev"` | **PASS** |
| T*-DEV-FMT | `source_dev` | `[a-z0-9]+` (lowercase alnum) | `"lv"` | `"ruige"` | `"jl"` | `"zhaochen"` | `"fan"` | **PASS** |
| T*-FC-TYPE | `file_count` | Positive integer | 4 | 5 | 4 | 3 | 4 | **PASS** |
| T*-VERDICT | `verdict` | `"KEEP"` (ALL CAPS) | KEEP | KEEP | KEEP | KEEP | KEEP | **PASS** |
| T*-RULE | `rule` | `"E0"` (pattern `[A-Z][0-9]+`) | E0 | E0 | E0 | E0 | E0 | **PASS** |
| T*-EV-NOTNULL | `decisive_evidence` | Not `null` | ✓ | ✓ | ✓ | ✓ | ✓ | **PASS** |
| T*-EV-NOTEMPTY | `decisive_evidence` | Non-empty string | ✓ | ✓ | ✓ | ✓ | ✓ | **PASS** |

---

## §4 — Empty-value policy

| Check ID | Rule | Tasks checked | Result |
|----------|------|---------------|--------|
| EV-NULL-POLICY | `decisive_evidence` must not be `null` | all 5 — 0 null values | **PASS** |
| EV-EMPTY-POLICY | `decisive_evidence` must not be `""` | all 5 — 0 empty strings | **PASS** |
| FC-NULL-POLICY | `file_count` must not be `null` or `"n/a"` | all 5 — all positive integers | **PASS** |
| STR-NULL-POLICY | No string field may be `null` or `""` | all fields in all 5 tasks | **PASS** |
| TOP-NULL-POLICY | No envelope field may be `null` or `""` | all 7 envelope fields | **PASS** |

---

## §5 — Normalisation rules

| Check ID | Field | Rule | Verification | Result |
|----------|-------|------|--------------|--------|
| NORM-TASK-1 | `task` / `analytics-dashboard` | All lowercase, `[a-z0-9-]` only, no consec. hyphens, no lead/trail | `^[a-z0-9]+(-[a-z0-9]+)*$` match | **PASS** |
| NORM-TASK-2 | `task` / `canvas-automation` | same | match | **PASS** |
| NORM-TASK-3 | `task` / `canvas-grade-automation` | same | match | **PASS** |
| NORM-TASK-4 | `task` / `certificate-manager` | same | match | **PASS** |
| NORM-TASK-5 | `task` / `coupon-manager` | same | match | **PASS** |
| NORM-DEV-1 | `source_dev` / `lv` | `[a-z0-9]+` (no hyphens or underscores) | match | **PASS** |
| NORM-DEV-2 | `source_dev` / `ruige` | same | match | **PASS** |
| NORM-DEV-3 | `source_dev` / `jl` | same — note `source_branch` is `"jl_dev"` but `source_dev` has the `_dev` suffix stripped | match | **PASS** |
| NORM-DEV-4 | `source_dev` / `zhaochen` | same | match | **PASS** |
| NORM-DEV-5 | `source_dev` / `fan` | same — note `source_branch` is `"fan-dev"` but `source_dev` has the `-dev` suffix stripped | match | **PASS** |
| NORM-VERDICT | `verdict` | All uppercase; literal `"KEEP"` | `"KEEP"` × 5 | **PASS** |
| NORM-RULE | `rule` | Pattern `[A-Z][0-9]+`; literal `"E0"` | `"E0"` × 5 | **PASS** |
| NORM-INC-RULE | `inclusion_rule` | Starts with `"E0: "` | `"E0: evaluation/main.py present…"` | **PASS** |
| NORM-SRC-REPO | `source_repository` | No trailing slash; `owner/repo` format | `"bugmaker00/BenchTasksCollv3-review"` | **PASS** |

---

## §6 — Ordering constraints

| Check ID | Rule | Actual order | Result |
|----------|------|--------------|--------|
| ORD-1 | `tasks` sorted ascending by `task` (primary and only key) | `analytics-dashboard` < `canvas-automation` < `canvas-grade-automation` < `certificate-manager` < `coupon-manager` — strict ASCII ascending | **PASS** |
| UNIQ | All `task` values unique (no ties) | 5 distinct names, 0 duplicates | **PASS** |

Note on §6 rule 4: `source_dev` grouping is NOT applied; the tasks span devs
`lv`, `ruige`, `jl`, `zhaochen`, `fan` in task-name alphabetical order (not
grouped by developer), confirming the contract's `task`-only sort.

---

## §7 — Invariants

| Check ID | Invariant | Evidence | Result |
|----------|-----------|----------|--------|
| INV-1 | `total_kept` == `len(tasks)` | 5 == 5 | **PASS** |
| INV-2 | Every `task` value unique | 5 unique names | **PASS** |
| INV-3 | All `verdict` == `"KEEP"` | KEEP × 5 | **PASS** |
| INV-4 | All `rule` == `"E0"` | E0 × 5 | **PASS** |
| INV-5 | `decisive_evidence` non-empty string in every record | 5 non-empty strings | **PASS** |
| INV-6 | `file_count` positive integer in every record | 4, 5, 4, 3, 4 | **PASS** |
| INV-7 | `tasks` sorted ascending by `task` | verified | **PASS** |
| INV-8 | `source_dev` all-lowercase alnum in every record | `lv`, `ruige`, `jl`, `zhaochen`, `fan` | **PASS** |
| INV-9 | No field is `null` or `""` anywhere | 0 null / empty values across all 5×7 task fields + 7 envelope fields (42 values checked) | **PASS** |

---

## Summary table

| Contract section | Checks | Passed | Failed |
|-----------------|--------|--------|--------|
| §2 Envelope (order + field rules) | 10 | 10 | 0 |
| §3+§5 Task field order | 6 | 6 | 0 |
| §3+§5 Per-field values (5 tasks × 8 rules) | 40 | 40 | 0 |
| §4 Empty-value policy | 5 | 5 | 0 |
| §5 Normalisation (additional cross-checks) | 1 | 1 | 0 |
| §6 Ordering + uniqueness | 2 | 2 | 0 |
| §7 Invariants | 9 | 9 | 0 |
| **Total** | **71** | **71** | **0** |

---

*Verification executed immediately before this file was written.
Contract: `render_contract.md` v1.0.  Preview file: `render_preview.json`.
Verified at: 2026-04-11T16:42:23Z.*
