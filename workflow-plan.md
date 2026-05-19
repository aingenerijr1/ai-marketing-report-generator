# Workflow Plan

## Purpose
This file outlines the planned automation workflow for the AI Marketing Performance Report Generator.

The goal is to document how data will move from the spreadsheet into an AI-generated marketing report.

## Current Manual Workflow

Right now, the project works as a spreadsheet prototype.

1. Weekly marketing performance data is entered into the `Raw Data` tab.
2. The `Weekly Comparison` tab compares the previous week and current week.
3. The spreadsheet calculates numeric changes and percentage changes.
4. The `AI Prompt Input` tab turns the metrics into marketing-friendly language.
5. The final prompt block combines the context, metric changes, key insight, recommendation, and report instructions.
6. The `Generated Report` tab stores a sample report output.

## Planned Automated Workflow

The future automated workflow will use n8n or a similar automation tool.

1. Google Sheets stores the weekly marketing performance data.
2. n8n reads the latest weekly data or final prompt block from Google Sheets.
3. n8n formats the data into a structured prompt or JSON payload.
4. n8n sends the prompt or JSON data to an AI model.
5. The AI model generates a weekly marketing performance report.
6. n8n saves the generated report back to Google Sheets, Google Docs, email, or another output location.

## Planned Workflow Diagram

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
