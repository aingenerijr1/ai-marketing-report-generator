# AI Marketing Performance Report Generator

## Project Summary

This project turns weekly marketing or website performance data into a structured AI-ready performance report.

The goal is to create a workflow that can compare weekly metrics, identify key changes, prepare a clean AI prompt, validate the report inputs, flag unusual metric changes, and eventually generate a polished marketing performance summary using automation.

The current version includes a working Google Sheets prototype and a manual n8n test workflow. The n8n workflow can read spreadsheet data, check report readiness, block not-ready runs, log blocked workflow runs, and isolate the final AI-ready prompt for a future AI API step.

The AI API has not been connected yet.

## Problem It Solves

Marketing reporting often requires manually reviewing metrics, calculating week-over-week changes, identifying trends, checking for data quality issues, and writing summaries.

This project is designed to automate part of that process by turning raw performance data into a structured report workflow with validation, warning logic, AI-ready prompt output, readiness checks, and automation logging.

The project is also designed to make future AI-generated reports safer by checking whether the report is ready before sending data to an AI model.

## Planned Tools

- Google Sheets
- n8n
- JavaScript basics
- JSON
- AI API
- GitHub
- Markdown documentation

## Current Status

Day 5 complete: The project now has a working spreadsheet prototype, documentation layer, n8n read tests, readiness gate, false branch message, Automation Log writeback, Final Prompt isolation, and AI API preparation plan.

The n8n workflow can currently:

- Read the Raw Data tab
- Read the AI Prompt Input tab
- Read the Automation Output tab
- Isolate the Final Review Status row
- Check whether the report is ready
- Route not-ready or warning-review cases to a false branch
- Create a false branch status message
- Write blocked workflow runs to the Automation Log tab
- Continue through the ready path
- Isolate the Final Prompt row for a future AI API test

The next technical phase is to prepare and test the AI API step.

The AI API has not been connected yet.

## Day 1 Progress

- Created GitHub repository
- Added starter README documentation
- Created local project folder
- Created Google Sheet with project tabs
- Added sample weekly marketing performance data
- Built first Weekly Comparison tab
- Added week-over-week change formulas
- Created AI Prompt Input tab
- Added sample Generated Report output

## Day 2 Progress

- Cleaned up AI Prompt Input wording
- Created a combined final prompt block for AI reporting
- Tested increase/decrease logic by temporarily changing sample data
- Confirmed the prompt updates dynamically when Raw Data changes
- Created a sample JSON data file to represent the marketing report data in a structured format
- Created a reusable report prompt template
- Created a sample generated report output
- Created a data dictionary to explain the spreadsheet and JSON fields
- Created a workflow plan for the current manual process and future n8n automation
- Created an n8n build checklist
- Created API basics notes
- Created example API request documentation
- Created example API response documentation
- Created testing scenarios documentation
- Created test data scenarios in JSON
- Practiced reading nested JSON objects, arrays, and null values

## Day 3 Progress

- Created error-handling documentation for missing data, zero values, negative values, large changes, vague AI output, failed API requests, and empty AI responses
- Created a spreadsheet validation checklist
- Added a validation section to the AI Prompt Input tab
- Added Required Data Status logic
- Added Prompt Status logic
- Added Report Readiness logic
- Added warning logic for unusual traffic, conversion, and CTA click changes
- Added Final Review Status logic
- Added a Validation Summary line
- Updated the final AI prompt formula to include the validation summary
- Tested missing required data behavior
- Tested large conversion change warning behavior
- Fixed a circular reference issue caused by the final prompt and validation formulas depending on each other
- Documented the formula debugging process and the corrected formula flow
- Created validation logic documentation
- Created formula debugging notes
- Updated the README at the end of the work session

## Day 4 Progress

