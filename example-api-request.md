# Example API Request

## Purpose
This file shows what a future API request might look like for the AI Marketing Performance Report Generator.

The goal is to understand how n8n could send marketing performance data to an AI model and receive a generated report.

## Plain-English Version

n8n sends a request to an AI model that says:

"Here is the weekly marketing performance data. Please generate a structured marketing performance report with an executive summary, key metric changes, business interpretation, and recommended next actions."

## Request Type

This would likely use a `POST` request because n8n is sending data to the AI model.

## Example Request Body

```json
{
  "task": "generate_marketing_report",
  "reportFormat": {
    "sections": [
      "Executive Summary",
      "Key Metric Changes",
      "Business Interpretation",
      "Recommended Next Actions"
    ]
  },
  "inputData": {
    "reportPeriod": {
      "previousWeekStart": "2026-05-04",
      "currentWeekStart": "2026-05-11"
    },
    "metrics": [
      {
        "metric": "users",
        "previousWeek": 1250,
        "currentWeek": 1390,
        "change": 140,
        "percentChange": "11.20%",
        "direction": "increase"
      },
      {
        "metric": "sessions",
        "previousWeek": 1600,
        "currentWeek": 1785,
        "change": 185,
        "percentChange": "11.56%",
        "direction": "increase"
      },
      {
        "metric": "engagementRate",
        "previousWeek": "62%",
        "currentWeek": "66%",
        "change": "4 percentage points",
        "percentChange": "6.45%",
        "direction": "increase"
      },
      {
        "metric": "conversions",
        "previousWeek": 48,
        "currentWeek": 57,
        "change": 9,
        "percentChange": "18.75%",
        "direction": "increase"
      },
      {
        "metric": "ctaClicks",
        "previousWeek": 135,
        "currentWeek": 162,
        "change": 27,
        "percentChange": "20.00%",
        "direction": "increase"
      }
    ],
    "topChannel": "Organic Search",
    "topPage": "/services",
    "keyInsight": "Traffic, engagement, conversions, and CTA clicks all increased compared to the previous week.",
    "recommendedAction": "Review what drove the increase in Organic Search traffic and consider applying similar SEO or content tactics to other high-value pages."
  }
}
