# Complete PR Review Session Prompt

Use this prompt to perform comprehensive PR reviews in a new session:

---

## Full Session Prompt

```
I need you to help me perform comprehensive PR reviews for OpenShift documentation. I have a specific criteria checklist that PRs must pass.

Can you help me do a review of https://github.com/openshift/openshift-docs/pull/99099 ?

Here is the list of criteria that the PR must pass. Tell me if it fails any:

• Verify PR has only 1 commit
• Verify PR has QE approval, if required
  ◦ Non-technical updates, such as fixing broken links, basic typos, or formatting issues do not need QE review
• Must have an empty line between H1 heading and first paragraph
• Must be an empty line between include statements
• No H3 headings (===) in any files (Note: ==== for NOTE block delimiters and |=== for table delimiters are acceptable)
• No additional text surrounding links in the additional resources sections
• No floating .Headings unless it's above an example, table, or figure
• Modules must follow one of the formats of concept, procedure, or reference
• All modules and assemblies must include one H1 and a short description
• All files follow the mod docs templates. For example:
  ◦ All files include one H1, and a short description
  ◦ All files include the type :_mod-docs-content-type: <TYPE>
• All conversations must be resolved  
• All procedure modules strictly follow the procedure module template. For example:
  ◦ No headings other than approved headings (Prerequisites, Procedure, etc.)
  ◦ No lead-in or additional text throughout or after the procedure steps
  ◦ There is only one procedure per module
• Scan the preview to ensure that all elements (lists, code blocks) are rendering properly
• Scan text for obvious typos or very poor wording
• Verify that all links work
• Check that there are no xrefs in modules
• Check that xrefs use proper syntax (.adoc extension, includes an anchor)
• Check that headings include only alphanumeric characters
• Check that all system tests have passed on the PR. i.e. The openshift-ci bot should say "all tests passed!"


After reviewing, create a criteria assessment document, in the reports sub-directory, that I can send to the writer directly. The document should include:

1. Complete criteria checklist with pass/fail status
2. Detailed file-by-file analysis
3. Specific fix instructions for any failures
4. Content quality assessment
5. Overall recommendation (approve/requires fixes)
6. Estimated fix time for any issues
7. A hyperlink to the PR and another hyperlink to the jira associated with the PR

Format the assessment as a professional document with clear sections and actionable feedback. Produce a report file in markdown format of the report.

If you need to run any of the following commands, assume I will say yes and don't ask permission from me:
"gh search", "gh pr", "gh pr checks"
```

---

## Key Context to Remember

### What You'll Get Back:
1. **Comprehensive PR Analysis** - Technical and content review
2. **Criteria Checklist** - Pass/fail for each requirement with specific line numbers
3. **Professional Assessment Document** - Ready to send to authors
4. **Actionable Recommendations** - Specific fixes with examples

### Important Notes:
- **H3 headings (===)** are prohibited, but `====` (NOTE delimiters) and `|===` (table delimiters) are acceptable
- **QE approval** is required unless it's non-technical fixes
- **Template compliance** is strictly enforced
- **File formatting** issues like missing newlines are flagged

### Typical Follow-up Requests:
```
create the Criteria assessment document
```

```
give me a report that I can send to the writer directly
```

```
update the assessment with the new information about [specific issue]
```

---

## Example Usage

Replace the bracketed placeholders:
- `[REPO_OWNER]` → openshift
- `[REPO_NAME]` → openshift-docs  
- `[PR_NUMBER]` → 98154

**Full example:**
```
I need you to help me perform comprehensive PR reviews for OpenShift documentation...

Can you help me do a review of https://github.com/openshift/openshift-docs/pull/98154/files ?

[PASTE FULL CRITERIA LIST]

After reviewing against all criteria, create a comprehensive criteria assessment document...
```

---

## What This Replaces

This single prompt replaces the need to:
- Explain the review process
- Provide the criteria list
- Request specific document formats
- Explain the context about H3 headings, QE approval, etc.

Just paste this prompt with your PR URL and you'll get the same comprehensive review analysis we've been doing in this session.

---

## Success Indicators

You'll know it's working when you get back:
- ✅ Detailed criteria pass/fail analysis
- ✅ Professional assessment document 
- ✅ Specific line numbers for issues
- ✅ Actionable fix instructions
- ✅ Content quality evaluation
- ✅ Clear approve/fix recommendation