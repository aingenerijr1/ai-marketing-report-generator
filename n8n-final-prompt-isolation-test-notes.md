# n8n Final Prompt Isolation Test Notes

## Purpose

This file documents the Final Prompt isolation test for the AI Marketing Performance Report Generator n8n workflow.

The goal of this test was to confirm that n8n can find and isolate the Final Prompt row from the Automation Output tab after the report passes the readiness check.

This is important because the Final Prompt value is the text that will eventually be sent to an AI model.

## Test Summary

The Final Prompt isolation test successfully confirmed that n8n can locate the Final Prompt row from the Automation Output tab.

The workflow first checks whether the report is ready.

When the report is ready, the workflow reads the Automation Output tab again and uses an If node to find the Final Prompt row.

The true branch returned one item containing the final AI-ready prompt.

## Workflow Name

AI Marketing Report Generator - Google Sheets Read Test

## Workflow Type

Manual test workflow

The workflow is still a manual test workflow.

It is not scheduled yet.

## Workflow Nodes Used

The test workflow used:

- Manual Trigger
- Raw Data Sheet node
- AI Prompt Input Sheet node
- Automation Output Sheet node
- Find Final Review Status node
- Check If Report Is Ready node
- Read Automation Output for Prompt node
- Find Final Prompt node

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
True Branch
   ↓
Read Automation Output for Prompt
   ↓
Find Final Prompt
```

## Final Prompt Isolation Logic

The Find Final Prompt node checks:

```text
Field is equal to Final Prompt
```

Expected result:

Only the row where the Field value is Final Prompt should continue through the true branch.

## Test Result

Result:

Successful.

The Find Final Prompt true branch returned one item.

That item contained:

- Field: Final Prompt
- Value: Full AI-ready prompt text

## Screenshot Evidence

Recommended screenshot file:

`screenshots/16-n8n-final-prompt-isolation-test.png`

This screenshot should show the Find Final Prompt node returning one item with the Final Prompt row.

## What This Test Proves

This test proves that:

- n8n can read the Automation Output tab.
- n8n can isolate the Final Review Status row.
- n8n can check whether the report is ready.
- n8n can continue through the ready path.
- n8n can read the Automation Output tab again on the ready path.
- n8n can isolate the Final Prompt row.
- n8n can access the final AI-ready prompt text.

## Why This Matters

This matters because the workflow should only prepare the final prompt after the report is ready.

The project now has a safer sequence:

1. Read spreadsheet output.
2. Check readiness.
3. Continue only if ready.
4. Find the final AI prompt.
5. Prepare for a future AI API step.

This prevents the workflow from sending incomplete or questionable data to an AI model.

## What Was Not Tested Yet

This test did not include:

- AI API connection
- Sending the final prompt to an AI model
- Receiving generated report output
- Saving generated report output
- Email or Google Docs delivery
- Scheduled automation

Those steps should be added later in small layers.

## Current Automation Status

Completed:

- n8n can read the Raw Data tab.
- n8n can read the AI Prompt Input tab.
- n8n can read the Automation Output tab.
- n8n can isolate Final Review Status.
- n8n can check whether the report is ready.
- n8n can route blocked runs to a false branch.
- n8n can log blocked runs in the Automation Log tab.
- n8n can isolate the Final Prompt row after the report passes readiness.

Not completed:

- AI API request
- Automated report generation
- Automated report saving
- Email or Google Docs output
- Scheduled workflow
- Success logging after generated report output

## Recommended Next Step

The next recommended step is to create a simple AI API preparation plan.

The workflow should not connect to the AI API until the request structure is clear.

A useful next documentation file would be:

`n8n-ai-api-prep-plan.md`

That file should explain:

- What prompt text will be sent
- Which node will send the request
- What output format is expected
- What should happen if the AI request fails
- Where the generated report should be saved

## Main Takeaway

The Final Prompt isolation test was successful.

The ready path can now find the exact final prompt text that will eventually be sent to an AI model.

This is the correct checkpoint before preparing the AI API step.
