# 交接文件（HANDOFF）— GLP-1 RA 孕期暴露研究

> 給下一個 Claude session（或任何接手者）的完整脈絡。
> 讀完本文件即可接續工作，不需回頭找舊對話。
> 最後更新：2026-09-09

---

## 0. 給新 session 的開場提示（直接複製貼上）

```
我在做「GLP-1 受體促效劑於孕期暴露」的藥物流行病學研究（台灣全國連結資料）。
請先讀 HANDOFF.md 了解全部脈絡，再讀 feasibility_count_analysis_plan.md、
statistical_analysis_plan.md、letter_commentary_skeleton.md 三份文件。
讀完後告訴我你理解的「目前狀態」與「下一步」，再等我指示。
```

---

## 1. 專案一句話

**評估育齡糖尿病女性孕期周邊（孕前～第一孕期）暴露 GLP-1 RA 與母嬰／新生兒結局之關聯**，
使用台灣全國連結資料（健保申報＋出生通報＋多重死因檔），並以 NAHSIT 做量化偏差分析。

- 合作／指導：蕭斐元老師（資料夾命名可見）
- 核心角度：「育齡女性正集體進入 GLP-1 時代，但周產期安全證據在亞洲幾近空白」

## 2. 兩條路線策略（最重要的設計決策）

```
可行性計數（feasibility_count_analysis_plan.md）
        │
        ├─ 暴露孕次夠、discordant 母親夠 ──► Full article
        │                                    （SAP：statistical_analysis_plan.md）
        │
        └─ 數量不足 / 細格 <3 ──────────────► Commentary / Research Letter
                                             （letter_commentary_skeleton.md）
```

**先做計數、再決定走哪條路。** 計數階段只計數、不估效應、不檢定。

## 3. 三份文件現況

| 檔案 | 內容 | 狀態 |
|---|---|---|
| `feasibility_count_analysis_plan.md` | 可行性計數計畫：資料來源、母嬰連結、**所有操作型定義**（妊娠時間軸、GLP-1 暴露窗、對照組、結局、共變項）、7 張 shell tables、判讀準則、預標偏差 | ✅ 初稿完成 |
| `statistical_analysis_plan.md` | SAP v0.1：estimand（ICH E9(R1)）、主動對照新使用者世代＋同母不同孕三角驗證、PS/IPTW、modified Poisson、8 項敏感度分析（含 NAHSIT QBA）、RECORD-PE 報告 | ✅ 初稿完成（v0.1 草案） |
| `letter_commentary_skeleton.md` | 短文骨架：Hook → Gap → 台灣數據錨點 → 方法學洞見 → 行動呼籲；含標題候選、預留數據位、兩種期刊家族微調、投稿前檢核表 | ✅ 骨架完成，待填數據 |

**文件間關係**：計數計畫是「定義的單一來源」，SAP 與骨架皆以 § 引用它。改定義只改計數計畫。

## 4. 已定案的關鍵設定（不要重新討論）

- **分析單位＝妊娠**（非活產），以因應活產偏差
- **暴露藥品**：ATC A10BJ 系列；tirzepatide 單獨標記、不併入 A10BJ
- **暴露窗優先序**：T1 > 孕前停藥 > 任一孕期；孕前周邊 = LMP 前 90 天
- **LMP 推估**：分娩日 − 出生通報實記妊娠週數
- **主動對照**：胰島素（A10A）、SGLT2i（A10BK）、DPP-4i（A10BH）、metformin（A10BA）
- **主要結局**：主要先天畸形（嬰兒一歲內 Q 碼，EUROCAT/MACDP 排除輕微異常）
- **主分析**：主動對照新使用者世代 + IPTW + modified Poisson（RR、RD）
- **三角驗證**：同母不同孕 conditional logistic
- **未測量混雜**（HbA1c、BMI、孕期增重）：同母設計 + NAHSIT QBA
- **新使用者 washout**：12 個月
- **釋出規範**：HWDC 細格 <3 不得釋出

## 5. 待辦（Open Items）

### 需要研究者提供的資訊
- [ ] 各資料檔實際可得年度 → 定研究期間
- [ ] GLP-1／對照藥之健保藥品代碼對照表（含 tirzepatide 代碼與 ATC 歸類確認）
- [ ] 目標期刊與文類（糖尿病內分泌 vs 產科周產期；Letter / Comment / Research Letter）
- [ ] 若走 Letter to Editor：標靶論文 DOI
- [ ] SAP 的嚴格版結局定義中「≥2 次診斷間隔天數」
- [ ] IRB／資料使用核准字號

### 可由 Claude 接續的工作
- [ ] 文獻整理：近期第一孕期 GLP-1 暴露與先天畸形之世代研究（2–3 篇）、live-birth bias / sibling design / QBA 方法學文獻，回填骨架各段「引用類型」
- [ ] 全球／育齡女性 GLP-1 處方趨勢數據（骨架 §1 預留數據位）
- [ ] NAHSIT 育齡女性肥胖／糖尿病前期／代謝症候群盛行率（骨架 §3）
- [ ] 計數結果出來後：回填骨架 §3、SAP §10 檢力
- [ ] 可考慮加：陰性對照結局清單、詳細 ICD/處置碼附錄、SAS/R 分析腳本骨架

## 6. 技術與環境

### GitHub
- Repo：`https://github.com/elise-github/elise-github`
- 分支：`claude/glp1-pregnancy-research-mpy5r`
- PR：#1（草稿，開啟中）`https://github.com/elise-github/elise-github/pull/1`
- Commit 歷程：
  1. `41236d4` 新增可行性計數分析計畫與操作型定義
  2. `d980355` 新增 letter/commentary 投稿短文骨架
  3. `699aaa3` 新增統計分析計畫（SAP）
  4. 本次：新增 HANDOFF.md

### 本機資料夾（Mac）
```
/Users/ect/Library/CloudStorage/Dropbox-E/Tan Elise/A03 Brainstoming/01_GLP1 and Pregancy
```
（資料夾名稱 `Brainstoming`、`Pregancy` 為實際磁碟名稱，含拼字誤植，指令請照原樣使用）

### 把 repo 拉到本機
```bash
cd "/Users/ect/Library/CloudStorage/Dropbox-E/Tan Elise/A03 Brainstoming/01_GLP1 and Pregancy"
git clone https://github.com/elise-github/elise-github.git .
git checkout claude/glp1-pregnancy-research-mpy5r
```
若資料夾非空，改 clone 到子資料夾 `glp1-repo` 再 checkout。

### 換帳號後的注意事項
- 新帳號的 Claude session **沒有舊對話記憶**，一切以本文件與三份 .md 為準。
- 網頁版／雲端 Claude Code **無法存取本機檔案**；要直接讀寫 Dropbox 資料夾請在 Mac 上跑本機版 Claude Code（在資料夾內執行 `claude`）。
- 新帳號若要接續 GitHub 工作，需確認該帳號對 `elise-github/elise-github` 有寫入權限。
- 建議在新 session 直接從本分支續作，或另開分支 `claude/glp1-pregnancy-research-v2`。

## 7. 舊 session 中的誤植（避免混淆）

舊對話曾提到三份文件名為 `GLP1_pregnancy_research_proposal.md` 等——**那是錯的**。
實際檔名以本文件 §3 的表格為準。
