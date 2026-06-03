# n8n False Branch Test Notes

## Purpose

This file documents the false branch message test for the AI Marketing Performance Report Generator n8n workflow.

The goal of this test was to confirm that the workflow can produce a clear status message when the report is not ready to continue.

This is important because the workflow should not silently fail or continue toward AI generation when the spreadsheet validation status says the report is not ready.

## Test Summary

The false branch message test successfully confirmed that the n8n workflow can create a clear message when the readiness check does not pass.

The workflow used an If node to check whether Final Review Status was Ready to generate report.

When the report was not ready, the workflow moved through the false branch and used a Set node to create a status message.

## Workflow Name

AI Marketing Report Generator - Google Sheets Read Test

## Workflow Type

Manual test workflow

## Workflow Nodes Used

The test workflow used:

- Manual Trigger
- Google Sheets node for Automation Output
- If node for readiness checking
- Set node for the false branch message

## Workflow Structure

```text
Manual Trigger
   ↓
Google Sheets Node
   ↓
Get Row(s) from Automation Output tab
   ↓
If Node
   ↓
False Branch
   ↓
Set Node
   ↓
Create status_message
```

## Google Sheet Used

Spreadsheet:

AI Marketing Performance Report Generator

Sheet/tab used by n8n:

Automation Output

## Readiness Check Logic

The If node checked:

```text
Field is equal to Final Review Status
AND
Value is equal to Ready to generate report
```

If both conditions were true, the workflow passed the readiness check.

If the conditions were not true, the workflow moved through the false branch.

## False Branch Message

The Set node created this field:

```text
status_message
```

The Set node used this value:

```text
Report not generated. Review spreadsheet validation status before continuing.
```

## Test Result

Result:

Successful.

The false branch produced the expected status message when the readiness check did not pass.

This confirms that the workflow can provide a clear review message instead of failing silently or continuing incorrectly.

## Screenshot Evidence

Screenshot file:

`screenshots/12-n8n-false-branch-message-test.png`

The screenshot shows the false branch Set node producing the status message.

## What This Test Proves

This test proves that:

- n8n can read the Automation Output tab.
- n8n can check Final Review Status.
- n8n can send non-ready cases to the false branch.
- The false branch can create a clear status message.
- The workflow can avoid continuing toward AI generation when the report is not ready.
- The project now has a basic false branch behavior.

## Why This Matters

This matters because automation workflows should explain what happened when they do not continue.

If required data is missing or warnings need review, the workflow should not generate a report.

The false branch message makes the workflow easier to understand and easier to debug.

## What Was Not Tested Yet

This test did not include:

- AI API connection
- Sending the final prompt to an AI model
- Saving the false branch message back to Google Sheets
- Sending a review email
- Creating a Google Docs report
- Scheduled automation
- Separate messages for missing data versus warning review

Those steps should be added later in small layers.

## Current Automation Status

Completed:

- n8n can read the Raw Data tab.
- n8n can read the AI Prompt Input tab.
- n8n can read the Automation Output tab.
- n8n can identify when Final Review Status is Ready to generate report.
- n8n can avoid passing the readiness check when required data is missing.
- n8n can avoid passing the readiness check when warnings need review.
- n8n can create a false branch status message.

Not completed:

- AI API request
- Automated report generation
- Automated report saving
- Review message saved back to Google Sheets
- Email or Google Docs output
- Scheduled workflow

## Important Testing Note

Any temporary test data should be restored after testing.

The project should end this test with the spreadsheet showing:

```text
Final Review Status = Ready to generate report
```

## Recommended Next Step

The next recommended step is to update the n8n readiness documentation to reflect that the false branch message now works.

After that, the project can decide whether to:

- Save the false branch message back to Google Sheets
- Create a cleaner report generation branch
- Prepare the final prompt for an AI API test
- Stop for the day and update the README

The AI API should still wait until the readiness and false branch logic are clearly documented.

## Main Takeaway

The false branch message test was successful.

The workflow now has a basic way to explain why report generation should not continue when the spreadsheet validation status is not ready.

This makes the future AI reporting workflow safer, clearer, and easier to debug.
