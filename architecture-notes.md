# Architecture Notes: AI Marketing Performance Report Generator

## Purpose

This file explains the current architecture of the AI Marketing Performance Report Generator and how the project is planned to evolve into an automated reporting workflow.

The current version is a spreadsheet-based prototype. It uses Google Sheets to organize weekly marketing performance data, compare current and previous week metrics, generate AI-ready prompt language, validate the data, flag unusual changes, and prepare a final prompt for report generation.

The future version will connect this spreadsheet workflow to n8n and an AI API so the report generation process can become more automated.

## Architecture Overview

The project is structured around four main layers:

1. Data input layer
2. Calculation layer
3. Prompt and validation layer
4. Report output layer

Each layer has a specific role in the reporting process.

```text
Raw Data
   ↓
Weekly Comparison
   ↓
AI Prompt Input
   ↓
Validation and Warning Logic
   ↓
Final Prompt
   ↓
Generated Report
```

This structure keeps the workflow organized and makes it easier to test, debug, document, and eventually automate.

## Current System Components

## 1. Data Input Layer

The Raw Data tab is the starting point of the workflow.

It stores the weekly marketing performance data for two reporting periods:

- Previous week
- Current week

The current sample metrics include:

- Users
- Sessions
- Engagement rate
- Conversions
- CTA clicks
- Top channel
- Top page
- Notes

This layer is important because the rest of the workflow depends on clean and complete source data.

If the Raw Data tab is missing important values, the final report should not be generated until the data is reviewed.

## 2. Calculation Layer

The Weekly Comparison tab compares the previous week against the current week.

It calculates:

- Current value
- Previous value
- Numeric change
- Percent change

The compared metrics include:

- Users
- Sessions
- Engagement rate
- Conversions
- CTA clicks

This layer turns raw weekly data into performance trends.

Instead of only showing isolated numbers, the spreadsheet can explain whether performance increased, decreased, or stayed the same.

## 3. Prompt and Validation Layer

The AI Prompt Input tab is the main logic layer of the project.

It turns the comparison data into plain-English lines that can be used in an AI-generated report.

Example prompt line:

Users increased from 1,250 to 1,390, an 11.20% increase.

For engagement rate, the prompt uses percentage-point wording instead of treating the change like a normal count-based metric.

Example engagement rate line:

Engagement rate increased from 62% to 66%, a 4.0 percentage-point lift.

This layer also includes the validation logic that checks whether the report is ready to generate.

## Validation Gate

The validation gate checks the source fields and report readiness before the final prompt is used.

Current validation fields include:

- Required Data Status
- Prompt Status
- Report Readiness
- Traffic Change Warning
- Conversion Change Warning
- CTA Click Change Warning
- Final Review Status
- Validation Summary

The validation logic follows this structure:

```text
Source fields
   ↓
Prompt Status
   ↓
Report Readiness
   ↓
Final Review Status
   ↓
Validation Summary
   ↓
Final Prompt
```

This structure helps avoid circular reference errors and makes the workflow easier to troubleshoot.

The validation gate helps prevent a polished report from being generated when:

- Required data is missing
- Prompt source fields are incomplete
- Traffic changes look unusually large
- Conversion changes need review
- CTA click changes need review
- The final review status is not ready

## Warning Logic

The spreadsheet includes warning checks for unusual metric changes.

Current warning checks include:

- Users or sessions changing by more than 100%
- Conversions changing by more than 50%
- CTA clicks changing by more than 50%

These warnings do not automatically mean the data is wrong.

They mean the data should be reviewed before generating a final report.

This is important because an AI-generated report can sound polished even when the input data has problems. The warning logic adds a basic safety check before report generation.

## 4. Report Output Layer

The Generated Report tab stores a sample report output.

The sample report includes:

- Weekly Marketing Performance Summary
- Metric changes
- Business interpretation
- Recommended next action

This output shows what the final AI-generated report could look like once the spreadsheet is connected to n8n and an AI API.

In the current version, the report output is manually generated and pasted into the spreadsheet.

In the future version, the report output should be generated automatically.

## Planned Automation Architecture

The future version of this project will use n8n to connect the spreadsheet to an AI model.

Planned automated workflow:

```text
Google Sheets
   ↓
n8n
   ↓
Validation Check
   ↓
AI API
   ↓
Generated Report
   ↓
Google Sheets, Google Docs, or Email
```

## Planned Automation Steps

The planned automation should work like this:

1. n8n reads the weekly marketing performance data from Google Sheets.
2. n8n checks whether the report is ready to generate.
3. If required data is missing, the workflow stops or sends a review notice.
4. If warning notes are present, the workflow stops or asks for review.
5. If the report is ready, n8n sends the prompt or JSON payload to an AI model.
6. The AI model generates a structured weekly marketing performance report.
7. n8n saves the generated report to Google Sheets, Google Docs, or email.

## Data Flow

The project data currently moves through the system in this order:

```text
Raw metric values
   ↓
Week-over-week calculations
   ↓
Plain-English prompt lines
   ↓
Validation checks
   ↓
Warning checks
   ↓
Final review status
   ↓
Validation summary
   ↓
Final AI-ready prompt
   ↓
Generated report output
```

This flow makes the reporting process easier to understand and easier to automate later.

## Why This Architecture Matters

This architecture matters because it separates the reporting process into clear stages.

Each stage has a specific job:

- Raw Data stores the source information.
- Weekly Comparison calculates changes.
- AI Prompt Input prepares the report language.
- Validation checks confirm readiness.
- Warning notes flag unusual changes.
- Final Review Status controls whether the report should move forward.
- Final Prompt prepares the AI-ready output.
- Generated Report stores the final report example.

This makes the system easier to test and explain.

It also makes the project stronger as a portfolio piece because it shows more than a simple spreadsheet. It shows workflow thinking, validation logic, automation planning, and business process improvement.

## Current Limitations

The current version is still a prototype.

Current limitations include:

- The data is entered manually.
- The report is not generated automatically yet.
- n8n is not connected yet.
- The AI API is not connected yet.
- The report output is currently a sample.
- Warning logic is basic and could be expanded.
- Validation logic is useful but still early.

These limitations are expected for the current stage of the project.

The main goal right now is to document the system clearly before connecting automation.

## Future Improvements

Future improvements could include:

- Connect Google Sheets to n8n.
- Build a simple n8n workflow that reads spreadsheet data.
- Send the final prompt to an AI API.
- Save the generated report automatically.
- Add email or Google Docs output.
- Add stronger warning rules.
- Add conditional formatting in Google Sheets.
- Add better error handling for failed API requests.
- Add a workflow run log.
- Add screenshots of the completed n8n workflow.

## Portfolio Explanation

This project demonstrates how a manual marketing reporting process can be turned into a structured, automation-ready workflow.

It shows early skills in:

- Marketing technology
- Spreadsheet logic
- Reporting workflows
- AI prompt preparation
- JSON and API planning
- Validation logic
- Error handling
- Automation planning
- Workflow documentation
- Business process improvement

The current architecture is intentionally simple, but it creates a strong foundation for the future automated version.
