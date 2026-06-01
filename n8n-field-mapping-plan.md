# n8n Field Mapping Plan: AI Marketing Performance Report Generator

## Purpose

This file maps the current Google Sheet structure to the fields that n8n will eventually read during the automation phase.

The goal is to make the first n8n workflow easier to build by clearly identifying:

- Which spreadsheet tabs matter
- Which fields should be read first
- Which fields are source data
- Which fields are calculated
- Which fields are used for validation
- Which fields may be sent to an AI model later

## Current Google Sheet Tabs

The Google Sheet currently includes these tabs:

- Raw Data
- Weekly Comparison
- AI Prompt Input
- Generated Report
- Notes

Each tab has a different role in the reporting workflow.

## Recommended First Tab for n8n

The first tab n8n should read is:

Raw Data

Reason:

The Raw Data tab contains the original weekly marketing performance metrics. It is the cleanest source layer and is the best place to test whether n8n can connect to the spreadsheet successfully.

The first n8n test should only confirm that data can be read from Google Sheets.

It should not generate a report yet.

It should not call an AI API yet.

## Raw Data Field Mapping

The Raw Data tab contains the main input fields for the reporting workflow.

| Spreadsheet Field | Purpose | Example Value | n8n Use |
| --- | --- | --- | --- |
| Week Start Date | Identifies the reporting week | 2026-05-04 | Used to separate previous week and current week |
| Users | Website user count | 1250 | Used for traffic comparison |
| Sessions | Website session count | 1600 | Used for traffic comparison |
| Engagement Rate | Engagement quality metric | 62% | Used for engagement comparison |
| Conversions | Conversion count | 48 | Used for conversion comparison |
| CTA Clicks | Call-to-action click count | 135 | Used for CTA performance comparison |
| Top Channel | Highest-performing channel | Organic Search | Used for report context |
| Top Page | Highest-performing page | /services | Used for report context |
| Notes | Extra reporting context | Organic traffic remained the top driver | Used for insight and recommendation context |

## Previous Week Sample Row

The previous week sample data is:

| Field | Value |
| --- | --- |
| Week Start Date | 2026-05-04 |
| Users | 1250 |
| Sessions | 1600 |
| Engagement Rate | 62% |
| Conversions | 48 |
| CTA Clicks | 135 |
| Top Channel | Organic Search |
| Top Page | /services |

## Current Week Sample Row

The current week sample data is:

| Field | Value |
| --- | --- |
| Week Start Date | 2026-05-11 |
| Users | 1390 |
| Sessions | 1785 |
| Engagement Rate | 66% |
| Conversions | 57 |
| CTA Clicks | 162 |
| Top Channel | Organic Search |
| Top Page | /services |

## Weekly Comparison Field Mapping

The Weekly Comparison tab contains calculated comparison values.

This tab may be useful later because it already calculates changes before n8n reads the data.

| Field Type | Purpose | n8n Use |
| --- | --- | --- |
| Metric Name | Identifies the metric being compared | Used to label report sections |
| Previous Value | Shows previous week value | Used in AI report context |
| Current Value | Shows current week value | Used in AI report context |
| Change | Shows numeric change | Used to describe movement |
| Percent Change | Shows relative change | Used to describe performance trend |
| Key Insight | Summarizes the main takeaway | Used in final report prompt |
| Potential Recommendation | Suggests next action | Used in final report prompt |

## AI Prompt Input Field Mapping

The AI Prompt Input tab contains the final prompt language and validation logic.

This tab may become the best tab for n8n to read after the first basic Google Sheets test works.

| Field | Purpose | n8n Use |
| --- | --- | --- |
| Report Context | Explains the reporting situation | Sent to AI model |
| Performance Data | Lists metric changes in plain English | Sent to AI model |
| Key Insight | Summarizes the main trend | Sent to AI model |
| Recommended Action | Suggests next step | Sent to AI model |
| Final Prompt to Send to AI | Full prompt block | Sent to AI model |
| Required Data Status | Checks whether required data is present | Used before report generation |
| Prompt Status | Checks whether prompt source fields are ready | Used before report generation |
| Report Readiness | Determines whether report can move forward | Used as automation gate |
| Warning Notes | Flags unusual changes | Used as automation gate |
| Final Review Status | Final ready/not ready status | Used as automation gate |
| Validation Summary | Summary added to final prompt | Sent to AI model or used in logs |

