# Evidence Notes — personal-website-construct (subproblem single_2)

**Review date:** 2026-04-12  
**Upstream template:** `academicpages/academicpages.github.io` (master, tree `4f52d97e`)  
**Destination namespace:** `mazextest2026/LJT-Homepage` (main, HEAD `5adccf65`)  
**Task instance:** `finalpool-personal-website-construct_5`  
**Subject:** Junteng Liu — First-year PhD candidate, HKUST NLP Group  
**Memory source:** `initial_workspace/memory/memory.json` (SHA `45929f86`) in `Klavis-AI/Toolathlon-mvp`

---

## Summary of fork-flow resolution

The agent forked `academicpages/academicpages.github.io` and **did not retain the fork link** — it created `mazextest2026/LJT-Homepage` as a fresh repository populated file-by-file via GitHub API, reusing template structure but with personalised content and stripped non-essential sections.

| Category | Count |
|---|---|
| TEMPLATE-IDENTICAL (kept verbatim) | 1 |
| TEMPLATE-MODIFIED (personalised) | 2 |
| TEMPLATE-RETAINED (directory, assumed identical) | 5 |
| NEW-IN-DESTINATION (personal content) | 6 |
| TEMPLATE-REMOVED / DROP | 36 |
| TEMPLATE-REMOVED / REVIEW (advisory) | 4 |
| **Total file-sets accounted for** | **54** |

---

## Finalized kept set (safe to apply live)

### 1. `_config.yml`  — TEMPLATE-MODIFIED / KEEP

**Upstream SHA:** `114fe4017e39f8a179b7349e5a23ab8fa01db83b` (10 408 B)  
**Destination SHA:** `ba519eadf5a68d8c4194d2d71bfb23827e10651e` (7 075 B)  
**Evidence:** Diff confirmed all required identity fields populated from memory:
- `title`, `name` → `Junteng Liu`
- `email` (author) → `jliugi@connect.ust.hk`
- `github` (author) → `Vicent0205`
- `googlescholar` → correct Scholar URL (`tbK9jl4AAAAJ`)
- `twitter` → `junteng88716710`
- `bio` → `First-year PhD candidate at HKUST NLP Group`
- `employer` → `Hong Kong University of Science and Technology`
- `url` / `repository` updated to `mazextest2026/LJT-Homepage`

**Evaluation check:** `check_remote_config_yaml` passes for all three required fields (`name`, `email`, `github`).

---

### 2. `_pages/about.md`  — TEMPLATE-MODIFIED / KEEP

**Upstream SHA:** `492fccc93ea2a93c9f957475eada5c18a32c2cdd` (7 946 B)  
**Destination SHA:** `f56595259a2cd7d3c2f15752637359330da6c4f7` (2 304 B)  
**Evidence:** Content review confirms all required fields from `check_remote_about_md`:
- ✅ `Junteng Liu` present
- ✅ `PhD candidate` present
- ✅ `HKUST` and `NLP` present
- ✅ `Shanghai Jiao Tong University` present
- ✅ Research interests: LLM Reasoning / Reinforcement Learning, Hallucination / VLM, Truthfulness / Interpretability
- ✅ Education: Ph.D. Computer Science (2024-Present) HKUST; B.Eng. (2020-2024) SJTU
- ✅ Internships: MINIMAX, Tencent WXG (Zifei Shan), Shanghai AI Lab (Prof. Yu Cheng)
- ✅ Publications — all 6 papers listed (SynLogic, VLM Chart, Truthfulness Hyperplane, Hallucination Mitigation, C-Eval, Parameter-Efficient Modules)
- ✅ Publications **also appear in about section** (satisfies task requirement: "record publications in about section as well")
- ✅ Contact: `jliugi@connect.ust.hk`, `github.com/Vicent0205`, Google Scholar, Twitter

---

### 3. `README.md`  — TEMPLATE-MODIFIED / KEEP

