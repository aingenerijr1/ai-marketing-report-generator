# Data Dictionary

## Purpose
This file explains the fields used in the AI Marketing Performance Report Generator project.

The goal is to make the spreadsheet data, JSON sample data, and future automation workflow easier to understand.

## Report Period Fields

| Field | Meaning | Example |
|---|---|---|
| `previousWeekStart` | Start date of the previous reporting week | `2026-05-04` |
| `currentWeekStart` | Start date of the current reporting week | `2026-05-11` |

## Metric Fields

| Field | Meaning | Example |
|---|---|---|
| `metric` | The name of the marketing performance metric | `users` |
| `previousWeek` | The value from the previous week | `1250` |
| `currentWeek` | The value from the current week | `1390` |
| `change` | The difference between current week and previous week | `140` |
| `percentChange` | The percent increase or decrease from the previous week | `11.20%` |
| `direction` | Whether the metric increased, decreased, or stayed the same | `increase` |

## Marketing Fields

| Field | Meaning | Example |
|---|---|---|
| `topChannel` | The traffic channel with the strongest performance | `Organic Search` |
| `topPage` | The top-performing page for the reporting period | `/services` |
| `keyInsight` | A plain-English summary of the main performance trend | `Traffic, engagement, conversions, and CTA clicks all increased.` |
| `recommendedAction` | Suggested next step based on the data | `Review what drove the increase in Organic Search traffic.` |

## Spreadsheet Tabs

| Tab | Purpose |
|---|---|
| Raw Data | Stores the weekly marketing performance data |
| Weekly Comparison | Compares previous week and current week metrics |
| AI Prompt Input | Turns spreadsheet values into marketing-friendly prompt text |
| Generated Report | Stores or previews the final report output |
| Notes | Tracks project progress, learning notes, and JSON practice |

## Notes
This data dictionary will be updated as the project becomes more automated and additional fields are added.