- Created a local `screenshots` folder
- Took and saved screenshots of the main Google Sheet tabs
- Uploaded screenshots to GitHub
- Created `workflow-diagram.md`
- Created `screenshot-guide.md`
- Created `case-study-draft.md`
- Added a Day 4 progress note in the Google Sheet Notes tab
- Added a screenshots and project evidence section to the case study
- Updated the workflow diagram to show the validation gate
- Created `architecture-notes.md`
- Created `portfolio-summary.md`
- Created `demo-walkthrough.md`
- Created `project-review-checklist.md`
- Created `n8n-readiness-plan.md`
- Created `n8n-field-mapping-plan.md`
- Created `lessons-learned.md`
- Created `interview-talking-points.md`
- Created `repo-file-index.md`
- Reviewed the project documentation files and confirmed the repo organization matches the project checklist
- Practiced walking through the project using the demo walkthrough
- Added an additional Day 4 progress note in the Google Sheet Notes tab
- Saved the first n8n Google Sheets read test as the next step for the next work session

## Day 5 Progress

- Created the first n8n workflow for the project
- Confirmed n8n can read the Raw Data tab from Google Sheets
- Created `n8n-first-test-notes.md`
- Confirmed n8n can read the AI Prompt Input tab
- Created `n8n-ai-prompt-input-test-notes.md`
- Created a new Google Sheet tab named `Automation Output`
- Confirmed n8n can read the Automation Output tab
- Created `n8n-automation-output-test-notes.md`
- Built a readiness check using an If node
- Confirmed n8n can identify when Final Review Status is Ready to generate report
- Created `n8n-readiness-check-test-notes.md`
- Tested the not-ready path by temporarily clearing required data
- Confirmed the workflow does not pass the readiness check when required data is missing
- Created `n8n-not-ready-path-test-notes.md`
- Tested the warning-review path by temporarily increasing conversions
- Confirmed the workflow does not pass the readiness check when warnings need review
- Created `n8n-warning-review-path-test-notes.md`
- Created `n8n-readiness-gate-summary.md`
- Created `n8n-false-branch-plan.md`
- Added a false branch message in n8n
- Confirmed the false branch message works
- Created `n8n-false-branch-test-notes.md`
- Updated `n8n-readiness-plan.md` for false branch progress
- Created `n8n-current-workflow-summary.md`
- Created a new Google Sheet tab named `Automation Log`
- Cleaned up the readiness flow by adding a separate `Find Final Review Status` node
- Confirmed the cleaned-up readiness flow works
- Created `n8n-clean-readiness-flow-test-notes.md`
- Confirmed n8n can write a not-ready blocked run to the Automation Log tab
- Created `n8n-automation-log-test-notes.md`
- Confirmed n8n can write a warning-review blocked run to the Automation Log tab
- Created `n8n-warning-review-log-test-notes.md`
- Updated `n8n-current-workflow-summary.md`
- Created `n8n-logging-summary.md`
- Confirmed the ready path can isolate the Final Prompt row
- Created `n8n-final-prompt-isolation-test-notes.md`
- Created `n8n-ai-api-prep-plan.md`
- Added a Day 5 progress note in the Google Sheet Notes tab
- Corrected screenshot references so the documentation only claims screenshots that actually exist

## Current Spreadsheet Workflow

```text
Raw Data
   ↓
Weekly Comparison
   ↓
AI Prompt Input
   ↓
Automation Output
   ↓
n8n Workflow
```

## Current n8n Workflow

The current n8n workflow is a manual test workflow.

It currently follows this structure:

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
Read Automation Output for Prompt
   ↓
Find Final Prompt
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

## Current Formula Logic

The spreadsheet now uses formulas to:

- Pull weekly performance data from the Raw Data tab
- Compare previous week and current week metrics
- Calculate numeric and percentage changes
- Generate marketing-friendly prompt lines
- Identify whether metrics increased, decreased, or stayed the same
- Use percentage-point wording for engagement rate changes
- Combine individual prompt lines into one final AI-ready prompt block
- Check whether required data is present
- Check whether the final prompt source fields are ready
- Flag unusual metric changes for review
- Calculate a final review status
- Add validation status into the final prompt
- Send key automation fields into the Automation Output tab

## Current Validation Flow

The spreadsheet includes a validation and warning layer.

Current validation flow:

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
   ↓
