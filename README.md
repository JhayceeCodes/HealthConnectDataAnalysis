# HealthConnect Appointment Analysis

Exploratory and advanced analysis of the HealthConnect appointment dataset, focused on understanding appointment attendance, identifying patterns associated with no-shows, validating key relationships, and generating actionable business insights.

This project forms part of the **Data Analytics track at Analyst Lab Africa**, using Python to move from initial data assessment and analytical planning into exploratory analysis, deeper analytical validation, and decision support.

---

## Project Objectives

The analysis focuses on understanding:

- Appointment attendance and no-show patterns.
- The relationship between previous no-show behaviour and current outcomes.
- The relationship between booking lead time and appointment outcomes.
- Appointment attendance across reminder channels and appointments without reminders.
- Reminder coverage across different booking lead-time groups.
- Higher-risk appointment segments based on booking lead time and previous no-show behaviour.
- Appointment demand across days and time periods.
- Waiting time and its relationship with appointment outcomes.
- Differences in outcomes across appointment types and patient characteristics.
- Potential operational opportunities for improving appointment attendance.

---

## Dataset

The HealthConnect dataset contains:

- **5,000 appointment records**
- **18 variables**
- Appointment, patient, reminder, scheduling, accessibility, and outcome information.

Key variables include:

| Category | Variables |
|---|---|
| Appointment | `appointment_id`, `appointment_type`, `appointment_date`, `appointment_day`, `appointment_time` |
| Patient | `patient_id`, `gender`, `age`, `age_group` |
| Booking History | `booking_date`, `booking_lead_days`, `previous_appointments`, `previous_no_shows` |
| Reminders | `reminder_sent`, `reminder_channel` |
| Accessibility | `distance_to_clinic_km`, `waiting_time_minutes` |
| Outcome | `appointment_outcome` |

The dataset is synthetic and anonymised.

---

## Analysis Process

The analysis was conducted using:

- **Python**
- **Pandas**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook**

The workflow included:

1. Data validation and quality checks.
2. Data type preparation.
3. Missing-value investigation.
4. Exploratory data analysis.
5. KPI calculation.
6. Comparative analysis across relevant variables.
7. Deeper analysis of booking lead time and previous no-show behaviour.
8. Higher-risk segment analysis.
9. Reminder coverage and effectiveness analysis.
10. Statistical validation using Chi-square tests and Cramér's V.
11. Visualisation and interpretation.
12. Business insight generation.
13. Recommendations and limitation assessment.
14. Cross-track analytical handoff to Data Science.
15. Independent KPI and analytical finding validation.
16. Visualisation validation and refinement.
17. Cross-track model validation and analytical refinement.
18. Retesting and final validation.

Missing `reminder_channel` values were interpreted as **"No reminder"**, based on the dataset's data dictionary.

---

## Key KPIs

| KPI | Description |
|---|---|
| **No-Show Rate** | Proportion of appointments resulting in a no-show. |
| **Reminder Effectiveness Rate** | Attendance rate across reminder statuses/channels. |
| **Reminder Non-send Rate** | Proportion of appointments that did not receive a reminder. |
| **Average Waiting Time** | Average recorded waiting time for appointments. |

---

## Key Findings

### 1. No-shows are a major attendance challenge

No-shows represent approximately **48%** of all appointments, making them the most common appointment outcome.

### 2. Booking lead time is associated with no-show behaviour

No-show rates increased consistently as booking lead time increased.

Appointments booked **0–2 days in advance** had a no-show rate of approximately **24%**, compared with approximately **60%** for appointments booked **31+ days in advance**.

A Chi-square test confirmed a statistically significant association between booking lead time and appointment outcome (`p < 0.001`), with a Cramér's V of **0.185**, indicating a modest association.

### 3. Previous no-show history remains relevant

Patients with previous no-shows generally showed higher current no-show rates.

The relationship between previous no-show history and appointment outcome was statistically significant (`p < 0.001`), although the Cramér's V of **0.091** indicates a relatively weak association.

This suggests that previous no-show behaviour can provide useful context when assessing appointment attendance, but should not be considered in isolation.

### 4. Combining booking lead time and previous no-shows identifies higher-risk segments

Combining booking lead time with previous no-show history revealed several appointment segments with substantially higher observed no-show rates.

Longer booking lead times were associated with higher no-show rates even among patients without previous no-shows, while the combination of longer lead times and previous no-show history produced some of the highest observed rates.

These segments should be treated as **higher-risk groups identified through the analysis**, rather than as formal predictive risk categories.

### 5. Reminder coverage has room for improvement

Approximately **27.3%** of appointments did not have a recorded reminder.

Reminder coverage was relatively consistent across booking lead-time groups, with approximately 26–28% of appointments in each group having no recorded reminder.

### 6. Reminder coverage and channel differences require further testing

Within the higher-risk appointment segments analysed, the no-reminder group recorded a no-show rate of approximately **61%**, compared with approximately **55% for SMS**.

Although SMS recorded the lowest no-show rate among the reminder channels in these segments, the differences between individual reminder channels were relatively modest.

The findings therefore support improving reminder coverage and testing targeted reminder strategies, rather than selecting a single channel based on these observational results.

### 7. Appointment demand is concentrated in the morning and afternoon

Most appointments occur during the morning and afternoon, while evening appointment volumes are considerably lower.

Daily appointment volumes are relatively similar, although **Monday morning** records the highest individual day-time appointment volume.

### 8. Several factors show limited differentiation

Waiting time, appointment type, and age group show relatively similar outcome distributions across their respective categories.

Distance to the clinic shows slightly higher median values for no-show and cancelled appointments, but the distributions overlap considerably.

---

