# n8n Logging Summary

## Purpose

This file summarizes the logging layer for the AI Marketing Performance Report Generator n8n workflow.

The goal of the logging layer is to record blocked workflow runs in Google Sheets so the workflow does not fail silently when the report is not ready to generate.

## Logging Overview

The workflow currently uses the Automation Log tab in Google Sheets to record blocked runs.

A blocked run happens when the report should not continue toward future AI generation.

Examples of blocked runs include:

- Required data is missing
- Warning checks need review
- Final Review Status is not Ready to generate report

## Automation Log Tab

The Automation Log tab includes these columns:

| Column | Purpose |
| --- | --- |
| Timestamp | Records when the workflow log row was created |
| Status | Shows whether the report was generated or not generated |
| Message | Explains why the workflow stopped |
| Final Review Status | Stores the spreadsheet readiness status |
| Notes | Adds extra context about the workflow result |

## Current False Branch Message

When the report is not ready, the workflow creates this message:

```text
Report not generated. Review spreadsheet validation status before continuing.
```

This message is created in n8n before the workflow writes a row to the Automation Log tab.

## Current Logging Workflow

```text
Manual Trigger
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

## Logging Test 1: Missing Data

The first logging test used the missing-data path.

Test setup:

- Raw Data!B3 was temporarily cleared.
- Final Review Status changed to Not ready to generate report.
- The workflow ran through the false branch.
- n8n appended a row to the Automation Log tab.
- Raw Data!B3 was restored to 1390.

Result:

Successful.

The workflow logged the blocked run when required data was missing.

## Logging Test 2: Warning Review

The second logging test used the warning-review path.

Test setup:

- Raw Data!E3 was temporarily changed from 57 to 100.
- Final Review Status changed to Review warnings before generating report.
- The workflow ran through the false branch.
- n8n appended a row to the Automation Log tab.
- Raw Data!E3 was restored to 57.

Result:

Successful.

The workflow logged the blocked run when warning review was needed.

## What the Logging Layer Proves

The logging layer proves that:

- n8n can append rows to Google Sheets.
- The workflow can record blocked runs.
- Missing-data cases can be logged.
- Warning-review cases can be logged.
- The workflow provides traceability before future AI generation.
- The Automation Log tab can be used to review what happened after a workflow run.

## Why This Matters

This matters because automation workflows should be understandable when they stop.

If the workflow does not generate a report, the user should be able to see why.

The Automation Log tab makes the workflow easier to debug, explain, and improve.

## Related Documentation

Related files:

- `n8n-automation-log-test-notes.md`
- `n8n-warning-review-log-test-notes.md`
- `n8n-current-workflow-summary.md`
- `n8n-false-branch-test-notes.md`
- `n8n-readiness-gate-summary.md`

## What Is Not Built Yet

The logging layer does not yet include:

- Separate custom messages for missing data versus warning review
- A generated report success log
- AI API response logging
- Email or Google Docs delivery logging
- Scheduled run logging

Those can be added later.

## Recommended Next Step

The next recommended step is to prepare the ready path for a future AI API test.

Before connecting the AI API, the workflow should isolate the Final Prompt row from the Automation Output tab and confirm the prompt text is available inside n8n.

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

## Main Takeaway

The logging layer is working.

The workflow now records blocked runs when the report is not ready or warnings need review.

This makes the automation safer and easier to debug before connecting the workflow to an AI model.
