# HealthConnect Executive Summary

## Overview

HealthConnect is a healthcare appointment management initiative focused on improving appointment attendance, clinic capacity utilisation, and patient experience.

This analysis examined appointment outcomes, booking behaviour, previous no-show history, reminder coverage, and operational patterns to identify factors associated with missed appointments and opportunities for improvement.

The core findings were independently validated and reviewed through cross-functional collaboration with the Data Science and GenAI teams.

---

## Business Objective

The analysis aims to help HealthConnect:

- Reduce missed appointments.
- Improve reminder coverage and patient engagement.
- Better manage appointment demand and booking pressure.
- Improve clinic capacity utilisation and patient experience.

The analysis identifies relationships and operational patterns in the available data; it does not establish causation.

---

## Key Performance Indicators

| KPI | Description |
|---|---|
| **No-Show Rate** | Proportion of appointments where the patient did not attend. |
| **Reminder Effectiveness Rate** | Attendance rate across reminder statuses and channels. |
| **Reminder Non-send Rate** | Proportion of appointments with no recorded reminder. |
| **Average Waiting Time** | Average recorded patient waiting time. |

The KPIs were independently recalculated and validated.

- **No-Show Rate:** 48.46%
- **Reminder Non-send Rate:** 27.32%

---

## Key Findings

### 1. Longer Booking Lead Times Are Associated With Higher No-Show Rates

No-show rates increased from **24.18% for appointments booked 0–2 days in advance to 60.49% for appointments booked 31+ days in advance**.

The relationship was statistically significant:

- χ² = 341.12
- df = 8
- p < 0.001
- Cramér's V = 0.185

This represents a modest association and should not be interpreted as evidence that longer lead times directly cause no-shows.

### 2. Previous No-Show Behaviour Is Associated With Future Appointment Outcomes

Previous no-show behaviour was significantly associated with current appointment outcomes:

- χ² = 83.38
- df = 10
- p < 0.001
- Cramér's V = 0.091

The relatively weak effect size suggests that previous no-shows are better considered alongside other appointment characteristics rather than as a standalone risk classification.

### 3. Higher-Risk Segments Combine Long Lead Times With Previous No-Shows

The highest observed no-show rates were concentrated among appointments with longer booking lead times and previous no-show history.

For example:

- **2 previous no-shows** + **31+ day lead time:** 71.20%
- **1 previous no-show** + **31+ day lead time:** 66.37%
- **0 previous no-shows** + **31+ day lead time:** 55.18%

These are analytical segments for monitoring and targeted engagement, not formal individual-level risk classifications.

### 4. Reminder Coverage Is Incomplete

No reminder was recorded for **27.32% of appointments**.

No-reminder rates remained relatively consistent across booking lead-time groups, suggesting that the higher no-show rates associated with longer lead times are not simply explained by lower reminder coverage.

### 5. Reminder Differences Are Observational

Observed attendance rates were:

| Reminder Status / Channel | Attendance Rate |
|---|---:|
| SMS | 49.60% |
| Email | 46.53% |
| WhatsApp | 44.60% |
| No reminder | 42.68% |

The differences are observational and do not establish that a particular reminder channel causes better attendance. Targeted testing would be required to assess intervention effectiveness.

---

## Analytical Validation

The core KPIs, findings, higher-risk segments, reminder analysis, and key visualisations were independently reproduced against the underlying dataset.

Cross-functional Data Science validation also identified a multicollinearity issue in the candidate feature set involving `previous_appointments`, `previous_no_shows`, and the derived `previous_no_show_rate`.

The feature set was refined by removing the collinear raw-count variables and retaining `previous_no_show_rate`. Its coefficient changed from **-0.106 to +0.195**, aligning with the validated Analytics finding without materially changing predictive performance.

Additional testing found negligible value from adding `booking_lead_group` or an explicit interaction between previous no-show rate and booking lead time once the continuous variables were included.

---

## Recommendations

Based on the validated findings, HealthConnect should:

1. **Improve reminder coverage** and monitor the reminder non-send rate.
2. **Target appointment engagement** around longer booking lead times and previous no-show history.
3. **Investigate virtual-care suitability** for appointment types that do not require in-person clinical procedures.
4. **Align staffing and resources** with periods of higher appointment demand.
5. **Collect patient feedback** to better understand barriers to attendance, appointment preferences, and patient experience.
6. **Measure intervention outcomes** rather than relying solely on observational relationships.

---

## Proposed Solution

HealthConnect could explore a combination of operational and digital interventions.

General Consultations and Follow-ups represent **70.14% of appointment volume**, making them important categories for investigating virtual-care suitability. Specialist Consultations may also be suitable in selected cases, while Diagnostic Tests would generally remain in-person.

In collaboration with the **GenAI team**, HealthConnect has proposed an AI-assisted virtual consultation solution for suitable appointment types. The solution could support structured information gathering, routine consultation workflows, communication, and escalation to healthcare professionals where in-person assessment is required.

The proposed solution is intended to **support clinical workflows, not replace clinical judgement**. Its effectiveness and suitability should be evaluated through controlled implementation, clinical oversight, patient feedback, and measurable operational outcomes.

---

## Limitations

- The dataset is observational and does not establish causation.
- Reminder channel comparisons may be influenced by how reminders were assigned.
- Higher-risk segments are group-level analytical patterns, not individual patient risk classifications.
- The dataset does not fully explain why patients miss or cancel appointments.
- The proposed virtual-care and GenAI solutions have not yet been evaluated through real-world implementation.
- Patient acceptance and experience require direct feedback.
- Predictive modelling should support operational decision-making rather than replace clinical judgement.

---

## Next Steps

1. Define suitable use cases for virtual consultations.
2. Develop and evaluate the proposed GenAI-assisted workflow with appropriate safeguards.
3. Collect structured patient feedback.
4. Pilot selected interventions with clear success metrics.
5. Monitor attendance, booking lead times, waiting times, reminder coverage, and patient experience.
6. Refine interventions based on measured outcomes and feedback.

---

## Conclusion

The HealthConnect analysis identified clear patterns associated with missed appointments, particularly longer booking lead times and previous no-show behaviour.

Independent validation confirmed the core analytical findings, while Data Science collaboration identified and corrected a multicollinearity issue in the predictive feature set.

The findings provide a basis for targeted engagement, improved reminder coverage, and exploration of virtual consultations for suitable appointment types. In collaboration with the GenAI team, a proposed AI-assisted consultation solution provides one potential avenue for reducing unnecessary in-person demand while improving access and patient experience.

The next priority is to move from validated findings to measured, patient-centred interventions.