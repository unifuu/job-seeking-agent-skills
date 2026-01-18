# Job Description Analysis & Interview Strategy Skill

## Description

Analyzes job posting URLs (especially from Japanese job sites like Green, Wantedly, etc.) and creates comprehensive interview strategies. Includes interviewer research capabilities.

## Instructions

1. Accept job posting URL from user
2. Fetch and parse the page content
3. Extract and analyze key sections
4. Cross-reference with `about_me` profile
5. Generate detailed interview strategy covering every JD point
6. Optionally research interviewer background if name is provided
7. Save to `strategies/[CompanyName]_面接戦略.md`

## Trigger Commands

Simply paste the URL or provide interviewer name:

```bash
# Direct URL input triggers analysis
Input: "https://xxxx.com/company/xxxx/job/xxxx"
Input: "この求人を分析: [URL]"
Input: "[URL]"

# After initial analysis, add interviewer research
Input: "Research interviewer: [Name]"
Input: "面接官を調査: [Name]"
Input: "[Name]さんについて調べて"
```

## Analysis Sections

### 1. 配属部署 (Department/Team)

Extract and analyze:

- Department name and structure
- Team size and composition
- Reporting lines
- Collaboration scope

### 2. 概要 (Overview)

Extract and analyze:

- Position summary
- Main responsibilities
- Role expectations
- Impact scope

### 3. この仕事で得られるもの (What You'll Gain)

Extract and analyze:

- Learning opportunities
- Skill development areas
- Career growth potential
- Unique experiences

### 4. 応募資格 (Requirements) ⭐ CRITICAL

Parse EVERY requirement:

- **必須条件 (Required)**: Each point individually
- **歓迎条件 (Preferred)**: Each point individually
- **求める人物像 (Desired Traits)**: Character and mindset
- Create specific strategy for each point

### 5. 選考プロセス (Selection Process)

Extract:

- Number of interview rounds
- Interview format (online/offline)
- Assessment methods
- Timeline expectations

### 6. その他重要情報 (Other Critical Info)

Extract:

- Work style (remote/hybrid/office)
- Tech stack mentioned
- Company culture indicators
- Benefits and perks
- Salary range if mentioned

## Output Format

```markdown
---
company: [Company Name]
position: [Job Title]
job_url: [URL]
source: [Job board name]
date_analyzed: [Date]
interview_stage: 未設定
preparation_status: 分析完了
---

# [Company Name] - [Position] 求人分析・面接対策

## 📊 求人情報分析

### 配属部署

**部署名**: [Department name]
**チーム構成**: [Team structure]
**役割**: [Your role in the team]

**面接でのポイント**:

- [Point about team fit]
- [Question you should ask about the team]

---

### 職務概要

[Detailed overview from JD]

**この職務の本質**:

- [Core responsibility 1]
- [Core responsibility 2]
- [Core responsibility 3]

**面接でアピールすべき点**:

- [How your experience aligns with responsibility 1]
- [How your experience aligns with responsibility 2]

---

### この仕事で得られるもの

[What the job offers for growth]

**キャリア成長の観点**:

- [Growth opportunity 1] → あなたの目標「[Your goal]」と一致
- [Growth opportunity 2] → [How this benefits you]

**面接での活用法**:
志望動機で「[成長機会]に魅力を感じた」と具体的に言及

---

## 🎯 応募資格の完全分析と対策

### 必須条件

#### 必須条件 1: [Requirement text]

**原文**: [Exact text from JD]

**解釈**: [What this really means]

**あなたの該当経験**:

- [Your relevant experience/project]
- 期間: [Duration]
- 成果: [Results achieved]

**面接での回答例**:
```

[Specific answer in Japanese addressing this requirement with STAR method]

状況(Situation): [Context]
課題(Task): [Challenge]
行動(Action): [What you did]
結果(Result): [Outcome with numbers if possible]

```

**補足資料**:
- GitHub: [Link if relevant]
- 実績: [Specific metrics]

**想定質問**:
- "[この必須条件に関連する深掘り質問]"

**回答戦略**: [How to answer effectively]

---

#### 必須条件 2: [Requirement text]
[Same detailed format as above for EACH requirement]

---

#### 必須条件 3: [Requirement text]
[Same detailed format as above for EACH requirement]

---

### 歓迎条件

#### 歓迎条件 1: [Preferred requirement text]
**原文**: [Exact text from JD]

**該当状況**:
- ✅ 該当する / ⚠️ 部分的に該当 / ❌ 未経験

**あなたの経験**:
[If applicable: detailed experience]
[If not: how you plan to address this gap or compensate]

**アピール方法**:
```

[How to present this in interview]

```

**未経験の場合の対策**:
- [How to show willingness to learn]
- [Related experience that transfers]
- [Already started learning (if true)]

---

#### 歓迎条件 2: [Preferred requirement text]
[Same format for EACH preferred requirement]

---

### 求める人物像

#### 人物像 1: [Trait/mindset description]
**求められる資質**: [What they're looking for]

**あなたのマッチング**:
- [Example from your experience showing this trait]
- [Specific situation demonstrating this]

**面接でのアピール方法**:
```

