# n8n AI API Prep Plan

## Purpose

This file prepares the AI API step for the AI Marketing Performance Report Generator n8n workflow.

The goal is to define what the workflow should send to an AI model, what response it should expect, and what should happen if the request fails.

The AI API should not be connected until the prompt, readiness check, and output plan are clear.

## Current Workflow Status

The current n8n workflow can:

- Read the Raw Data tab.
- Read the AI Prompt Input tab.
- Read the Automation Output tab.
- Isolate the Final Review Status row.
- Check whether the report is ready.
- Route not-ready or warning-review cases to a false branch.
- Write blocked workflow runs to the Automation Log tab.
- Continue through the ready path.
- Isolate the Final Prompt row.

The workflow does not yet call an AI API.

## Current Ready Path

The ready path currently works like this:

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
Read Automation Output for Prompt
   ↓
Find Final Prompt
```

## AI API Input

The AI API should eventually receive the value from the Final Prompt row.

Source:

Automation Output tab

Field:

Final Prompt

Value:

Full AI-ready prompt text

## Prompt Content

The Final Prompt currently includes:

- Report context
- Performance data
- Users change
- Sessions change
- Engagement rate change
- Conversions change
- CTA clicks change
- Key insight
- Recommended action
- Validation summary
- Report formatting instructions

## AI API Goal

The AI model should generate a weekly marketing performance report.

The report should include:

- Executive Summary
- Key Metric Changes
- Business Interpretation
- Recommended Next Actions

## Expected AI Response

The expected response should be a structured written report.

Example structure:

```text
## Executive Summary

[Short summary of weekly performance]

## Key Metric Changes

[Bullet list or short explanation of metric changes]

## Business Interpretation

[Plain-English explanation of what the changes may mean]

## Recommended Next Actions

[Suggested next steps based on the data]
```

## Future AI API Node

The future AI API step may use one of these options:

- n8n OpenAI node
- HTTP Request node connected to an AI API
- Another AI model integration supported by n8n

The exact option can be chosen later.

## Important API Safety Notes

Before connecting the AI API:

- Do not expose API keys in public GitHub files.
- Do not paste API keys into README files.
- Use n8n credentials or environment variables when possible.
- Do not send private or sensitive client data.
- Use sample data for testing.
- Keep the first test simple.

## First AI API Test Goal

The first AI API test should be simple.

Goal:

Send the final prompt to an AI model and receive a generated report response.

The first AI API test should not include:

- Scheduled automation
- Email delivery
- Google Docs creation
- Complex error handling
- Multiple report formats
- Production data

## Suggested First AI Workflow

```text
Ready Path
   ↓
Find Final Prompt
   ↓
AI API Node
   ↓
View Generated Report Output
```

## What to Check During First AI Test

When the AI response comes back, check:

- Did the API request succeed?
- Did the AI model receive the full prompt?
- Did the response include all requested sections?
- Is the report clear and useful?
- Did the report follow the requested structure?
- Did the report avoid making unsupported claims?
- Did the response mention validation status appropriately?

## Possible AI API Issues

Possible issues include:

- API credential setup problems
- Prompt text not passing correctly
- AI response too vague
- AI response missing requested sections
- AI response adding unsupported assumptions
- AI response too long or too short
- API rate limit or usage error
- Empty response
- Failed request

These should be documented during testing.

## Future Error Handling

Later, the workflow should handle AI API failures.

Possible failure behavior:

```text
AI API request fails
   ↓
Create error message
   ↓
Append error row to Automation Log
   ↓
Stop workflow
```

Possible error log message:

```text
Report generation failed because the AI API request did not complete successfully.
```

## Future Success Logging

Later, the workflow should also log successful report generation.

Possible success log row:

| Field | Example Value |
| --- | --- |
| Timestamp | Current run timestamp |
| Status | Generated |
| Message | Report generated successfully. |
| Final Review Status | Ready to generate report |
| Notes | AI report output was created from the final prompt. |

## Future Report Saving

After the AI response works, the generated report should be saved somewhere.

Possible destinations:

- Generated Report tab in Google Sheets
- Google Docs
- Email
- Markdown file
- Notion page
- Airtable record

The simplest first destination is probably the Generated Report tab in Google Sheets.

## Recommended Build Order

Recommended build order from here:

1. Document the AI API preparation plan.
2. Decide which AI node or API method to use.
3. Confirm where the API key or credential will be stored.
4. Send the Final Prompt value to the AI model.
5. View the AI response inside n8n.
6. Check whether the response follows the requested structure.
7. Document the first AI API test.
8. Add success or failure logging.
9. Save the generated report output.

## What Not to Do Yet

Do not schedule the workflow yet.

Do not use private client data.

Do not add email delivery yet.

Do not add Google Docs output yet.

Do not overbuild error handling before the first simple AI test works.

The next technical win should be sending the final prompt to an AI model and viewing the response.

## Main Takeaway

The workflow is ready to prepare for the AI API step, but the AI API should be added carefully.

The current priority is to keep the workflow safe:

1. Validate the data.
2. Continue only when ready.
3. Isolate the final prompt.
4. Send the prompt to AI.
5. Review the response.
6. Save or log the result later.
