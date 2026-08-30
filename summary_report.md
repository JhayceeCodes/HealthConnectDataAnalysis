# Week 4 Project Summary

## 1. Problem

HealthConnect Clinic is experiencing challenges with missed patient appointments and requires a better understanding of the factors associated with appointment attendance and no-shows.

The project focuses on using appointment data to identify patterns that can support improved appointment management and patient attendance.

## 2. Resources Used

The Week 4 analysis was based on:

- **HealthConnect Appointment Dataset** — 5,000 anonymised appointment records.
- **HealthConnect Data Dictionary** — definitions and context for the dataset variables.
- **Python** — primary analytical environment.
- **Pandas** — data loading, validation, and exploratory analysis.
- **Matplotlib / Seaborn** — planned for exploratory visualisation.

## 3. Key Observations

Initial data-quality assessment identified:

- 5,000 appointment records across 18 variables.
- No duplicate records or duplicate appointment IDs.
- Most variables contain complete observations.
- Missing values exist in `reminder_channel`, `distance_to_clinic_km`, and `waiting_time_minutes`.
- `None` values in `reminder_channel` represent appointments where no reminder was sent.
- Booking and appointment date fields require conversion to datetime for temporal analysis.

These observations informed the proposed analytical questions and approach.

## 4. Proposed Approach

The analysis will use descriptive and exploratory data analysis to investigate:

- Appointment attendance and no-show patterns.
- Reminder effectiveness and reminder coverage.
- The relationship between previous no-shows and current outcomes.
- Appointment volumes across days and time periods.
- The relationship between waiting time and appointment outcomes.
- Differences in outcomes across appointment types.

Analysis will primarily use frequency and proportion comparisons, grouped analysis, temporal analysis, and exploratory visualisations.

## 5. Key Considerations

The analysis will account for:

- Missing values in selected variables.
- The interpretation of `None` reminder channels as non-reminded appointments.
- Potentially small groups when comparing categories.
- The distinction between association and causation.
- The anonymised and synthetic nature of the patient data.
- Potential bias when comparing reminder channels if different patient or appointment groups receive different reminder methods.

## 6. Proposed Focus for Week 5

Week 5 will build on the exploratory findings by conducting deeper analysis of the identified attendance patterns and relationships.

The proposed focus is to:

1. Calculate and evaluate the identified KPIs.
2. Analyse the strongest relationships affecting appointment outcomes.
3. Develop relevant visualisations to communicate key findings.
4. Validate notable patterns through appropriate comparisons and segmentation.
5. Translate the findings into practical recommendations for improving appointment attendance and reminder processes.