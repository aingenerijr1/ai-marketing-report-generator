# Testing Scenarios

## Purpose
This file lists testing scenarios for the AI Marketing Performance Report Generator.

The goal is to make sure the spreadsheet, prompt logic, JSON structure, and future n8n workflow can handle realistic marketing reporting situations.

## Scenario 1: All Metrics Increase

### Description
All major metrics improve compared to the previous week.

### Expected Behavior
The report should describe the week as positive overall.

### Metrics Example
- Users increase
- Sessions increase
- Engagement rate increases
- Conversions increase
- CTA clicks increase

### Expected Report Language
The report should use words like:

- increased
- improved
- positive performance
- stronger engagement
- higher conversion activity

## Scenario 2: One Metric Decreases

### Description
Most metrics improve, but one metric decreases.

### Expected Behavior
The report should mention the improvement, but also call out the decline clearly.

### Metrics Example
- Users decrease
- Sessions increase
- Engagement rate increases
- Conversions increase
- CTA clicks increase

### Expected Report Language
The report should say something like:

"Users decreased compared to the previous week, but engagement and conversion activity improved."

## Scenario 3: Engagement Improves but Conversions Drop

### Description
Traffic quality appears stronger, but users are not completing the desired action.

### Expected Behavior
The report should explain that better engagement does not always mean better conversion performance.

### Metrics Example
- Users increase
- Sessions increase
- Engagement rate increases
- Conversions decrease
- CTA clicks decrease

### Expected Recommendation
Review CTA placement, offer clarity, landing page friction, and conversion paths.

## Scenario 4: Traffic Increases but Engagement Drops

### Description
More users visit the site, but engagement rate decreases.

### Expected Behavior
The report should avoid assuming that all traffic growth is good.

### Metrics Example
- Users increase
- Sessions increase
- Engagement rate decreases
- Conversions stay the same
- CTA clicks stay the same

### Expected Recommendation
Review traffic sources, landing page relevance, and whether the new traffic matches the intended audience.

## Scenario 5: No Change

### Description
One or more metrics stay the same compared to the previous week.

### Expected Behavior
The report should use "stayed the same" language instead of increase or decrease language.

### Metrics Example
- Users stay the same
- Sessions stay the same
- Engagement rate stays the same
- Conversions stay the same
- CTA clicks stay the same

### Expected Report Language
The report should say something like:

"Performance remained stable compared to the previous week."

## Scenario 6: Missing Data

### Description
One or more required fields are blank.

### Expected Behavior
The workflow should not generate a misleading report.

### Example Missing Fields
- Missing current week users
- Missing engagement rate
- Missing conversions
- Missing top channel
- Missing recommended action

### Expected Recommendation
The workflow should flag missing data and ask for the missing values before generating the report.

## Scenario 7: Unusually Large Change

### Description
A metric changes by a very large amount.

### Expected Behavior
The report should call out the large change and recommend investigation.

### Metrics Example
- Users increase by more than 100%
- Conversions decrease by more than 50%
- CTA clicks spike unexpectedly

### Expected Recommendation
Check for tracking issues, campaign launches, seasonality, bot traffic, or data entry errors.

## Testing Notes

For version one, the most important tests are:

1. All metrics increase
2. One metric decreases
3. A metric stays the same
4. Missing data exists
5. A very large change appears

## Future Automation Testing

When n8n is added, the workflow should be tested to confirm that:

- n8n reads the correct spreadsheet data
- n8n sends the correct prompt or JSON payload
- the AI model returns a usable report
- the report is saved to the correct location
- errors are documented clearly
