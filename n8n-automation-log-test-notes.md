# n8n Automation Log Test Notes

## Purpose

This file documents the Automation Log write test for the AI Marketing Performance Report Generator n8n workflow.

The goal of this test was to confirm that n8n can write a false branch status message back to Google Sheets when the report is not ready to generate.

This is important because the workflow should leave a visible record when it stops instead of failing silently or continuing incorrectly.

## Test Summary

The Automation Log write test successfully confirmed that n8n can append a new row to the Automation Log tab in Google Sheets.

The test used the not-ready path by temporarily clearing a required metric value in the Raw Data tab.

When the spreadsheet validation status changed to not ready, the n8n workflow routed the run through the false branch, created a status message, and wrote a log row to the Automation Log tab.

## Workflow Name

AI Marketing Report Generator - Google Sheets Read Test

## Workflow Type

Manual test workflow

## Workflow Nodes Used

The test workflow used:

- Manual Trigger
- Raw Data Sheet node
- AI Prompt Input Sheet node
- Automation Output Sheet node
- Find Final Review Status node
- Check If Report Is Ready node
- Edit Fields node
- Google Sheets Append Row node for Automation Log

## Workflow Structure

```text
Manual Trigger
   ↓
Raw Data Sheet
   ↓
AI Prompt Input Sheet
   ↓
Automation Output Sheet
   ↓
Find Final Review Status
   ↓
Check If Report Is Ready
   ↓
False Branch
   ↓
Edit Fields
   ↓
Append Row to Automation Log
```

## Google Sheet Used

Spreadsheet:

AI Marketing Performance Report Generator

Tabs used:

- Raw Data
- Automation Output
- Automation Log

## Automation Log Tab Structure

The Automation Log tab includes these columns:

| Column | Purpose |
| --- | --- |
| Timestamp | Records when the workflow log row was created |
| Status | Shows whether the report was generated or not generated |
| Message | Explains why the workflow stopped |
| Final Review Status | Stores the spreadsheet readiness status |
| Notes | Adds extra context about the workflow result |

## Test Setup

The test used the missing-data path.

Temporary change:

- Cell changed: Raw Data!B3
- Original value: 1390
- Temporary test value: blank

This caused the spreadsheet validation logic to change the Final Review Status away from Ready to generate report.

## False Branch Message

The false branch created this message:

```text
Report not generated. Review spreadsheet validation status before continuing.
```

## Automation Log Row

The workflow successfully appended a row to the Automation Log tab.

Expected log fields:

| Field | Expected Value |
| --- | --- |
| Timestamp | Current n8n run timestamp |
| Status | Not Generated |
| Message | Report not generated. Review spreadsheet validation status before continuing. |
| Final Review Status | Not ready to generate report |
| Notes | Workflow stopped because report was not ready or needed review. |

## Test Result

Result:

Successful.

n8n wrote a false branch log row to the Automation Log tab.

This confirms that the workflow can record why report generation did not continue.

## Data Restoration

After the test, the missing value was restored.

Restored value:

- Cell: Raw Data!B3
- Value: 1390

After restoring the value, the spreadsheet validation status returned to Ready to generate report.

## Screenshot Evidence

Recommended screenshot file:

`screenshots/14-n8n-automation-log-write-test.png`

This screenshot should show either the successful n8n append row node output or the new row added to the Automation Log tab.

## What This Test Proves

This test proves that:

- n8n can read the Automation Output tab.
- n8n can check whether the report is ready.
- n8n can route not-ready cases through the false branch.
- n8n can create a status message.
- n8n can append a row to Google Sheets.
- The workflow can leave a record when report generation does not continue.
- The project now has a basic workflow logging layer.

## Why This Matters

This matters because automation workflows need traceability.

If a workflow stops because the report is not ready, the user should be able to see what happened.

The Automation Log tab creates a simple record of blocked workflow runs.

This will make the future AI reporting workflow easier to debug and explain.

## What Was Not Tested Yet

This test did not include:

- Warning review log test
- AI API connection
- Sending the final prompt to an AI model
- Saving generated report output
- Sending report output to Google Docs or email
- Scheduled automation

Those steps should be added later in small layers.

## Current Automation Status

Completed:

- n8n can read the Raw Data tab.
- n8n can read the AI Prompt Input tab.
- n8n can read the Automation Output tab.
- n8n can isolate the Final Review Status row.
- n8n can check whether the report is ready.
- n8n can create a false branch message.
- n8n can append a false branch log row to the Automation Log tab.
- The spreadsheet test value was restored after testing.

Not completed:

- Warning review log test
- AI API request
- Automated report generation
- Automated report saving
- Email or Google Docs output
- Scheduled workflow

## Recommended Next Step

The next recommended step is to test the Automation Log with the warning review path.

This should confirm that the workflow also logs a stopped run when warnings need review.

A possible test:

1. Temporarily change Raw Data!E3 from 57 to 100.
2. Confirm Final Review Status changes to Review warnings before generating report.
3. Run the workflow.
4. Confirm a new Automation Log row is created.
5. Restore Raw Data!E3 to 57.

## Main Takeaway

The Automation Log write test was successful.

The workflow now has a basic logging layer that records when report generation does not continue.

This makes the automation safer, clearer, and easier to debug before connecting the workflow to an AI model.