Automation Output
```

This structure helps prevent circular reference issues and makes the workflow easier to troubleshoot.

## Current n8n Readiness Gate

The n8n workflow uses two steps for readiness checking.

Step 1:

```text
Find Final Review Status
```

This node checks:

```text
Field is equal to Final Review Status
```

Step 2:

```text
Check If Report Is Ready
```

This node checks:

```text
Value is equal to Ready to generate report
```

If the report is ready, the workflow continues through the true branch.

If the report is not ready or warnings need review, the workflow moves through the false branch and writes a row to the Automation Log tab.

## Automation Output Tab

The Automation Output tab was added to make n8n automation cleaner.

It uses a two-column structure:

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

It includes these columns:

| Column | Purpose |
| --- | --- |
| Timestamp | Records when the workflow log row was created |
| Status | Shows whether the report was generated or not generated |
| Message | Explains why the workflow stopped |
| Final Review Status | Stores the spreadsheet readiness status |
| Notes | Adds extra context about the workflow result |

The workflow currently logs blocked runs when:

- Required data is missing
- Warnings need review
- Final Review Status is not Ready to generate report

## Planned Automation Flow

The future workflow will use n8n to connect the spreadsheet data to an AI reporting process.

Planned flow:

```text
Google Sheets
   ↓
n8n workflow
   ↓
Validation and readiness check
   ↓
Final Prompt isolation
   ↓
AI API
   ↓
Generated Report output
   ↓
Google Sheets, Google Docs, or Email
```

## First AI API Goal

The next technical goal is to test sending the Final Prompt value to an AI model.

The first AI API goal should be simple:

```text
Ready path
   ↓
Find Final Prompt
   ↓
AI API node
   ↓
