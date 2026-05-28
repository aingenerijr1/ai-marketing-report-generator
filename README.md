# AI Marketing Performance Report Generator

## Project Summary
This project turns weekly marketing or website performance data into a structured AI-ready performance report.

The goal is to create a workflow that can compare weekly metrics, identify key changes, prepare a clean AI prompt, validate the report inputs, and eventually generate a polished marketing performance summary using automation.

## Problem It Solves
Marketing reporting often requires manually reviewing metrics, calculating week-over-week changes, identifying trends, checking for data quality issues, and writing summaries.

This project is designed to automate part of that process by turning raw performance data into a structured report workflow with validation, warning logic, and AI-ready prompt output.

## Planned Tools
- Google Sheets
- n8n
- JavaScript basics
- JSON
- AI API
- GitHub

## Current Status
Day 3: Spreadsheet prototype, dynamic prompt logic, JSON sample data, API documentation, workflow planning, testing scenarios, validation logic, error-handling documentation, and GitHub documentation are in progress.

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

## Current Workflow Draft
Raw Data -> Weekly Comparison -> AI Prompt Input -> Final Prompt Block -> Generated Report

## Current Formula Logic
The spreadsheet now uses formulas to:
- Pull weekly performance data from the Raw Data tab
- Compare previous week and current week metrics
- Calculate numeric and percentage changes
- Generate marketing-friendly prompt lines
- Identify whether metrics increased, decreased, or stayed the same
- Combine individual prompt lines into one final AI-ready prompt block
- Check whether required data is present
- Check whether the final prompt source fields are ready
- Flag unusual metric changes for review
- Add validation status into the final prompt

## Current AI Prompt Flow
Raw Data -> Weekly Comparison -> AI Prompt Input -> Validation Summary -> Final Prompt Block -> Generated Report

## Current Validation Flow
The spreadsheet now includes a basic validation and warning layer.

Current validation flow:

```text
Raw Data
   ↓
Weekly Comparison calculations
   ↓
AI Prompt Input validation checks
   ↓
Warning checks
   ↓
Final Review Status
   ↓
Validation Summary
   ↓
Final Prompt Block
```

## Planned Automation Flow
The future workflow will use n8n to connect the spreadsheet data to an AI reporting process.

Planned flow:

```text
Google Sheets
   ↓
Weekly Comparison formulas
   ↓
AI Prompt Input
   ↓
Validation checks
   ↓
n8n workflow
   ↓
AI API
   ↓
Generated Report output
```

## Project Files
This repo currently includes:

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

The goal is to make sure the final workflow does not only work when every metric improves.

## Validation and Error Handling
The spreadsheet now includes a basic quality-control layer before report generation.

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

## Current Project Status
The project currently has a working spreadsheet prototype and supporting GitHub documentation.

The spreadsheet can compare weekly performance data, calculate changes, generate marketing-friendly prompt lines, validate report readiness, flag unusual metric changes, and create a final prompt block for AI reporting.

The GitHub repo now includes structured sample data, a reusable prompt template, a sample report output, a data dictionary, workflow planning notes, API learning notes, request and response examples, testing scenario data, error-handling notes, validation documentation, and formula debugging notes.

## Upcoming Work
Next steps include:
- Review the current documentation for clarity
- Add screenshots of the Google Sheet and key tabs
- Add a simple workflow diagram or architecture diagram
- Continue learning how n8n workflows use spreadsheet or JSON data
- Create or log into n8n
- Start
