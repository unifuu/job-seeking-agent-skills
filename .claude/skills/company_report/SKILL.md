# Company Report Skill

## Trigger

report, status, overview, summary, レポート, 状況, 概要, サマリー, 進捗, rank, ranking, compare, comparison, ランキング, 比較, 順位, 評価

## Description

Generates a comprehensive status report of all companies in the job search pipeline. Provides an overview of application statuses, timelines, key metrics, and a ranking of active companies (excluding failed/withdrawn applications).

## Instructions

1. Scan all markdown files in the "companies" folder
2. Extract key information from each company file:
   - Company name
   - `status` from frontmatter
   - `match_score` from frontmatter
   - `date` from frontmatter (research date)
   - Technology stack details from `## 💻 技術スタック`
   - Foreign support details from `## 🌍 海外展開と外国人雇用`
   - SES classification from `## ⚠️ SES 判定`
   - Company stability info from `## 📋 基本情報`
   - Key notes from `## 📝 メモ` section
3. Organize companies by status
4. Calculate statistics and metrics
5. **Generate ranking** for companies NOT in failed/withdrawn status (exclude statuses containing "落ち" or "辞退")
6. Output results in markdown format for Obsidian

## Report Sections

### 1. Executive Summary

- Total companies researched
- Status breakdown (count and percentage)
- Average match score
- Recent activity summary

### 2. Companies by Status

- **検討中 (Under Consideration)**: Companies being evaluated
- **応募予定 (Planning to Apply)**: Ready to apply
- **応募済み (Applied)**: Applications submitted
- **面接予定 (Interview Scheduled)**: Active interview process
- **辞退 (Declined/Rejected)**: Not pursuing

### 3. Company Ranking (Active Companies Only)

- Rank companies based on weighted criteria
- Exclude companies with status containing "落ち" or "辞退"
- Show top companies with detailed scoring breakdown

### 4. Timeline View

- Companies researched this week
- Companies researched this month
- Upcoming deadlines or actions

### 5. Match Score Analysis

- High priority (★★★★★, ★★★★☆)
- Medium priority (★★★☆☆)
- Low priority (★★☆☆☆, ★☆☆☆☆)

### 6. Action Items

- Companies ready to apply
- Follow-ups needed
- Research gaps to fill

### 7. Key Metrics

- Application conversion rate
- Average time in each status
- Tech stack distribution
- SES vs non-SES ratio
- Foreign-friendly companies count

## Ranking Criteria

### Primary Criteria (High Weight)

1. **適合性スコア (Compatibility / Match Score)** - Weight: 40%

   - Based directly on the `match_score` (1-5 stars) in the file frontmatter.
   - Represents the overall alignment with the user's profile and goals.

2. **技術スタックの質 (Tech Stack Quality)** - Weight: 20%
   - Modernity of technologies used (Go, Cloud-native, etc.)
   - Consistency with modern development practices
   - Derived from `## 💻 技術スタック` section

### Secondary Criteria (Medium Weight)

3. **外国人受入れ体制 (Foreign Employee Support)** - Weight: 15%

   - Visa sponsorship availability
   - Active hiring of foreign engineers
   - English/Global environment
   - Derived from `## 🌍 海外展開と外国人雇用` section

4. **非 SES 度 (Non-SES Score)** - Weight: 15%
   - Ratio of in-house development vs SES
   - Product ownership
   - Derived from `## ⚠️ SES 判定` section

### Tertiary Criteria (Lower Weight)

5. **企業安定性 (Company Stability)** - Weight: 10%
   - Capital size, employee count, history
   - Derived from `## 📋 基本情報` section

## Scoring System

### Compatibility Score

- **5 Points**: `match_score: 5`
- **4 Points**: `match_score: 4`
- **3 Points**: `match_score: 3`
- **2 Points**: `match_score: 2`
- **1 Point**: `match_score: 1`

### Tech Stack Quality Scoring

- **5 Points**: Modern stack (e.g., Go/Rust, AWS/GCP, K8s), microservices, clear tech culture
- **4 Points**: Standard modern stack, some legacy but moving forward
- **3 Points**: Average stack, mix of modern and legacy
- **2 Points**: Legacy heavy, slow adoption of new tech
- **1 Point**: Outdated technologies only

## Output Format

