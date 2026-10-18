# 核心資料與 Knowledge

只保留 **4份knowledge、7份結果資料**，以及本說明。皆來自正式全量結果，沒有重新推論或變更資料內容。

| 階段 | 檔案 | 內容 |
| --- | --- | --- |
| R1 | [r1_knowledge.json](r1_knowledge.json) | v2.2契約及原屬性定義參考 |
| R1 | [r1_structured_reports.json](r1_structured_reports.json) | R1原始structured reports，保留中英文原文及split；已排除指定五例 |
| R2 | [r2_knowledge.json](r2_knowledge.json) | 四欄知識、anatomy v3.2、實際effective knowledge及prompt/schema |
| R2 | [r2_image_cards.jsonl](r2_image_cards.jsonl) | 每張影像的四欄預測及confidence/reason |
| R3 | [r3_knowledge.json](r3_knowledge.json) | 依序包含Round1、Round2、Round3、位置拆分及Round4所需規則／prompt |
| R3 | [r3_image_structured_reports.jsonl](r3_image_structured_reports.jsonl) | Round4後最終image-level reports |
| R3 | [r3_case_structured_reports.jsonl](r3_case_structured_reports.jsonl) | Round4後最終case-level reports，Instance仍按影像分開 |
| R4 | [r4_knowledge.json](r4_knowledge.json) | 屬性轉tag規則、taxonomy及group契約 |
| R4 | [r4_tag_dictionary.json](r4_tag_dictionary.json) | group、single/multiple選取方式及tag定義 |
| R4 | [r4_group_benchmark.jsonl.gz](r4_group_benchmark.jsonl.gz) | 逐屬性／group的tags、status及有效性／完整來源遮罩 |
| R4 | [r4_tag_annotations.jsonl.gz](r4_tag_annotations.jsonl.gz) | assigned tags展平清單 |

資料為 **2,452 cases／4,904張**。UID **191780** 缺少Instance配對，仍是partial／null，不是無Instance；完整訓練時需排除該例兩張。Case report必須共同輸入兩張影像。

R4定義99個groups，目前69個有完整assigned樣本。預設使用label_set_valid=true且complete_source_for_training=true的group作target，未描述／unknown不當negative。壓縮檔以gzip逐行解析。

Knowledge保留實際JSON值及prompt／程式規則原文，不另外制定新規則。R1定義含歷史參考；R3保留的claim不代表已逐項視覺驗證。

中間payload、claim audit、訓練重複匯出、人工評估、進度及manifest均不放本目錄。原始各階段結果未搬移或改動；前次完整彙整保存在[備份](../archive/main_results_full_20261018/main_results/README.md)。

彙整／驗證入口：scripts/collect_main_results.py（--resume／--verify-only）。
SHA及驗證紀錄在目錄外：scripts/main_results_collection_audit.json。
