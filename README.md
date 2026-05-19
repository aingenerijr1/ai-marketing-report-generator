# AI Marketing Performance Report Generator

## Project Summary
This project turns weekly marketing or website performance data into a structured AI-ready performance report.

The goal is to create a workflow that can compare weekly metrics, identify key changes, prepare a clean AI prompt, and eventually generate a polished marketing performance summary using automation.

## Problem It Solves
Marketing reporting often requires manually reviewing metrics, calculating week-over-week changes, identifying trends, and writing summaries.

This project is designed to automate part of that process by turning raw performance data into a structured report workflow.

## Planned Tools
- Google Sheets
- n8n
- JavaScript basics
- JSON
- AI API
- GitHub

## Current Status
Day 2: Spreadsheet prototype, dynamic prompt logic, JSON sample data, API documentation, workflow planning, testing scenarios, and GitHub documentation are in progress.

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

## Current AI Prompt Flow
Raw Data -> Weekly Comparison -> AI Prompt Input -> Final Prompt Block -> Generated Report

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

## Current Project Status
The project currently has a working spreadsheet prototype and supporting GitHub documentation.

The spreadsheet can compare weekly performance data, calculate changes, generate marketing-friendly prompt lines, and create a final prompt block for AI reporting.

The GitHub repo now includes structured sample data, a reusable prompt template, a sample report output, a data dictionary, workflow planning notes, API learning notes, request and response examples, and testing scenario data.

## Upcoming Work
Next steps include:
- Review the current documentation for clarity
- Add error-handling notes for missing data, bad inputs, and failed API responses
- Continue learning basic JSON structure
- Learn how n8n workflows use spreadsheet or JSON data
- Connect spreadsheet data to an automation workflow
- Test an AI-generated report output
- Add screenshots and workflow documentation later in the project

## Portfolio Goal
This project is part of a larger AI, automation, and marketing technology learning plan.

The final version should demonstrate the ability to structure marketing data, prepare AI-ready inputs, use automation tools, understand basic API request and response flow, test realistic reporting scenarios, and explain the business value of the workflow.
