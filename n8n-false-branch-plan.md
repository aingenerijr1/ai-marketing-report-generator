# n8n False Branch Plan

## Purpose

This file explains what should happen when the AI Marketing Performance Report Generator n8n workflow does not pass the readiness check.

The goal is to define the false branch behavior before connecting the workflow to an AI API.

The workflow should not send anything to an AI model unless the spreadsheet says the report is ready.

## Current Readiness Check

The workflow currently reads the Automation Output tab from Google Sheets.

The key readiness field is:

Final Review Status

The n8n If node checks:

```text
Field is equal to Final Review Status
AND
Value is equal to Ready to generate report
```

If both conditions are true, the workflow can continue.

If either condition is false, the workflow should stop or require review.

## Why the False Branch Matters

The false branch matters because not every report should continue to AI generation.

The report should not continue when:

- Required data is missing
- Prompt source fields are incomplete
- Warning notes need review
- Final Review Status is not ready
- The spreadsheet output is unclear

Without a false branch plan, the workflow could fail silently or become confusing.

## Current False Branch Situation

Right now, the If node sends non-ready rows to the false branch.

The workflow does not yet do anything useful with those false branch results.

That is acceptable for the current test phase, but the workflow should eventually handle false branch outcomes clearly.

## Possible False Branch Outcomes

The workflow may need to handle two main false branch cases.

## Case 1: Not Ready

This happens when required data is missing or prompt source fields are incomplete.

Example status:

Not ready to generate report

Recommended behavior:

- Stop the workflow
- Do not call the AI API
- Log that required data is missing
- Optionally write a review note back to Google Sheets later

## Case 2: Review Warnings

This happens when all required data exists, but one or more metric changes are unusually large.

Example status:

Review warnings before generating report

Recommended behavior:

- Stop the workflow
- Do not call the AI API
- Log that warnings need review
- Optionally send a review notice later
- Optionally write a warning status back to Google Sheets later

## Simple False Branch Version

The first false branch version should stay simple.

Recommended first version:

```text
If Final Review Status is not Ready to generate report
   ↓
Stop workflow
   ↓
Do not send prompt to AI
```

This is enough for the first version.

The workflow does not need email, Slack, Google Docs, or advanced error handling yet.

## Future False Branch Version

A future version could add a clearer review process.

Possible future workflow:

```text
If Final Review Status is not Ready to generate report
   ↓
Create review message
   ↓
Save review message to Google Sheets
   ↓
Stop workflow
```

Possible review message:

```text
Report was not generated because the current validation status is not ready. Please review the Automation Output tab before running the workflow again.
```

## Future Warning Review Version

A future warning-specific branch could handle warning review separately.

Possible future workflow:

```text
If Final Review Status is Review warnings before generating report
   ↓
Create warning review message
   ↓
Save warning review message to Google Sheets
   ↓
Stop workflow
```

Possible warning review message:

```text
Report was not generated because one or more warning checks need review. Please review traffic, conversion, and CTA click warning notes before generating the report.
```

## Future Not-Ready Version

A future not-ready branch could handle missing data separately.

Possible future workflow:

```text
If Final Review Status is Not ready to generate report
   ↓
Create missing data message
   ↓
Save missing data message to Google Sheets
   ↓
Stop workflow
```

Possible missing data message:

```text
Report was not generated because required metric data is missing. Please complete the required fields in the Raw Data tab before running the workflow again.
```

## Recommended Next Build Step

The next build step should be simple.

Recommended next n8n test:

Add a basic false branch message using a Set node.

The Set node can create a simple field such as:

```text
status_message = Report not generated. Review spreadsheet validation status before continuing.
```

This would prove that the false branch can create a clear output message.

## What Not to Add Yet

Do not add the AI API yet.

Do not add email output yet.

Do not add Google Docs output yet.

Do not add scheduled automation yet.

Do not add multiple branches until the simple false branch message works.

The next goal is only to make the false branch easier to understand.

## Safe Build Order

Recommended build order:

1. Create the false branch plan.
2. Add a Set node to the false branch.
3. Create a simple review message.
4. Test the false branch with missing data.
5. Test the false branch with warning review status.
6. Restore test data after each test.
7. Document the false branch test.
8. Then decide whether to move toward the AI API step.

## Current Status

Completed:

- Raw Data read test
- AI Prompt Input read test
- Automation Output read test
- Ready path test
- Not-ready path test
- Warning review path test
- Readiness gate summary

Not completed:

- False branch message
- False branch test notes
- AI API connection
- Automated report generation
- Automated report saving
- Scheduled automation

## Main Takeaway

The false branch should protect the workflow from generating a report when the spreadsheet says the data is not ready or warnings need review.

The simplest next step is to add a basic false branch message before connecting anything to AI.
