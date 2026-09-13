# Week 6 Project Summary

## What I Planned to Accomplish in Week 6

Building on the initial EDA completed in Week 5, the goal for Week 6 was to move toward **deeper analysis, findings validation, and cross-track integration**.

The planned activities were to:

- Further investigate the factors associated with appointment no-shows.
- Validate the strongest findings identified during Week 5.
- Examine relationships between multiple appointment and patient characteristics.
- Evaluate reminder coverage and effectiveness within higher-risk appointment segments.
- Review and refine the existing KPI framework.
- Translate validated findings into more targeted business recommendations.
- Provide relevant analytical findings to the Data Science track for further modelling.
- Document the analytical handoff and prepare requirements for Week 7 testing.

## What I Actually Completed

During Week 6, I extended the HealthConnect analysis beyond the initial EDA by focusing on **booking lead time, previous no-show behaviour, reminder coverage, and higher-risk appointment segments**.

The work completed included:

- Investigated the relationship between booking lead time and appointment outcomes.
- Grouped booking lead time into meaningful intervals to compare outcome distributions.
- Examined booking lead time alongside previous no-show history.
- Identified higher-risk appointment segments based on combinations of booking lead time and previous no-show behaviour.
- Evaluated reminder coverage across different booking lead-time groups.
- Examined reminder effectiveness within the identified higher-risk segments.
- Reviewed and validated the existing KPI set against the deeper findings.
- Conducted Chi-square tests and calculated Cramér's V to statistically validate key relationships.
- Refined the key findings and business recommendations based on the additional analysis.
- Documented analytical inputs for handoff to the Data Science track.
- Defined analytical testing requirements for Week 7.

## Key Findings and Development Outcomes

The deeper analysis produced several important refinements to the Week 5 findings.

- **Booking lead time showed a clear relationship with appointment outcomes.** No-show rates increased consistently as booking lead time increased, rising from approximately **24% for appointments booked 0–2 days in advance to 60% for appointments booked 31+ days in advance**.

- **The booking lead time relationship was statistically significant.** The Chi-square test produced a p-value below 0.001, while Cramér's V of **0.185** indicated a modest association.

- **Previous no-show history remained relevant.** The relationship between previous no-shows and current appointment outcomes was statistically significant, although the Cramér's V of **0.091** indicated a relatively weak association.

- **Combining booking lead time and previous no-show history revealed higher-risk segments.** The highest observed no-show rates were concentrated among appointments with longer booking lead times, particularly when previous no-show history was also present.

- **Long booking lead time was relevant even among patients without previous no-shows.** This suggests that previous no-show history alone does not capture all of the variation in no-show behaviour.

- **Reminder coverage remained incomplete.** Approximately **27% of appointments had no recorded reminder**, and reminder coverage was relatively consistent across booking lead-time groups.

- **Reminder coverage appeared more important than channel differences within the higher-risk segments.** The no-reminder group recorded a no-show rate of approximately **61%**, compared with approximately **55% for SMS**, while differences between the individual reminder channels remained relatively modest.

- **The Week 5 reminder finding was therefore refined.** Although SMS had the highest attendance proportion, the analysis does not provide sufficient evidence to conclude that SMS is substantially more effective than other channels.

- **Not all variables were strong differentiators of appointment outcomes.** Waiting time, age group, appointment type, and distance to the clinic showed relatively limited differences or substantial overlap across outcomes.

Overall, the Week 6 analysis shifted the focus from simply identifying individual factors toward **considering booking lead time, previous no-show behaviour, and reminder coverage together when designing targeted interventions**.

## Major Challenges Encountered

Several challenges were encountered during the deeper analysis:

- Determining how to define higher-risk appointment segments without introducing an arbitrary risk threshold.

- Interpreting combinations of booking lead time and previous no-show history while accounting for smaller segment sizes.

- Distinguishing statistical significance from practical significance when validating relationships.

- Avoiding causal interpretations when comparing reminder outcomes across observational groups.

- Deciding how far to extend the analysis without unnecessarily duplicating the visualisations and findings already established during Week 5.

- Determining how the analytical findings could provide useful inputs to the Data Science track without presenting the analysis as a predictive model.

These challenges reinforced the importance of combining **descriptive analysis, statistical validation, practical interpretation, and appropriate limitations** when developing business insights.

## Important Decisions Made and Why

### Focusing on Booking Lead Time

