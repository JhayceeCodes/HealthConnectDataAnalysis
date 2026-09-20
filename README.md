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

No-shows represent approximately **47.5%** of all appointments, making them the most common appointment outcome.

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

### 6. Reminder coverage may be more important than channel choice

Within the higher-risk appointment segments analysed, the no-reminder group recorded a no-show rate of approximately **61%**, compared with approximately **55% for SMS**.

Although SMS recorded the lowest no-show rate among the reminder channels in these segments, the differences between individual channels were relatively modest.

Therefore, the analysis does not establish that one reminder channel is substantially more effective than another. The findings instead support further investigation into **reminder coverage and targeted reminder strategies**.

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

Based on the analysis:

- **Improve reminder coverage** by reducing the proportion of appointments without recorded reminders.

- **Prioritise targeted reminder interventions** for appointments with longer booking lead times and previous no-show history.

- **Avoid relying on a single reminder channel.** Although SMS recorded the lowest no-show rate among reminder channels within the higher-risk segments, the differences between channels were relatively modest.

- **Investigate reasons for repeated no-shows** through patient feedback or targeted surveys rather than assuming the underlying causes.

- **Use booking lead time as an additional monitoring dimension** when identifying appointments that may require greater attention.

- **Align staffing and resources with appointment demand**, particularly during morning and afternoon periods.

- **Monitor attendance outcomes after interventions** to determine whether changes in reminder coverage or strategy produce measurable improvements.

These recommendations are based on observed associations in the dataset and should be validated through further testing, predictive modelling, or real-world operational data.

---

## Cross-Track Contribution

### Data Analytics → Data Science

The validated Week 6 findings were provided to the **Data Science track** to
support modelling of appointment no-show behaviour.

The handoff highlighted:

- Booking lead time as a candidate modelling feature.
- Previous no-show history as an additional candidate feature.
- Higher-risk combinations of booking lead time and previous no-show history.
- Reminder coverage as an important consideration.
- Reminder channel outcomes within higher-risk segments.

The Data Science team used these findings to develop and evaluate a no-show
prediction model. The modelling results confirmed that **booking lead time and
previous no-show history contained the main predictive signal** in the dataset,
while a more complex feature set did not provide additional benefit.

The modelling process also identified **`previous_no_show_rate`** as a useful
derived feature for future analytical work.

The resulting model achieved a ROC-AUC of approximately **0.69** and is
intended for **risk ranking and triage rather than automated decision-making**.
The Data Science findings provide a further basis for testing targeted
reminder strategies in the next stage of the HealthConnect project.

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

## Week 7 Next Steps

The next stage of the analysis will focus on **analytical testing and decision support**.

Planned activities include:

- Validate the identified higher-risk segments using additional statistical or modelling approaches.
- Evaluate reminder strategies within higher-risk appointment groups.
- Test the relationship between reminder coverage and appointment outcomes.
- Compare reminder channels while accounting for relevant patient and appointment characteristics where possible.
- Review Data Science model outputs against the analytical findings.
- Evaluate feature importance and model performance.
- Measure practical changes in no-show rate, attendance rate, and reminder coverage where intervention or test data becomes available.

The overall objective is to move from **identifying and validating higher-risk patterns toward testing whether targeted interventions can produce measurable improvements in appointment attendance**.

---

## Project Structure

```text
.

├── README.md

├── data
│   ├── HealthConnect_Appointment_Data.csv
│   └── HealthConnect_Data_Dictionary.xlsx

├── healthconnect_analysis.ipynb

└── summary_report.md