View generated report response
```

The first AI API test should not include:

- Scheduled automation
- Email delivery
- Google Docs creation
- Complex error handling
- Multiple report formats
- Production data

## Project Files

This repo currently includes:

- `README.md`  
  The main project overview and progress log.

- `sample-report-data.json`  
  Structured sample marketing performance data that represents the weekly report input.

- `report-prompt-template.md`  
  A reusable AI prompt template for generating weekly marketing performance summaries.

- `sample-generated-report.md`  
  A sample report output showing what the final AI-generated report should look like.

- `data-dictionary.md`  
  Documentation explaining the fields used in the spreadsheet, JSON sample data, and future automation workflow.

- `workflow-plan.md`  
  A plain-English plan for how data currently moves through the spreadsheet and how it will eventually move through n8n and an AI API.

- `n8n-build-checklist.md`  
  A checklist for building the future n8n automation workflow.

- `api-basics.md`  
  Beginner-friendly notes explaining APIs, requests, responses, GET, POST, JSON, endpoints, payloads, and API key safety.

- `example-api-request.md`  
  A sample API request showing how n8n might send structured marketing data to an AI model.

- `example-api-response.md`  
  A sample API response showing what an AI-generated marketing report could return.

- `testing-scenarios.md`  
  Documentation for testing increases, decreases, no-change situations, missing data, and unusual metric changes.

- `test-data-scenarios.json`  
  Sample JSON test data for multiple reporting scenarios.

- `error-handling-notes.md`  
  Documentation explaining possible data issues, AI output issues, API failures, and expected handling behavior.

- `spreadsheet-validation-checklist.md`  
  A checklist for reviewing required fields, numeric values, report logic, warning signs, and missing data before generating a report.

- `validation-logic-summary.md`  
  A plain-English explanation of the validation formulas, warning logic, final review status, and how this could support n8n later.

- `formula-debugging-notes.md`  
  Notes explaining the circular reference issue, what caused it, how it was fixed, and what was learned from the debugging process.

- `workflow-diagram.md`  
  A workflow diagram showing the current spreadsheet process, validation gate, and planned n8n automation flow.

- `screenshot-guide.md`  
  A guide explaining what each screenshot shows and why it matters.

- `case-study-draft.md`  
  A detailed portfolio case study draft for the project.

- `architecture-notes.md`  
  A plain-English explanation of the project architecture, including the data input layer, calculation layer, prompt and validation layer, report output layer, and planned automation layer.

- `portfolio-summary.md`  
  A shorter project summary for portfolio pages, LinkedIn, or quick project explanations.

- `demo-walkthrough.md`  
  A guided walkthrough for explaining the project in a portfolio review, GitHub walkthrough, or interview.

- `project-review-checklist.md`  
  A checklist for reviewing the spreadsheet prototype, validation logic, screenshots, documentation, and portfolio readiness.

- `n8n-readiness-plan.md`  
  A plan for safely moving through the n8n automation steps.

- `n8n-field-mapping-plan.md`  
  A field mapping guide that explains which spreadsheet tabs and fields n8n should eventually read.

- `lessons-learned.md`  
  Notes summarizing the technical, workflow, debugging, documentation, and business lessons from the project.

- `interview-talking-points.md`  
  Interview-style explanations, project pitches, debugging examples, business value notes, and resume-style bullet drafts.

- `repo-file-index.md`  
  A file index that explains what each major repo file is used for.

- `n8n-first-test-notes.md`  
  Notes documenting the first n8n Google Sheets read test.

- `n8n-ai-prompt-input-test-notes.md`  
  Notes documenting the n8n AI Prompt Input read test.

- `n8n-automation-output-test-notes.md`  
  Notes documenting the n8n Automation Output read test.

- `n8n-readiness-check-test-notes.md`  
  Notes documenting the first readiness check test.

- `n8n-not-ready-path-test-notes.md`  
  Notes documenting the missing-data not-ready path test.

- `n8n-warning-review-path-test-notes.md`  
  Notes documenting the warning-review path test.

- `n8n-readiness-gate-summary.md`  
  A summary of the n8n readiness gate and tested outcomes.

- `n8n-false-branch-plan.md`  
  A plan for handling not-ready and warning-review cases.

- `n8n-false-branch-test-notes.md`  
  Notes documenting the false branch message test.

- `n8n-current-workflow-summary.md`  
  A current summary of the n8n workflow structure and completed tests.

- `n8n-clean-readiness-flow-test-notes.md`  
  Notes documenting the cleaned-up readiness flow.

- `n8n-automation-log-test-notes.md`  
  Notes documenting the Automation Log write test for missing data.

- `n8n-warning-review-log-test-notes.md`  
  Notes documenting the Automation Log write test for warning review status.

- `n8n-logging-summary.md`  
  A summary of the n8n logging layer.

- `n8n-final-prompt-isolation-test-notes.md`  
  Notes documenting the Final Prompt isolation test on the ready path.

- `n8n-ai-api-prep-plan.md`  
  A plan for the future AI API step.

## Screenshot Files

The repo currently includes the following screenshot files:

- `screenshots/01-raw-data.png`  
  Shows the sample weekly marketing performance data used as the project input.

- `screenshots/02-weekly-comparison.png`  
  Shows the week-over-week comparison formulas for users, sessions, engagement rate, conversions, and CTA clicks.

- `screenshots/03-ai-prompt-input.png`  
  Shows the AI-ready prompt structure, validation checks, warning notes, and final review status.

- `screenshots/04-generated-report.png`  
  Shows a sample generated weekly marketing performance summary.

- `screenshots/05-notes-progress-log.png`  
  Shows the project notes and progress log used to document the build process.

- `screenshots/06-n8n-google-sheets-read-test.png`  
  Shows the first successful n8n Google Sheets read test.

- `screenshots/07-n8n-ai-prompt-input-read-test.png`  
  Shows the successful n8n AI Prompt Input read test.

- `screenshots/08-n8n-automation-output-read-test.png`  
  Shows the successful n8n Automation Output read test.

- `screenshots/09-n8n-readiness-check-test.png`  
  Shows the first successful n8n readiness check.

- `screenshots/10-n8n-not-ready-path-test.png`  
  Shows the not-ready path test.

- `screenshots/11-n8n-warning-review-path-test.png`  
  Shows the warning-review path test.

- `screenshots/12-n8n-false-branch-message-test.png`  
  Shows the false branch message test.

- `screenshots/13-n8n-clean-readiness-flow-confirmed.png`  
  Shows the cleaned-up readiness flow with the Final Review Status row isolated.

## Sample Data File

This repo includes a sample JSON file:

`sample-report-data.json`

This file represents the weekly marketing performance data in a structured format that could later be used by n8n, an API request, or an AI reporting workflow.

## Data Dictionary

This repo also includes a data dictionary:

`data-dictionary.md`

The data dictionary explains the meaning of each major field used in the project, including report period fields, metric fields, marketing fields, and spreadsheet tabs.

## API Learning Notes

This project includes beginner API documentation to explain how data may eventually move between Google Sheets, n8n, and an AI model.

The current API notes cover:

- What an API is
- What requests and responses are
- The difference between GET and POST
- How JSON is used in API payloads
- Why API keys should not be committed to GitHub

## Testing Plan

The project includes testing documentation for realistic reporting situations.

Current test scenarios include:

- All metrics increase
- Users decrease while conversions increase
- Traffic increases while engagement drops
- Missing data
- Metrics staying the same
- Unusually large changes
- n8n read tests
- n8n readiness tests
- n8n false branch tests
- n8n Automation Log write tests

The goal is to make sure the final workflow does not only work when every metric improves.

## Validation and Error Handling

The spreadsheet includes a quality-control layer before report generation.

Current validation checks include:

- Required metric data is present
- Final prompt source fields are ready
- Report readiness status is calculated
- Traffic changes are checked for unusual movement
- Conversion changes are checked for unusual movement
- CTA click changes are checked for unusual movement
- Final review status determines whether the report is ready or needs review
- Validation summary is included in the final AI prompt

Current validation outputs include:

- `All required metric data present`
- `Missing required metric data`
- `Final prompt source fields ready`
- `Final prompt source fields missing`
- `Ready to generate report`
- `Not ready to generate report`
- `Review warnings before generating report`

## Formula Debugging Note

During Day 3, a circular reference issue appeared after the validation summary was added into the final prompt.

The issue happened because the final prompt formula referenced validation status while the prompt status formula was checking the final prompt cell.

The formula flow was corrected by changing Prompt Status to check the source fields instead of checking the final combined prompt cell.

Corrected logic flow:

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

This allowed the validation summary to appear in the final prompt without causing `#REF!` errors.

