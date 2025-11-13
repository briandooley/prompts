📊 Comprehensive Jira Analysis Report Generation Prompt

  Use this prompt to generate a complete Jira analysis report with staleness detection, epic analysis, long-term filtering, story points validation, and weekend work analysis.

  ---
  🎯 Comprehensive Jira Analysis Request

  Please generate a comprehensive Jira analysis report with the following specifications:

  👥 Jira Users to Analyze:

  - <jira user>
  - <jira user>

  🚫 Excluded Jira Projects:

  - WFLY, JDG, JBEAP, EAPDOC, ELY, RHDEVDOCS

  🔴 Staleness Criteria:

  - Definition: Issues not updated by any human (non-bot) user in >10 working days
  - Eligible Statuses: Only flag as stale if status is "In Progress", "Review", "Code Review", "ON_QA", or "ON_DEV"
  - Important: Resolved/closed issues cannot be stale
  - Bot Filtering: Exclude updates from: automation, jira-bot, noreply, system
  - Working Days: Exclude weekends from staleness calculation
  - Long-term Filtering: Issues with "long-term" labels should NOT be counted as stale but reported separately

  📈 Epic Analysis:

  - Epic Detection: Identify issues with issuetype = "Epic"
  - Epic Notation: Add "📈 EPIC with X unresolved issues remaining" note
  - Issue Counting: Count unresolved child issues within each epic using JQL: "Epic Link" = "{epic_key}" AND status not in (Closed, Resolved, Done)
  - Epic Context: Provides management insight into epic completion status

  ⏳ Long-term Issue Handling:

  - Label Detection: Check for labels: 'long-term', 'long term', 'longterm', 'long_term'
  - Filtering Logic: Issues with long-term labels should be excluded from stale count
  - Separate Reporting: Show long-term issues in dedicated "⏳ Long-term Jiras (not counted as stale)" sections
  - Notation: Add "⏳ LONG-TERM" marker to these issues

  📊 Story Points Validation:

  - Valid Values: Only 0, 1, 2, 3, 5, 8, 13 are allowed
  - Categories to Flag:
    - ❌ Missing: Resolved issues without story points
    - 🔴 Too Large: Any value > 13 (should be broken down)
    - 🟡 Non-Fibonacci: Any value not in the valid set
    - 🟠 Invalid Format: Non-numeric or decimal values
  - Date Filter: Only include resolved issues that were resolved on or after July 1st, 2025
  - Analysis Scope: Active statuses and closed/resolved statuses

  🏖️ Weekend Work Detection:

  - Target Days: Flag Saturday and Sunday updates
  - User Filtering: Only count weekend updates made by users in the specified list above
  - Bot Exclusion: Filter out all bot activity from weekend detection
  - Purpose: Identify work-life balance concerns

  📋 Required Report Sections:

  1. 📈 Executive Summary:
    - Total open Jiras count
    - Stale Jiras count and percentage 🔴
    - Weekend updated Jiras count and percentage 🏖️
    - Story Points issues count 📊
  2. 👥 Individual User Analysis: For each user show:
    - Summary Statistics:
        - Open Jiras count
      - Stale Jiras count
      - Long-term Jiras count
      - Weekend Updated Jiras count
      - Story Points Issues count
    - 🔴 Stale Jiras Section: Detailed list with working days and epic notation
    - ⏳ Long-term Jiras Section: Separate list for long-term labeled issues
    - 📊 Story Points Issues: Categorized validation problems
    - ✅ Clean Records: Show "No Stale Jiras" for users with clean records
  3. 🏖️ Weekend Work Analysis: (if any found)
    - Table of weekend-updated Jiras
    - User who made the weekend update
    - Date, time, and day of week
  4. ⚙️ Report Configuration:
    - Complete user list documentation
    - Staleness criteria explanation
    - Epic analysis methodology
    - Long-term filtering rules
    - Bot filtering methodology
    - Story points validation rules
    - Weekend detection criteria

  🔧 Technical Requirements:

  - Authentication: Use Jira REST API with Bearer token authentication
  - Base URL: https://issues.redhat.com
  - Output Format: Markdown with clickable links and visual indicators
  - Visual Indicators: 🔴🟡🟠❌✅🏖️📊📈⏳
  - File Name: Enhanced_User_Activity_Report_Since_July_1st_YYYY-MM-DD.md
  - Performance: Handle large datasets with proper rate limiting

  📝 Environment Setup:

  JIRA_API_TOKEN="your_token_here" python3 jira_analysis_report.py

  🎯 Success Criteria:

  - Accurate Staleness: Only truly stale issues (excluding long-term labeled ones)
  - Epic Context: Clear epic status with child issue counts
  - Management Insights: Actionable data for prioritization decisions
  - Story Points Quality: Help improve estimation practices
  - Work-Life Balance: Highlight weekend work concerns
  - Clean Separation: Long-term vs. stale vs. story point issues clearly distinguished

  📊 Expected Output:

  - Professional markdown report with comprehensive analysis
  - Clear visual indicators and categorization
  - Clickable Jira links for easy navigation
  - Executive summary for management overview
  - Detailed user breakdowns for team leads
  - Full file path display upon completion

  ---
  Note: This prompt assumes you have the enhanced jira_analysis_report.py script with epic detection, long-term filtering, and story points validation features. The script should handle all
  specified criteria automatically and generate a comprehensive, actionable report.