[Story or example to share in interview]

```

---

#### 人物像 2: [Trait/mindset description]
[Same format for EACH trait]

---

## 📋 選考プロセス対策

### プロセス概要
[Selection process from JD]

### 各ステップの対策

#### ステップ1: [Step name]
**内容**: [What happens in this step]

**準備事項**:
- [ ] [Preparation item 1]
- [ ] [Preparation item 2]
- [ ] [Preparation item 3]

**重点対策**:
- [Strategy for this step]

---

#### ステップ2: [Step name]
**内容**: [What happens in this step]

**想定される評価ポイント**:
- [Evaluation criteria 1]
- [Evaluation criteria 2]

**対策**:
- [Strategy for this step]

---

## 💡 その他重要情報の活用

### 働き方
**勤務形態**: [Work style from JD]
**勤務地**: [Location]
**リモート**: [Remote policy]

**面接での確認事項**:
- [Question about work arrangement]
- [Question about flexibility]

---

### 技術スタック
**記載されている技術**:
- [Tech 1]
- [Tech 2]
- [Tech 3]

**あなたの経験との対比**:
| 技術 | 経験レベル | 実務年数 | アピールポイント |
|------|-----------|---------|----------------|
| [Tech 1] | ⭐⭐⭐⭐⭐ | [X]年 | [Key point] |
| [Tech 2] | ⭐⭐⭐⭐☆ | [X]年 | [Key point] |
| [Tech 3] | ⭐⭐⭐☆☆ | [X]年 | [Learning plan] |

**技術的な質問対策**:
- [Likely technical question 1]
  - 回答: [Your answer]
- [Likely technical question 2]
  - 回答: [Your answer]

---

### 企業文化・価値観
**求人から読み取れる文化**:
- [Culture indicator 1]
- [Culture indicator 2]

**カルチャーフィット質問への対策**:
```

Q: "当社の[文化的特徴]についてどう思いますか?"
A: [Your thoughtful answer showing alignment]

```

---

## 🎤 想定質問リスト(JDベース)

### 必須条件に関する深掘り質問

**Q1: [必須条件1に基づく質問]**
```

面接官の意図: [What they want to know]

回答例:
[Detailed answer in Japanese]

アピールポイント:

- [Key point to emphasize]

```

---

**Q2: [必須条件2に基づく質問]**
[Same format]

---

### 歓迎条件に関する質問

**Q1: [歓迎条件1に基づく質問]**
[Same format]

---

### 職務内容に関する質問

**Q1: "[概要から想定される質問]"**
[Same format]

---

### 成長意欲に関する質問

**Q1: "この仕事で何を得たいですか?"**
```

回答戦略: JDの「この仕事で得られるもの」セクションを活用

回答例:
[Answer referencing specific growth opportunities from JD]

````

---

## 🔍 逆質問リスト(JDベース)

### 配属部署について
1. [Question about team structure mentioned in JD]
2. [Question about collaboration mentioned in overview]
3. [Question about day-to-day work]

### 技術・プロジェクトについて
1. [Question about tech stack mentioned]
2. [Question about technical challenges]
3. [Question about development process]

### 成長機会について
1. "[「得られるもの」セクションの内容を深掘りする質問]"
2. [Question about skill development]
3. [Question about career path]

### 選考について
1. "次の選考ステップで重視される点を教えていただけますか?"
2. "[選考プロセスに関する具体的な質問]"

---

## 📚 準備チェックリスト

### 応募資格の証拠準備
- [ ] 必須条件1の証拠: [Specific document/code/project]
- [ ] 必須条件2の証拠: [Specific document/code/project]
- [ ] 必須条件3の証拠: [Specific document/code/project]
- [ ] 歓迎条件の該当部分: [What you have]

### 技術準備
- [ ] [Tech 1]の復習・デモ準備
- [ ] [Tech 2]の実装例準備
- [ ] [Related concept]の説明準備

### ストーリー準備
- [ ] JD必須条件に対応するプロジェクト事例×3
- [ ] チーム開発の事例
- [ ] 困難を乗り越えた事例
- [ ] 技術的な判断をした事例

### 企業研究
- [ ] 会社の最新ニュース
- [ ] プロダクト/サービスの体験
- [ ] 競合との差別化ポイント理解
- [ ] 配属部署の詳細情報

---

## 👤 面接官情報

### 面接官: [未設定]

