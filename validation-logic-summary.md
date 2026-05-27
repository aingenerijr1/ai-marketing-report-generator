# Validation Logic Summary

## Purpose
This file explains the validation and warning logic used in the AI Marketing Performance Report Generator spreadsheet.

The goal is to make sure the report is only generated when the input data is complete, the final prompt is ready, and unusual metric changes have been reviewed.

## Why This Logic Matters
AI-generated reports can sound polished even when the input data is incomplete or incorrect.

This validation layer helps prevent the workflow from generating a misleading report from bad data.

## Validation Section

The validation section lives in the `AI Prompt Input` tab.

It currently checks:

- Required data status
- Final prompt status
- Report readiness
- Traffic change warning
- Conversion change warning
- CTA click change warning
- Final review status

## Required Data Status

### Cell
`B23`

### Formula Purpose
Checks whether the required metric data exists in the `Raw Data` tab.

### Formula Logic
The formula checks whether the expected cells in `Raw Data!A2:F3` are filled in.

That range includes two weeks of data for:

- Week start date
- Users
- Sessions
- Engagement rate
- Conversions
- CTA clicks

### Possible Outputs

```text
All required metric data present
```

or

```text
Missing required metric data
```

### Why It Matters
The report should not be generated if required weekly data is missing.

## Prompt Status

### Cell
`B24`

### Formula Purpose
Checks whether the final AI prompt block exists.

### Formula Logic
The formula checks whether cell `A20` contains text.

### Possible Outputs

```text
Final prompt block ready
```

or

```text
Final prompt block missing
```

### Why It Matters
The AI workflow needs a complete prompt before it can generate a useful report.

## Report Readiness

### Cell
`B25`

### Formula Purpose
Combines required data status and prompt status into one readiness check.

### Formula Logic
If required metric data is present and the final prompt block is ready, the report is marked as ready.

### Possible Outputs

```text
Ready to generate report
```

or

```text
Not ready to generate report
```

### Why It Matters
This gives the spreadsheet a simple gate before report generation.

## Traffic Change Warning

### Cell
`B28`

### Formula Purpose
Checks whether users or sessions changed by more than 100%.

### Formula Logic
The formula reviews the percent change values for:

- Users
- Sessions

If either metric changes by more than 100%, the warning appears.

### Possible Outputs

```text
Traffic change looks normal.
```

or

```text
Review unusual traffic change before generating report.
```

### Why It Matters
A very large traffic change may be caused by a real campaign, but it could also indicate tracking issues, bot traffic, seasonality, or data entry problems.

## Conversion Change Warning

### Cell
`B29`

### Formula Purpose
Checks whether conversions changed by more than 50%.

### Formula Logic
The formula reviews the percent change value for conversions.

If conversions change by more than 50%, the warning appears.

### Possible Outputs

```text
Conversion change looks normal.
```

or

```text
Review large conversion change before generating report.
```

### Why It Matters
A large conversion change should be reviewed before the report makes business recommendations.

## CTA Click Change Warning

### Cell
`B30`

### Formula Purpose
Checks whether CTA clicks changed by more than 50%.

### Formula Logic
The formula reviews the percent change value for CTA clicks.

If CTA clicks change by more than 50%, the warning appears.

### Possible Outputs

```text
CTA click change looks normal.
```

or

```text
Review large CTA click change before generating report.
```

### Why It Matters
A large CTA click change could signal improved user interest, tracking changes, landing page changes, or a data quality issue.

## Final Review Status

### Cell
`B32`

### Formula Purpose
Combines the validation status and warning checks into one final decision.

### Formula Logic
The formula checks:

1. Whether the report is ready to generate
2. Whether traffic changes look normal
3. Whether conversion changes look normal
4. Whether CTA click changes look normal

### Possible Outputs

```text
Ready to generate report
```

or

```text
Review warnings before generating report
```

or

```text
Not ready to generate report
```

### Why It Matters
This gives the spreadsheet one clear status that can eventually guide the n8n workflow.

## Manual Tests Completed

### Missing Data Test
The current week users value was temporarily deleted.

Expected result:

```text
Missing required metric data
Not ready to generate report
```

The value was restored, and the status returned to ready.

### Conversion Warning Test
The current week conversions value was temporarily changed from `57` to `100`.

Expected result:

```text
Review large conversion change before generating report.
Review warnings before generating report
```

The value was restored, and the final review status returned to ready.

## Current Validation Flow

```text
Raw Data
   ↓
Weekly Comparison calculations
   ↓
AI Prompt Input validation checks
   ↓
Warning checks
   ↓
Final Review Status
   ↓
Generate report or review issues
```

## How This Could Support n8n Later

When n8n is added, the workflow could check the final review status before sending data to an AI model.

Possible logic:

```text
If Final Review Status = Ready to generate report
   Send prompt to AI model
Else
   Stop workflow and notify user to review the spreadsheet
```

This would help prevent the automation from generating reports when data is missing or unusual.

## Future Improvements

Possible improvements include:

- Adding a validation summary directly in the spreadsheet
- Adding conditional formatting for warning cells
- Adding more detailed error messages
- Checking for negative values
- Checking for blank top channel or top page fields
- Creating an n8n branch for failed validation
- Sending an email notification when validation fails
- Adding human approval before final report delivery
