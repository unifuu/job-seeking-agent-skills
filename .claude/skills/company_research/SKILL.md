# Company Research Skill

## Trigger

research, 調査, 会社, 企業, 会社情報, 企業分析, 企業調査, company, company analysis, company research, 株式会社, 合同会社, 有限会社, 株式会社.\*, ㈱

## Description

Search and analyze company information for job hunting purposes, including employee interviews. Output results in Japanese markdown format compatible with Obsidian.

**IMPORTANT:** If the user provides ONLY a company name (e.g., "株式会社XXX", "CompanyA", "CompanyB") without any other commands or context, this skill MUST be triggered to research that company.

## Instructions

When given a company name, research and provide the following information in Japanese:

1. **基本情報 (Basic Information)**
   - 設立年 (Year established)
   - 本社所在地 (Headquarters location)
   - 事業領域 (Business domain)
   - 主要事業内容 (Core business operations)
   - 従業員数 (Number of employees)
   - 資本金 (Capital)

2. **技術スタック (Technology Stack)**
   - 使用している主要技術 (Main technologies used)
   - バックエンド技術 (Backend technologies)
   - フロントエンド技術 (Frontend technologies if applicable)
   - モバイルアプリ開発の有無 (Mobile app development presence)
   - インフラ・クラウド環境 (Infrastructure and cloud environment)

3. **採用要件 (Hiring Requirements)**
   - 求められるスキルレベル (Required skill level)
   - 学歴要件 (Educational requirements)
   - 経験年数 (Years of experience required)
   - 語学要件 (Language requirements)

4. **海外展開と外国人雇用 (Global Expansion and Foreign Employee Acceptance)**
   - 海外拠点の有無 (Presence of overseas offices)
   - グローバル事業の規模 (Scale of global business)
   - 外国人社員の割合 (Percentage of foreign employees)
   - 社内公用語 (Company language policy)

5. **SES 判定 (SES Classification)**
   - SES 企業か否か (Whether company is SES-type)
   - 自社開発と客先常駐の比率 (Ratio of in-house vs client site work)
   - 案件形態 (Project types: 請負/委任/派遣)
   - キャリアパス (Career path opportunities)

6. **適合性評価 (Compatibility Assessment)**
   - Evaluate based on provided user profile (if available) or general job-seeking context:
     - マッチ度 (Match score: ★☆☆☆☆ to ★★★★★)
     - 強み (Strengths/advantages)
     - 懸念点 (Concerns/potential issues)
     - 推奨アクション (Recommended actions)

7. **社員インタビュー (Employee Interviews)**
   - Search for employee interviews using multiple strategies
   - Find at least 3 interviews if available
   - Extract key information: employee role, highlights, quotes
   - Analyze common themes across interviews

## Interview Search Strategies

### Primary Sources

- Company career/recruitment website (採用サイト)
- Company official blog
- Wantedly company page
- Green company page
- LinkedIn company page

### Secondary Sources

- Tech blog posts
- Conference presentations
- Podcast interviews
- YouTube videos
- News articles featuring employees

### Search Queries

- "[Company Name] 社員インタビュー"
- "[Company Name] 社員の声"
- "[Company Name] 先輩社員インタビュー"
- "[Company Name] employee interview"
- "[Company Name] 採用サイト インタビュー"

### Quality Guidelines

- Prefer at least 3 distinct interviews
- Each interview should have substantial content
- Prefer recent interviews (within last 2-3 years)
- Include source URLs for verification
- Extract direct quotes when possible
- Note any specific technologies, tools, or practices mentioned

## Output Format

Create a markdown file with the following structure:

```markdown
---
company: [Company Name]
date: [Current Date]
status: [検討中/応募予定/応募済み/面接予定/辞退]
match_score: [1-5 stars]
---

# [Company Name] - 企業調査レポート

## 📋 基本情報

[Basic information details]

## 💻 技術スタック

[Technology stack details]

## 🎯 採用要件

[Hiring requirements details]

## 🌍 海外展開と外国人雇用

[Global expansion details]

## ⚠️ SES 判定

[SES classification details]

## ✅ 適合性評価

**マッチ度**: ★★★☆☆

**強み**:

- [Advantage 1]
- [Advantage 2]

**懸念点**:

- [Concern 1]
- [Concern 2]

**推奨アクション**:

- [Action 1]
- [Action 2]

## 👥 社員インタビュー

> 📊 収集数: [X]件

### インタビュー 1: [Employee Name] - [Position/Role]

**基本情報**:

- **氏名**: [Name or 匿名]
- **所属**: [Department/Team]
- **役職**: [Position]
- **入社年**: [Year] ([X]年目)
- **出典**: [Source URL]

**主なポイント**:

- **入社のきっかけ**: [Why they joined]
- **仕事内容**: [Current responsibilities]
- **やりがい**: [What they find rewarding]
- **技術環境**: [Technologies and tools]
- **会社文化**: [Company culture and atmosphere]
- **成長機会**: [Career growth opportunities]

**重要な引用**:

> "[Key quote from the interview]"

---

### インタビュー 2: [Employee Name] - [Position/Role]

[Same structure as above]

---

### インタビュー 3: [Employee Name] - [Position/Role]

[Same structure as above]

---

### 🔍 共通テーマ分析

**技術面**:

- [Common technical themes]
- [Technologies frequently mentioned]

**文化面**:

- [Cultural aspects]
- [Work style and environment]

**キャリア面**:

- [Career growth opportunities]
- [Learning and development]

**インサイト**:

- この会社に向いている人: [Type of person who would fit]
- 注目ポイント: [Key highlights]
- 懸念点: [Any concerns mentioned]

---

## 🔗 参考リンク

- 公式サイト: [URL]
- 採用ページ: [URL]
- その他: [URLs]

## 📝 メモ

[Additional notes]
```

## Usage Example

Input: `株式会社[会社名]`
Input: `[会社名]株式会社`
Output: Markdown file saved as `companies/[Input].md`

## Notes

- Use web search to gather current information
- All content should be written in Japanese
- If the `companies` directory does not exist, create it first
- Reference any user information found in the workspace for compatibility assessment
- Save output in format suitable for Obsidian vault under the `companies/` directory
- If fewer than 3 interviews found, include what's available and note the limitation
- If company has no public interviews, note this in the 社員インタビュー section
- Cross-reference interview content with other company research data
- Flag any contradictions between interviews and official company information