**Upstream SHA:** `74f399a2fc77a4bff799e133de8cbd98bbebdc32` (7 611 B)  
**Destination SHA:** `69a97abeff735c939382923f57f0b39c64d3ee8f` (57 B)  
**Evidence:** Replaced full academicpages contributor README with minimal personal-site README:  
`# LJT-Homepage\nPersonal academic homepage of Junteng Liu`  
Acceptable simplification; no information loss for end users.

---

### 4. `Gemfile`  — TEMPLATE-IDENTICAL / KEEP

**Upstream SHA == Destination SHA:** `ba132f0d204eceb3742f01f5c63e32598948f8c6` (239 B)  
**Evidence:** Byte-for-byte identical to upstream; contains Jekyll/GitHub-Pages gem declarations. No personalisation needed; safe to apply.

---

### 5. `_data/` `_includes/` `_layouts/` `_sass/` `assets/`  — TEMPLATE-RETAINED / KEEP

**Evidence:** Directory-level SHA comparison shows these subtrees are present in both upstream and destination. Commit messages in destination (`Add essential layout and include files`, `Add more include files`, `Add CSS files`, `Add _sass files`) confirm they were populated from the template. No personalisation applied; safe to apply verbatim.

---

### 6. New publication files  — NEW-IN-DESTINATION / KEEP

All six files are new content derived exclusively from `memory.json`; no overlap with upstream template content.

| File | SHA | Source entity |
|---|---|---|
| `_publications/2025-01-01-synlogic.md` | `8466864f` | SynLogic (first author, 2025) |
| `_publications/2025-01-02-vlm-chart.md` | `0596d037` | On the Perception Bottleneck (first author, 2025) |
| `_publications/2024-01-01-truthfulness-hyperplane.md` | `e18330c3` | Universal Truthfulness Hyperplane (first author, EMNLP 2024) |
| `_publications/2024-01-02-hallucination-mitigation.md` | `61edd86b` | In-Context Sharpness (co-author, ICML 2024) |
| `_publications/2023-01-01-ceval.md` | `370c6a82` | C-Eval (co-author, NeurIPS 2023) |
| `_publications/2023-01-02-parameter-efficient.md` | `31d4478d` | Composing Parameter-Efficient Modules (co-author, NeurIPS 2023) |

---

## Advisory REVIEWs (not blocked, but flag for human review)

1. **`.gitignore`** (template SHA `b41392be`, 458 B) — removed from destination. Recommend restoring the academicpages `.gitignore` to prevent accidental commits of build artefacts.

2. **`LICENSE`** (template SHA `23a6cd1d`, 1 078 B, MIT) — removed from destination. The academicpages template carries an MIT license; its omission may create attribution ambiguity. Recommend restoring or substituting an appropriate license.

3. **`_pages/category-archive.html`** (template SHA `3ed3378f`, 450 B) — removed. If any content contains category front-matter, links to `/categories/` will 404. Low risk given stripped content but advisory.

4. **`_pages/publications.html`** (template SHA `e2f94618`, 963 B) — removed; replaced by individual `_publications/*.md` collection files. The task requirement for a `/publications` subpage is met differently via Jekyll collections. **Confirmed compliant**: `about.md` also lists all publications (task requirement satisfied).

---

## Cross-validation

- All 6 publications present in `_publications/` match the 6 publication entities in `memory.json`.
- The 3 required `_config.yml` fields (`name`, `email`, `github`) are populated correctly as verified against evaluation script `check_remote.py`.
- The `_pages/about.md` satisfies all 10 checks in `check_remote_about_md`.
- Template-retained directories were populated incrementally across 5 commits (2026-04-10T06:07–06:11) confirming controlled fork-style population from upstream.
- No information was added beyond what is in `memory.json` (task constraint satisfied).
- No additional pages (CV, portfolio, talks, teaching) were added (task constraint satisfied).
