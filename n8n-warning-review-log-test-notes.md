# n8n Warning Review Log Test Notes

## Purpose

This file documents the warning review Automation Log test for the AI Marketing Performance Report Generator n8n workflow.

The goal of this test was to confirm that n8n can write a log row to the Automation Log tab when the spreadsheet says warnings need review before report generation.

This is important because the workflow should not continue to AI generation when unusual metric changes may need manual review.

## Test Summary

The warning review log test successfully confirmed that n8n can append a new row to the Automation Log tab when Final Review Status is Review warnings before generating report.

The test was performed by temporarily increasing the current week conversions value in the Raw Data tab.

When the conversion change became unusually large, the spreadsheet warning logic changed the Final Review Status to Review warnings before generating report.

The n8n workflow then routed the run through the false branch, created a status message, and wrote a log row to the Automation Log tab.

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

## Test Setup

The test used the warning review path.

Temporary change:

- Cell changed: Raw Data!E3
- Original value: 57
- Temporary test value: 100

This caused the spreadsheet warning logic to detect an unusually large conversion change.

## Expected Spreadsheet Status

After changing Raw Data!E3 to 100, the expected Final Review Status was:

```text
Review warnings before generating report
```

## Expected n8n Behavior

The workflow should not pass the ready check.

Expected behavior:

- n8n reads the Automation Output tab.
- n8n finds the Final Review Status row.
- Check If Report Is Ready does not pass because the value is not Ready to generate report.
- The workflow moves through the false branch.
- The Edit Fields node creates a status message.
- The Google Sheets Append Row node writes a new row to the Automation Log tab.

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
| Final Review Status | Review warnings before generating report |
| Notes | Workflow stopped because report was not ready or needed review. |

## Test Result

Result:

Successful.

n8n wrote a warning review log row to the Automation Log tab.

This confirms that the workflow can record when report generation is blocked because warnings need review.

## Data Restoration

After the test, the temporary value was restored.

Restored value:

- Cell: Raw Data!E3
- Value: 57

After restoring the value, the spreadsheet validation status returned to Ready to generate report.

## Screenshot Evidence

Recommended screenshot file:

`screenshots/15-n8n-warning-review-log-test.png`

This screenshot should show either the successful n8n append row node output or the new warning review row added to the Automation Log tab.

## What This Test Proves

This test proves that:

- Spreadsheet warning logic can detect unusual metric changes.
- The Automation Output tab reflects warning review status.
- n8n can read the updated Final Review Status.
- n8n can route warning review cases through the false branch.
- n8n can create a false branch status message.
- n8n can append a warning review log row to the Automation Log tab.
- The workflow can leave a record when report generation is blocked due to warning review.

## Why This Matters

This matters because complete data is not always safe data.

A report can have all required fields present but still need review if a metric changes in an unusual way.

This test confirms that the workflow can log warning review cases instead of blindly continuing toward AI report generation.

## Current Automation Status

Completed:

- n8n can read the Raw Data tab.
- n8n can read the AI Prompt Input tab.
- n8n can read the Automation Output tab.
- n8n can isolate the Final Review Status row.
- n8n can check whether the report is ready.
- n8n can create a false branch message.
- n8n can append a not-ready log row to the Automation Log tab.
- n8n can append a warning review log row to the Automation Log tab.
- The spreadsheet test value was restored after testing.

Not completed:

- AI API request
- Automated report generation
- Automated report saving
- Email or Google Docs output
- Scheduled workflow
- Separate custom messages for missing data versus warning review

## Recommended Next Step

The next recommended step is to update the current n8n workflow summary to include the Automation Log write tests.

After that, the project can decide whether to continue improving the logging branch or prepare the true branch for a future AI API test.

The AI API should still wait until the current workflow documentation is updated.

## Main Takeaway

The warning review log test was successful.

The workflow now logs both major blocked-run cases:

- Missing required data
- Warning review needed

This makes the automation safer, clearer, and easier to debug before connecting the workflow to an AI model.
