# n8n AI Prompt Input Test Notes

## Purpose

This file documents the second n8n test for the AI Marketing Performance Report Generator.

The goal of this test was to confirm that n8n can read the AI Prompt Input tab from the project Google Sheet.

This test is important because the AI Prompt Input tab contains the final AI-ready prompt, validation information, warning notes, and report readiness logic.

## Test Summary

The AI Prompt Input read test successfully connected to Google Sheets and read the AI Prompt Input tab from the AI Marketing Performance Report Generator spreadsheet.

The test confirmed that n8n can access the spreadsheet tab that prepares the prompt and validation information for future AI report generation.

## Workflow Name

AI Marketing Report Generator - Google Sheets Read Test

## Workflow Type

Manual test workflow

## Workflow Nodes Used

The test workflow used:

- Manual Trigger
- Google Sheets node for Raw Data
- Google Sheets node for AI Prompt Input

## Workflow Structure

```text
Manual Trigger
   ↓
Google Sheets Node
   ↓
Get Row(s) from AI Prompt Input tab
   ↓
View Output Data
```

## Google Sheet Used

Spreadsheet:

AI Marketing Performance Report Generator

Sheet/tab:

AI Prompt Input

## Google Sheets Node Settings

The Google Sheets node was configured to:

- Use Google Sheets credentials
- Select the AI Marketing Performance Report Generator spreadsheet
- Select the AI Prompt Input tab
- Use the Get Row(s) operation
- Read existing rows from the sheet

## Test Result

Result:

Successful.

n8n was able to read the AI Prompt Input tab from Google Sheets.

This confirms that n8n can access the prompt preparation and validation area of the spreadsheet.

## Data Observed in n8n

The output showed that n8n could read rows from the AI Prompt Input tab.

The visible output included content related to:

- Report Context
- Performance Data
- Users change summary
- Sessions change summary
- Engagement rate change summary
- Conversions change summary
- CTA clicks change summary
- Key Insight
- Recommended Action
- Final Prompt to Send to AI

## Important Output Structure Note

The AI Prompt Input tab did not appear as cleanly structured as the Raw Data tab.

In the n8n output, much of the content appeared under a column named:

`Report Prompt Input`

Another column appeared as:

`col_2`

The `col_2` values appeared mostly empty.

This means n8n can read the tab, but the tab may not yet be structured in the cleanest way for future automation.

## What This Means

The test worked, but the output structure may need improvement before sending the final prompt to an AI API.

The current spreadsheet layout is useful for humans because it is readable inside Google Sheets.

However, n8n may need a cleaner automation-friendly structure later.

A future improvement could be to create a small dedicated output area or tab with clear field names such as:

- Final Prompt
- Final Review Status
- Validation Summary
- Warning Notes
- Report Readiness

This would make it easier for n8n to identify exactly which values to use.

## Screenshot Evidence

Screenshot file:

`screenshots/07-n8n-ai-prompt-input-read-test.png`

The screenshot shows the successful n8n read test for the AI Prompt Input tab and the output data returned from Google Sheets.

## What This Test Proves

This test proves that:

- n8n can access the AI Prompt Input tab.
- n8n can read prompt-related spreadsheet content.
- n8n can read the area where report context and performance data are prepared.
- The project is ready to think about a cleaner automation-friendly output structure.
- The project should still avoid connecting the AI API until the required prompt and validation fields are easier to isolate.

## What Was Not Tested Yet

This test did not include:

- AI API connection
- Sending the final prompt to an AI model
- Checking Final Review Status with n8n logic
- Branching based on report readiness
- Saving generated report output
- Sending report output to Google Docs or email
- Scheduled automation

Those steps should be added later in small layers.

## Current Automation Status

Completed:

- n8n can read the Raw Data tab.
- n8n can read the AI Prompt Input tab.
- n8n can access the spreadsheet data needed for future automation.

Not completed:

- Clean extraction of only the final prompt
- Clean extraction of Final Review Status
- Clean extraction of Validation Summary
- Clean extraction of Warning Notes
- Readiness check logic
- AI API request
- Automated report generation
- Automated report saving

## Recommended Next Step

The next recommended step is to create or identify a cleaner automation-friendly output area in Google Sheets.

This area should make it easy for n8n to read only the fields needed for automation.

Possible future structure:

| Field | Value |
| --- | --- |
| Final Prompt | Full AI-ready prompt |
| Final Review Status | Ready to generate report |
| Validation Summary | Validation status: Ready to generate report. |
| Warning Notes | Traffic, conversion, and CTA click warning status |
| Report Readiness | Ready to generate report |

This would help n8n read the exact values needed before connecting the AI API.

## Safe Build Order From Here

Recommended next build order:

1. Document the AI Prompt Input read test.
2. Save the screenshot evidence.
3. Review whether the AI Prompt Input tab needs a cleaner output section.
4. Create an automation-friendly output area if needed.
5. Test whether n8n can read that cleaner output area.
6. Add a simple readiness check.
7. Only then test sending the final prompt to an AI model.

## Main Takeaway

The AI Prompt Input read test was successful.

n8n can read the tab that contains prompt preparation and validation information.

The next challenge is not connection access.

The next challenge is making the prompt and validation fields easier for n8n to isolate and use reliably.
