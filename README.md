# HealthConnect Appointment Analysis

Exploratory data analysis of the HealthConnect appointment dataset, focused on understanding appointment attendance and identifying factors associated with no-shows.

As part of the Week 4 Data Analytics track at the Analyst Lab Africa internship, this project uses Python to assess data quality, explore appointment patterns, define relevant KPIs, and establish the direction for subsequent analysis.

## Project Objectives

The analysis aims to investigate:

- Appointment attendance and no-show behaviour
- The relationship between previous no-shows and current outcomes
- Reminder effectiveness and non-reminder appointments
- Appointment volume across days and time periods
- The relationship between waiting time and appointment outcomes
- Differences in outcomes across appointment types

## Dataset

The project uses a synthetic and anonymised HealthConnect appointment dataset containing **5,000 appointment records and 18 variables**.

Key data areas include:

- Patient demographics
- Appointment details
- Booking information
- Previous appointment history
- Reminder information
- Distance to clinic
- Waiting time
- Appointment outcomes

A supporting data dictionary is provided to document the dataset variables and their definitions.

## Week 4 Highlights

Initial data quality assessment found:

- 5,000 appointment records
- No duplicate records or duplicate appointment IDs
- Missing values in `reminder_channel`, `distance_to_clinic_km`, and `waiting_time_minutes`
- Booking and appointment dates currently require datetime conversion for time-based analysis
- `reminder_channel` is recorded as `None` when no reminder was sent

The initial analysis also identified five potential KPIs:

- No-Show Rate
- Reminder Effectiveness Rate
- Reminder Non-send Rate
- Average Waiting Time
- Appointment Volume

## Deliverables

| File | Description |
|---|---|
| [`healthconnect_analysis.ipynb`](healthconnect_analysis.ipynb) | Python notebook containing the Week 4 analysis, data-quality assessment, business questions, KPIs, and initial analytical approach |
| [`summary_report.md`](summary_report.md) | Concise project summary covering the problem, observations, proposed approach, considerations, and Week 5 focus |
| [`HealthConnect_Appointment_Data.csv`](data/HealthConnect_Appointment_Data.csv) | Source appointment dataset |
| [`HealthConnect_Data_Dictionary.xlsx`](data/HealthConnect_Data_Dictionary.xlsx) | Dataset definitions and supporting documentation |

## Project Structure

```text
.
|-- README.md
|-- data
|   |-- HealthConnect_Appointment_Data.csv
|   `-- HealthConnect_Data_Dictionary.xlsx
|-- healthconnect_analysis.ipynb
`-- summary_report.md
```

## Tools & Technologies
- Python
- Pandas
- Jupyter Notebook


## Next Steps
Week 5 will build on the initial assessment by conducting deeper exploratory analysis of the identified business questions and KPIs, followed by visualisation of key patterns and development of evidence-based recommendations.