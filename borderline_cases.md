# Borderline Cases — Closest Rejected Tasks

This document explains the nine tasks that were **nearest to the inclusion
boundary** (Rule E3). They are structurally complete, carry no CJK
contamination, and were present in earlier intermediate finalpools
(e.g., `mcpmark-eval-1031/BenchTasksCollv3@finalpool`, committed 2026-03-23).
They were excluded from the canonical `bugmaker00/BenchTasksCollv3-review@finalpool`
(committed 2026-04-09) during final editorial review for **semantic redundancy**.

## How E3 differs from E1 / E2

| Rule | Trigger | Objective test |
|------|---------|----------------|
| E1 | CJK characters in any `docs/` file | File size exceeds `107 + len(name)` B (agent_system_prompt) or `59 + 2×len(name)` B (task.md) |
| E2 | Missing `evaluation/main.py` or required workspace dir | Directory listing check |
| **E3** | **Task semantics fully subsumed by a kept task** | **Human editorial judgment; cross-checked against finalpool set** |

## E3 Task Profiles

---

### 1. `fan/review-aggregator`  
**Source branch:** `fan-dev` | **Developer:** fan  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 124 B (✓) · task.md 93 B (✓) · user\_system\_prompt.md 52 B (✓)  
**Why rejected:** Review aggregation (collecting and summarising user reviews) is functionally subsumed by **`feedback-collector`** (kept; aggregates user feedback) and **`sentiment-analyzer`** (kept; analyses tone of collected input). Adding a third task on the same feedback-ingestion loop would create near-duplicate evaluation scenarios.  
**Kept alternatives:** `feedback-collector`, `sentiment-analyzer`

---

### 2. `fan/wishlist-manager`  
**Source branch:** `fan-dev` | **Developer:** fan  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 123 B (✓) · task.md 91 B (✓) · user\_system\_prompt.md 51 B (✓)  
**Why rejected:** Wish-list management is a narrow sub-feature of product catalogue management. **`product-catalog`** (kept) and **`content-manager`** (kept) already cover adding, organising, and retrieving item records; a standalone wish-list task would exercise the same MCP tool paths (file I/O, list manipulation).  
**Kept alternatives:** `product-catalog`, `content-manager`

---

### 3. `gyy/comment-moderator`  
**Source branch:** `gyy` | **Developer:** gyy  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 124 B (✓) · task.md 93 B (✓) · user\_system\_prompt.md 52 B (✓)  
**Why rejected:** Comment moderation is a subset of content management and publication workflows. **`social-publisher`** (kept) covers publishing and managing posts; **`content-scheduler`** (kept) covers scheduling content changes. Moderating comments exercises the same read–classify–update tool loop.  
**Kept alternatives:** `social-publisher`, `content-scheduler`

---

### 4. `haoze/thumbnail-creator`  
**Source branch:** `haoze` | **Developer:** haoze  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 124 B (✓) · task.md 93 B (✓) · user\_system\_prompt.md 52 B (✓)  
**Why rejected:** Thumbnail creation is a strict sub-task of image processing (resize, crop, compress). **`image-processor`** (kept, wenshuo) already provides a complete image-manipulation task. A separate thumbnail task would be a proper subset of that evaluation surface.  
**Kept alternative:** `image-processor`

---

### 5. `junxian/url-shortener`  
**Source branch:** `junxian_dev` | **Developer:** junxian  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 120 B (✓) · task.md 85 B (✓) · user\_system\_prompt.md 48 B (✓)  
**Why rejected:** Both `url-shortener` and **`qr-generator`** (kept) are link-utility tasks that encode a URL into a compact, shareable form. `qr-generator` was retained because QR codes require a richer tool interaction (image generation + encoding). A URL shortener in this benchmark would probe only string manipulation and a simple API call.  
**Kept alternative:** `qr-generator`

---

