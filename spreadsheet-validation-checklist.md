# Spreadsheet Validation Checklist

## Purpose
This checklist defines what should be reviewed before the AI Marketing Performance Report Generator creates a final report.

The goal is to prevent missing, incorrect, or misleading data from becoming a polished but inaccurate AI-generated report.

## Why Validation Matters
A marketing report is only useful if the input data is trustworthy.

If the spreadsheet contains missing values, incorrect formatting, or unusual spikes, the workflow should flag those issues before generating the report.

## Required Fields Checklist

Before generating a report, confirm that these fields are filled in:

- [ ] Previous week start date
- [ ] Current week start date
- [ ] Previous week users
- [ ] Current week users
- [ ] Previous week sessions
- [ ] Current week sessions
- [ ] Previous week engagement rate
- [ ] Current week engagement rate
- [ ] Previous week conversions
- [ ] Current week conversions
- [ ] Previous week CTA clicks
- [ ] Current week CTA clicks
- [ ] Top channel
- [ ] Top page
- [ ] Key insight
- [ ] Recommended action

## Numeric Validation Checklist

Confirm that numeric fields are valid:

- [ ] Users are not blank
- [ ] Sessions are not blank
- [ ] Conversions are not blank
- [ ] CTA clicks are not blank
- [ ] Users are not negative
- [ ] Sessions are not negative
- [ ] Conversions are not negative
- [ ] CTA clicks are not negative
- [ ] Engagement rate is formatted as a percentage
- [ ] Percent change formulas are calculating correctly

## Logic Validation Checklist

Confirm that the report logic makes sense:

- [ ] If current week is greater than previous week, the prompt says increased
- [ ] If current week is less than previous week, the prompt says decreased
- [ ] If current week equals previous week, the prompt says stayed the same
- [ ] Engagement rate uses percentage-point wording where needed
- [ ] The final prompt block includes all key metrics
- [ ] The final prompt block includes the key insight
- [ ] The final prompt block includes the recommended action

## Warning Signs

The workflow should be reviewed carefully if any of these happen:

- Users increase or decrease by more than 100%
- Sessions increase or decrease by more than 100%
- Conversions drop by more than 50%
- CTA clicks drop by more than 50%
- Engagement rate changes by more than 20 percentage points
- Users are zero
- Sessions are zero
- Current week values are missing
- The final prompt block is blank

## Missing Data Handling

If required data is missing, the workflow should not generate a final report.

Instead, it should show a message such as:

```text
Report cannot be generated because required data is missing. Please review the Raw Data tab.
```

## Large Change Handling

If a metric changes by an unusually large amount, the report should mention that the change may need review.

Example:

```text
Users increased significantly compared to the previous week. This may reflect a campaign launch, tracking change, unusual traffic source, or data entry issue.
```

## Version 1 Validation Goal

For the first version of this project, validation should focus on:

1. Required fields are filled in
2. Numeric fields are not negative
3. Engagement rate is formatted correctly
4. Increase/decrease/stayed the same language works
5. Missing data is flagged before report generation
6. Large changes are called out for review

## Future Improvements

Later versions could add:

- Google Sheets data validation rules
- Conditional formatting for missing values
- Warning messages inside the spreadsheet
- n8n error branches
- Automated email alerts for failed reports
- A human approval step before final delivery
- A validation summary section in the AI Prompt Input tab
