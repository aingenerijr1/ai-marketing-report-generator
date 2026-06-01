# Repo File Index: AI Marketing Performance Report Generator

## Purpose

This file explains what each file in the AI Marketing Performance Report Generator repo is used for.

The goal is to make the project easier to review, explain, and maintain as it grows from a spreadsheet prototype into a future n8n automation workflow.

## Main Project Files

### README.md

The main entry point for the project.

This file should explain the project goal, problem solved, tools used, current status, setup notes, screenshots, and progress updates.

The README should be updated at the end of each work session.

### case-study-draft.md

A detailed portfolio case study draft.

This file explains the project summary, problem, workflow, tools, validation logic, business value, challenges, lessons learned, and future improvements.

### portfolio-summary.md

A shorter project summary for portfolio pages, LinkedIn, or quick project explanations.

This file is easier to skim than the full case study.

### demo-walkthrough.md

A guided walkthrough for explaining the project in a portfolio review, GitHub walkthrough, or interview.

This file explains how to present the Raw Data tab, Weekly Comparison tab, AI Prompt Input tab, validation section, generated report, documentation, and planned automation.

### interview-talking-points.md

A collection of interview-style explanations for the project.

This file includes short project pitches, business value, technical explanations, debugging examples, future plans, and resume-style bullet drafts.

## Workflow and Architecture Files

### workflow-diagram.md

Explains the current spreadsheet workflow and planned automated workflow.

This file includes Mermaid diagrams showing how data moves from Raw Data to Weekly Comparison, AI Prompt Input, validation checks, final prompt, and generated report.

### workflow-plan.md

Outlines the original planned workflow for the project.

This file helps explain the intended project flow from spreadsheet input to AI-generated reporting output.

### architecture-notes.md

Explains the project architecture in plain English.

This file breaks the system into layers:

- Data input layer
- Calculation layer
- Prompt and validation layer
- Report output layer
- Future automation layer

### n8n-readiness-plan.md

Prepares the project for the first n8n automation step.

This file explains that the first n8n goal is to connect n8n to Google Sheets and read data before adding AI or report generation.

### n8n-field-mapping-plan.md

Maps the Google Sheet tabs and fields to the data n8n will eventually read.

This file explains which fields come from Raw Data, Weekly Comparison, and AI Prompt Input.

### n8n-build-checklist.md

A checklist for building the future n8n workflow.

This file should be used later when the project moves from spreadsheet prototype into automation.

## Data and API Files

### sample-report-data.json

A JSON example of the sample weekly marketing performance data.

This file shows how spreadsheet data could be represented as structured data for automation or an API request.

### test-data-scenarios.json

A JSON file with multiple test scenarios.

This file helps test different reporting situations, including missing data, metric increases, metric decreases, and unusual changes.

### api-basics.md

Beginner notes about APIs.

This file explains basic API concepts that will be useful when the project connects to an AI model.

### example-api-request.md

An example of what an API request might look like.

This file helps explain what data could be sent from n8n to an AI model.

### example-api-response.md

An example of what an API response might look like.

This file helps explain what the AI model might return after receiving the report prompt or payload.

## Prompt and Report Files

### report-prompt-template.md

A reusable prompt template for generating a weekly marketing performance report.

This file helps separate the prompt structure from the spreadsheet logic.

### sample-generated-report.md

A sample report output generated from the project data.

This file shows what the final AI-generated marketing performance summary could look like.

## Validation, Testing, and Debugging Files

### spreadsheet-validation-checklist.md

A checklist for reviewing spreadsheet validation logic.

This file helps confirm that required data, prompt readiness, warning notes, and final review status are working correctly.

### validation-logic-summary.md

A plain-English explanation of the validation logic.

This file explains how the project checks whether the report is ready to generate.

### formula-debugging-notes.md

Notes about spreadsheet formula issues and fixes.

This file includes the circular reference issue and the corrected validation logic flow.

### error-handling-notes.md

Notes about possible errors and edge cases.

This file helps prepare the future automation workflow to handle missing data, unusual values, failed API requests, and unclear AI output.

### testing-scenarios.md

A list of testing scenarios for the reporting workflow.

This file helps confirm the project works beyond the happy path.

### project-review-checklist.md

A final review checklist for the current documentation and spreadsheet prototype phase.

This file helps confirm the repo is organized before moving into the n8n automation phase.

## Documentation and Evidence Files

### screenshot-guide.md

Explains what each screenshot shows and why it matters.

This file helps reviewers understand the visual evidence in the screenshots folder.

### lessons-learned.md

Documents the main lessons learned during the spreadsheet prototype and documentation phase.

This file includes technical, workflow, debugging, documentation, and business lessons.

### repo-file-index.md

This file.

It acts as the map for the project repo and explains the purpose of each major file.

## Screenshot Files

### screenshots/01-raw-data.png

Shows the Raw Data tab with sample weekly marketing performance data.

### screenshots/02-weekly-comparison.png

Shows the Weekly Comparison tab with week-over-week comparison formulas.

### screenshots/03-ai-prompt-input.png

Shows the AI Prompt Input tab with prompt lines, validation checks, warning notes, and final review status.

### screenshots/04-generated-report.png

Shows the Generated Report tab with a sample weekly marketing performance report.

### screenshots/05-notes-progress-log.png

Shows the Notes tab with project progress notes and learning documentation.

## Current Repo Status

The repo currently documents a spreadsheet-based prototype.

The project includes:

- Source data
- Weekly comparison logic
- AI-ready prompt preparation
- Validation checks
- Warning logic
- Sample generated report output
- JSON examples
- API planning notes
- Screenshots
- Case study documentation
- Workflow diagrams
- Architecture notes
- Interview talking points
- n8n readiness planning

## Not Built Yet

The following items are not built yet:

- n8n workflow connection
- Google Sheets connection inside n8n
- AI API request
- Automated report generation
- Automated saving to Google Sheets, Google Docs, or email
- n8n workflow screenshots
- Final automated demo

These items belong to the next technical phase.

## How to Use This Index

Use this file when reviewing the repo or explaining the project.

Suggested review order:

1. Start with `README.md`.
2. Review `portfolio-summary.md` for the short project explanation.
3. Review `case-study-draft.md` for the detailed project story.
4. Review `workflow-diagram.md` and `architecture-notes.md` for the system structure.
5. Review `screenshot-guide.md` and the screenshots folder for visual evidence.
6. Review `validation-logic-summary.md` and `formula-debugging-notes.md` for the strongest technical logic.
7. Review `n8n-readiness-plan.md` and `n8n-field-mapping-plan.md` for the future automation path.
8. Review `interview-talking-points.md` before using the project in career materials.

## Main Takeaway

This repo is more than a collection of files.

It documents the process of turning a manual marketing reporting workflow into a structured, validation-ready, automation-ready system.

The current version proves the spreadsheet logic and documentation layer.

The next phase will prove the automation layer.
