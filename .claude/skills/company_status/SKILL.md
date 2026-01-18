# Company Status Management Skill

## Description

Updates the application status for companies in your job hunt tracker. Modifies the YAML frontmatter in company research files with standardized status values.

## Instructions

1. Parse user input to identify company name and desired status
2. Locate the corresponding company file in the companies folder
3. Update the `status` field in YAML frontmatter
4. Add timestamp and status history
5. Confirm the update with Japanese output

## Standardized Status Values

### 検討段階 (Consideration Phase)

- `検討中` - Under consideration, researching
- `興味あり` - Interested, need more research
- `保留` - On hold, waiting for better timing

### 応募段階 (Application Phase)

- `応募予定` - Planning to apply
- `応募準備中` - Preparing application materials
- `応募済み` - Application submitted
- `書類選考中` - Document screening in progress

### 選考段階 (Selection Phase)

- `一次面接予定` - First interview scheduled
- `一次面接完了` - First interview completed
- `二次面接予定` - Second interview scheduled
- `二次面接完了` - Second interview completed
- `最終面接予定` - Final interview scheduled
- `最終面接完了` - Final interview completed
- `選考待ち` - Waiting for selection result

### 成功 (Success)

- `内定` - Job offer received
- `内定承諾` - Offer accepted
- `入社予定` - Joining scheduled

### 不成功 (Unsuccessful)

- `書類落ち` - Failed at document screening
- `一次面接落ち` - Failed at first interview
- `二次面接落ち` - Failed at second interview
- `最終面接落ち` - Failed at final interview
- `辞退` - Withdrew application
- `見送り` - Decided not to pursue

## Command Patterns

### Status Update Commands

```bash
# English commands
"[Company Name] failed"           → 書類落ち (default fail)
"[Company Name] passed"           → 書類選考中 → 一次面接予定
"[Company Name] first interview"  → 一次面接予定
"[Company Name] offer"            → 内定
"[Company Name] rejected"         → 書類落ち
"[Company Name] withdrew"         → 辞退

# Japanese commands
"[Company Name] 書類落ち"
"[Company Name] 応募済み"
"[Company Name] 一次面接予定"
"[Company Name] 内定"

# Status-specific keywords
"failed" / "落ち" / "不合格"      → Determine phase and set appropriate fail status
"passed" / "合格" / "通過"        → Advance to next phase
"interview" / "面接"              → Set interview status
"offer" / "内定"                  → 内定
"withdrew" / "辞退"               → 辞退
"apply" / "応募"                  → 応募済み
```

### Automatic Phase Detection

When user says "failed" without specifying phase:

1. Check current status in file
2. Apply appropriate fail status:
   - If `応募済み` or `書類選考中` → `書類落ち`
   - If `一次面接予定` or `一次面接完了` → `一次面接落ち`
   - If `二次面接予定` or `二次面接完了` → `二次面接落ち`
   - If `最終面接予定` or `最終面接完了` → `最終面接落ち`

## File Update Format

### YAML Frontmatter Structure

```yaml
---
company: [Company Name]
date: 2026-01-15
status: 一次面接予定
match_score: 4
last_updated: 2026-01-17
status_history:
  - date: 2026-01-10
    status: 検討中
    note: Initial research
  - date: 2026-01-12
    status: 応募予定
    note: Prepared resume
  - date: 2026-01-15
    status: 応募済み
    note: Applied via company website
  - date: 2026-01-17
    status: 一次面接予定
    note: Interview scheduled for 2026-01-22
---
```

### Update Actions

1. **Update `status` field** to new status value
2. **Update `last_updated`** to current date
3. **Append to `status_history`** with:
   - Current date
   - New status
   - Optional note (auto-generated or user-provided)

## Output Format

### Success Response (Japanese)

