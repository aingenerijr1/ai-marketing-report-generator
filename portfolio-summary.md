# Portfolio Summary: AI Marketing Performance Report Generator

## Project Overview

The AI Marketing Performance Report Generator is a spreadsheet-based reporting prototype that prepares weekly marketing performance data for an AI-generated summary report.

The project compares previous week and current week metrics, calculates week-over-week changes, creates AI-ready prompt language, validates report readiness, flags unusual metric changes, and prepares a final prompt that could later be sent to an AI model through n8n.

## Problem Solved

Weekly marketing reporting can be repetitive and time-consuming.

A marketer or analyst often has to collect performance data, compare metrics, identify trends, write a summary, make recommendations, and check whether the data is complete.

This project creates a more structured workflow for that process.

Instead of starting from scratch each week, the system prepares the data, comparison logic, validation checks, and AI-ready reporting prompt in one repeatable flow.

## Who This Is For

This type of workflow could support:

- Marketing teams
- Web teams
- Growth teams
- Marketing operations teams
- Small business owners
- Agencies
- Analysts preparing weekly reports

## Tools and Concepts Used

Current tools and concepts used:

- Google Sheets
- GitHub
- Markdown documentation
- Spreadsheet formulas
- AI prompt design
- Validation logic
- Warning logic
- JSON examples
- API request and response planning
- Workflow documentation

Planned future tools:

- n8n
- AI API
- Google Docs or email output

## How It Works

The current version uses a Google Sheet with five main tabs:

- Raw Data
- Weekly Comparison
- AI Prompt Input
- Generated Report
- Notes

The workflow moves through these stages:

```text
Raw Data
   ↓
Weekly Comparison
   ↓
AI Prompt Input
   ↓
Validation Checks
   ↓
Warning Notes
   ↓
Final Review Status
   ↓
Final Prompt
   ↓
Generated Report
```

## Key Features

The current prototype includes:

- Sample weekly marketing data
- Week-over-week comparison formulas
- Dynamic prompt lines for AI report generation
- Required data validation
- Warning checks for unusual metric changes
- Final review status
- Validation summary added to the final prompt
- Sample generated report output
- JSON sample data
- API request and response examples
- Testing scenarios
- Screenshot documentation
- Workflow diagram
- Case study draft
- Architecture notes

## Sample Metrics

The project currently tracks:

- Users
- Sessions
- Engagement rate
- Conversions
- CTA clicks
- Top channel
- Top page
- Notes

## Business Value

This project shows how a manual reporting process can become more structured, consistent, and automation-ready.

Potential business benefits include:

- Reducing manual reporting time
- Creating more consistent weekly summaries
- Helping teams identify important metric changes
- Improving report quality through validation checks
- Preventing AI-generated reports from using incomplete data
- Creating a workflow that can later be automated through n8n

## Technical Value

This project demonstrates early skills in:

- Spreadsheet logic
- Reporting workflows
- AI prompt preparation
- Validation logic
- Error handling planning
- JSON structure
- API concepts
- Automation planning
- GitHub documentation
- Business process improvement

## Current Status

The current version is a working spreadsheet prototype supported by GitHub documentation.

Automation has not been connected yet.

The next technical phase is to connect Google Sheets to n8n, read the spreadsheet data, check report readiness, send the final prompt or JSON payload to an AI API, and save the generated report output.

## Future Improvements

Future improvements include:

- Connect Google Sheets to n8n
- Build the first simple n8n workflow
- Send the final prompt to an AI model
- Save the generated report automatically
- Add email or Google Docs output
- Add conditional formatting for warning checks
- Add stronger error handling
- Add screenshots of the n8n workflow

## Portfolio Positioning

This project connects marketing reporting experience with technical workflow-building skills.

It shows the ability to understand a business reporting problem, structure the data, create validation logic, prepare AI-ready prompts, document the workflow, and plan a future automation layer.
