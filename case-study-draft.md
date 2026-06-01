Case Study Draft: AI Marketing Performance Report Generator
Project Summary

The AI Marketing Performance Report Generator is a spreadsheet-based reporting prototype that turns weekly marketing performance data into a structured AI-ready report workflow.

The project compares previous week and current week metrics, calculates week-over-week changes, generates marketing-friendly prompt language, validates report readiness, flags unusual changes, and prepares a final prompt that could later be sent to an AI model through n8n.

This is the first portfolio project in a six-month learning plan focused on AI automation, marketing technology, analytics, APIs, workflow systems, and business process improvement.

Problem It Solves

Marketing reporting often requires manual work across several steps:

Collecting weekly performance data
Comparing current performance against the previous week
Calculating numeric and percentage changes
Identifying meaningful trends
Writing a clear summary
Making recommendations
Checking whether the data is complete and trustworthy

This project is designed to reduce that manual reporting burden by creating a repeatable workflow that prepares structured data and AI-ready prompts for weekly marketing performance summaries.

Who Would Use It

This type of workflow could be useful for:

Marketing teams
Web teams
Growth teams
Marketing operations teams
Small business owners
Agencies
Analysts preparing weekly reports
Anyone who needs repeatable marketing performance summaries
Current Project Status

The current version is a spreadsheet prototype supported by GitHub documentation.

The project currently includes:

Google Sheet with structured tabs
Raw weekly marketing performance data
Week-over-week comparison formulas
Dynamic AI prompt input
Final AI-ready prompt block
Validation checks
Warning logic for unusual changes
Sample generated report output
JSON sample data
API request and response examples
Testing scenarios
Error-handling notes
Screenshot documentation
Workflow diagram
Formula debugging notes

Automation through n8n has not been connected yet. That will come in a later project phase.

Tools and Technologies Used

Current tools and concepts used:

Google Sheets
GitHub
Markdown documentation
JSON
Basic API concepts
Spreadsheet formulas
Validation logic
AI prompt design
Workflow planning

Planned tools for later phases:

n8n
AI API
Google Docs or email output
Possible scheduled automation
Spreadsheet Structure

The Google Sheet includes these tabs:

Tab	Purpose
Raw Data	Stores weekly marketing performance data
Weekly Comparison	Compares previous week and current week metrics
AI Prompt Input	Converts spreadsheet values into AI-ready prompt language
Generated Report	Stores a sample report output
Notes	Tracks progress, learning notes, JSON practice, and debugging notes
Current Workflow

The current manual spreadsheet workflow is:

Weekly marketing data is entered into the Raw Data tab.
The Weekly Comparison tab pulls values from Raw Data.
The spreadsheet calculates numeric changes and percentage changes.
The AI Prompt Input tab converts metrics into plain-English prompt lines.
Validation checks confirm whether required data is present.
Warning checks flag unusual metric changes.
The Final Review Status determines whether the report is ready.
The Validation Summary is added to the final prompt.
The final prompt can be used to generate a marketing report.
A sample report output is stored in the Generated Report tab.
Workflow Diagram

Current spreadsheet workflow:

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
Final Prompt Block
↓
Generated Report

Planned automated workflow:

Google Sheets
↓
n8n workflow
↓
AI API
↓
Generated Report Output
↓
Google Sheets, Google Docs, or Email

Metrics Used

The prototype currently uses these sample marketing metrics:

Users
Sessions
Engagement rate
Conversions
CTA clicks
Top channel
Top page
Notes
Sample Data

The current sample data compares two weekly reporting periods.

Previous week:

Week start date: 2026-05-04
Users: 1,250
Sessions: 1,600
Engagement rate: 62%
Conversions: 48
CTA clicks: 135
Top channel: Organic Search
Top page: /services

Current week:

Week start date: 2026-05-11
Users: 1,390
Sessions: 1,785
Engagement rate: 66%
Conversions: 57
CTA clicks: 162
Top channel: Organic Search
Top page: /services
Formula Logic

The spreadsheet calculates week-over-week changes for:

Users
Sessions
Engagement rate
Conversions
CTA clicks

The AI Prompt Input tab uses formulas to create plain-English reporting lines.

Example output:

Users increased from 1,250 to 1,390, a 11.20% increase.

For engagement rate, the prompt uses percentage-point wording:

Engagement rate increased from 62% to 66%, a 4.0 percentage-point lift.

Validation Logic

The spreadsheet includes a validation section that checks whether the report is ready to generate.

Current validation checks include:

Required data is present
Final prompt source fields are ready
Report readiness status is calculated
Traffic change warnings are checked
Conversion change warnings are checked
CTA click change warnings are checked
Final Review Status is calculated
Validation Summary is added to the final prompt

Current validation outputs include:

All required metric data present
Missing required metric data
Final prompt source fields ready
Final prompt source fields missing
Ready to generate report
Not ready to generate report
Review warnings before generating report
Warning Logic

The spreadsheet includes warning logic for unusual metric changes.

Current warning checks include:

Users or sessions changing by more than 100%
Conversions changing by more than 50%
CTA clicks changing by more than 50%

This helps prevent the workflow from generating a polished report from data that may need review.

Error Handling

The project includes documentation for possible issues such as:

Missing data
Zero values
Negative values
Very large metric changes
Engagement rate formatting issues
Direction mismatches
AI output that is too vague
AI output that ignores negative metrics
Failed API requests
Empty AI API responses

The goal is to make the future automated workflow more reliable before connecting n8n or an AI API.

JSON and API Learning

The project includes JSON examples that represent the marketing performance data in a structured format.

The repo includes:

sample-report-data.json
test-data-scenarios.json
example-api-request.md
example-api-response.md
api-basics.md

These files show how the spreadsheet data could eventually be passed to an automation workflow or AI model.

Sample API Flow

The planned API flow is:

n8n reads spreadsheet data.
n8n formats the data as a prompt or JSON payload.
n8n sends a request to an AI model.
The AI model returns a generated marketing report.
n8n saves or sends the report.

In this workflow:

The request is the data sent to the AI model.
The response is the report returned by the AI model.
Testing Scenarios

The project includes testing scenarios for realistic reporting situations.

Current scenarios include:

All metrics increase
Users decrease while conversions increase
Traffic increases while engagement drops
Missing data
Metrics staying the same
Unusually large changes

The goal is to avoid only testing the happy path where every metric improves.

Screenshots

The project includes screenshots for:

Raw Data tab
Weekly Comparison tab
AI Prompt Input tab
Generated Report tab
Notes progress log

These screenshots provide visual evidence of the project workflow and spreadsheet prototype.

Sample Output

The sample generated report includes:

Executive Summary
Key Metric Changes
Business Interpretation
Recommended Next Actions

The report explains that users, sessions, engagement rate, conversions, and CTA clicks all increased compared to the previous week.

It also recommends reviewing Organic Search performance and the /services page to understand what contributed to the positive results.

Business Value

This project shows how a marketing reporting process could become more consistent and efficient.

Potential business benefits include:

Reducing manual reporting time
Creating more consistent weekly summaries
Helping teams identify important metric changes
Improving reporting quality through validation checks
Making AI-generated reports safer by checking data readiness first
Creating a repeatable workflow that could later be automated
Challenges and Fixes
Challenge: Creating Dynamic Prompt Lines

The first version of the AI Prompt Input tab used manually written prompt text.

Fix:

The prompt lines were updated to use spreadsheet formulas that pull values from the Weekly Comparison tab.

Challenge: Handling Increases and Decreases

The first dynamic prompt formulas used generic “changed from” language.

Fix:

The formulas were updated with IF logic so they could say increased, decreased, or stayed the same.

Challenge: Avoiding Misleading Reports

The project needed a way to prevent report generation when required data was missing.

Fix:

A validation section was added to check required data, prompt readiness, warnings, and final review status.

Challenge: Circular Reference Error

A #REF! error appeared after adding validation summary into the final prompt.

Cause:

The final prompt formula referenced validation status, while the prompt status formula was checking the final prompt cell.

Fix:

Prompt Status was changed to check source fields instead of checking the final prompt cell.

Corrected logic:

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

What I Learned

This project helped build practice with:

Structuring a portfolio project
Using GitHub for documentation
Creating spreadsheet formulas
Building dynamic prompt text
Reading and writing JSON
Understanding basic API request and response flow
Planning n8n automation
Thinking through validation and error handling
Debugging spreadsheet formula logic
Documenting work as the project develops
What I Would Improve Next

Next improvements include:

Add more screenshots
Add a cleaner workflow or architecture diagram
Improve spreadsheet formatting
Add conditional formatting for validation warnings
Create a separate validation summary area
Start learning how n8n reads Google Sheets data
Build the first simple n8n workflow
Test sending the prompt to an AI model
Save the generated report to Google Sheets or Google Docs
Future Version

A future automated version should:

Read weekly data from Google Sheets.
Check validation status.
Stop if data is missing or warnings need review.
Send a prompt or JSON payload to an AI model.
Generate a structured marketing report.
Save the report to Google Sheets, Google Docs, or email.
Log errors or failed runs.
Include screenshots and documentation for the final workflow.
Portfolio Positioning

This project demonstrates early skills in:

AI workflow design
Marketing technology
Reporting automation
Spreadsheet logic
JSON structure
API concepts
Error handling
Workflow documentation
Business process improvement

The project connects marketing reporting experience with technical workflow-building skills.