## Statistical Validation

Two key relationships identified during the deeper analysis were statistically tested:

| Relationship | Chi-square | Cramér's V | Interpretation |
|---|---:|---:|---|
| Booking Lead Time × Appointment Outcome | 341.12 | 0.185 | Statistically significant, modest association |
| Previous No-Shows × Appointment Outcome | 83.38 | 0.091 | Statistically significant, relatively weak association |

Both relationships were statistically significant at `p < 0.001`.

The results provide additional support for the patterns observed during the exploratory and deeper analysis. Booking lead time showed the stronger association of the two variables tested.

---

## Selected Visualisations

### Appointment Outcomes

![Appointment Outcomes](images/appointment_outcomes.png)

The distribution of attended, no-show, and cancelled appointments, highlighting the high proportion of no-show appointments.

### Appointment Outcomes by Reminder Status/Channel

![Appointment Outcomes by Reminder Status](images/reminder_outcomes.png)

Comparison of appointment outcomes across SMS, Email, WhatsApp, and appointments without a reminder.

### Appointment Outcomes by Previous No-Shows

![Appointment Outcomes by Previous No-Shows](images/previous_no_shows.png)

Shows the increasing no-show proportion associated with higher previous no-show counts.

### Appointment Volume by Day and Time

![Appointment Volume by Day and Time](images/appointment_volume_heatmap.png)

Shows how appointment demand is distributed across days of the week and time periods.

---

## Business Recommendations

Based on the validated analysis:

- **Improve reminder coverage** by reducing the proportion of appointments without recorded reminders.

- **Prioritise targeted reminder interventions** for appointments with longer booking lead times and previous no-show history.

- **Avoid relying on a single reminder channel.** Although SMS recorded the lowest no-show rate among reminder channels within the higher-risk segments, the differences between channels were relatively modest and observational.

- **Investigate reasons for repeated no-shows** through patient feedback or targeted surveys rather than assuming the underlying causes.

- **Use booking lead time as an additional monitoring dimension** when identifying appointments that may require greater attention.

- **Align staffing and resources with appointment demand**, particularly during morning and afternoon periods.

- **Monitor attendance outcomes after interventions** to determine whether changes in reminder coverage or strategy produce measurable improvements.

These recommendations are based on observed associations and predictive signals in the dataset. They should be validated through controlled intervention testing or appropriate real-world operational data before drawing causal conclusions.

---

## Cross-Track Contribution

### Data Analytics → Data Science

The validated Analytics findings were provided to the **Data Science track** for independent modelling validation.

The handoff highlighted:

- Booking lead time as a candidate modelling feature.
- Previous no-show history as an additional candidate feature.
- Higher-risk combinations of booking lead time and previous no-show history.
- Reminder coverage as an important consideration.
- Reminder channel outcomes within higher-risk segments.

The Data Science track used these findings to develop and evaluate a no-show prediction model.

The modelling confirmed that **booking lead time and previous no-show behaviour contained useful predictive signal**. Cross-track validation also identified a multicollinearity issue in the Week 6 candidate feature set, where `previous_appointments`, `previous_no_shows`, and the derived `previous_no_show_rate` were included simultaneously.

Removing the collinear raw-count variables and retaining `previous_no_show_rate` corrected the coefficient direction from **-0.106 to +0.195**, while predictive performance remained effectively unchanged.

Further testing showed that:

- `booking_lead_group` was redundant for predictive modelling when continuous `booking_lead_days` was included.
- An explicit interaction between `previous_no_show_rate` and `booking_lead_days` provided negligible additional predictive value.
- Reminder variables provided statistically significant additional predictive information beyond lead time and patient history, while remaining non-causal evidence.

The refined candidate feature set is:

`booking_lead_days` + `previous_no_show_rate` + `is_new_patient` + `reminder_sent` + `reminder_channel`

The cross-track validation therefore not only supported the analytical findings but also resulted in a refinement of the Data Science modelling approach.

---

## Limitations

- The dataset is **synthetic and anonymised**, so findings may not fully represent real-world patient behaviour or clinic operations.

- The analysis identifies associations but does not establish causal relationships.

- Some higher-risk segments contain relatively small numbers of appointments, making their observed rates more variable and requiring cautious interpretation.

- Reminder channel comparisons may be influenced by differences in the types of patients or appointments receiving each channel.

- Reminder data indicates the recorded reminder channel but does not establish whether a patient received, opened, or engaged with the reminder.

- `distance_to_clinic_km` and `waiting_time_minutes` contain a small number of missing observations.

- The dataset does not contain potentially relevant context such as reasons for missed appointments, patient satisfaction, health status, or socioeconomic circumstances.

- The higher-risk segments identified in the analysis are not predictive risk classifications. Further modelling and validation are required before using them for automated risk prediction or intervention.

---

## Week 8 Next Steps

The next stage of the HealthConnect project will focus on **Final Integration → Presentation**.

Planned activities include:

- Integrate the validated Analytics and Data Science outputs into the wider HealthConnect solution.
- Consolidate the final KPIs, validated findings, and recommendations.
- Ensure consistency between the analytical findings and the refined Data Science model.
- Finalise dashboards, visualisations, and presentation materials.
- Review project documentation across the different tracks.
- Prepare and deliver the final HealthConnect project presentation.

The overall objective is to move from **validated analytical work toward a coherent, integrated, and presentation-ready HealthConnect solution**.

---

## Project Structure

```text
.
├── README.md
├── data
│   ├── HealthConnect_Appointment_Data.csv
│   └── HealthConnect_Data_Dictionary.xlsx
├── healthconnect_analysis.ipynb
├── healthconnect_testing.ipynb
└── summary_report.md
```