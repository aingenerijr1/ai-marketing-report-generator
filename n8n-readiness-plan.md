# n8n Readiness Plan: AI Marketing Performance Report Generator

## Purpose

This file outlines the readiness plan for connecting the AI Marketing Performance Report Generator to n8n.

The goal is to move carefully from the current spreadsheet prototype into the first automation phase without trying to automate everything at once.

The first n8n goal is simple:

Connect n8n to Google Sheets and read the weekly marketing data.

The first n8n goal is not to connect the AI API immediately.

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

Not completed yet:

- n8n connection
- Google Sheets connection inside n8n
- AI API request
- Automated report generation
- Automated report saving
- n8n workflow screenshots

## Why n8n Comes Next

n8n is the next technical step because it will eventually connect the spreadsheet data to an automated workflow.

The future workflow should be able to:

1. Read weekly marketing data from Google Sheets.
2. Check whether the report is ready.
3. Send the prompt or structured data to an AI model.
4. Receive a generated report.
5. Save or send the report output.

However, the first step should only focus on reading the spreadsheet data.

## Safe Build Order

The automation should be built in small layers.

Recommended build order:

1. Connect n8n to Google Sheets.
2. Read rows from the Raw Data tab.
3. Confirm the data appears correctly inside n8n.
4. Identify the previous week and current week rows.
5. Confirm the field names and values are understandable.
6. Decide whether n8n should read from Raw Data, Weekly Comparison, or AI Prompt Input.
7. Test a simple workflow run.
8. Document what worked.
9. Take a screenshot of the successful n8n data read.
10. Only then plan the AI API step.

## First n8n Test Goal

The first n8n test should answer one question:

Can n8n successfully read the Google Sheet data?

The workflow does not need to generate a report yet.

The workflow does not need to use an AI model yet.

The workflow does not need to send an email yet.

Success means n8n can connect to the Google Sheet and display the spreadsheet data inside the workflow.

## Recommended First n8n Workflow

The first workflow should be simple.

Planned workflow:

```text
Manual Trigger
   ↓
Google Sheets Node
   ↓
Read Rows
   ↓
View Output Data
```

## First Workflow Components

The first workflow should include:

- Manual Trigger node
- Google Sheets node
- Google account connection
- Spreadsheet selection
- Sheet/tab selection
- Read rows operation
- Output data review

## Data to Read First

Start by reading from the Raw Data tab.

Reason:

The Raw Data tab is the cleanest source layer and contains the original weekly metric values.

The first test should confirm that n8n can read:

- Week start date
- Users
- Sessions
- Engagement rate
- Conversions
- CTA clicks
- Top channel
- Top page
- Notes

## Questions to Answer During First Test

When the data appears in n8n, answer these questions:

- Does each row appear correctly?
- Are the column names clear?
- Are numbers coming through correctly?
- Is engagement rate readable?
- Are dates formatted clearly?
- Can n8n distinguish previous week from current week?
- Is the output data easy to use for the next step?

## Possible Issues to Watch For

Possible setup issues:

- Google account connection does not work.
- n8n cannot access the spreadsheet.
- Wrong spreadsheet is selected.
- Wrong tab is selected.
- Header row is not detected correctly.
- Dates are formatted strangely.
- Percent values appear differently than expected.
- Blank cells create confusing output.
- Data appears, but field names are unclear.

These are normal beginner automation issues.

The goal is to identify and fix them one at a time.

## What Not to Do Yet

Do not add the AI API yet.

Do not build the full report generation workflow yet.

Do not add email output yet.

Do not overcomplicate the first workflow with conditions, filters, or multiple branches.

Do not rebuild the spreadsheet unless the n8n output shows that something needs to be adjusted.

The first automation win is simply reading data successfully.

## First n8n Success Criteria

The first n8n step is successful when:

- n8n connects to Google Sheets.
- n8n reads the Raw Data tab.
- The previous week row appears in the output.
- The current week row appears in the output.
- The key metric fields are visible.
- The data structure is understandable.
- A screenshot is captured for documentation.

## Documentation to Add After First Test

After the first successful n8n test, add documentation for:

- What workflow was created
- Which Google Sheet tab was read
- What data appeared in n8n
- Any setup issues encountered
- How the issue was fixed
- Screenshot of the n8n workflow
- Screenshot of the n8n output data

Potential future file:

`n8n-first-test-notes.md`

## Future n8n Workflow Plan

After n8n can read the Google Sheet, the workflow can be expanded.

Future workflow:

```text
Manual Trigger or Schedule Trigger
   ↓
Google Sheets: Read Data
   ↓
Check Report Readiness
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
Check Report Readiness
   ↓
If Not Ready
   ↓
Stop Workflow
   ↓
Send Review Notice or Log Issue
```

## Future AI API Step

The AI API step should come after the Google Sheets data is readable and reliable.

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

## Version 2 Automation Goal

Version 2 automation goal:

Use n8n to read the final AI-ready prompt from the spreadsheet.

## Version 3 Automation Goal

Version 3 automation goal:

Send the final prompt to an AI model and receive a generated report.

## Version 4 Automation Goal

Version 4 automation goal:

Save the generated report output back to Google Sheets, Google Docs, or email.

## Final Reminder

The project should move forward in small working layers.

The next technical step is not to build the whole automation system.

The next technical step is to prove that n8n can read the Google Sheet data.
