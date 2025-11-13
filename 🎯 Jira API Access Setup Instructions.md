  🎯 Jira API Access Setup Instructions

  You need to gain access to my Red Hat Jira instance at https://issues.redhat.com. Follow these steps in exact order:

  Step 1: Set Environment Variable

  export JIRA_API_TOKEN=<TOKEN>
  
  Step 2: Test Authentication

  Use Bearer token authentication (not Basic Auth) with this test command:
  curl -H "Authorization: Bearer $JIRA_API_TOKEN" -H "Accept: application/json" "https://issues.redhat.com/rest/api/2/search?jql=reporter=currentUser()&maxResults=1"

  Expected Success Response: JSON with {"startAt":0,"maxResults":1,"total":X,"issues":[...]}

  Step 3: Verify Access

  If you get 401/403 errors, try these authentication methods in order:
  1. Authorization: Bearer $JIRA_API_TOKEN (preferred)
  2. Authorization: Basic $JIRA_API_TOKEN
  3. -u "<jira username>:$JIRA_API_TOKEN"

  Step 4: Confirm Working Setup

  Once authenticated, fetch a sample issue to verify full access:
  curl -H "Authorization: Bearer $JIRA_API_TOKEN" -H "Accept: application/json" "https://issues.redhat.com/rest/api/2/search?jql=assignee=currentuser()&maxResults=1"

  ---
  🚨 Troubleshooting Common Issues

  If you get 401 Unauthorized:
  - Token not set properly → Re-export JIRA_API_TOKEN
  - Wrong auth method → Use Bearer, not Basic

  If you get 403 Forbidden:
  - Token working but no API permissions → Continue anyway, report may still generate with limited data

  If you get 404 Not Found:
  - URL typo → Verify https://issues.redhat.com endpoint
  - Invalid JQL → Simplify test query

  ---
  ✅ Success Criteria

  You should be able to:
  1. ✅ Get JSON response from /rest/api/2/search endpoint
  2. ✅ Query issues by assignee (e.g., assignee=currentuser())
  3. ✅ Access issue details and metadata

  Once these work, you have full API access and can run my comprehensive Jira analysis scripts.

  🔑 Key Points to Remember

  1. Always use Bearer token - this is what works with Red Hat Jira
  2. Username is <jira username> - but use the token for API access
  3. Base URL is https://issues.redhat.com - not cloud instance
  4. Some changelog endpoints return 404 - this is normal, continue processing
  5. The script handles rate limiting - don't worry about API limits