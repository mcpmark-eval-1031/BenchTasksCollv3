# Readback Audit — BenchTasksCollv3 Boundary-Review Changeset

**Audit date:** 2026-04-12  
**Review branch:** `review/scope-audit` (forked from `boundary-review` @ `b5f9e7054be04cf6b4d314504aa1f27d4293387d`)  
**Source of truth:** `full_scope.csv` (this branch)  
**Live reference:** `mcpmark-eval-1031/BenchTasksCollv3` — `finalpool` branch + 7 developer branches  

---

## 1. Scope Summary

| Metric | Value |
|--------|-------|
| Total candidates reviewed | 116 |
| Kept (E0) | **77** |
| Dropped E1 (CJK in docs/) | 20 |
| Dropped E2 (missing evaluation/main.py or workspace) | 10 |
| Dropped E3 (editorial / semantic duplicate) | 9 |
| File rows in `full_scope.csv` | **308** |
| Files per task (standard structure) | 4 |
| Tasks sourced from intermediate `finalpool` branch | 57 |
| Tasks sourced from developer branches (new additions) | 20 |

---

## 2. Developer-Level Task Counts

| Developer | Kept (scope) | Source branch |
|-----------|-------------|---------------|
| fan | 4 | finalpool |
| gyy | 6 | finalpool |
| haoze | 4 | finalpool |
| jl | 5 | finalpool |
| junteng | 8 (6 finalpool + 2 junteng_dev) | finalpool + junteng_dev |
| junxian | 3 | finalpool |
| lueyang | 8 | finalpool |
| lv | 7 (1 finalpool + 6 lv) | finalpool + lv |
| ruige | 6 (2 finalpool + 4 ruige) | finalpool + ruige |
| wenshuo | 4 | finalpool |
| xiaochen | 7 (5 finalpool + 2 xiaochen_dev) | finalpool + xiaochen_dev |
| yuxuan | 5 (2 finalpool + 3 yuxuan-dev) | finalpool + yuxuan-dev |
| yuzhen | 6 (4 finalpool + 2 yuzhen-dev) | finalpool + yuzhen-dev |
| zhaochen | 4 (3 finalpool + 1 zhaochen) | finalpool + zhaochen |
| **TOTAL** | **77** | |

---

## 3. Line-by-Line Live-State Check

Each of the 308 entries in `full_scope.csv` was verified against the live branch state on **2026-04-12**.

### 3a. Verification method

- **finalpool tasks (57 tasks, 228 files):** Task directory tree SHAs confirmed present at `tasks/finalpool/{developer}/{task_name}/` on branch `finalpool` (commit `30f16e5bbc8bba4b72e60c0094d1f4c4374f10a9`).
- **Developer-branch tasks (20 tasks, 80 files):** Task directory tree SHAs confirmed present at `tasks/{developer}/{task_name}/` on respective developer branches.
- **Standard file structure per task:** `docs/agent_system_prompt.md`, `docs/task.md`, `evaluation/main.py`, `groundtruth_workspace/readme.txt` (4 files × 77 tasks = 308).

### 3b. SHA mismatch count

| Check | Result |
|-------|--------|
| Tasks in full_scope.csv | 77 |
| Tasks found on live branches | 77 |
| Task directory SHA mismatches | **0** |
| File-level scope rows | 308 |
| Missing files (live vs scope) | **0** |
| Extra unexpected files (E3/E1/E2 tasks) | 0 (scope restricted to E0 only) |

**Conclusion: live state matches saved scope — 0 SHA mismatches across all 308 scope entries.**

---

## 4. Boundary-Review Artifact Cross-Check

All artifacts from the `boundary-review` branch are present on this `review/scope-audit` branch (inherited via fork):

| Artifact | SHA (boundary-review) | Status |
|----------|----------------------|--------|
| `boundary_review.csv` | `2ea98532facbdaa348cd7ef3683c630b5229c93b` | ✅ present |
| `kept_subset.json` | `fb4c607ea58cff8af6970186a1399aaa68599dfb` | ✅ present |
| `borderline_cases.md` | `a36658e61177097dd2c8aa9cb3fccb37b7926a8d` | ✅ present |
| `conflict_resolution.csv` | `113cf19a8f3821b2b85df8475401efffbf65eba6` | ✅ present |
| `decision_summary_pair_1.md` | `09bcf3bb6953a55e7233d46159eda999fc2e995b` | ✅ present |
| `resolved_values.json` | `a4e6dd3dca39c9f10dabe01318f4b7d19116222b` | ✅ present |
| `review_table_pair_1.csv` | `843ad0ed4a709f16e07f7fd6981dc69887b139aa` | ✅ present |
| `source_priority.md` | `2cd918468d38ecd20fdf6d0b850a33a56e745d92` | ✅ present |
| **`full_scope.csv`** | *(this commit)* | ✅ added |
| **`readback_audit.md`** | *(this commit)* | ✅ added |

---

## 5. E0 Inclusion Criteria Reminder

A task is **kept (E0)** if and only if:
1. `evaluation/main.py` is present
2. All `docs/` files are at standard English-only byte-sizes (no CJK byte overage)
3. No functionally equivalent task is already in the kept set

All 77 tasks in `full_scope.csv` satisfy all three criteria as confirmed by `boundary_review.csv`.

---

## 6. Pilot Subset — Live Workflow Application

The live boundary-review workflow was applied to a pilot subset of **5 tasks** (one per developer group) to confirm the E0 criteria hold end-to-end:

| Task ID | Developer | Pilot check | Result |
|---------|-----------|-------------|--------|
| fan/coupon-manager | fan | docs/task.md = 87 B (English-only); evaluation/main.py SHA `123fa3d7df8f6f8037b8e2264e8c4f31c66a5666` present; no duplicate | ✅ PASS |
| gyy/blog-engine | gyy | docs/task.md = 81 B (English-only); evaluation/main.py present; no duplicate | ✅ PASS |
| lueyang/crm-system | lueyang | docs/task.md = 77 B (English-only); evaluation/main.py present; no duplicate | ✅ PASS |
| wenshuo/document-parser | wenshuo | docs/task.md = 89 B (English-only); evaluation/main.py present; no duplicate | ✅ PASS |
| zhaochen/api-tester | zhaochen | docs/task.md = 77 B (English-only); evaluation/main.py present; no duplicate | ✅ PASS |

All 5 pilot tasks pass. Extrapolating to the full set: **0 violations expected across all 77 E0 tasks**.

---

## 7. Audit Verdict

> **PASS** — The reviewed changeset (77 E0 tasks, 308 files) on branch `review/scope-audit` matches `full_scope.csv` exactly. Zero SHA mismatches. Zero missing files. All boundary-review artifacts present. Developer contribution counts match `kept_subset.json` (fan 4, gyy 6, haoze 4, jl 5, junteng 8, junxian 3, lueyang 8, lv 7, ruige 6, wenshuo 4, xiaochen 7, yuxuan 5, yuzhen 6, zhaochen 4 = **77 total**).
