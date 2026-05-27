# Error Handling Notes

## Purpose
This file documents possible errors and edge cases for the AI Marketing Performance Report Generator.

The goal is to make the future spreadsheet, n8n workflow, and AI reporting process more reliable.

## Why Error Handling Matters
Marketing reports can become misleading if the data is missing, incorrect, incomplete, or unusually large.

A good reporting workflow should not blindly generate a report from bad data. It should either flag the issue, ask for review, or explain that the report cannot be completed yet.

## Common Data Issues

### 1. Missing Data

#### Example
A required field is blank.

Possible missing fields:
- Current week users
- Current week sessions
- Engagement rate
- Conversions
- CTA clicks
- Top channel
- Top page
- Key insight
- Recommended action

#### Expected Behavior
The workflow should flag the missing field before generating a final report.

#### Example Message
```text
Report cannot be generated because current week users is missing.
```

### 2. Zero Values

#### Example
A metric is entered as `0`.

This is different from missing data.

A value of `0` means the metric is known and the result was zero.

A blank or `null` value means the metric is missing or unknown.

#### Expected Behavior
The workflow should treat zero as a real value, but it should still check whether the zero makes sense.

#### Example
If conversions are `0`, the report can mention that no conversions were recorded.

If users are `0`, the workflow should ask whether tracking is broken or data is missing.

### 3. Negative Values

#### Example
A metric is entered as a negative number.

Possible issue:

```text
Users = -50
```

#### Expected Behavior
The workflow should flag negative values for review because most marketing performance metrics should not be negative.

#### Example Message
```text
Users cannot be negative. Please review the Raw Data tab.
```

### 4. Very Large Changes

#### Example
Users increase from 1,250 to 10,000 in one week.

#### Possible Causes
- Campaign launch
- Viral content
- Bot traffic
- Tracking issue
- Data entry error
- Seasonal spike

#### Expected Behavior
The report should mention the large change and recommend investigation.

#### Example Report Language
```text
Users increased significantly compared to the previous week. This may indicate a successful campaign, but the size of the increase should be reviewed for tracking issues or unusual traffic sources.
```

### 5. Engagement Rate Formatting Issues

#### Example
Engagement rate is entered as:

```text
66
```

instead of:

```text
66%
```

#### Expected Behavior
The workflow should expect a consistent percentage format.

#### Possible Fix
Use spreadsheet formatting so engagement rate values are always treated as percentages.

### 6. Direction Mismatch

#### Example
The current week value is higher than the previous week value, but the JSON direction says:

```json
"direction": "decrease"
```

#### Expected Behavior
The workflow should calculate direction from the numbers whenever possible instead of relying only on manually entered direction labels.

### 7. AI Output Is Too Vague

#### Example
The AI returns:

```text
Performance was good this week.
```

#### Issue
This is not specific enough for a useful marketing report.

#### Expected Behavior
The prompt should require specific metrics, business interpretation, and recommended next actions.

#### Better Output
```text
Users increased by 11.20%, sessions increased by 11.56%, and conversions increased by 18.75%, suggesting stronger traffic volume and improved conversion activity.
```

### 8. AI Output Ignores Negative Metrics

#### Example
Users decrease, but the AI only talks about conversions increasing.

#### Expected Behavior
The report should mention both positive and negative changes.

A balanced report is more useful than a report that only highlights wins.

### 9. API Request Fails

#### Example
n8n sends data to an AI API, but the request fails.

#### Possible Causes
- Invalid API key
- Wrong endpoint
- Missing required field
- Rate limit
- Network error
- Bad JSON formatting

#### Expected Behavior
The workflow should log the error and avoid saving a fake or empty report.

#### Example Message
```text
AI report generation failed. Check API credentials, request format, and required fields.
```

### 10. AI API Returns an Empty Response

#### Example
The API request succeeds, but the generated report is blank.

#### Expected Behavior
The workflow should check whether the response includes report content before saving it.

#### Example Message
```text
AI response was empty. Report was not saved.
```

## Basic Validation Rules

Before generating a report, the workflow should check:

- Required fields are not blank
- Numeric metrics are not negative
- Engagement rate is formatted as a percentage
- Previous week and current week values exist
- The final prompt block is not empty
- JSON data is valid
- AI response includes usable report content

## Version 1 Error Handling Goal

For the first version, the workflow should be able to handle:

1. Missing required data
2. One metric decreasing
3. A metric staying the same
4. Very large metric changes
5. Failed AI/API response

## Future Improvements

Possible future improvements include:

- Adding spreadsheet validation rules
- Adding warning messages in the AI Prompt Input tab
- Adding an n8n error branch
- Sending an error notification email
- Logging failed workflow runs
- Preventing report generation when required data is missing
- Adding a human review step before final report delivery
