# Demo Walkthrough: AI Marketing Performance Report Generator

## Purpose

This file explains how to walk someone through the AI Marketing Performance Report Generator as a portfolio project.

The goal is to make the project easy to explain in an interview, portfolio review, or GitHub walkthrough.

This walkthrough focuses on the current spreadsheet prototype and the planned automation path.

## Short Project Explanation

The AI Marketing Performance Report Generator is a spreadsheet-based prototype that prepares weekly marketing performance data for an AI-generated report.

It compares current week and previous week metrics, calculates changes, creates AI-ready prompt language, checks whether the data is complete, flags unusual metric changes, and prepares a final prompt that could later be sent to an AI model through n8n.

## Demo Script

Here is a simple way to explain the project:

This project solves a common marketing operations problem: weekly reporting is repetitive, manual, and easy to make inconsistent.

I built a spreadsheet workflow that takes weekly marketing performance data, compares it against the previous week, turns the results into plain-English prompt lines, validates whether the report is ready, and prepares a final AI-ready prompt.

The current version is a working spreadsheet prototype. The next version will connect the spreadsheet to n8n and an AI API so the report can be generated and saved automatically.

## Step 1: Show the Raw Data Tab

Start with the Raw Data tab.

Explain:

The Raw Data tab stores weekly marketing performance data for two reporting periods:

- Previous week
- Current week

The sample data includes:

- Users
- Sessions
- Engagement rate
- Conversions
- CTA clicks
- Top channel
- Top page
- Notes

Demo talking point:

This tab is the source data layer. The rest of the workflow depends on this data being complete and accurate.

## Step 2: Show the Weekly Comparison Tab

Move to the Weekly Comparison tab.

Explain:

This tab compares the previous week against the current week.

It calculates:

- Previous value
- Current value
- Numeric change
- Percent change

Demo talking point:

Instead of manually comparing numbers each week, the spreadsheet calculates the week-over-week changes automatically.

## Step 3: Show the AI Prompt Input Tab

Move to the AI Prompt Input tab.

Explain:

This tab converts the comparison data into plain-English reporting lines that can be used in an AI-generated report.

Example:

Users increased from 1,250 to 1,390, an 11.20% increase.

For engagement rate, the spreadsheet uses percentage-point wording so the report is more accurate.

Demo talking point:

This is where the spreadsheet starts turning raw numbers into language that an AI model can use.

## Step 4: Show the Validation Section

Stay on the AI Prompt Input tab and show the validation fields.

Explain:

The project includes validation checks before the final prompt is used.

Current validation fields include:

- Required Data Status
- Prompt Status
- Report Readiness
- Warning Notes
- Final Review Status
- Validation Summary

Demo talking point:

This validation layer helps prevent the workflow from generating a polished report when the source data is missing or needs review.

## Step 5: Show the Warning Notes

Show the warning logic.

Explain:

The spreadsheet flags unusual metric changes before report generation.

Current warning checks include:

- Users or sessions changing by more than 100%
- Conversions changing by more than 50%
- CTA clicks changing by more than 50%

Demo talking point:

The warning logic does not automatically mean the data is wrong. It means the data should be reviewed before creating a final report.

## Step 6: Show the Final Prompt

Show the final AI-ready prompt block.

Explain:

The final prompt combines:

- Report context
- Performance data
- Key insight
- Recommended action
- Validation summary

Demo talking point:

This final prompt is designed to be sent to an AI model in a later version of the project.

## Step 7: Show the Generated Report Tab

Move to the Generated Report tab.

Explain:

This tab stores a sample report output.

The sample report includes:

- Weekly Marketing Performance Summary
- Metric changes
- Business interpretation
- Recommended next action

Demo talking point:

This shows what the final generated report could look like once the workflow is connected to n8n and an AI API.

## Step 8: Show the GitHub Documentation

Open the GitHub repo and explain the supporting documentation.

Important files include:

- README.md
- case-study-draft.md
- workflow-diagram.md
- screenshot-guide.md
- architecture-notes.md
- portfolio-summary.md
- validation-logic-summary.md
- formula-debugging-notes.md
- spreadsheet-validation-checklist.md
- error-handling-notes.md
- sample-report-data.json
- test-data-scenarios.json
- example-api-request.md
- example-api-response.md

Demo talking point:

The documentation shows the project was not just built visually. It was planned, tested, debugged, and documented as a portfolio project.

## Step 9: Explain the Planned Automation

Explain the future version.

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

Demo talking point:

The current version prepares the logic and structure. The next technical step is connecting Google Sheets to n8n so the workflow can read the data and send the final prompt to an AI model.

## Interview-Style Explanation

If asked to explain the project in an interview, use this version:

I built a spreadsheet-based AI marketing reporting prototype that takes weekly performance data, compares it against the previous week, creates AI-ready prompt language, validates whether the data is ready, and prepares a final reporting prompt.

The project uses Google Sheets formulas, validation logic, warning checks, JSON examples, API planning, and GitHub documentation.

The current version is a prototype, and the next version will connect to n8n and an AI API to generate the report automatically.

## Skills This Project Demonstrates

This project demonstrates:

- Marketing reporting knowledge
- Spreadsheet logic
- Week-over-week performance analysis
- AI prompt preparation
- Validation logic
- Warning and error-handling planning
- JSON structure
- API request and response planning
- Workflow documentation
- Automation planning
- Business process improvement

## Strongest Project Talking Points

The strongest parts of this project are:

- It solves a real reporting problem.
- It uses realistic marketing metrics.
- It includes validation before report generation.
- It documents error handling and testing scenarios.
- It prepares the workflow for future n8n automation.
- It connects marketing experience with technical system-building.

## Current Status

The current version is a documented spreadsheet prototype.

Completed so far:

- Raw Data tab
- Weekly Comparison tab
- AI Prompt Input tab
- Generated Report tab
- Notes tab
- Validation logic
- Warning logic
- Sample generated report
- Screenshots
- Workflow diagram
- Case study draft
- Architecture notes
- Portfolio summary
- JSON examples
- API planning notes
- Testing scenarios
- Error-handling documentation

Not completed yet:

- n8n connection
- AI API connection
- Automated report generation
- Automated saving or emailing of report output

## Next Technical Step

The next technical phase is to start learning how n8n reads Google Sheets data.

The first automation goal should be simple:

Use n8n to read data from the Google Sheet.

The first goal is not to connect the AI API immediately.

The safer build order is:

1. Confirm n8n can access the Google Sheet.
2. Read the current week and previous week rows.
3. View the data inside n8n.
4. Confirm the data structure.
5. Then plan the AI API step.

## Done When

This file is complete when it gives a clear project walkthrough that can be used to explain the spreadsheet, validation logic, documentation, and planned automation path.