## n8n Testing Summary

The n8n workflow has completed these tests:

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
- Final Prompt isolation test

## Project Evidence

The project currently includes:

- Working Google Sheet prototype
- Sample weekly marketing performance data
- Week-over-week comparison formulas
- Dynamic AI prompt input
- Validation checks
- Warning logic
- Final review status
- Validation summary
- Automation Output tab
- Automation Log tab
- Sample generated report output
- Screenshots
- Workflow diagram
- Case study draft
- Architecture notes
- Portfolio summary
- Demo walkthrough
- Lessons learned
- Interview talking points
- n8n readiness plan
- Field mapping plan
- n8n workflow test notes
- n8n readiness gate summary
- n8n logging summary
- AI API prep plan
- Repo file index

## Current Project Status

The project currently has a working spreadsheet prototype, supporting GitHub documentation, and a manual n8n workflow.

The spreadsheet can compare weekly performance data, calculate changes, generate marketing-friendly prompt lines, validate report readiness, flag unusual metric changes, and create a final prompt block for AI reporting.

The n8n workflow can read spreadsheet data, check whether the report is ready, block not-ready or warning-review runs, write blocked runs to the Automation Log tab, and isolate the Final Prompt row for a future AI API test.

The GitHub repo now includes structured sample data, a reusable prompt template, a sample report output, a data dictionary, workflow planning notes, API learning notes, request and response examples, testing scenario data, error-handling notes, validation documentation, formula debugging notes, screenshots, a workflow diagram, a screenshot guide, a case study draft, architecture notes, portfolio summary, demo walkthrough, n8n readiness planning, field mapping, lessons learned, interview talking points, logging summaries, AI API preparation notes, and a repo file index.

## Upcoming Work

Next steps include:

- Decide which AI API method to use in n8n
- Decide where the AI API credential will be stored
- Keep API keys out of GitHub
- Send the Final Prompt value to an AI model
- View the generated report response inside n8n
- Check whether the response follows the requested structure
- Document the first AI API test
- Add success or failure logging
- Save the generated report output to Google Sheets, Google Docs, or another destination

## Next Session Starting Point

Start with the first AI API test preparation.

The goal for the next session is not to build the full final automation.

The next goal is to choose the safest AI API approach in n8n and prepare a simple test that sends the isolated Final Prompt value to an AI model.

Suggested next workflow layer:

```text
Ready path
   ↓
Find Final Prompt
   ↓
AI API node
   ↓
View generated report response
```

The session is successful when n8n can send the Final Prompt value to an AI model and display the generated response inside n8n.

Generated report saving, email delivery, Google Docs output, and scheduled automation should come later.
