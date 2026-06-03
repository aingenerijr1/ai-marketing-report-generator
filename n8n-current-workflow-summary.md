# n8n Current Workflow Summary

## Purpose

This file summarizes the current state of the n8n workflow for the AI Marketing Performance Report Generator.

The goal is to provide a simple snapshot of what the workflow currently does, what has been tested, and what still needs to be built.

## Current Workflow Name

AI Marketing Report Generator - Google Sheets Read Test

## Current Workflow Type

Manual test workflow

The workflow is currently run manually for testing.

It is not scheduled yet.

## Current Workflow Goal

The current goal of the workflow is to prove that n8n can:

- Connect to Google Sheets
- Read source marketing data
- Read prompt and validation fields
- Check whether the report is ready
- Route not-ready cases to a false branch message
- Write blocked workflow runs to the Automation Log tab

The workflow does not generate a report yet.

The workflow does not call an AI API yet.

## Current Workflow Nodes

The current workflow includes:

- Manual Trigger
- Google Sheets node for Raw Data
- Google Sheets node for AI Prompt Input
- Google Sheets node for Automation Output
- Find Final Review Status node
- Check If Report Is Ready node
- Edit Fields node for false branch message
- Google Sheets Append Row node for Automation Log

## Current Workflow Structure

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
True Branch: Report is ready
   ↓
Future AI API step

False Branch:
   ↓
Edit Fields
   ↓
Create status_message
   ↓
Append Row to Automation Log
```

## Readiness Check Flow

The workflow now uses two steps for readiness checking.

## Step 1: Find Final Review Status

The first If node is named:

Find Final Review Status

It checks:

```text
Field is equal to Final Review Status
```

Purpose:

This node isolates the one row from the Automation Output tab that contains the final readiness status.

## Step 2: Check If Report Is Ready

The second If node is named:

Check If Report Is Ready

It checks:

```text
Value is equal to Ready to generate report
```

Purpose:

This node checks whether the isolated Final Review Status row says the report is ready.

## False Branch Message

When the report is not ready, the false branch creates this message:

```text
Report not generated. Review spreadsheet validation status before continuing.
```

This message is created with the Edit Fields node.

## Automation Log Writeback

The workflow now writes blocked workflow runs to the Automation Log tab in Google Sheets.

The Automation Log tab includes these columns:

| Column | Purpose |
| --- | --- |
| Timestamp | Records when the workflow log row was created |
| Status | Shows whether the report was generated or not generated |
| Message | Explains why the workflow stopped |
| Final Review Status | Stores the spreadsheet readiness status |
| Notes | Adds extra context about the workflow result |

## Automation Log Row Example

A blocked workflow run writes a row like this:

| Field | Example Value |
| --- | --- |
| Timestamp | Current n8n run timestamp |
| Status | Not Generated |
| Message | Report not generated. Review spreadsheet validation status before continuing. |
| Final Review Status | Not ready to generate report |
| Notes | Workflow stopped because report was not ready or needed review. |

## Current Spreadsheet Source

The workflow reads from the Google Sheet:

AI Marketing Performance Report Generator

The workflow has tested these tabs:

- Raw Data
- AI Prompt Input
- Automation Output
- Automation Log

## Automation Output Tab

The Automation Output tab was added to make n8n automation cleaner.

It uses a simple two-column structure:

| Field | Value |
| --- | --- |
| Final Prompt | Full AI-ready prompt |
| Final Review Status | Ready to generate report |
| Validation Summary | Validation status summary |
| Warning Notes | Traffic, conversion, and CTA click warning status |
| Report Readiness | Report readiness status |
| Required Data Status | Required data status |
| Prompt Status | Prompt source field status |
| Traffic Change Warning | Traffic warning status |
| Conversion Change Warning | Conversion warning status |
| CTA Click Change Warning | CTA click warning status |

## Automation Log Tab

The Automation Log tab was added so n8n can record blocked workflow runs.

It currently supports logging when:

- Required data is missing
- Warnings need review
- Final Review Status is not Ready to generate report

## Tests Completed

The following n8n tests are complete:

- Raw Data read test
- AI Prompt Input read test
- Automation Output read test
- Ready path test
- Not-ready path test
- Warning review path test
- False branch message test
- Clean readiness flow test
- Automation Log write test for missing data
- Automation Log write test for warning review status

## Screenshot Evidence

The current n8n workflow is supported by these screenshots:

- `screenshots/06-n8n-google-sheets-read-test.png`
- `screenshots/07-n8n-ai-prompt-input-read-test.png`
- `screenshots/08-n8n-automation-output-read-test.png`
- `screenshots/09-n8n-readiness-check-test.png`
- `screenshots/10-n8n-not-ready-path-test.png`
- `screenshots/11-n8n-warning-review-path-test.png`
- `screenshots/12-n8n-false-branch-message-test.png`
- `screenshots/13-n8n-clean-readiness-flow-confirmed.png`

Additional recommended screenshots:

- `screenshots/14-n8n-automation-log-write-test.png`
- `screenshots/15-n8n-warning-review-log-test.png`

## Related Documentation Files

Related n8n documentation files include:

- `n8n-first-test-notes.md`
- `n8n-ai-prompt-input-test-notes.md`
- `n8n-automation-output-test-notes.md`
- `n8n-readiness-check-test-notes.md`
- `n8n-not-ready-path-test-notes.md`
- `n8n-warning-review-path-test-notes.md`
- `n8n-readiness-gate-summary.md`
- `n8n-false-branch-plan.md`
- `n8n-false-branch-test-notes.md`
- `n8n-readiness-plan.md`
- `n8n-field-mapping-plan.md`
- `n8n-current-workflow-summary.md`
- `n8n-clean-readiness-flow-test-notes.md`
- `n8n-automation-log-test-notes.md`
- `n8n-warning-review-log-test-notes.md`

## What Works Now

The workflow currently works for:

- Reading source spreadsheet data
- Reading prompt-related spreadsheet data
- Reading clean automation output fields
- Isolating the Final Review Status row
- Checking whether the report is ready
- Passing the workflow only when the report is ready
- Blocking missing-data cases
- Blocking warning-review cases
- Creating a false branch status message
- Writing missing-data blocked runs to Automation Log
- Writing warning-review blocked runs to Automation Log

## What Is Not Built Yet

The workflow does not yet include:

- AI API connection
- Sending the final prompt to an AI model
- Saving generated report output
- Sending email or Google Docs output
- Scheduled automation
- Separate false branch messages for missing data versus warning review
- True branch report generation logic

## Recommended Next Step

The next recommended technical step is to prepare the true branch for a future AI API test.

Before calling an AI model, the workflow should identify and isolate the Final Prompt row from the Automation Output tab.

The next safe build layer should be:

```text
Ready path
   ↓
Find Final Prompt
   ↓
Confirm final prompt value is available
   ↓
Stop before AI API
```

The AI API should still wait until the workflow can clearly isolate the final prompt text.

## Main Takeaway

The current n8n workflow has a working validation and logging gate.

It can read the spreadsheet, check report readiness, block not-ready or warning-review cases, and write blocked runs to the Automation Log tab.

This creates a safer foundation before connecting the workflow to an AI API.