## Recommended n8n Reading Strategy

The recommended reading strategy should happen in stages.

## Stage 1: Read Raw Data

Goal:

Confirm n8n can connect to Google Sheets and read the source data.

Workflow:

```text
Manual Trigger
   ↓
Google Sheets: Read Raw Data
   ↓
View Output
```

Success means:

- n8n connects to the Google Sheet.
- n8n reads the Raw Data tab.
- Previous week row appears.
- Current week row appears.
- Field names are clear.
- Values are readable.

## Stage 2: Read AI Prompt Input

Goal:

Confirm n8n can read the final AI-ready prompt and validation status.

Workflow:

```text
Manual Trigger
   ↓
Google Sheets: Read AI Prompt Input
   ↓
View Final Prompt and Validation Status
```

Success means:

- n8n can read the final prompt.
- n8n can read Final Review Status.
- n8n can read Validation Summary.
- n8n can identify whether the report is ready.

## Stage 3: Add a Readiness Check

Goal:

Use the spreadsheet validation status to decide whether the automation should continue.

Workflow:

```text
Manual Trigger
   ↓
Google Sheets: Read AI Prompt Input
   ↓
Check Final Review Status
   ↓
If Ready: Continue
   ↓
If Not Ready: Stop
```

Success means:

- The workflow only continues when the report is ready.
- The workflow stops when data is missing or warnings need review.

## Stage 4: Prepare for AI API

Goal:

Prepare the final prompt or structured payload for an AI model.

Workflow:

```text
Manual Trigger
   ↓
Google Sheets: Read Final Prompt
   ↓
Check Validation Status
   ↓
Prepare AI Request
```

Success means:

- The final prompt is available inside n8n.
- The validation status is available inside n8n.
- The workflow is ready for an AI API test.

## Fields n8n Should Read First

For the first test, n8n should read these Raw Data fields:

- Week Start Date
- Users
- Sessions
- Engagement Rate
- Conversions
- CTA Clicks
- Top Channel
- Top Page
- Notes

## Fields n8n Should Read Later

For the AI report generation workflow, n8n should eventually read:

- Final Prompt to Send to AI
- Final Review Status
- Validation Summary
- Report Context
- Performance Data
- Key Insight
- Recommended Action
- Warning Notes

## Fields That Should Control Automation

These fields should help determine whether the workflow continues or stops:

- Required Data Status
- Prompt Status
- Report Readiness
- Warning Notes
- Final Review Status

Recommended rule:

If Final Review Status is Ready to generate report, the workflow can continue.

If Final Review Status is Not ready to generate report, the workflow should stop.

If Final Review Status says Review warnings before generating report, the workflow should stop or require manual review.

## Important Beginner Note

n8n may display spreadsheet data differently than Google Sheets.

Possible differences include:

- Dates may appear in a different format.
- Percentages may appear as decimals.
- Blank cells may appear as empty values.
- Column names may need to be cleaned.
- Numbers may appear as text.
- Some rows may include unexpected empty fields.

This is normal.

The first goal is to see what n8n receives, not to fix everything immediately.

## First n8n Test Questions

When n8n reads the Raw Data tab, answer these questions:

- Did the connection work?
- Did the correct spreadsheet open?
- Did the correct tab open?
- Did the previous week row appear?
- Did the current week row appear?
- Are the metric names readable?
- Are the metric values readable?
- Does engagement rate appear as a percentage or decimal?
- Do the week start dates look correct?
- Are there any blank or confusing fields?

## Recommended First Screenshot

After the first successful n8n test, take a screenshot showing:

- The Manual Trigger node
- The Google Sheets node
- The successful output data

Suggested screenshot filename:

`screenshots/06-n8n-google-sheets-read-test.png`

## Documentation After First n8n Test

After completing the first n8n test, create a file named:

`n8n-first-test-notes.md`

That file should document:

- What workflow was created
- Which Google Sheet was connected
- Which tab was read
- What data appeared in n8n
- Any issues encountered
- How those issues were fixed
- What screenshot was captured
- What the next automation step should be

## Summary

This field mapping plan connects the current spreadsheet prototype to the future n8n workflow.

The safest next technical step is to read the Raw Data tab in n8n and confirm the spreadsheet data appears correctly.

Once that works, the project can move toward reading the final prompt, checking validation status, and eventually sending the prompt to an AI model.
