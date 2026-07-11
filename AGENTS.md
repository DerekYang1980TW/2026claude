# Agent 協作指引（schema: v2）

多 agent 協作專案：Claude Code / Codex / Antigravity 輪流接手。
本檔是規則層；操作 SOP 在各 agent 的 startup/shutdown 技能。

## 專案資訊
- 名稱：2026claude／目的：班級工具總專案（教學工具集，工具在 `tools/<工具名>/`）
- Obsidian 筆記：`2026claude/工作筆記.md`；交班 log：`2026claude/工作筆記-log.md`（append-only）

## schema v2
- HANDOFF.md frontmatter：last_agent / updated_at(ISO8601含時區) / handoff_id / handoff_to / schema / dispatch_status
- 筆記 frontmatter：last_agent / updated_at / handoff_id / schema / project
- handoff_id：每次收工生成（`<ts>-<agent>-<4hex>`），三處同寫（HANDOFF、筆記 frontmatter、log 末筆）；開工一致性檢查以此為準
- 鎖定標題（不得改名或自創變體）：`## current_status 上次做到哪`（覆寫,≤10行）、`## next_steps 下一步`（覆寫）、`## project_goal 專案目標`、`## pitfalls 踩坑筆記`（append）、`## decisions 決策紀錄`（append）
- 寫入契約：筆記只允許段落級修改，禁止整檔覆寫；未知段落原樣保留；工具可不同（patch_note / apply_patch / replace_file_content），契約必須相同

## 規矩
- HANDOFF.md ≤20 行；next_steps 必須自足（禁「詳見筆記」）
- log 只 append；寫前重讀 HANDOFF.md 防並發；衝突即停不猜測
- 不主動 git pull/commit/push（明確同意才動）
- .claude/ .codex/ .gemini/ .env credentials 必 gitignore；學生資料一律去識別化（只用座號＋班級代號）
- 派工：僅使用者明說「派工」才啟動（規範見軍師 agent 的 dispatch 技能）；士兵環境變數 AGENT_ROLE=worker，只寫 tasks/<任務>/，不碰本檔/HANDOFF/筆記
