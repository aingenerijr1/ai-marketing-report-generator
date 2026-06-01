# Interview Talking Points: AI Marketing Performance Report Generator

## Purpose

This file captures clear interview-style talking points for the AI Marketing Performance Report Generator.

The goal is to explain the project in a confident, honest, and practical way without overstating what has been built.

The current version is a spreadsheet prototype with documentation, validation logic, screenshots, JSON examples, API planning notes, and a future n8n automation plan.

n8n and the AI API have not been connected yet.

## Short Project Pitch

I built a spreadsheet-based AI marketing reporting prototype that prepares weekly marketing performance data for an AI-generated report.

The project compares current week and previous week metrics, calculates week-over-week changes, creates AI-ready prompt language, validates whether the report is ready, flags unusual metric changes, and prepares a final prompt that could later be sent to an AI model through n8n.

## Slightly Longer Project Explanation

This project solves a common marketing operations problem: weekly reporting can be repetitive, manual, and inconsistent.

I created a Google Sheets workflow that organizes weekly marketing metrics, compares current performance against the previous week, turns the results into plain-English report language, and checks whether the data is complete before a final report is generated.

The project is currently a working spreadsheet prototype. The next technical phase is to connect the sheet to n8n, read the data, check report readiness, and eventually send the final prompt to an AI API.

## Problem It Solves

The project is designed to reduce manual work in weekly marketing reporting.

The manual process usually includes:

- Collecting weekly performance data
- Comparing current week against previous week
- Calculating metric changes
- Identifying trends
- Writing a summary
- Making recommendations
- Checking whether the data is complete

This project makes that process more structured and repeatable.

## Who Would Use It

This workflow could be useful for:

- Marketing teams
- Web teams
- Growth teams
- Marketing operations teams
- Small business owners
- Agencies
- Analysts preparing weekly reports

## Tools and Concepts Used

The current project uses:

- Google Sheets
- Spreadsheet formulas
- GitHub
- Markdown documentation
- JSON examples
- API request and response planning
- AI prompt design
- Validation logic
- Warning logic
- Workflow documentation

Planned future tools include:

- n8n
- AI API
- Google Docs, Google Sheets, or email output

## How the Current Workflow Works

The current workflow moves through these stages:

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
Validation Summary
   ↓
Final Prompt
   ↓
