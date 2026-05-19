# Example API Response

## Purpose
This file shows what a future API response might look like for the AI Marketing Performance Report Generator.

The goal is to understand what the AI model may send back after receiving marketing performance data from n8n.

## Plain-English Version

After n8n sends the weekly marketing data to the AI model, the AI model sends back a generated report.

That returned message is called the API response.

## Example Response Body

```json
{
  "report": {
    "title": "Weekly Marketing Performance Report",
    "executiveSummary": "This week showed positive performance across all major marketing metrics. Users, sessions, engagement rate, conversions, and CTA clicks all increased compared to the previous week.",
    "keyMetricChanges": [
      "Users increased from 1,250 to 1,390, a 11.20% increase.",
      "Sessions increased from 1,600 to 1,785, a 11.56% increase.",
      "Engagement rate increased from 62% to 66%, a 4.0 percentage-point lift.",
      "Conversions increased from 48 to 57, a 18.75% increase.",
      "CTA clicks increased from 135 to 162, a 20.00% increase."
    ],
    "businessInterpretation": "Organic Search was the top channel and /services was the top page. This suggests that SEO-driven traffic and service-related content may have contributed to the improved performance.",
    "recommendedNextActions": [
      "Review Organic Search landing pages to identify what contributed to the traffic increase.",
      "Analyze the /services page to understand why it performed well.",
      "Apply successful SEO or content tactics to other high-value pages.",
      "Continue monitoring conversions and CTA clicks to confirm whether the trend continues next week."
    ]
  }
}
```

## How This Response Could Be Used

n8n could use this response to:

- Save the full report to Google Sheets
- Create a Google Doc
- Send the report by email
- Store the response for future reporting
- Pass the report into another workflow step

## Request vs Response

| Concept | Meaning | Project Example |
|---|---|---|
| Request | Data sent to another system | n8n sends marketing data to the AI model |
| Response | Data returned by that system | The AI model returns the generated report |

## Notes

This is a sample response format, not a live API response.

A real API response may include extra information such as:

- Model name
- Token usage
- Response ID
- Status codes
- Error messages
- Timestamps