面接官の名前が分かったら、名前を直接入力して調査:
```bash
Input: "山田太郎"
Input: "Research interviewer: 田中花子"
````

調査内容:

- プロフィール・経歴
- 技術的な専門性
- 過去のインタビュー記事
- SNS投稿から見える価値観
- 想定される質問スタイル

---

## 📝 面接メモ(面接後に記入)

### 実際に聞かれた質問

1.
2.
3.

### JD分析との差異

- [JDから予想した質問との違い]
- [予想外の重視ポイント]

### 回答の振り返り

**良かった点**:

- **改善点**:

-

### 次回への活かし方

- ***

## 🔗 関連リンク

- 求人URL: [Original URL]
- 企業調査: [[../companies/[CompanyName]_企業調査]]
- 会社公式サイト: [URL]
- プロダクト: [URL]

---

**分析日**: [Date]
**最終更新**: [Date]
**次回更新**: 面接後

````

## Interviewer Research Section

When user provides interviewer name, append this section:

```markdown
---

## 👤 面接官詳細調査: [Interviewer Name]

### 基本情報
**名前**: [Full name]
**役職**: [Title/Position]
**所属**: [Department]
**経歴**: [Career background if found]

### オンライン情報
**見つかった情報源**:
- LinkedIn: [Profile summary if found]
- Twitter/X: [Key insights from posts]
- 技術ブログ: [Articles written]
- カンファレンス登壇: [Talks given]
- GitHub: [Notable contributions]
- Qiita/Zenn: [Technical posts]

### 技術的な専門性
**得意分野**:
- [Area 1 based on their content]
- [Area 2 based on their content]

**関心事項**:
- [Interest 1 from their posts/articles]
- [Interest 2 from their posts/articles]

### 価値観・考え方
**ブログ/SNSから読み取れる価値観**:
- [Value 1 with quote if possible]
- [Value 2 with quote if possible]

**重視していそうなポイント**:
- [Point 1]
- [Point 2]

### 過去のインタビュー記事分析
**見つかった記事**:
1. [Article title] - [URL]
   - 要約: [Key points]
   - 引用: "[Notable quote]"

**インタビューから読み取れる採用基準**:
- [Criterion 1]
- [Criterion 2]

### 想定される質問スタイル
**質問の傾向**:
- [Tendency 1 based on their background]
- [Tendency 2 based on their expertise]

**深掘りされそうなテーマ**:
1. [Theme 1] - [Why they'd ask about this]
2. [Theme 2] - [Why they'd ask about this]

### 対策

**アピールすべきポイント**:
- [Point 1 that would resonate with this interviewer]
- [Point 2 that would resonate with this interviewer]

**避けるべき話題**:
- [Topic 1 if any red flags found]

**使える共通点**:
- [Common interest/background if found]
- [Shared technical interest if found]

**準備すべき具体例**:
この面接官の専門性を考慮すると:
1. [Example 1 to prepare]
2. [Example 2 to prepare]

**逆質問案(この面接官向け)**:
1. "[面接官の専門性に基づく質問]"
2. "[面接官の経歴に基づく質問]"
3. "[面接官の記事内容に基づく質問]"

---

### 調査実施日: [Date]
**情報源の信頼性**: [Assessment]
**次回更新**: [When to refresh this info]
````

## Workflow

### Step 1: Initial URL Analysis

```bash
User: "https://xxxx.com/company/xxxx/job/xxxx"

System:
1. Fetches URL content
2. Parses all sections
3. Generates comprehensive strategy
4. Saves to strategies/[CompanyName]_面接戦略.md
```

### Step 2: Interviewer Research (Optional)

```bash
User: "xxxx xxxx"
OR
User: "Research interviewer: xxxx xxxx"

System:
1. Searches for the person online
2. Analyzes their public content
3. Appends interviewer section to existing file
4. Updates strategy based on interviewer profile
```

## Integration Features

### Auto-Reference about_me

- Automatically matches your skills against each JD requirement
- Generates specific examples from your background
- Identifies gaps and suggests how to address them

### Auto-Reference company_research

- If company research file exists, incorporates that data
- Aligns interview strategy with company culture
- Adds context from company background

### Update company_status

- After creating interview prep, suggests updating status
- Links interview rounds to preparation stages

## Advanced Commands

```bash
# Create strategy and research interviewer in one input
Input: "https://[URL] interviewer: xxxx xxxx"

# Update existing strategy with new interviewer
Input: "Add interviewer for [CompanyName]: xxxx xxxx"

# Compare multiple job postings
Input: "Compare: [URL1] vs [URL2]"

# Extract just the requirements
Input: "Requirements only: [URL]"
```

## File Naming Convention

Format: `[CompanyName].md`

Examples:

- `CompanyA.md`
- `CompanyB.md`
- `CompanyC.md`

All files saved to `strategies/` folder.

## Supported Job Boards

Optimized for:

- Green (green-japan.com)
- Wantedly
- Bizreach
- Findy
- Lapras
- Direct company career pages

Can parse any job posting with structured HTML.

## Notes

- Every single JD point gets individual analysis
- Focuses heavily on 応募資格 as it's most critical
- Provides specific, actionable answers
- Interviewer research uses public information only
- All content in Japanese for direct interview use
- Updates based on actual interview feedback

## Privacy & Ethics

- Only uses publicly available information for interviewer research
- Does not scrape private/paywalled content
- Respects robots.txt
- No personal contact information is stored
- Focus on professional public profiles only