```markdown
✅ **ステータス更新完了**

**企業名**: [Company Name]
**前回のステータス**: 応募済み
**新しいステータス**: 一次面接予定
**更新日時**: 2026-01-17

📝 **メモ**: 一次面接が 2026-01-22 に予定されました

---

**現在の選考状況**:

- 検討中: 5 社
- 応募済み: 3 社
- 面接予定: 2 社
- 内定: 0 社
- 不合格: 1 社
```

### Error Response

```markdown
❌ **エラー**

企業ファイルが見つかりませんでした: [Company Name]

**確認事項**:

- 企業名のスペルを確認してください
- companies フォルダにファイルが存在するか確認してください
- ファイル名: [予想されるファイル名]
```

## Advanced Features

### Batch Updates

```bash
# Update multiple companies
Update status: CompanyA failed, CompanyB passed, CompanyC first interview
```

### Add Notes

```bash
# Add custom note to status update
[CompanyName] 一次面接予定 note: 2026-01-22 10:00 オンライン面接
```

### Status Query

```bash
# Check current status
What's the status of [CompanyName]?

# List all by status
Show all companies with status 応募済み
```

### Rollback

```bash
# Undo last status change
Rollback status for [CompanyName]
```

## Status Flow Chart

```
検討中 → 興味あり → 応募予定 → 応募準備中 → 応募済み
                                              ↓
                                         書類選考中
                                         ↙        ↘
                                   書類落ち      一次面接予定
                                                    ↓
                                                一次面接完了
                                                ↙        ↘
                                      一次面接落ち      二次面接予定
                                                           ↓
                                                       二次面接完了
                                                       ↙        ↘
                                             二次面接落ち      最終面接予定
                                                                  ↓
                                                              最終面接完了
                                                              ↙        ↘
                                                    最終面接落ち      内定
                                                                        ↓
                                                                    内定承諾
                                                                        ↓
                                                                    入社予定

                        (Any stage) → 辞退 (voluntary withdrawal)
                        (Any stage) → 保留 (on hold)
```

## Usage Examples

### Example 1: Document Screening Failed

```bash
Input: "[CompanyName] failed"
Current status: 応募済み
Action: Update to 書類落ち
Output: "[CompanyName]の書類選考が不合格になりました。他の機会を探しましょう。"
```

### Example 2: Passed to Interview

```bash
Input: "[CompanyName] passed"
Current status: 応募済み
Action: Update to 一次面接予定
Output: "[CompanyName]の書類選考を通過しました!一次面接の準備を始めましょう。"
```

### Example 3: Received Offer

```bash
Input: "[CompanyName] offer"
Current status: 最終面接完了
Action: Update to 内定
Output: "おめでとうございます![CompanyName]から内定を獲得しました!🎉"
```

### Example 4: Withdrew Application

```bash
Input: "[CompanyName] withdrew"
Current status: 二次面接予定
Action: Update to 辞退
Output: "[CompanyName]への応募を辞退しました。"
```

## Statistics Tracking

After each update, display summary:

```markdown
📊 **全体の選考状況**

**アクティブ**:

- 検討中: 3 社
- 応募準備中: 2 社
- 応募済み: 4 社
- 面接段階: 5 社
  - 一次面接: 2 社
  - 二次面接: 2 社
  - 最終面接: 1 社

**結果**:

- 内定: 1 社 🎉
- 不合格: 3 社
  - 書類落ち: 1 社
  - 一次面接落ち: 1 社
  - 二次面接落ち: 1 社
- 辞退: 2 社

**成功率**:

- 書類通過率: 75% (3/4)
- 面接通過率: 60% (3/5)
- 全体成功率: 20% (1/5)
```

## Integration

Works seamlessly with:

- `company_research` - Creates initial files with default status
- `company_ranking` - Rankings consider current application status
- Obsidian Dataview - Query and visualize status across all companies

## Notes

- Status values are standardized for consistency
- History is preserved for tracking progress
- Japanese status names are used throughout
- Automatic phase detection reduces manual input
- Statistics help track job search performance
