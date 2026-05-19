# n8n Build Checklist

## Purpose
This checklist outlines the steps needed to turn the AI Marketing Performance Report Generator from a spreadsheet prototype into an automated reporting workflow.

The goal is to use n8n to read marketing performance data, send the data to an AI model, and save or deliver a generated report.

## Current Project Assets

Before building the n8n workflow, the project already includes:

- Google Sheet with project tabs
- Raw Data tab with sample weekly marketing metrics
- Weekly Comparison tab with formula-based metric comparisons
- AI Prompt Input tab with dynamic prompt lines
- Final prompt block for AI reporting
- Generated Report tab with sample output
- `sample-report-data.json`
- `report-prompt-template.md`
- `sample-generated-report.md`
- `data-dictionary.md`
- `workflow-plan.md`

## n8n Setup

- [ ] Create or log into an n8n account
- [ ] Create a new workflow
- [ ] Name the workflow `AI Marketing Report Generator`
- [ ] Identify whether the workflow will run manually or on a schedule
- [ ] Add notes inside n8n explaining the purpose of the workflow

## Google Sheets Connection

- [ ] Connect Google Sheets to n8n
- [ ] Select the AI Marketing Performance Report Generator spreadsheet
- [ ] Choose the correct tab to read from
- [ ] Test whether n8n can read spreadsheet rows
- [ ] Confirm that the final prompt block can be accessed
- [ ] Confirm that the latest weekly data can be identified

## Data Formatting

- [ ] Decide whether n8n should use the final prompt block or structured JSON data
- [ ] Map spreadsheet fields into clear variable names
- [ ] Confirm previous week and current week values are included
- [ ] Confirm calculated changes are included
- [ ] Confirm key insight and recommended action are included
- [ ] Test the formatted data before sending it to AI

## AI Model Connection

- [ ] Choose the AI provider or model
- [ ] Add the API credentials safely
- [ ] Make sure private API keys are not stored in GitHub
- [ ] Create the AI prompt message
- [ ] Send test data to the AI model
- [ ] Review the generated report output
- [ ] Adjust the prompt if the report is too vague or too long

## Report Output

Choose one output destination for the first version:

- [ ] Save the generated report back to Google Sheets
- [ ] Save the generated report to Google Docs
- [ ] Send the generated report by email
- [ ] Save the generated report somewhere else

For version one, the preferred output is:

```text
Google Sheets or Google Docs
