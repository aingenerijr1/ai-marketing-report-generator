# AI Marketing Performance Report Generator

## Project Summary
This project will turn weekly marketing or website performance data into a structured AI-generated performance report.

## Problem It Solves
Marketing reporting often requires manually reviewing metrics, calculating week-over-week changes, identifying trends, and writing summaries. This project will automate part of that process.

## Planned Tools
  - Google Sheets
  - n8n
  - Javascript Basics
  - JSON
  - AI API
  - GitHub

## Current Status
Day 1: Project setup and spreadsheet prototype started.

## Day 1 Progress
  - Created GitHub Repository
  - Added starter README documentation
  - Created local project folder
  - Created Google Sheet with project tabs
  - Added sample weekly marketing performance data
  - Built first Weekly Comparison tab
  - Added week-over-week change formulas
  - Created AI Prompt Input tab
  - Added sample Generated Report output

## Current Workflow Draft
Raw Data -> Weekly Comparison -> AI Prompt Input -> Generated Report

## Next Steps
  - Improve the Weekly Comparison formulas
  - Make the AI Prompt Input tab pull values dynamically
  - Create a cleaner report prompt template
  - Begin learning how n8n can read spreadsheet data

## Day 2 Progress
  - Cleaned up AI Prompt Input wording
  - Created a combined final prompt block for AI reporting
  - Tested increase/decrease logic by temporarily changing sample data
  - Confirmed the prompt updates dynamically when Raw Data changes
  - Created a sample JSON data file to represent the marketing report data in a structured format

## Current Formula Logic
The spreadsheet now uses formulas to:
  - Pull weekly performance data from the Raw Data tab
  - Compare previous week and current week metrics
  - Calculate numberic and precentage changes
  - Generate marketing-friendly prompt lines
  - Indentify whether metrics inceased, decreased, or stayed the same

## Current AI Prompt Flow
Raw Data -> Weekly Comparison -> AI Prompt Input -> Final Prompt Block -> Generated Report

## Sample Data File
This repo includes a sample JSON file:

'sample-report-data.json'

This file represents the weekly marketing performance data in a structured format that could later be used by n8n, an API request, or an AI reporting workflow.
