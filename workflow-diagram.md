# Workflow Diagram

## Purpose
This file shows the current and planned workflow for the AI Marketing Performance Report Generator.

The goal is to explain how marketing performance data moves from raw input to weekly comparison, validation, AI prompt creation, and eventual report generation.

## Current Spreadsheet Workflow

```mermaid
flowchart TD
    A[Raw Data tab] --> B[Weekly Comparison tab]
    B --> C[AI Prompt Input tab]
    C --> D[Validation Check]
    D --> E[Warning Notes]
    E --> F[Final Review Status]
    F --> G[Validation Summary]
    G --> H[Final Prompt to Send to AI]
    H --> I[Generated Report tab]
```

## Planned Automated Workflow

```mermaid
flowchart TD
    A[Google Sheets] --> B[Weekly Comparison formulas]
    B --> C[AI Prompt Input]
    C --> D[Validation Checks]
    D --> E{Ready to generate report?}
    E -->|Yes| F[n8n workflow]
    E -->|No| G[Stop and review data]
    F --> H[AI API]
    H --> I[Generated Report]
    I --> J[Google Sheets, Google Docs, or Email Output]
```

## Notes
The current version is still a spreadsheet prototype.

The future version will use n8n to read the spreadsheet data, check whether the report is ready, send the prompt or JSON payload to an AI model, and save the generated report output.
