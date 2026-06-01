# Project Review Checklist: AI Marketing Performance Report Generator

## Purpose

This checklist is used to review the current state of the AI Marketing Performance Report Generator before moving into the next technical phase.

The goal is to confirm that the spreadsheet prototype, documentation, screenshots, workflow notes, and portfolio materials are organized enough to support the future n8n automation phase.

## Current Project Phase

Current phase:

Spreadsheet prototype and documentation layer

The project is not connected to n8n yet.

The current goal is to make sure the existing spreadsheet workflow is clear, tested, documented, and easy to explain before adding automation.

## Spreadsheet Review

Review the Google Sheet and confirm the following items are complete.

- Raw Data tab exists.
- Weekly Comparison tab exists.
- AI Prompt Input tab exists.
- Generated Report tab exists.
- Notes tab exists.
- Raw Data contains previous week and current week sample data.
- Weekly Comparison pulls values from Raw Data.
- Weekly Comparison calculates numeric changes.
- Weekly Comparison calculates percent changes.
- AI Prompt Input creates dynamic prompt lines.
- AI Prompt Input uses increased, decreased, or stayed the same wording.
- Engagement rate uses percentage-point wording.
- Final prompt includes report context.
- Final prompt includes performance data.
- Final prompt includes key insight.
- Final prompt includes recommended action.
- Final prompt includes validation summary.
- Generated Report contains a sample output.
- Notes tab includes project progress notes.

## Validation Review

Review the validation section and confirm the following items are complete.

- Required Data Status exists.
- Prompt Status exists.
- Report Readiness exists.
- Traffic Change Warning exists.
- Conversion Change Warning exists.
- CTA Click Change Warning exists.
- Final Review Status exists.
- Validation Summary exists.
- Missing data test was completed.
- Warning logic test was completed.
- Final Review Status returns to ready when data is restored.
- Circular reference issue was fixed.
- Validation logic checks source fields instead of checking the final prompt cell.

## Screenshot Review

Confirm that the screenshots folder includes these files.

- `screenshots/01-raw-data.png`
- `screenshots/02-weekly-comparison.png`
- `screenshots/03-ai-prompt-input.png`
- `screenshots/04-generated-report.png`
- `screenshots/05-notes-progress-log.png`

Confirm that the screenshots show:

- Source data
- Weekly comparison formulas
- AI prompt input
- Validation checks
- Warning notes
- Generated report output
- Progress notes

## GitHub Documentation Review

Confirm that the repo includes the following documentation files.

- `README.md`
- `sample-report-data.json`
- `report-prompt-template.md`
- `sample-generated-report.md`
- `data-dictionary.md`
- `workflow-plan.md`
- `n8n-build-checklist.md`
- `api-basics.md`
- `example-api-request.md`
- `example-api-response.md`
- `testing-scenarios.md`
- `test-data-scenarios.json`
- `error-handling-notes.md`
- `spreadsheet-validation-checklist.md`
- `validation-logic-summary.md`
- `formula-debugging-notes.md`
- `workflow-diagram.md`
- `screenshot-guide.md`
- `case-study-draft.md`
- `architecture-notes.md`
- `portfolio-summary.md`
- `demo-walkthrough.md`
- `project-review-checklist.md`

## Case Study Review

Review `case-study-draft.md` and confirm that it explains:

- Project summary
- Problem it solves
- Who would use it
- Current project status
- Tools and technologies used
- Spreadsheet structure
- Current workflow
- Workflow diagram
- Metrics used
- Sample data
- Formula logic
- Validation logic
- Warning logic
- Error handling
- JSON and API learning
- Sample API flow
- Testing scenarios
- Screenshots and project evidence
- Sample output
- Business value
- Challenges and fixes
- What was learned
- Future improvements
- Portfolio positioning

## Architecture Review

Review `architecture-notes.md` and confirm that it explains:

- Data input layer
- Calculation layer
- Prompt and validation layer
- Report output layer
- Validation gate
- Warning logic
- Planned automation architecture
- Current limitations
- Future improvements
- Portfolio explanation

## Demo Review

Review `demo-walkthrough.md` and confirm that it explains how to walk through:

- Raw Data tab
- Weekly Comparison tab
- AI Prompt Input tab
- Validation section
- Warning notes
- Final prompt
- Generated Report tab
- GitHub documentation
- Planned automation
- Interview-style explanation
- Skills demonstrated
- Current status
- Next technical step

## Portfolio Readiness Check

This project is portfolio-ready at the documentation prototype level when the following are true.

- The spreadsheet workflow works with sample data.
- The comparison formulas work.
- The prompt lines update dynamically.
- The validation checks work.
- The warning logic works.
- The final prompt is ready to use.
- The sample generated report is included.
- Screenshots are uploaded.
- The workflow diagram is updated.
- The case study draft is written.
- The architecture notes are written.
- The portfolio summary is written.
- The demo walkthrough is written.
- The project limitations are honest.
- The future automation path is clear.

## Not Yet Complete

These items are intentionally not complete yet.

- n8n workflow connection
- Google Sheets connection inside n8n
- AI API request from n8n
- Automated report generation
- Automated saving to Google Sheets, Google Docs, or email
- n8n workflow screenshots
- Final automated demo

These should be handled in the next technical phase.

## Next Technical Phase

The next technical phase should begin with a simple n8n test.

The first automation goal should be:

Connect n8n to Google Sheets and read the weekly marketing data.

The first automation goal should not be:

Connect everything to AI immediately.

Safer build order:

1. Confirm n8n can access the Google Sheet.
2. Read rows from the Raw Data tab.
3. View the returned data inside n8n.
4. Confirm the data structure.
5. Decide which fields the AI prompt needs.
6. Then test sending data to an AI model.

## Final Day 4 Check

Before ending Day 4, confirm:

- Screenshots are uploaded.
- Case study draft is updated.
- Workflow diagram is updated.
- Architecture notes are created.
- Portfolio summary is created.
- Demo walkthrough is created.
- Project review checklist is created.
- Notes tab includes the Day 4 progress note.
- README still needs to be updated before signing off.

## README Reminder

Do not update the README until the work session is ending.

When the session is ending, update the README with the Day 4 progress summary.
