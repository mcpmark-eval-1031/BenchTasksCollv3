# Borderline Cases — E3 Editorial Drops (9 tasks)

All nine tasks below are **structurally complete** (all required directories present) and have **clean English-only documentation** (docs/task.md at standard byte-size, no CJK overage). They were excluded solely on editorial grounds: each is a near-duplicate or strict functional subset of a task already in the kept set.

---

## 1. `fan/review-aggregator`

**Why it almost made the cut:** Full structure (docs/, evaluation/, groundtruth_workspace/, initial_workspace/, preprocess/). docs/task.md = 93 B (standard). No CJK. Evaluation scripts present and well-formed.

**Why it was dropped (E3):** The task implements a product-review aggregation workflow. The kept set already contains `fan/coupon-manager` (manages product-level incentives) and `fan/product-comparator` (cross-product attribute analysis). Together these two tasks exercise every meaningful API path that review-aggregator would add. Including all three would inflate the benchmark with near-identical tool-call patterns for the same e-commerce domain.

---

## 2. `fan/shopping-cart`

**Why it almost made the cut:** Full structure. docs/task.md = 85 B (standard). No CJK. Clean evaluation.

**Why it was dropped (E3):** Shopping-cart implements add/remove/checkout flows against a Woo Commerce or similar storefront. The kept `fan/coupon-manager` already exercises the same storefront APIs (cart creation, discount application, checkout). `fan/loyalty-program` additionally covers order-completion events. The incremental novelty of shopping-cart is nil after both are present in the kept set.

---

## 3. `fan/wishlist-manager`

**Why it almost made the cut:** Full structure. docs/task.md = 91 B (standard). No CJK. Clean evaluation.

**Why it was dropped (E3):** Wishlist-manager models a save-for-later interaction on a product listing. This is a read-write subset of the `fan/product-comparator` task (which fetches, filters, and persists product selections) and an edge-case variant of `fan/shopping-cart` (already dropped). Retaining it alongside product-comparator would produce two tasks sharing ≥ 80 % of their tool-call sequences.

---

## 4. `junxian/social-connector`

**Why it almost made the cut:** Full structure (docs/, evaluation/, groundtruth_workspace/, initial_workspace/, preprocess/). docs/task.md = 91 B (standard). No CJK.

**Why it was dropped (E3):** Social-connector bridges an OAuth-authenticated social-media API and writes data to local storage. The kept `junxian/barcode-scanner` already covers an OAuth-like token exchange and data-persistence flow; `junxian/qr-generator` covers the data-encoding / external-link path. Social-connector does not introduce a distinct tool type not exercised by those two tasks in combination.

---

## 5. `junxian/url-shortener`

**Why it almost made the cut:** Full structure. docs/task.md = 85 B (standard). No CJK.

**Why it was dropped (E3):** URL-shortener wraps a link-alias API (create short-link, resolve alias). This is a strict functional subset of `junxian/qr-generator`, which already encodes and resolves URL-based payloads. Both tasks exercise the same create-and-retrieve round-trip; url-shortener does not expose any tool capability beyond qr-generator.

---

## 6. `junxian/weather-service`

**Why it almost made the cut:** Full structure. docs/task.md = 89 B (standard). No CJK.

**Why it was dropped (E3):** Weather-service is a read-only API data-lookup task (query → parse → display). Its interaction pattern — authenticate, call a REST endpoint, parse JSON, format output — is structurally identical to `junxian/currency-converter` already in the kept set. Retaining both would provide no additional coverage of tool-calling behaviour.

---

## 7. `xiaochen/code-reviewer`

**Why it almost made the cut:** Full structure (docs/, evaluation/, groundtruth_workspace/). docs/task.md = 85 B (standard). No CJK. Present in the intermediate finalpool as of 2026-03-23.

**Why it was dropped (E3):** Code-reviewer performs static analysis and lint-style feedback on source files. The kept `xiaochen/security-scanner` already covers code-analysis tool interactions (static analysis, vulnerability pattern matching, report generation) as a strict superset of what code-reviewer exercises. This is the canonical E3 example from the boundary review PR.

---

## 8. `wenshuo/image-processor`

**Why it almost made the cut:** Full structure. docs/task.md = 91 B (standard). No CJK.

**Why it was dropped (E3):** Image-processor transforms binary file formats (resize, convert, compress). The kept `wenshuo/document-parser` already exercises a binary-file-read → structured-output pipeline for documents, and `wenshuo/workflow-automation` already chains multi-step file-transformation operations. Image-processor does not add a tool-calling pattern not already present in the combination of those two tasks.

---

## 9. `wenshuo/scheduler`

**Why it almost made the cut:** Full structure. docs/task.md = 77 B (standard). No CJK.

**Why it was dropped (E3):** Scheduler implements time-based task triggering (cron-style). This is a restricted specialisation of `wenshuo/workflow-automation`, which already covers multi-step automated pipelines with conditional branching and state persistence. Scheduler's tool-call footprint is a proper subset of workflow-automation's footprint; keeping both would duplicate coverage without adding novel evaluation signal.
