# n8n Warning Review Path Test Notes

## Purpose

This file documents the warning review path test for the AI Marketing Performance Report Generator n8n workflow.

The goal of this test was to confirm that the workflow does not continue as ready when the spreadsheet validation logic says warnings need review.

This is important because the automation should not send data to an AI model when unusual metric changes may need manual review first.

## Test Summary

The warning review path test successfully confirmed that the n8n readiness check does not pass when the spreadsheet says warnings need review.

The test was performed by temporarily increasing the current week conversions value in the Raw Data tab.

When the conversion change became unusually large, the spreadsheet warning logic changed the Final Review Status to Review warnings before generating report.

The n8n If node then correctly prevented that row from passing the readiness check.

## Workflow Name

AI Marketing Report Generator - Google Sheets Read Test

## Workflow Type

Manual test workflow

## Workflow Nodes Used

The test workflow used:

- Manual Trigger
- Google Sheets node for Automation Output
- If node for readiness checking

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
Check Final Review Status
```

## Google Sheet Used

Spreadsheet:

AI Marketing Performance Report Generator

Sheet/tab used by n8n:

Automation Output

Source tab temporarily changed for the test:

Raw Data

## Test Setup

The test was performed by temporarily changing the current week Conversions value from 57 to 100.

Temporary change:

- Cell changed: Raw Data!E3
- Original value: 57
- Temporary test value: 100

This caused the spreadsheet warning logic to detect an unusually large conversion change.

## Expected Result

When Raw Data!E3 was changed to 100, the workflow should not pass the readiness check.

Expected behavior:

- Conversion Change Warning should show that the conversion change needs review.
- Final Review Status should change to Review warnings before generating report.
- The If node should not send the Final Review Status row to the True Branch.
- The workflow should treat the report as needing review before generation.

## Test Result

Result:

Successful.

The n8n readiness check did not pass when the spreadsheet showed Review warnings before generating report.

This confirmed that the workflow can recognize warning review status and avoid continuing as if the report is fully ready.

## Data Restoration

After the test, the temporary value was restored.

Restored value:

- Cell: Raw Data!E3
- Value: 57

After restoring the value, the spreadsheet validation status returned to Ready to generate report.

## Screenshot Evidence

Screenshot file:

`screenshots/11-n8n-warning-review-path-test.png`

The screenshot shows the n8n readiness check behavior when the report required warning review due to an unusually large conversion change.

## What This Test Proves

This test proves that:

- Spreadsheet warning logic can detect unusual metric changes.
- The Automation Output tab reflects warning review status.
- n8n can read the updated Final Review Status.
- The If node does not pass the readiness check when warnings need review.
- The workflow has a stronger validation gate before future AI generation.
- The project can avoid generating polished AI reports from data that may need review.

## Why This Matters

This matters because complete data is not always safe data.

A report may have all required fields present but still need manual review if a metric changes in an unusual way.

This test confirms that the workflow can block report generation when the spreadsheet says warning review is needed.

That makes the future AI reporting workflow more reliable and safer.

## What Was Not Tested Yet

This test did not include:

- AI API connection
- Sending the final prompt to an AI model
- A custom false branch message
- A manual review notification
- Saving generated report output
- Sending report output to Google Docs or email
- Scheduled automation

Those steps should be added later in small layers.

## Current Automation Status

Completed:

- n8n can read the Raw Data tab.
- n8n can read the AI Prompt Input tab.
- n8n can read the Automation Output tab.
- n8n can identify when Final Review Status is Ready to generate report.
- n8n can avoid passing the readiness check when required data is missing.
- n8n can avoid passing the readiness check when warnings need review.
- The spreadsheet value was restored after testing.

Not completed:

- False branch handling message
- Manual review notification
- AI API request
- Automated report generation
- Automated report saving
- Scheduled workflow

## Important Testing Note

This test used a temporary spreadsheet change.

The test data should not be left changed after the test.

Raw Data!E3 should be restored to:

57

The project should end the test with Final Review Status showing:

Ready to generate report

## Recommended Next Step

The next recommended step is to document the overall readiness gate.

The project now has three readiness tests:

- Ready path test
- Not-ready path test
- Warning review path test

Together, these prove that the workflow can check whether the report should continue before future AI generation.

A useful next documentation file would be:

`n8n-readiness-gate-summary.md`

This file should explain the full readiness gate and the three tested outcomes.

## Safe Build Order From Here

Recommended next build order:

1. Document the warning review path test.
2. Save the screenshot evidence.
3. Create a readiness gate summary.
4. Add a simple false branch plan.
5. Decide how the workflow should handle not-ready and warning statuses.
6. Only after readiness logic is clear, test sending the final prompt to an AI model.

## Main Takeaway

The warning review path test was successful.

n8n can now recognize that the workflow should not continue when the spreadsheet says warnings need review.

This strengthens the automation validation gate before future AI report generation.