### 6. `lueyang/lead-tracker`  
**Source branch:** `lueyang-dev` | **Developer:** lueyang  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 119 B (✓) · task.md 83 B (✓) · user\_system\_prompt.md 47 B (✓)  
**Why rejected:** Lead tracking is the first stage of the CRM pipeline. **`crm-system`** (kept) and **`contact-manager`** (kept) already cover the full lifecycle from contact creation to relationship management. A standalone lead-tracking task duplicates those evaluation scenarios.  
**Kept alternatives:** `crm-system`, `contact-manager`

---

### 7. `wenshuo/document-parser`  
**Source branch:** `wenshuo-dev` | **Developer:** wenshuo  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt  
**Doc sizes:** agent\_system\_prompt.md 122 B (✓) · task.md 89 B (✓) · user\_system\_prompt.md 50 B (✓)  
**Why rejected:** Document parsing (extract text/structure from files) is a sub-operation of file management and search. **`file-manager`** (kept, ruige) and **`search-engine`** (kept, wenshuo — same developer) already exercise file I/O and content extraction. Including this task would give wenshuo an effectively duplicate entry alongside `search-engine`.  
**Kept alternatives:** `file-manager`, `search-engine`

---

### 8. `xiaochen/code-reviewer`  
**Source branch:** `xiaochen_dev` | **Developer:** xiaochen  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 120 B (✓) · task.md 85 B (✓) · user\_system\_prompt.md 48 B (✓)  
**Why rejected:** Code review (static analysis, identifying issues, suggesting fixes) is functionally subsumed by **`security-scanner`** (kept), which performs a superset of the code-analysis workflow. Retaining both would make the xiaochen developer set top-heavy with nearly-identical developer-tool tasks.  
**Kept alternative:** `security-scanner`

---

### 9. `zhaochen/markdown-converter`  
**Source branch:** `zhaochen` | **Developer:** zhaochen  
**Structure:** docs (3 files) · evaluation/main.py · groundtruth\_workspace/readme.txt · initial\_workspace/readme.txt · preprocess/main.py  
**Doc sizes:** agent\_system\_prompt.md 125 B (✓) · task.md 95 B (✓) · user\_system\_prompt.md 53 B (✓)  
**Why rejected:** Markdown-to-HTML/PDF conversion is a narrow instance of template rendering. **`template-engine`** (kept, same developer zhaochen) already covers text transformation with substitution and formatting logic. Including both tasks from the same developer would bias zhaochen’s contribution toward text-processing.  
**Kept alternative:** `template-engine`

---

## Summary Table

| Task | Branch | Rule | Closest kept alternative(s) |
|------|--------|------|------------------------------|
| review-aggregator | fan-dev | E3 | feedback-collector, sentiment-analyzer |
| wishlist-manager | fan-dev | E3 | product-catalog, content-manager |
| comment-moderator | gyy | E3 | social-publisher, content-scheduler |
| thumbnail-creator | haoze | E3 | image-processor |
| url-shortener | junxian_dev | E3 | qr-generator |
| lead-tracker | lueyang-dev | E3 | crm-system, contact-manager |
| document-parser | wenshuo-dev | E3 | file-manager, search-engine |
| code-reviewer | xiaochen_dev | E3 | security-scanner |
| markdown-converter | zhaochen | E3 | template-engine |

## Inclusion boundary clarification

A task is **kept (E0)** if it satisfies all three conditions simultaneously:

1. **Structural completeness** — `evaluation/main.py` present **and** all required workspace directories present  
2. **English-only documentation** — no CJK characters; all doc files at standard template byte-sizes  
3. **Semantic uniqueness** — no functionally equivalent task already in the kept set

The nine E3 tasks satisfy conditions 1 and 2 but fail condition 3.  
Tasks failing condition 1 are classified E2; tasks failing condition 2 are classified E1.  
E1 and E2 failures are detected objectively; E3 failures require editorial judgment.
