# n8n Readiness Plan: AI Marketing Performance Report Generator

## Purpose

This file outlines the readiness plan for connecting the AI Marketing Performance Report Generator to n8n.

The goal is to move carefully from the current spreadsheet prototype into automation without trying to automate everything at once.

## Current Project Status

The current version is a spreadsheet-based prototype supported by GitHub documentation.

Completed so far:

- Google Sheet with structured tabs
- Raw weekly marketing performance data
- Weekly comparison formulas
- AI-ready prompt input
- Validation checks
- Warning logic
- Final review status
- Validation summary
- Sample generated report output
- Screenshots
- Workflow diagram
- Case study draft
- Architecture notes
- Portfolio summary
- Demo walkthrough
- Project review checklist
- n8n readiness planning
- n8n field mapping plan
- Lessons learned
- Interview talking points
- Repo file index
- First n8n Google Sheets read test
- n8n first test notes

Not completed yet:

- Reading the AI Prompt Input tab in n8n
- Reading Final Review Status in n8n
- Reading Validation Summary in n8n
- Adding a readiness check in n8n
- AI API request
- Automated report generation
- Automated report saving
- n8n workflow screenshots beyond the first read test

## First n8n Milestone

The first n8n milestone is complete.

Milestone:

Connect n8n to Google Sheets and read the Raw Data tab.

Result:

Successful.

n8n was able to access the AI Marketing Performance Report Generator spreadsheet and read the Raw Data tab.

This confirms that the project can move from a spreadsheet-only prototype into an automation workflow.

## Completed First Test Workflow

The first test workflow used this structure:

```text
Manual Trigger
   ↓
Google Sheets Node
   ↓
Get Row(s) from Raw Data tab
   ↓
View Output Data
```

## What the First Test Proved

The first n8n test proved that:

- n8n can connect to the project Google Sheet.
- n8n can access the Raw Data tab.
- n8n can read existing spreadsheet rows.
- Previous week and current week source data can be brought into n8n.
- The project is ready for the next automation layer.

## Why This Matters

This matters because the future automated workflow depends on n8n being able to read spreadsheet data first.

Before adding AI, API requests, validation branches, or report saving, the project needed to prove that the source data can enter the automation system.

That foundation is now working.

## Next n8n Goal

The next n8n goal is:

Read the AI Prompt Input tab and confirm n8n can access the final prompt and validation status.

The next test should check whether n8n can read:

- Final Prompt to Send to AI
- Final Review Status
- Validation Summary
- Warning Notes

This step should happen before connecting the AI API.

## Safe Build Order From Here

Recommended build order:

1. Read Raw Data from Google Sheets. Completed.
2. Document the successful read test. Completed.
3. Read AI Prompt Input from Google Sheets.
4. Confirm n8n can access the final prompt and validation status.
5. Add a simple readiness check.
6. Continue only if Final Review Status is ready.
7. Test sending the prompt to an AI model.
8. Save the generated report output.

## Next Test Workflow

The next test workflow should be simple:

```text
Manual Trigger
   ↓
Google Sheets Node
   ↓
Read AI Prompt Input tab
   ↓
View Final Prompt and Validation Status
```

## What Not to Do Yet

Do not add the AI API yet.

Do not build the full report generation workflow yet.

Do not add email output yet.

Do not add Google Docs output yet.

Do not overcomplicate the next test with too many conditions.

The next automation win is simply reading the final prompt and validation fields successfully.

## Questions to Answer During the Next Test

When n8n reads the AI Prompt Input tab, answer these questions:

- Does the final prompt appear inside n8n?
- Does Final Review Status appear inside n8n?
- Does Validation Summary appear inside n8n?
- Do Warning Notes appear inside n8n?
- Are the field names readable?
- Is the final prompt text complete?
- Does the output structure look usable for a future AI API request?

## Possible Issues to Watch For

Possible issues:

- The AI Prompt Input tab may be harder to read than the Raw Data tab.
- Some cells may appear as blank fields.
- Long prompt text may appear in a nested or expanded field.
- Merged cells may cause confusing output.
- Header names may need to be adjusted.
- n8n may read rows differently than expected.
- The final prompt may need to be placed in a clearer table format later.

These issues are normal.

The goal is to observe what n8n receives before changing the spreadsheet.

## Documentation to Add After the Next Test

After the AI Prompt Input read test, add documentation for:

- What tab was read
- Whether the final prompt appeared
- Whether validation status appeared
- Whether warning notes appeared
- Any structure issues
- Any spreadsheet adjustments needed
- Screenshot of the n8n output
- Next recommended automation step

Potential future file:

`n8n-ai-prompt-input-test-notes.md`

## Future n8n Workflow Plan

After n8n can read the AI Prompt Input tab, the workflow can be expanded.

Future workflow:

```text
Manual Trigger or Schedule Trigger
   ↓
Google Sheets: Read AI Prompt Input
   ↓
Check Final Review Status
   ↓
If Ready
   ↓
Send Prompt or JSON Payload to AI API
   ↓
Receive Generated Report
   ↓
Save Report Output
```

If the report is not ready:

```text
Check Final Review Status
   ↓
If Not Ready
   ↓
Stop Workflow
   ↓
Send Review Notice or Log Issue
```

## Future AI API Step

The AI API step should come after the Google Sheets prompt and validation data are readable and reliable.

The AI API step will eventually need:

- Final prompt text
- Report context
- Performance metric changes
- Key insight
- Recommended action
- Validation summary
- Clear output instructions

The AI model should return a structured weekly marketing performance report.

## Future Report Output Options

Possible output destinations:

- Generated Report tab in Google Sheets
- Google Docs
- Email
- Markdown file
- Notion page
- Airtable record

The simplest first output option is probably the Generated Report tab in Google Sheets.

## Version 1 Automation Goal

Version 1 automation goal:

Read data from Google Sheets in n8n and confirm the output.

Status:

Complete.

## Version 2 Automation Goal

Version 2 automation goal:

Use n8n to read the final AI-ready prompt and validation status from the spreadsheet.

Status:

Next.

## Version 3 Automation Goal

Version 3 automation goal:

Send the final prompt to an AI model and receive a generated report.

Status:

Not started.

## Version 4 Automation Goal

Version 4 automation goal:

Save the generated report output back to Google Sheets, Google Docs, or email.

Status:

Not started.

## Final Reminder

The project should move forward in small working layers.

The first n8n layer is complete.

The next technical step is to prove that n8n can read the final prompt and validation status from the AI Prompt Input tab.
