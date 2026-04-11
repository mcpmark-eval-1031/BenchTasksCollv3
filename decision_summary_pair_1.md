# Decision Summary — Pair 1: Boundary-Review Repository Identification

**Subproblem:** Identify and preserve the exact canonical repository for the MCPBench-Dev project under ambiguous GitHub evidence introduced by the existence of a parallel intermediate snapshot.

**Generated from:** `review_table_pair_1.csv` (boundary-review branch, `bugmaker00/BenchTasksCollv3-review`)  
**Date:** 2026-04-11  
**Canonical finalpool commit:** `531b8ecc7c8d351a11f828fb88b6b34be91c5857`

---

## 1. The Two Repositories in the Pair

| Role | Repository | Branch | Date | Task count |
|------|-----------|--------|------|-----------|
| **Repo A — Intermediate snapshot** | `mcpmark-eval-1031/BenchTasksCollv3` | `finalpool` | 2026-03-23 | 67 (all KEEP) |
| **Repo B — Canonical (authoritative)** | `bugmaker00/BenchTasksCollv3-review` | `finalpool` | 2026-04-09 | 77 KEEP of 116 candidates |

---

## 2. The Two Review Dimensions

### Dimension 1 — Boundary-verdict (E-code)

Applied to all 116 candidate tasks in `bugmaker00/BenchTasksCollv3-review@boundary-review`:

| Verdict | Rule | Count | Meaning |
|---------|------|-------|--------|
| **KEEP** | E0 | **77** | Passes all three inclusion criteria |
| DROP | E1 | 20 | CJK characters detected in a `docs/` file |
| DROP | E2 | 10 | Missing `evaluation/main.py` or required workspace dir |
| DROP | E3 | 9 | Structurally complete and clean text; excluded for semantic overlap with a kept task |
| **Total** | | **116** | 14 developer branches × up to 10 tasks each |

Inclusion criteria for E0 (all three must hold):
1. `evaluation/main.py` is present  
2. All `docs/` files are at standard English-only template byte-sizes (no CJK overage)  
3. No functionally equivalent task already exists in the kept set

### Dimension 2 — Snapshot membership (Repo A vs Repo B)

Each of the 116 candidates is classified against the intermediate finalpool (`mcpmark-eval-1031/BenchTasksCollv3@finalpool`, 2026-03-23):

| in_intermediate_fp | Count | Breakdown |
|--------------------|-------|----------|
| YES — present in intermediate (verdict was KEEP) | 67 | 38 E0 + 20 E1 + 9 E3 |
| NO — added after intermediate (not present) | 49 | 39 E0 + 10 E2 |

Key observations:
- All **20 E1** tasks were in the intermediate and mis-classified as KEEP (CJK content was not detected under the intermediate's simpler criterion).
- All **9 E3** tasks were in the intermediate as KEEP but excluded by editorial curation in the canonical review (semantic overlap with kept tasks).
- All **10 E2** tasks were added after the intermediate; none passed the intermediate's structural check.

---

## 3. The Resolved Result

### 3.1 Canonical repository string

```
bugmaker00/BenchTasksCollv3-review
```

This is the sole authoritative repository for the MCPBench-Dev boundary review. The intermediate snapshot (`mcpmark-eval-1031/BenchTasksCollv3@finalpool`) is a **tertiary, superseded source** per priority rule SR-2 (later authoritative snapshot prevails).

### 3.2 Project name

**MCPBench-Dev** — per priority rule SR-4: `README.md` (active working name, consistent across all branches) wins over `README_BASE.md` ("BenchTaskCo llv2", historical base template) and the GitHub repository name (`BenchTasksCollv3-review`, which encodes version/role only).

### 3.3 Verdicts resolved across both dimensions

| Scenario | Dim-1 (E-code) | Dim-2 (in_intermediate) | Canonical verdict | Count |
|----------|---------------|------------------------|------------------|-------|
| Stable keep — in both pools | E0 | YES | KEEP | 38 |
| New keep — added after intermediate | E0 | NO | KEEP | 39 |
| CJK drop — was in intermediate as KEEP | E1 | YES | **DROP** (SR-2 wins) | 20 |
| Structure-incomplete drop — new only | E2 | NO | DROP | 10 |
| Editorial drop — was in intermediate as KEEP | E3 | YES | **DROP** (SR-2 wins) | 9 |

**Total tasks with verdict flip (intermediate KEEP → canonical DROP): 29** (20 E1 + 9 E3)

The 9 E3 tasks whose verdicts changed:
`code-reviewer`, `comment-moderator`, `document-parser`, `lead-tracker`, `markdown-converter`, `review-aggregator`, `thumbnail-creator`, `url-shortener`, `wishlist-manager`

### 3.4 Source-priority ruling applied

Rule **SR-2** governs the 29 verdict flips: the canonical finalpool (`bugmaker00/BenchTasksCollv3-review@finalpool`, 2026-04-09) is chronologically later and editorially more complete than the intermediate (`mcpmark-eval-1031/BenchTasksCollv3@finalpool`, 2026-03-23). The later, more-reviewed snapshot always supersedes the earlier one on the same repository lineage.

---

## 4. Verification Checklist

- [x] Dimension 1 (E-code) complete for all 116 candidates — sourced from `boundary_review.csv` (SHA `92d7707845d624ea9428cd6d6d2acb2f44b6aed1`)
- [x] Dimension 2 (snapshot membership) complete for all 116 candidates — sourced from intermediate finalpool README (`tasks/finalpool/README.md`, SHA `679cacc001162bab1cb767b25c7b4b3b1fb4c365`) listing 67 tasks
- [x] Both dimensions combined in `review_table_pair_1.csv` (116 rows, 8 columns)
- [x] Verdict counts verified: 77 KEEP + 20 E1 + 10 E2 + 9 E3 = 116 ✓
- [x] Intermediate task count verified: 38 E0 + 20 E1 + 9 E3 = 67 ✓
- [x] Canonical repo string confirmed: `bugmaker00/BenchTasksCollv3-review`
- [x] Project name confirmed: `MCPBench-Dev` (per SR-4 from `resolved_values.json`)
- [x] Finalpool commit SHA confirmed: `531b8ecc7c8d351a11f828fb88b6b34be91c5857`

---

## 5. Files Staged

| File | Purpose |
|------|--------|
| `review_table_pair_1.csv` | 116-row table combining Dim-1 (E-code verdict) and Dim-2 (intermediate snapshot membership) |
| `decision_summary_pair_1.md` | This document — final resolved result for subproblem pair 1 |

Both files are staged on the `boundary-review` branch of `bugmaker00/BenchTasksCollv3-review`, consistent with the existing PR #1 change set.
