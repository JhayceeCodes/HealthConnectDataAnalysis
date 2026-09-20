# Week 7 Project Summary

## What I Planned to Accomplish in Week 7

Building on the deeper analysis and cross-track integration completed in Week 6, the goal for Week 7 was to move from analysis toward **testing, refinement, and end-to-end validation**.

The planned activities were to:

- Independently validate the Week 6 KPI calculations and analytical findings.
- Check dashboard and visualisation outputs against the underlying data.
- Test the consistency of the key relationships identified during Week 6.
- Validate the higher-risk appointment segments.
- Reassess reminder coverage and effectiveness findings.
- Identify errors, inconsistencies, or weaknesses in the existing analysis.
- Refine visualisations and analytical interpretations where necessary.
- Perform meaningful cross-track validation with the Data Science track.
- Retest outputs after identified refinements.
- Document validated findings, remaining limitations, and recommendations for the next stage of HealthConnect.

## What I Actually Completed

During Week 7, I independently tested and validated the major analytical outputs produced during Week 6.

The work completed included:

- Independently recalculated and validated all four HealthConnect KPIs.
- Reproduced the booking lead time and no-show analysis.
- Independently reproduced the previous no-show and appointment outcome relationship.
- Revalidated the higher-risk appointment segments.
- Revalidated reminder coverage across booking lead-time groups.
- Revalidated reminder effectiveness across reminder channels and within higher-risk segments.
- Reproduced and validated the two major Week 6 visualisations.
- Reviewed the analytical interpretations for consistency with the underlying data.
- Conducted cross-track validation with the Data Science track.
- Identified and corrected a multicollinearity issue in the Data Science feature set.
- Retested the refined modelling approach.
- Documented the validated findings, refinements, remaining limitations, and implications for the next stage of the project.

## Key Findings and Development Outcomes

Week 7 testing confirmed that the major analytical findings from Week 6 were reproducible against the underlying dataset.

- **Booking lead time remained strongly associated with appointment outcomes.** Independently reproduced no-show rates increased from **24.18% for appointments booked 0–2 days in advance to 60.49% for appointments booked 31+ days in advance**.

- **The booking lead time relationship was statistically supported.** The independently reproduced Chi-square test produced χ² = **341.12**, df = **8**, p < 0.001, with Cramér's V = **0.185**, indicating a modest association.

- **Previous no-show behaviour remained statistically associated with current appointment outcomes.** The independently reproduced test produced χ² = **83.38**, df = **10**, p < 0.001, with Cramér's V = **0.091**, indicating a relatively weak association.

- **The higher-risk appointment segments identified in Week 6 were independently reproduced.** The observed highest-risk combinations remained concentrated among longer booking lead times combined with previous no-show history.

- **Reminder coverage remained relatively consistent across booking lead-time groups.** No-reminder rates ranged from approximately **24.75% to 28.36%**, with the 31+ day group at **27.22%**.

- **Reminder effectiveness findings were independently reproduced.** Overall attendance rates remained 46.53% for Email, 42.68% for no reminder, 49.60% for SMS, and 44.60% for WhatsApp.

- **Reminder differences remained observational rather than causal.** Although reminder variables provided additional predictive information in the Data Science validation, the available data does not establish that reminders themselves cause improved attendance.

- **The Week 6 visualisations were independently validated.** The appointment outcome distribution by booking lead time and the no-show heatmap by previous no-shows and booking lead time accurately represented the underlying data.

- **Cross-track validation confirmed the predictive relevance of booking lead time and previous no-show behaviour.** Data Science modelling independently supported the presence of these signals.

- **A modelling issue was identified and corrected during cross-track validation.** The Week 6 Data Science model included `previous_appointments`, `previous_no_shows`, and the derived `previous_no_show_rate` simultaneously. Their multicollinearity caused the rate feature to receive an incorrect negative coefficient.

- **The modelling feature set was refined.** Removing the collinear raw-count variables and retaining `previous_no_show_rate` changed its coefficient from **-0.106 to +0.195**, aligning the model with the validated Analytics finding without materially changing predictive performance.

- **Additional model complexity was not justified.** `booking_lead_group` provided negligible additional predictive value when continuous `booking_lead_days` was already included, while an explicit interaction between previous no-show rate and booking lead time produced negligible improvement.

Overall, Week 7 confirmed the reliability of the core Analytics outputs while identifying a substantive modelling refinement through cross-track validation.



## Major Challenges Encountered

Several challenges were encountered during Week 7 testing and refinement:

- Independently reproducing the Week 6 findings while maintaining the same analytical definitions and grouping logic.
- Distinguishing genuine inconsistencies from differences caused by rounding or presentation.
- Validating higher-risk segments without treating them as formal individual-level risk classifications.
- Ensuring that visualisations accurately reflected the independently recalculated values.
- Interpreting the Data Science modelling results alongside the descriptive and statistical Analytics findings.
- Identifying multicollinearity among related previous-appointment features.
- Determining whether additional model complexity provided enough improvement to justify its use.
- Maintaining appropriate non-causal interpretations of reminder-related findings.

