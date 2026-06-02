# n8n First Test Notes: Google Sheets Read Test

## Purpose

This file documents the first successful n8n test for the AI Marketing Performance Report Generator.

The goal of this test was to confirm that n8n can connect to the project Google Sheet and read data from the Raw Data tab.

This was the first automation step for the project.

## Test Summary

The first n8n test successfully connected to Google Sheets and read the Raw Data tab from the AI Marketing Performance Report Generator spreadsheet.

The test confirmed that n8n can access the source marketing performance data before adding AI, validation branches, report generation, or output saving.

## Workflow Name

AI Marketing Report Generator - Google Sheets Read Test

## Workflow Type

Manual test workflow

## Workflow Nodes Used

The first test workflow used:

- Manual Trigger
- Google Sheets node

## Workflow Structure

```text
Manual Trigger
   ↓
Google Sheets Node
   ↓
Get Row(s) from Raw Data tab
   ↓
View Output Data
```

## Google Sheet Used

Spreadsheet:

AI Marketing Performance Report Generator

Sheet/tab:

Raw Data

## Google Sheets Node Settings

The Google Sheets node was configured to:

- Use Google Sheets credentials
- Select the AI Marketing Performance Report Generator spreadsheet
- Select the Raw Data tab
- Use the Get Row(s) operation
- Read existing rows from the sheet

## Data Read From Google Sheets

The test confirmed that n8n could read the weekly marketing performance data from the Raw Data tab.

The Raw Data tab includes:

- Week Start Date
- Users
- Sessions
- Engagement Rate
- Conversions
- CTA Clicks
- Top Channel
- Top Page
- Notes

## Expected Rows

The expected rows were:

Previous week:

- Week start date: 2026-05-04
- Users: 1250
- Sessions: 1600
- Engagement Rate: 62%
- Conversions: 48
- CTA Clicks: 135
- Top Channel: Organic Search
- Top Page: /services

Current week:

- Week start date: 2026-05-11
- Users: 1390
- Sessions: 1785
- Engagement Rate: 66%
- Conversions: 57
- CTA Clicks: 162
- Top Channel: Organic Search
- Top Page: /services

## Test Result

Result:

Successful

n8n was able to read the Raw Data tab from Google Sheets.

This confirms that the project can move from a spreadsheet-only prototype into an automation workflow.

## Screenshot Evidence

Screenshot file:

`screenshots/06-n8n-google-sheets-read-test.png`

The screenshot shows the successful n8n Google Sheets read test and the output data returned from the Raw Data tab.

## What This Proves

This test proves that:

- n8n can connect to the project Google Sheet.
- n8n can access the Raw Data tab.
- n8n can read existing spreadsheet rows.
- The source marketing data can be brought into an automation workflow.
- The project is ready for the next automation layer.

## What Was Not Tested Yet

This test did not include:

- AI API connection
- Report generation
- Validation branching
- Final Review Status checks
- Saving output back to Google Sheets
- Sending output to Google Docs or email
- Scheduled automation

Those steps should be added later in small layers.

## Next Recommended Step

The next step should be to confirm how n8n reads the AI Prompt Input tab.

Specifically, the next test should check whether n8n can read:

- Final Prompt to Send to AI
- Final Review Status
- Validation Summary
- Warning Notes

This should happen before connecting the AI API.

## Safe Build Order From Here

Recommended next build order:

1. Read Raw Data from Google Sheets.
2. Document the successful read test.
3. Read AI Prompt Input from Google Sheets.
4. Confirm n8n can access the final prompt and validation status.
5. Add a simple readiness check.
6. Only continue if Final Review Status is ready.
7. Then test sending the prompt to an AI model.
8. Save the generated report output.

## Main Takeaway

The first n8n test was successful.

The project now has proof that Google Sheets data can be read by n8n, which is the foundation for the future automated AI marketing report workflow.
