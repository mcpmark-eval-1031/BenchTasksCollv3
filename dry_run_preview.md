# Dry-run preview: boundary-review workflow

Generated at: Wed Jun 17 22:54:43 UTC 2026

## Scope
- Reviewed repository: bugmaker00/BenchTasksCollv3-review
- Source PR: #1 (boundary-review branch)
- Reviewed candidate tasks: 116
- Kept (E0): 77
- Dropped (E1/E2/E3): 39
- Files in finalpool / full_scope.csv: 385
- Pilot tasks selected: 5 (analytics-dashboard, canvas-automation, canvas-grade-automation, certificate-manager, coupon-manager)
- Pilot files: 20

## Planned action per row of full_scope.csv

All 385 rows in `full_scope.csv` correspond to tasks with verdict `KEEP` (rule E0).
The dry-run action for every row is: **retain in canonical finalpool** — no deletion, no modification.

| task | source_branch | source_dev | file_count | verdict | rule | dry-run action |
| --- | --- | --- | --- | --- | --- | --- |
| activity-logger | lueyang-dev | lueyang | 5 | KEEP | E0 | retain in finalpool |
| alert-system | yuzhen-dev | yuzhen | 5 | KEEP | E0 | retain in finalpool |
| analytics-dashboard | lv | lv | 4 | KEEP | E0 | retain in finalpool |
| asset-optimizer | yuxuan-dev | yuxuan | 5 | KEEP | E0 | retain in finalpool |
| backup-utility | xiaochen_dev | xiaochen | 4 | KEEP | E0 | retain in finalpool |
| blog-engine | gyy | gyy | 6 | KEEP | E0 | retain in finalpool |
| booking-system | junteng_dev | junteng | 7 | KEEP | E0 | retain in finalpool |
| cache-optimizer | wenshuo-dev | wenshuo | 4 | KEEP | E0 | retain in finalpool |
| calendar-sync | junteng_dev | junteng | 6 | KEEP | E0 | retain in finalpool |
| canvas-automation | ruige | ruige | 5 | KEEP | E0 | retain in finalpool |
| canvas-grade-automation | jl_dev | jl | 4 | KEEP | E0 | retain in finalpool |
| certificate-manager | zhaochen | zhaochen | 3 | KEEP | E0 | retain in finalpool |
| chat-bot | lv | lv | 6 | KEEP | E0 | retain in finalpool |
| client-portal | lueyang-dev | lueyang | 7 | KEEP | E0 | retain in finalpool |
| cms-builder | gyy | gyy | 7 | KEEP | E0 | retain in finalpool |
| contact-manager | junteng_dev | junteng | 6 | KEEP | E0 | retain in finalpool |
| content-manager | yuxuan-dev | yuxuan | 7 | KEEP | E0 | retain in finalpool |
| content-scheduler | gyy | gyy | 5 | KEEP | E0 | retain in finalpool |
| coupon-manager | fan-dev | fan | 4 | KEEP | E0 | retain in finalpool |
| crm-system | lueyang-dev | lueyang | 7 | KEEP | E0 | retain in finalpool |
| customer-feedback-processor | jl_dev | jl | 5 | KEEP | E0 | retain in finalpool |
| data-analytics | ruige | ruige | 5 | KEEP | E0 | retain in finalpool |
| data-validator | yuzhen-dev | yuzhen | 5 | KEEP | E0 | retain in finalpool |
| deal-manager | lueyang-dev | lueyang | 5 | KEEP | E0 | retain in finalpool |
| deployment-tool | xiaochen_dev | xiaochen | 6 | KEEP | E0 | retain in finalpool |
| discount-calculator | fan-dev | fan | 4 | KEEP | E0 | retain in finalpool |
| email-campaign | lueyang-dev | lueyang | 6 | KEEP | E0 | retain in finalpool |
| email-classification-system | jl_dev | jl | 6 | KEEP | E0 | retain in finalpool |
| error-tracker | xiaochen_dev | xiaochen | 5 | KEEP | E0 | retain in finalpool |
| expense-tracker | ruige | ruige | 5 | KEEP | E0 | retain in finalpool |
| feedback-collector | lv | lv | 5 | KEEP | E0 | retain in finalpool |
| file-manager | ruige | ruige | 4 | KEEP | E0 | retain in finalpool |
| follow-up-reminder | lueyang-dev | lueyang | 5 | KEEP | E0 | retain in finalpool |
| form-builder | yuzhen-dev | yuzhen | 3 | KEEP | E0 | retain in finalpool |
| health-monitor | xiaochen_dev | xiaochen | 6 | KEEP | E0 | retain in finalpool |
| help-desk | junteng_dev | junteng | 6 | KEEP | E0 | retain in finalpool |
| image-processor | wenshuo-dev | wenshuo | 6 | KEEP | E0 | retain in finalpool |
| inventory-management | jl_dev | jl | 4 | KEEP | E0 | retain in finalpool |
| invoice-generator | yuzhen-dev | yuzhen | 4 | KEEP | E0 | retain in finalpool |
| load-balancer | zhaochen | zhaochen | 4 | KEEP | E0 | retain in finalpool |
| log-analyzer | ruige | ruige | 5 | KEEP | E0 | retain in finalpool |
| loyalty-program | fan-dev | fan | 5 | KEEP | E0 | retain in finalpool |
| media-organizer | haoze | haoze | 7 | KEEP | E0 | retain in finalpool |
| monitoring-agent | xiaochen_dev | xiaochen | 5 | KEEP | E0 | retain in finalpool |
| network-analyzer | yuxuan-dev | yuxuan | 3 | KEEP | E0 | retain in finalpool |
| order-processor | junteng_dev | junteng | 4 | KEEP | E0 | retain in finalpool |
| payment-processor | yuzhen-dev | yuzhen | 5 | KEEP | E0 | retain in finalpool |
| pdf-report-generator | jl_dev | jl | 6 | KEEP | E0 | retain in finalpool |
| permission-manager | yuzhen-dev | yuzhen | 5 | KEEP | E0 | retain in finalpool |
| personalization-service | lv | lv | 4 | KEEP | E0 | retain in finalpool |
| price-tracker | fan-dev | fan | 4 | KEEP | E0 | retain in finalpool |
| product-catalog | junteng_dev | junteng | 6 | KEEP | E0 | retain in finalpool |
| qr-generator | junxian_dev | junxian | 6 | KEEP | E0 | retain in finalpool |
| reminder-service | junteng_dev | junteng | 4 | KEEP | E0 | retain in finalpool |
| robots-handler | gyy | gyy | 7 | KEEP | E0 | retain in finalpool |
| sales-pipeline | lueyang-dev | lueyang | 3 | KEEP | E0 | retain in finalpool |
| scheduler | wenshuo-dev | wenshuo | 5 | KEEP | E0 | retain in finalpool |
| search-engine | wenshuo-dev | wenshuo | 7 | KEEP | E0 | retain in finalpool |
| security-scanner | xiaochen_dev | xiaochen | 5 | KEEP | E0 | retain in finalpool |
| sentiment-analyzer | lv | lv | 4 | KEEP | E0 | retain in finalpool |
| shipment-tracker | junteng_dev | junteng | 3 | KEEP | E0 | retain in finalpool |
| social-connector | junxian_dev | junxian | 7 | KEEP | E0 | retain in finalpool |
| social-publisher | gyy | gyy | 5 | KEEP | E0 | retain in finalpool |
| status-checker | xiaochen_dev | xiaochen | 5 | KEEP | E0 | retain in finalpool |
| storage-manager | zhaochen | zhaochen | 3 | KEEP | E0 | retain in finalpool |
| streaming-service | haoze | haoze | 5 | KEEP | E0 | retain in finalpool |
| subtitle-generator | haoze | haoze | 6 | KEEP | E0 | retain in finalpool |
| survey-builder | lv | lv | 4 | KEEP | E0 | retain in finalpool |
| sync-service | yuxuan-dev | yuxuan | 5 | KEEP | E0 | retain in finalpool |
| tag-manager | gyy | gyy | 7 | KEEP | E0 | retain in finalpool |
| task-scheduler | yuxuan-dev | yuxuan | 3 | KEEP | E0 | retain in finalpool |
| template-engine | zhaochen | zhaochen | 3 | KEEP | E0 | retain in finalpool |
| territory-manager | lueyang-dev | lueyang | 5 | KEEP | E0 | retain in finalpool |
| translation-api | junxian_dev | junxian | 5 | KEEP | E0 | retain in finalpool |
| video-trimmer | haoze | haoze | 4 | KEEP | E0 | retain in finalpool |
| voice-processor | lv | lv | 5 | KEEP | E0 | retain in finalpool |
| web-crawler | ruige | ruige | 4 | KEEP | E0 | retain in finalpool |

