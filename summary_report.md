# Week 5 Project Summary 

## 1. What I Planned to Accomplish in Week 5

Building on the analytical foundation established in Week 4, the goal for Week 5 was to move from planning into practical exploratory data analysis of the HealthConnect appointment dataset.

The planned activities were to:

- Prepare and validate the dataset for analysis.
- Explore appointment outcomes and attendance patterns.
- Investigate the business questions defined in Week 4.
- Calculate and evaluate the proposed KPIs.
- Develop relevant visualisations to communicate the findings.
- Identify meaningful patterns and potential business opportunities.
- Document limitations and translate the findings into recommendations.

## 2. What I Actually Completed

During Week 5, I completed the initial exploratory analysis of the HealthConnect appointment dataset using **Python, Pandas, Matplotlib, Seaborn, and Jupyter Notebook**.

The work completed included:

- Validated the dataset structure and data types.
- Confirmed the dataset contains **5,000 appointment records across 18 variables**.
- Checked for duplicates and inconsistent categorical values.
- Investigated missing values in `distance_to_clinic_km` and `waiting_time_minutes`.
- Converted date fields to appropriate datetime formats.
- Recoded missing `reminder_channel` values as **"No reminder"**, based on the data dictionary definition that missing values represent appointments where no reminder was sent.
- Conducted exploratory analysis across appointment outcomes, reminders, previous no-shows, appointment timing, appointment type, waiting time, age group, and distance to clinic.
- Calculated and reviewed the proposed KPIs.
- Developed charts and tables to support the analysis.
- Documented key findings, recommendations, limitations, and a conclusion in the analysis notebook.

## 3. Key Findings and Development Outcomes

The analysis produced several notable findings:

- **No-shows are the most common appointment outcome**, accounting for approximately **47.5%** of appointments, slightly above attended appointments at approximately 46.2%.
- **Previous no-show behaviour shows a strong association with future no-shows.** The current no-show rate increases from approximately **43.5% for patients with no previous no-shows to 68.0% among patients with three previous no-shows**.
- **Reminder coverage is incomplete.** Approximately **27.3% of appointments did not receive a recorded reminder**.
- Attendance proportions varied modestly across reminder channels, with **SMS showing the highest attendance proportion at approximately 50%**, followed by Email, WhatsApp, and the no-reminder group. The differences were not large enough to conclude that one channel is substantially more effective.
- Appointment demand is concentrated in the **morning and afternoon**, while evening appointments have considerably lower volumes.
- **Waiting times show limited differentiation across appointment outcomes**, with median waiting times generally falling within approximately 22–24 minutes.
- Appointment outcomes are broadly similar across appointment types and age groups.
- Distance to the clinic showed slightly higher median values for no-shows and cancellations than attended appointments, but the distributions overlapped considerably.

Overall, the analysis identified **previous no-show behaviour and reminder coverage as more notable areas for further attention**, while several other variables showed relatively weak differences across outcomes.

## 4. Major Challenges Encountered

Several challenges were encountered during the analysis:

- Determining how missing values in `reminder_channel` should be interpreted. The missing values were initially not represented as the literal string `"None"`, requiring reference to the data dictionary before recoding them as **"No reminder"**.
- Deciding which variables warranted visualisation and which were better represented using tables or descriptive statistics.
- Interpreting differences between groups without overstating them as causal relationships.
- Balancing the number of visualisations with the need to keep the notebook focused on the defined business questions.
- Determining how to treat missing observations in `distance_to_clinic_km` and `waiting_time_minutes` without introducing assumptions through unnecessary imputation.

These challenges reinforced the importance of using the data dictionary and analytical context when making data preparation and interpretation decisions.

## 5. Important Decisions Made and Why

### Recoding Missing Reminder Channels

Missing `reminder_channel` values were recoded as **"No reminder"** rather than treated as an unknown category because the data dictionary explicitly defines missing values as indicating that no reminder was sent.

### Reducing the KPI Set

The initial KPI consideration included appointment volume. This was removed from the final KPI set because total appointment volume is primarily a descriptive measure already covered through exploratory analysis rather than a strong KPI linked to the core business questions.

The final KPI set focused on:

- No-Show Rate
- Reminder Effectiveness Rate
- Reminder Non-send Rate
- Average Waiting Time

### Focusing Visualisations on Analytical Questions

Not every variable was given a standalone chart. Tables were used where they communicated the information more effectively, while visualisations were prioritised for comparisons and patterns that benefited from graphical representation.

### Avoiding Causal Conclusions

Observed relationships were treated as associations rather than evidence of causation. For example, the higher attendance proportion associated with SMS reminders does not establish that SMS itself causes higher attendance.

## 6. Changes to the Week 4 Approach

The overall Week 4 analytical direction was retained, but it was refined during implementation.

The main changes were:

- The analysis moved from the proposed exploratory plan into a more focused **question → analysis → visualisation → observation** structure.
- Appointment volume was removed from the KPI set and retained as an EDA/descriptive metric.
- Some proposed areas were deprioritised where the initial analysis showed limited differentiation.
- The analysis placed greater emphasis on **previous no-show behaviour and reminder coverage**, as these produced more meaningful findings.
- Separate visualisations were not created for every variable. Tables were used where appropriate to avoid unnecessary charts.
- The analysis was implemented as a **Python notebook rather than a dashboard**, keeping the initial analysis focused on exploration, interpretation, and documentation.

## 7. Cross-Track Collaboration Completed

The Week 5 analysis was carried out within the broader HealthConnect project, where Data Analytics contributes alongside the other professional tracks.

From the Data Analytics perspective, the completed work provides:

- Evidence-based findings on appointment attendance and no-show patterns.
- Identified variables and patterns that may be relevant to future predictive analysis.
- KPI definitions that can support broader project reporting.
- Business recommendations that can inform potential interventions.
- Documented limitations that should be considered by other tracks when using the dataset.

No specific cross-track implementation was completed during this stage. The main contribution was providing analytical findings and context that can support subsequent work across the HealthConnect project.

## 8. Remaining Work

The Week 5 analysis provides an initial analytical baseline, but several activities remain:

- Refine and validate the final findings.
- Review the recommendations against the analytical evidence.
- Finalise the project documentation.
- Update the GitHub README with the completed analysis and selected visualisations.
- Organise the repository and supporting files.
- Prepare the analysis for integration with subsequent HealthConnect project stages.
- Further investigate factors associated with repeated no-shows where appropriate.

## 9. Proposed Focus for Week 6

For Week 6, the focus should move from initial EDA toward **deeper analysis and analytical refinement**.

The proposed focus is to:

1. Further investigate the relationship between previous no-show behaviour and current appointment outcomes.
2. Examine reminder coverage and reminder-channel performance in greater detail.
3. Explore whether combinations of factors provide stronger explanations of no-show behaviour than individual variables.
4. Validate the strongest findings identified during Week 5.
5. Translate the validated findings into more targeted business recommendations.
6. Collaborate with the other HealthConnect tracks where the analytical findings can support their work.
7. Prepare the analysis for the next stage of the overall HealthConnect project.
