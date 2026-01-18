# Job Seeking Skills (Claude Code)

[日本語](README.ja.md)

This repository is designed to streamline and automate the company research process for job hunters using **Claude Code** skills. It generates structured markdown reports that are fully compatible with Obsidian.

## 🚀 Features

- **Automated Research**: Deep dive into company info, tech stack, and hiring requirements.
- **Status Tracking**: Manage application status and history.
- **Smart Ranking**: Score and rank companies based on your preferences.
- **JD Analysis**: Analyze job posting URLs and generate comprehensive interview strategies.
- **Reporting**: Visualize progress with comprehensive status reports.
- **Obsidian Ready**: Outputs formatted reports directly into your vault structure.

## 🛠 Available Skills

| Skill                 | Description                                              | Trigger                                       |
| --------------------- | -------------------------------------------------------- | --------------------------------------------- |
| **Company Research**  | Gathers company data and employee interviews             | `Research [Company]`, `[Company]について調査` |
| **Status Management** | Updates application status (Applied, Interview, etc.)    | `[Company] passed`, `[Company] 一次面接予定`  |
| **JD Analysis**       | Analyzes job posting URLs and creates interview strategy | Paste job posting URL directly                |
| **Progress Report**   | Generates status overview, metrics, and ranking          | `Generate report`, `レポート作成`             |

## 📁 Structure

- `companies/`: Company research reports (`[Company].md`)
- `strategies/`: Job description analysis and interview strategies
- `reports/`: Status and progress reports
- `about_me/`: Your profile and preferences
- `.claude/skills/`: Custom skill definitions

## 💡 Usage Examples

### 1. Research a Company

```bash
Research [CompanyName]
```

_Generates `companies/[CompanyName].md`_

### 2. Update Status

```bash
[CompanyName] passed to first interview
```

_Updates status in company file_

### 3. Analyze Job Posting

```bash
https://www.green-japan.com/company/xxxx/job/xxxxx
```

_Generates `strategies/[CompanyName].md` with comprehensive interview strategy_

### 4. Check Progress

```bash
Generate status report
```

_Creates a summary report of all your applications_