## Pilot subset (live workflow only)

The live workflow is applied only to the 5 representative tasks in `render_preview.json`:

| task | source_branch | files | live action |
| --- | --- | --- | --- |
| analytics-dashboard | lv | 4 | verify existence + contract conformance (docs/agent_system_prompt.md, docs/task.md, docs/user_system_prompt.md, evaluation/main.py) |
| canvas-automation | ruige | 5 | verify existence + contract conformance (docs/agent_system_prompt.md, docs/task.md, evaluation/main.py, initial_workspace/readme.txt, preprocess/main.py) |
| canvas-grade-automation | jl_dev | 4 | verify existence + contract conformance (docs/agent_system_prompt.md, docs/task.md, evaluation/main.py, groundtruth_workspace/readme.txt) |
| certificate-manager | zhaochen | 3 | verify existence + contract conformance (docs/agent_system_prompt.md, docs/task.md, evaluation/main.py) |
| coupon-manager | fan-dev | 4 | verify existence + contract conformance (docs/agent_system_prompt.md, docs/task.md, evaluation/main.py, groundtruth_workspace/readme.txt) |

## Non-pilot rows

365 files outside the pilot subset are left untouched in the live workflow.
They are recorded in `full_scope.csv` for audit but are not acted upon.

## Dropped tasks (not in finalpool)

39 candidate tasks were dropped during boundary review and therefore have no files in `full_scope.csv`:
- E1 (CJK in docs): 20 tasks
- E2 (missing evaluation/main.py or workspace): 10 tasks
- E3 (editorial near-miss): 9 tasks

See `boundary_review.csv`, `borderline_cases.md`, and `kept_subset.json` for the full evidence.