```markdown
---
generated: [Date and Time]
total_companies: [Number]
report_type: status_overview_with_ranking
---

# 就職活動状況レポート

> 📅 生成日時: [YYYY-MM-DD HH:MM]

## 📊 サマリー

- **調査企業数**: [X]社
- **応募済み**: [X]社
- **面接予定**: [X]社
- **平均マッチ度**: ★★★☆☆
- **今週の活動**: [X]社を調査

---

## 🎯 ステータス別企業一覧

### 🔥 面接予定 ([X]社)

| 企業名    | マッチ度 | 調査日     | メモ       |
| --------- | -------- | ---------- | ---------- |
| [Company] | ★★★★★    | 2026-01-15 | [Key note] |

### ✅ 応募済み ([X]社)

| 企業名    | マッチ度 | 応募日     | ステータス |
| --------- | -------- | ---------- | ---------- |
| [Company] | ★★★★☆    | 2026-01-10 | 書類選考中 |

### 📝 応募予定 ([X]社)

| 企業名    | マッチ度 | 優先度 | 次のアクション |
| --------- | -------- | ------ | -------------- |
| [Company] | ★★★★★    | 高     | 履歴書準備     |

### 🔍 検討中 ([X]社)

| 企業名    | マッチ度 | 調査日     | 主な特徴    |
| --------- | -------- | ---------- | ----------- |
| [Company] | ★★★☆☆    | 2026-01-12 | Go 言語使用 |

### ❌ 辞退・不合格 ([X]社)

| 企業名    | ステータス | 理由           |
| --------- | ---------- | -------------- |
| [Company] | 辞退       | SES 企業のため |
| [Company] | 書類落ち   | -              |

---

## 🏆 企業ランキング (アクティブ企業のみ)

> **評価基準**: 適合性(40%) + 技術スタック(20%) + 外国人受入れ(15%) + 非 SES(15%) + 安定性(10%)
>
> **対象**: 検討中・応募予定・応募済み・面接予定のステータスの企業 ([X]社)

### 1 位: [Company Name] - 総合スコア: [Score]/100

**🌟 総合評価**: ★★★★★
**現在のステータス**: [Status]

#### スコア内訳

- 適合性: [X]/40 点 - [Based on match_score]
- 技術スタック: [X]/20 点 - [Evaluation]
- 外国人受入れ: [X]/15 点 - [Evaluation]
- 非 SES 度: [X]/15 点 - [Evaluation]
- 企業安定性: [X]/10 点 - [Evaluation]

#### 強み

- [Strength 1]
- [Strength 2]

#### 懸念点

- [Concern 1]

#### 推奨アクション

- [Action]

---

### 2 位: [Company Name] - 総合スコア: [Score]/100

[Same format as above]

---

### 3 位: [Company Name] - 総合スコア: [Score]/100

[Same format as above]

---

## 📈 カテゴリ別トップ 3

### 技術スタックランキング

1. [Company] - [Score]点 - [コメント]
2. [Company] - [Score]点 - [コメント]
3. [Company] - [Score]点 - [コメント]

### 外国人フレンドリーランキング

1. [Company] - [Score]点 - [コメント]
2. [Company] - [Score]点 - [コメント]
3. [Company] - [Score]点 - [コメント]

---

## 📅 タイムライン

### 今週の活動 (Week of [Date])

- **新規調査**: [X]社
- **応募**: [X]社
- **面接**: [X]件

### 今月の活動 (Month of [Month])

- **新規調査**: [X]社
- **応募**: [X]社
- **面接**: [X]件

---

## ⭐ マッチ度別分析

### 高マッチ度 (★★★★★, ★★★★☆) - [X]社

1. [Company Name] - ★★★★★ - [Status]
2. [Company Name] - ★★★★☆ - [Status]

### 中マッチ度 (★★★☆☆) - [X]社

1. [Company Name] - ★★★☆☆ - [Status]

### 低マッチ度 (★★☆☆☆, ★☆☆☆☆) - [X]社

1. [Company Name] - ★★☆☆☆ - [Status]

---

## 🚀 次のアクション

### 今週中に実施

- [ ] [Company A] に応募書類提出
- [ ] [Company B] の面接準備
- [ ] [Company C] の追加調査

### 今月中に実施

- [ ] [Company D] に応募
- [ ] [Company E] の企業研究

---

## 📈 統計データ

### ステータス分布
```

検討中: ████████░░ 40% ([X]社)
応募予定: ███░░░░░░░ 30% ([X]社)
応募済み: ██░░░░░░░░ 20% ([X]社)
面接予定: █░░░░░░░░░ 10% ([X]社)
辞退・不合格: ░░░░░░░░░░ 0% ([X]社)

```

### 技術スタック

- **Go言語採用**: [X]社 ([X]%)
- **クラウドネイティブ**: [X]社 ([X]%)
- **モダンスタック**: [X]社 ([X]%)

### 企業タイプ

- **自社開発**: [X]社 ([X]%)
- **SES企業**: [X]社 ([X]%)
- **外国人採用積極**: [X]社 ([X]%)

### コンバージョン率

- **調査→応募予定**: [X]%
- **応募予定→応募済み**: [X]%
- **応募済み→面接**: [X]%

---

## 💡 インサイト

### 強み

- [Observation about your strengths based on high-match companies]

### 改善点

- [Suggestions based on patterns in low-match or declined companies]

### 推奨戦略

- [Strategic recommendations based on current pipeline]

---

## 📝 メモ

[Any additional notes or observations]

---

## 🔄 更新履歴

- [Date]: レポート生成
```

## Usage

```bash
# Generate status report with ranking
Input: "Generate a status report"
Input: "Show me the report"
Input: "Report plz"
Input: "Rank all companies"
Input: "ランキングして"

# In Japanese
Input: "レポート作成して"
Input: "状況報告"
Input: "進捗レポート"

# Output
Output: Markdown file saved as `reports/YYYYMMDD.md`
```

## Notes

- Report is generated from current state of all company files
- Status field in frontmatter must be one of: 検討中/応募予定/応募済み/面接予定/辞退/書類落ち/一次面接落ち/etc.
- If status is missing, company will be categorized as "検討中" by default
- **Ranking excludes** companies with status containing "落ち" or "辞退"
- Report file is saved in `reports/` directory with format `YYYYMMDD.md`
- **If report for today already exists, it will be overwritten** with the new report
- Previous day reports are kept for historical tracking
