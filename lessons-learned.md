# Lessons Learned: AI Marketing Performance Report Generator

## Purpose

This file documents the key lessons learned while building the AI Marketing Performance Report Generator.

The goal is to capture technical, workflow, debugging, documentation, and business lessons from the current spreadsheet prototype before moving into the n8n automation phase.

## Project Phase

Current phase:

Spreadsheet prototype and documentation layer

The project currently uses Google Sheets, spreadsheet formulas, validation logic, AI-ready prompt planning, JSON examples, API planning notes, screenshots, and GitHub documentation.

n8n and the AI API have not been connected yet.

## Lesson 1: Start With the Workflow Before the Automation

One important lesson from this project is that automation should not be added before the workflow is clear.

Before connecting n8n or an AI API, the project needed a clear manual process:

- Enter weekly data
- Compare current week against previous week
- Calculate metric changes
- Create AI-ready prompt language
- Validate the data
- Flag unusual changes
- Prepare a final prompt
- Store a sample report output

This made the system easier to understand before adding automation.

## Lesson 2: Spreadsheet Structure Matters

The project became easier to build once the Google Sheet was separated into clear tabs.

The main tabs are:

- Raw Data
- Weekly Comparison
- AI Prompt Input
- Generated Report
- Notes

Each tab has a specific purpose.

This structure makes the workflow easier to debug, explain, and eventually connect to n8n.

## Lesson 3: Raw Data Should Stay Separate From Calculations

Keeping the Raw Data tab separate from the Weekly Comparison tab made the project cleaner.

The Raw Data tab stores the source information.

The Weekly Comparison tab handles calculations.

This separation helps avoid confusion because source data and calculated outputs are not mixed together.

## Lesson 4: AI Prompts Work Better With Structured Inputs

The AI Prompt Input tab showed that AI prompts are stronger when the input is organized.

Instead of sending random data to an AI model, the spreadsheet prepares:

- Report context
- Performance data
- Key insight
- Recommended action
- Validation summary

This makes the future AI output more likely to be clear, consistent, and useful.

## Lesson 5: Dynamic Prompt Lines Reduce Manual Writing

The project uses formulas to create prompt lines automatically.

This reduces the amount of manual writing needed each week.

The prompt lines can describe whether metrics:

- Increased
- Decreased
- Stayed the same

This makes the workflow more repeatable.

## Lesson 6: Engagement Rate Needs Different Wording

Engagement rate should not be described the same way as count-based metrics like users, sessions, conversions, or CTA clicks.

For engagement rate, percentage-point wording is clearer.

Example:

Engagement rate increased from 62% to 66%, a 4.0 percentage-point lift.

This is more accurate than only describing the relative percent change.

## Lesson 7: Validation Is Important Before AI Generation

A major lesson from this project is that AI-generated reports should not be created from incomplete or questionable data.

The validation section helps check:

- Whether required data is present
- Whether prompt source fields are ready
- Whether the report is ready to generate
- Whether unusual changes need review
- Whether the final review status is ready

This makes the future automated workflow safer.

## Lesson 8: Warning Logic Helps Prevent Misleading Reports

The project includes warning logic for unusual metric changes.

Current warning checks include:

- Users or sessions changing by more than 100%
- Conversions changing by more than 50%
- CTA clicks changing by more than 50%

The warning logic does not mean the data is automatically wrong.

It means the data should be reviewed before generating a polished report.

This is useful because AI can make bad or incomplete data sound more confident than it should.

## Lesson 9: Circular References Can Break Spreadsheet Logic

A circular reference issue happened when the final prompt included the validation summary while the prompt status was checking the final prompt cell.

The issue created a #REF! error.

The fix was to change the logic so Prompt Status checked the source fields instead of checking the final prompt cell.

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

This made the validation flow cleaner and easier to troubleshoot.

## Lesson 10: Testing Should Include More Than the Happy Path

The project tested more than one perfect scenario.

Tests included:

- Missing data
- Restored data
- Unusual conversion changes
- Restored conversion values
- Final status returning to ready

This helped confirm that the validation and warning logic worked.

Future tests should include more negative and edge cases before automation is added.

## Lesson 11: Documentation Is Part of the Build

This project showed that documentation is not something to save until the end.

Documentation helped clarify:

- What the project does
- Why it matters
- How the workflow works
- What files exist
- What data is used
- What tests were completed
- What still needs to be built

The documentation also makes the project easier to explain as a portfolio piece.

## Lesson 12: Screenshots Provide Portfolio Evidence

Screenshots help prove that the project exists and show how it works.

The current screenshots show:

- Raw Data
- Weekly Comparison
- AI Prompt Input
- Generated Report
- Notes progress log

These screenshots make the project more understandable for someone viewing the GitHub repo or portfolio case study.

## Lesson 13: JSON and API Planning Help Prepare for Automation

The JSON and API notes helped connect the spreadsheet prototype to the future automation phase.

The project includes:

- Sample report data JSON
- Test data scenarios
- Example API request
- Example API response
- API basics notes

These files show how spreadsheet data could eventually move into n8n and then to an AI model.

## Lesson 14: The First n8n Step Should Be Small

The next technical phase should not try to automate everything at once.

The first n8n goal should be:

Connect n8n to Google Sheets and read the Raw Data tab.

The first n8n goal should not be:

Connect Google Sheets, validation logic, AI API, and report output all at the same time.

A smaller first step will make the automation easier to debug.

## Lesson 15: The Project Is Stronger When Framed as a Business System

This project is not just a spreadsheet.

It is a small business reporting system.

It connects:

- Marketing performance data
- Week-over-week analysis
- AI prompt preparation
- Validation checks
- Warning logic
- Report generation planning
- Documentation
- Future automation

This framing makes the project more useful for marketing technology, AI automation, analytics, and operations roles.

## Skills Practiced

This project helped build practice with:

- Google Sheets structure
- Spreadsheet formulas
- Week-over-week metric comparison
- AI prompt design
- Validation logic
- Warning logic
- JSON structure
- API request and response planning
- GitHub documentation
- Markdown files
- Screenshot documentation
- Workflow planning
- Debugging spreadsheet logic
- Portfolio project explanation

## What Still Needs Practice

Areas that still need more practice include:

- Connecting n8n to Google Sheets
- Reading spreadsheet data inside n8n
- Understanding n8n output data
- Building conditional logic in n8n
- Sending data to an AI API
- Handling failed API requests
- Saving generated output automatically
- Documenting automation screenshots
- Explaining the full automated workflow

## Main Takeaway

The biggest takeaway from this phase is that a good automation project starts with a clear process.

Before using n8n or an AI API, the project needed clean data, comparison logic, validation checks, warning rules, and documentation.

That foundation will make the next automation phase easier to build, test, explain, and improve.