These challenges reinforced the importance of **independent validation, cross-track testing, model simplicity, and clear distinction between association, prediction, and causation**.



## Important Decisions Made and Why

### Independently Validating Week 6 Findings

A separate Week 7 testing notebook was used to independently reproduce the Week 6 KPIs, analytical findings, statistical tests, and visualisations.

This provided a clearer separation between the original analysis and the validation process.

### Retaining the Existing KPI Framework

All four KPIs were independently recalculated and matched the original results. No new KPI was introduced because the existing framework remained relevant to the validated findings.

### Preserving Booking Lead Time as an Analytics Reporting Dimension

Booking lead time remained useful for communicating the observed increase in no-show rates across appointment groups.

However, Data Science validation showed that the grouped variable adds negligible predictive value once continuous `booking_lead_days` is included. The grouped representation will therefore remain useful for Analytics reporting while continuous lead time is preferred for predictive modelling.

### Correcting the Previous No-Show Feature Set

Cross-track validation identified multicollinearity between `previous_appointments`, `previous_no_shows`, and `previous_no_show_rate`.

The raw count variables were removed from the predictive model and `previous_no_show_rate` was retained. This corrected the coefficient direction without materially changing model performance.

### Avoiding Unnecessary Model Complexity

An explicit interaction between previous no-show rate and booking lead time produced negligible additional predictive value.

The simpler additive feature set was therefore retained.

### Maintaining Non-Causal Reminder Interpretation

Reminder variables demonstrated additional predictive information, but the observational dataset cannot establish whether reminders cause improved attendance.

The recommendation therefore remains focused on testing targeted reminder interventions rather than assuming a causal effect.



## Cross-Track Contribution

### Data Analytics → Data Science

The validated Analytics findings were provided to the **Data Science track** for independent modelling validation.

The handoff focused on:

- Booking lead time and its relationship with appointment outcomes.
- Previous no-show behaviour.
- Higher-risk combinations of booking lead time and previous no-shows.
- Reminder coverage.
- Reminder effectiveness and its non-causal interpretation.

The Data Science track tested these findings using predictive modelling and feature analysis.

The modelling confirmed that **booking lead time and previous no-show behaviour contained useful predictive signal**. However, the validation also identified a modelling issue in the Week 6 candidate feature set.

The Week 6 model included `previous_appointments`, `previous_no_shows`, and `previous_no_show_rate` simultaneously. Because the rate is derived from the two raw counts, the variables exhibited moderate-to-high multicollinearity. This caused `previous_no_show_rate` to receive an incorrect negative coefficient of **-0.106**.

The feature set was refined by removing the collinear raw-count variables and retaining `previous_no_show_rate`. After refinement, the coefficient changed to **+0.195**, aligning with the independently validated Analytics finding, while predictive performance remained effectively unchanged.

Additional cross-track testing showed that:

- `booking_lead_group` was redundant for predictive modelling when continuous `booking_lead_days` was included.
- An explicit `previous_no_show_rate × booking_lead_days` interaction provided negligible additional predictive value.
- Reminder variables added statistically significant predictive information beyond lead time and patient history, although this remains non-causal evidence.

> **Integration outcome:** The cross-track validation did more than confirm the Analytics findings. It identified and corrected a feature-design issue in the Week 6 Data Science model, resulting in a simpler and more consistent candidate feature set:
>
> `booking_lead_days` + `previous_no_show_rate` + `is_new_patient` + `reminder_sent` + `reminder_channel`




## Remaining Work

The main Analytics testing, validation, refinement, and cross-track validation activities have now been completed.

The remaining work is primarily focused on final integration and presentation:

- Integrate the validated Analytics and Data Science outputs into the wider HealthConnect solution.
- Consolidate the final KPIs, validated findings, and refined recommendations.
- Ensure that the corrected Data Science feature set and modelling conclusions are reflected consistently across project outputs.
- Finalise dashboards, visualisations, and other presentation materials.
- Review the project documentation for consistency across the Analytics and Data Science tracks.
- Prepare the final project presentation and supporting materials.
- Clearly communicate the project's validated findings, limitations, and practical implications.



## Proposed Focus for Week 8

Week 8 will focus on **Final Integration → Presentation**.

The proposed activities are to:

1. **Integrate the validated analytical and Data Science outputs** into the final HealthConnect solution.

2. **Consolidate the final findings and recommendations** from the completed analysis and testing phases.

3. **Finalise dashboards and visualisations** to ensure that they accurately communicate the validated findings and support business interpretation.

4. **Review and align project documentation** across the Analytics and Data Science tracks.

5. **Prepare the final presentation**, covering the problem, analytical approach, key findings, validation, cross-track contribution, recommendations, and limitations.

6. **Present the end-to-end HealthConnect solution**, demonstrating how the different project components contribute to the overall solution.

The overall objective is to move from **validated analytical work to a coherent, integrated, and presentation-ready HealthConnect solution**.