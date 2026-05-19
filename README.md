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
Day 2: Spreadsheet prototype, dynamic prompt logic, JSON sample data, prompt documentation, sample report output, and data dictionary documentation are in progress.

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
- Updated README documentation to reflect current project files and workflow progress

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

## Sample Data File
This repo includes a sample JSON file:

`sample-report-data.json`

This file represents the weekly marketing performance data in a structured format that could later be used by n8n, an API request, or an AI reporting workflow.

## Data Dictionary
This repo also includes a data dictionary:

`data-dictionary.md`

The data dictionary explains the meaning of each major field used in the project, including report period fields, metric fields, marketing fields, and spreadsheet tabs.

## Current Project Status
The project currently has a working spreadsheet prototype and supporting GitHub documentation.

The spreadsheet can compare weekly performance data, calculate changes, generate marketing-friendly prompt lines, and create a final prompt block for AI reporting.

The GitHub repo now includes structured sample data, a reusable prompt template, a sample report output, and a data dictionary.

## Upcoming Work
Next steps include:
- Continue learning basic JSON structure
- Learn how n8n workflows use spreadsheet or JSON data
- Connect spreadsheet data to an automation workflow
- Test an AI-generated report output
- Add screenshots and workflow documentation later in the project

## Portfolio Goal
This project is part of a larger AI, automation, and marketing technology learning plan. The final version should demonstrate the ability to structure marketing data, prepare AI-ready inputs, use automation tools, and explain the business value of the workflow.