Generated Report
```

The Raw Data tab stores the source weekly metrics.

The Weekly Comparison tab calculates changes between the previous week and current week.

The AI Prompt Input tab turns the comparison data into plain-English prompt language.

The validation section checks whether the report is ready.

The Generated Report tab stores a sample report output.

## Key Metrics Used

The project currently tracks:

- Users
- Sessions
- Engagement rate
- Conversions
- CTA clicks
- Top channel
- Top page
- Notes

## Strongest Technical Feature

The strongest technical feature is the validation gate.

The project does not just prepare a prompt. It checks whether the source data is complete and whether unusual metric changes need review before the report moves forward.

The validation logic includes:

- Required Data Status
- Prompt Status
- Report Readiness
- Traffic Change Warning
- Conversion Change Warning
- CTA Click Change Warning
- Final Review Status
- Validation Summary

This helps prevent a polished AI-generated report from being created from incomplete or questionable data.

## Example of Validation Thinking

If required data is missing, the report should not be generated.

If conversions or CTA clicks change unusually, the workflow should flag that for review.

The goal is not just to automate reporting.

The goal is to make the reporting workflow safer, clearer, and more reliable before automation is added.

## Debugging Example

One issue I ran into was a circular reference error in Google Sheets.

The final prompt included the validation summary, but the prompt status formula was checking the final prompt cell. That created a loop and caused a #REF! error.

I fixed it by changing Prompt Status so it checked the source fields instead of checking the final prompt cell.

The corrected logic became:

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

This made the workflow cleaner and easier to troubleshoot.

## Business Value

The business value of this project is that it makes weekly marketing reporting more consistent and repeatable.

Potential benefits include:

- Reduced manual reporting time
- More consistent weekly summaries
- Better visibility into performance changes
- Safer AI-generated reports through validation checks
- Clearer recommendations for marketing teams
- A foundation for future reporting automation

## What This Project Demonstrates

This project demonstrates early skills in:

- Marketing reporting
- Spreadsheet logic
- Week-over-week analysis
- AI prompt preparation
- Validation logic
- Warning and error-handling planning
- JSON structure
- API planning
- Workflow documentation
- Automation planning
- Business process improvement

## How I Would Explain the AI Part

The AI part of this project is not just a one-off prompt.

The project prepares structured input for a future AI model.

The spreadsheet creates the report context, performance data, key insight, recommended action, and validation summary. That final prompt can later be sent through n8n to an AI API.

The goal is to use AI as one step in a structured workflow, not as a replacement for data review.

## How I Would Explain the Automation Plan

The current version is the spreadsheet prototype.

The next version will use n8n to read the Google Sheet.

The first n8n goal is simple:

Connect n8n to Google Sheets and read the Raw Data tab.

After that works, the workflow can be expanded to read the final prompt, check Final Review Status, send the prompt to an AI API, and save the generated report output.

## What Is Not Built Yet

The following parts are not built yet:

- n8n connection
- AI API request
- Automated report generation
- Automated saving to Google Sheets, Google Docs, or email
- n8n workflow screenshots
- Full automated demo

This is important to say honestly if discussing the project.

## What I Would Build Next

The next technical step is to connect n8n to Google Sheets and confirm that n8n can read the Raw Data tab.

The safe build order is:

1. Connect n8n to Google Sheets.
2. Read rows from the Raw Data tab.
3. Confirm previous week and current week data appear correctly.
4. Check how dates and percentages appear inside n8n.
5. Document the first successful read test.
6. Then plan the AI API step.

## If Asked: Why Did You Start With Google Sheets?

I started with Google Sheets because it is a practical way to prototype a reporting workflow before adding automation.

It let me build and test the reporting logic, comparison formulas, validation checks, and prompt structure before connecting n8n or an AI API.

This made the project easier to debug and explain.

## If Asked: Why Not Build the Whole Automation First?

I did not want to automate a messy process.

I started by making the manual workflow clear first.

Once the data structure, validation logic, and prompt format were working, the project became much easier to prepare for automation.

## If Asked: What Was the Hardest Part?

One of the hardest parts was getting the validation logic right without creating circular references.

I had to think through the order of the logic so the final prompt could include the validation summary without the validation formulas depending on the final prompt itself.

## If Asked: What Did You Learn?

I learned that automation projects need a clear workflow before adding tools.

I also practiced spreadsheet formulas, validation logic, JSON structure, API planning, GitHub documentation, and explaining a technical system in business terms.

## If Asked: How Does This Connect to Marketing Technology?

This project connects directly to marketing technology because it focuses on reporting, performance data, workflow design, AI-assisted summaries, validation, and automation planning.

It is the kind of workflow a marketing operations, growth, analytics, or web team could use to make recurring reporting more efficient.

## If Asked: How Does This Connect to Software Development?

This project connects to software development because it uses structured data, logic, validation, debugging, documentation, and planned API-based automation.

Even though the current prototype is spreadsheet-based, the workflow is organized like a small system with inputs, processing, validation, outputs, and future integration points.

## Resume-Style Project Bullet Drafts

Possible project bullets:

- Built a spreadsheet-based AI marketing reporting prototype that compares weekly performance metrics, creates AI-ready prompt language, validates report readiness, and documents a future n8n automation path.
- Designed validation and warning logic to prevent report generation when required marketing data is missing or unusual metric changes need review.
- Created project documentation including workflow diagrams, architecture notes, JSON examples, API planning notes, testing scenarios, screenshots, and a portfolio case study draft.
- Planned an n8n automation workflow to read Google Sheets data, check report readiness, send a prompt to an AI API, and save the generated report output.

These bullets should be updated later after the n8n and AI API pieces are actually built.

## Main Interview Takeaway

The main takeaway is:

I can take a real marketing reporting problem, structure the data, build comparison and validation logic, prepare AI-ready inputs, document the workflow, and plan the next automation layer.

This project shows both business understanding and technical workflow thinking.