Booking lead time was introduced as an additional analytical dimension during Week 6 after the initial EDA showed the need to investigate other factors that could help explain differences in no-show behaviour.

The variable showed a consistent increase in no-show rates across longer booking intervals and therefore provided a useful basis for deeper analysis.

### Combining Booking Lead Time with Previous No-Shows

Rather than examining previous no-show behaviour independently, booking lead time was analysed alongside previous no-show history.

This helped identify combinations of characteristics associated with substantially higher observed no-show rates and provided a more useful basis for targeted intervention.

### Refining the Reminder Strategy Finding

The Week 5 analysis suggested that SMS had the highest attendance proportion among reminder channels.

Week 6 analysis refined this finding by examining reminder outcomes within higher-risk segments. While SMS continued to have the lowest observed no-show rate among the channels, the differences were relatively modest.

As a result, the recommendation shifted from selecting a single "best" channel toward **improving reminder coverage and investigating targeted reminder strategies**.

### Validating Key Relationships Statistically

Chi-square tests and Cramér's V were introduced to determine whether the key relationships observed during the analysis were statistically supported and to assess their strength.

This provided additional evidence while avoiding reliance on visual differences alone.

### Keeping the Analysis Focused

Rather than repeating Week 5 charts or adding visualisations for every new calculation, Week 6 focused on analyses that directly contributed to findings validation, risk segmentation, reminder strategy, and cross-track integration.

## Changes to the Week 5 Approach

The Week 5 analytical direction was retained but expanded in several ways:

- The analysis moved from primarily descriptive EDA toward **relationship analysis and statistical validation**.

- Booking lead time was introduced as an additional factor associated with appointment outcomes.

- Previous no-show behaviour was analysed alongside booking lead time to identify higher-risk combinations.

- Reminder effectiveness was evaluated within higher-risk segments rather than only across the overall dataset.

- The interpretation of reminder channels was refined to avoid treating SMS as definitively superior.

- The existing KPI set was reviewed rather than expanded unnecessarily.

- Statistical testing was introduced for the two key relationships identified during the deeper analysis.

- The analysis remained focused on evidence generation rather than attempting to build a predictive model within the Data Analytics track.

## Cross-Track Contribution Completed

### Data Analytics → Data Science

The validated Week 6 findings were prepared as an analytical handoff to the **Data Science track** to support further modelling of appointment no-show behaviour.

The handoff highlighted:

- Booking lead time as a candidate feature, with the strongest association among the two key behavioural variables tested.
- Previous no-show history as an additional candidate feature.
- Higher-risk combinations of booking lead time and previous no-show history.
- Reminder coverage as an important consideration, with approximately 27% of appointments having no recorded reminder.
- Reminder channel performance within higher-risk segments, while noting that channel differences were relatively modest.

These findings provide the Data Science team with **candidate variables and validated analytical patterns** to consider during feature selection, modelling, and model interpretation.

> **Integration outcome:** The Data Analytics findings will serve as a baseline for comparing Data Science model outputs with the observed patterns identified through EDA and statistical analysis.

## Remaining Work

Following the Week 6 analysis, the remaining work includes:

- Complete the Data Science integration and review model outputs against the analytical findings.
- Test the proposed reminder strategy using appropriate analytical or modelling approaches.
- Further evaluate reminder coverage and channel effectiveness.
- Assess whether the identified higher-risk segments remain consistent under predictive modelling.
- Measure the practical impact of potential reminder interventions against the established baseline.
- Finalise project documentation and repository updates.
- Prepare the analytical outputs for the next stage of the HealthConnect project.

## Proposed Focus for Week 7

For Week 7, the focus should move from **identifying and validating patterns toward analytical testing and decision support**.

The proposed focus is to:

1. **Validate the higher-risk segments** using additional statistical or modelling approaches.

2. **Evaluate reminder strategies** within higher-risk appointment groups.

3. **Test reminder coverage** to determine whether increased coverage is associated with improved appointment outcomes.

4. **Compare reminder channels** while accounting for differences in patient and appointment characteristics where possible.

5. **Review Data Science model outputs** against the relationships identified during Week 6.

6. **Evaluate feature importance and model performance** to determine which variables provide useful predictive information.

7. **Measure practical impact** using changes in no-show rate, attendance rate, and reminder coverage where intervention/test data becomes available.

The overall objective is to move HealthConnect from **identifying higher-risk patterns toward testing whether targeted interventions can produce measurable improvements in appointment attendance**.