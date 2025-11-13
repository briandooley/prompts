  📊 Comprehensive Stale Pull Requests Analysis Prompt

  Generate a detailed stale pull requests report for the following GitHub users with hold label detection, bot filtering, and weekend work
  analysis:

  👥 GitHub Users List:

  - <github username>
  - <github username>

  🚧 Hold Label Detection:

  - Identify: PRs with "do-not-merge/hold" label
  - Mark: Display these PRs with 🚧 ON HOLD indicator
  - Track: Include statistics for stale PRs that are intentionally on hold
  - Purpose: Distinguish between genuinely stale PRs vs. intentionally paused ones
  - Reporting: Show count and percentage of hold PRs in executive summary

  ⏰ Staleness Criteria:

  - Threshold: PRs not updated by humans in >10 working days
  - Bot Users to Ignore: openshift-ci, ocpdocs-previewbot, openshift-merge-robot
  - Working Days Calculation: Exclude weekends (Saturday/Sunday) from staleness count
  - Human Activity Only: Count only comments, commits, and events by non-bot users
  - Timeline Analysis: Check PR events and comments for last human interaction

  🏖️ Weekend Work Detection:

  - Include ONLY: Weekend updates made by users in the GitHub users list above
  - Exclude: Weekend updates made by bots or other users not in the specified list
  - Weekend Days: Saturday and Sunday (detect using date analysis)
  - Verification: Check actual events and comments to identify who made weekend updates
  - Accuracy: Do not flag weekend updates made by bots as human weekend work

  📋 Required Report Sections:

  📈 Executive Summary:

  - Total open PRs analyzed across all users
  - Number and percentage of stale PRs (🔴)
  - Number and percentage of stale PRs on hold (🚧)
  - Number and percentage of weekend updated PRs (🏖️)
  - Key performance indicators and alerts

  🏖️ Weekend Work Analysis Section (if any found):

  - Table showing weekend-updated PRs with:
    - PR title and link
    - Repository name
    - User who made the weekend update (from our specified list only)
    - Update date and time
    - Day of week
    - Weekend work icon (🏖️)

  👥 Individual User Analysis:

  - User-grouped sections with full names in format: "Full Name (username)"
  - Summary statistics for each user:
    - Total open PRs
    - Number of stale PRs
    - Number of weekend updated PRs
  - Detailed stale PRs list with:
    - PR title and clickable link
    - Number of working days stale
    - Repository name
    - 🚧 ON HOLD indicator for PRs with "do-not-merge/hold" label
    - Sorted by staleness (most stale first)
  - Show "✅ No Stale PRs" for users with clean records

  ⚙️ Report Configuration Section:

  - Complete list of included users with full names
  - Staleness criteria and threshold explanation
  - Bot filtering methodology and excluded bot users
  - Hold label detection explanation
  - Weekend detection criteria and user filtering rules
  - Working days calculation method

  📁 Output Requirements:

  File Format:

  - File Name: Enhanced_User_Activity_Report_Since_July_1st_{current_date}.md
  - Format: Professional markdown with tables, links, and visual indicators
  - Full Path Display: Show complete file system path to generated report
  - Console Summary: Display key statistics after generation

  Visual Indicators:

  - 🔴 for stale PRs
  - 🚧 for PRs on hold
  - 🏖️ for weekend work
  - ✅ for users with no stale PRs

  🔧 Technical Implementation:

  Data Collection:

  - Use GitHub CLI (gh) for API access
  - Include labels in PR data retrieval
  - Analyze PR events and comments for timeline reconstruction
  - Handle GitHub API rate limiting gracefully

  Processing Logic:

  - Filter out bot updates completely from staleness determination
  - Verify weekend updates are made by specified users only
  - Calculate working days excluding weekends
  - Cross-reference PR labels for hold status detection

  Error Handling:

  - Handle missing data gracefully
  - Continue processing if some users hit rate limits
  - Provide meaningful error messages for debugging

  📊 Expected Output Behavior:

  1. Search for open PRs authored by or assigned to each specified user
  2. For each PR, reconstruct timeline to find last human update
  3. Calculate working days since last human update (excluding weekends)
  4. Flag PRs >10 working days as stale
  5. Check for "do-not-merge/hold" labels and mark accordingly
  6. Identify weekend updates made specifically by users in our list (not bots)
  7. Generate comprehensive markdown report with all required sections
  8. Display final statistics and full file path

  🎯 Key Success Criteria:

  - Accurate staleness calculation based on human activity only
  - Proper identification of hold PRs with visual indicators
  - Correct weekend work detection (users in list only, not bots)
  - Professional report format with actionable insights
  - Clear differentiation between actionable stale PRs vs. intentionally paused ones
