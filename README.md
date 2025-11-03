# Customer IT Support Analysis

## Background and Overview

This project analyses an open-source IT support dataset sourced from Kaggle: [Customer IT Support - Ticket Dataset](https://www.kaggle.com/datasets/tobiasbueck/multilingual-customer-support-tickets).

The fictitious company dataset contains ticket metadata across departments, including priority, incident type, tags, and ticket text (subject, body, and agent response). The analysis uncovers patterns in workload distribution, urgency, and recurring issues, with the goal of improving operational resilience and the quality of support responses.

Key focus areas:
- Departmental workload distribution
- Analysis of the highest priority issues
- Ticket types and how they vary by department
- Most frequent tags used
- Repeated customer details requested in responses

An interactive Power BI dashboard is available [here](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/IT%20Support%20Dashboard.pbix).

The dataset used can be found [here](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Dataset/aa_dataset-tickets-multi-lang-5-2-50-version.csv).


## Data Structure Overview

The dataset contains 28,587 records with the following fields:

| Field    | Description                                      | Data Type |
|----------|--------------------------------------------------|-----------|
| Queue    | Department assigned to ticket                    | String    |
| Priority | Urgency of the issue (low, medium, high)         | String    |
| Language | Ticket language                                  | String    |
| Version  | Application version used                         | Number    |
| Subject  | Customer email subject                           | String    |
| Body     | Customer email body                              | String    |
| Answer   | Agent response                                   | String    |
| Type     | Ticket type (Incident, Request, Problem, Change) | String    |
| Tags     | Tags/categories assigned (10 columns in dataset) | String    |

For this analysis, the following amendments were made:
- Filtered to English-language tickets only (16,338 records; 42.9% reduction).
- Removed formatting artefacts (line breaks) from text fields.

### Representativeness Check
Before analysis, we validated that the English-only subset remained representative of the full dataset. To test whether filtering introduced sampling bias in English-language tickets (16,338 of 28,587 records), we compared the distributions of priority, type, and queue between the full and English-only datasets. Differences were minimal: total absolute proportion shifts were below 1.3 percentage points across all variables, and the largest single-category difference was 0.44 points for Product Support in queue. Chi-square tests showed no statistically significant divergence (p > 0.8 for all), and Cramér’s V values < 0.01 indicate negligible effect sizes. We therefore consider the English subset representative of the overall dataset for these top-level dimensions, with only trivial over-representation of Product Support tickets.


## Executive Summary

We analysed 16,338 English-language tickets. The findings show a high concentration of urgent work, pressure on Technical Support, and recurring requests for the same customer details.

- Workload concentration: Technical Support handles 4,737 of 16,338 tickets (29.0%), including 43.5% of all high-priority issues. This creates a single-point bottleneck.

- High-priority prevalence: 38.8% of all tickets are marked high priority — unusually high, suggesting recurring systemic issues rather than rare emergencies.

- Incident dominance: 40.2% of tickets are classified as Incidents (unplanned interruptions/reduced IT service quality).

- Tags: Most frequent tags (Tech Support, IT, Performance) highlight repeated usability and performance problems.

- Repeated details: Agents often request the same data (account numbers, software versions, error messages, transaction logs, contact numbers), creating delays and unnecessary back-and-forth.

Implication: Without intervention, Technical Support remains overloaded, urgent tickets dominate effort, and resolution speed suffers. Standardising intake, cross-training other teams, and addressing recurring issues will reduce risk and improve efficiency.

Below is the overview page from the Power BI dashboard, and more examples are included throughout the report.

![Executive overview](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Executive%20Overview.png)


## Insights Deep Dive

The second page of the dashboard shows a workload breakdown by department for priorities, incident types, and assigned tags. This page would be helpful for an IT manager to review the allocation of tasks for their various teams, ensuring each team has a balanced workload to avoid one particular team being burdened with too many urgent, critical problems all at once.

![Workload](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Workload.png)

The third page of the dashboard shows further supporting information relating to the assigned tags. Here, the IT manager can view the total number of a specific tag used, the number of live application versions in use, the correspondence between incident types and priorities, and example responses from their staff. 

![Tags & Themes](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Tags%20%26%20Themes.png)


### Department Workload & Priority

- Technical Support: 4,737 tickets (29.0%), of which 58.3% are high priority. Handles 43.5% of all high-priority tickets.

- IT Support: 938 high-priority tickets, representing 30.5% of their workload. Distribution is more balanced across priority levels.

- Product Support: 899 high-priority tickets (14.2%), but primarily handles medium-priority work (1,575; 51.3% of workload).

- Customer Service: 1,121 medium-priority tickets (46.5% of workload) and 837 low-priority tickets (34.7%). This aligns with their role handling simpler, lower-urgency requests.

Insight: Technical Support is disproportionately exposed to urgent issues, while Product Support and Customer Service focus more on medium and low-priority requests. This imbalance risks burnout in Technical Support and potential delays in critical cases.


### Incident Types by Department

Ticket types: Change, Incident, Problem, Request.

- Technical Support: 2,460 Incidents (51.9% of workload), including 1,444 high-priority cases (52.3% of their critical work).

- Product Support: 1,383 Incidents (45.0% of workload), with most at medium priority (49.5%).

- Problem-type tickets: Technical Support handles 1,023 (596 high-priority; 58.3% of their Problem workload). Product Support resolves 666 Problems, mostly medium priority (327; 49.1%).

Insight: Pattern is consistent with escalation from Product Support (medium priority) to Technical Support (high priority). While causality cannot be confirmed without timestamps, the distribution suggests a tiered resolution model.


### Tags

- Top tags overall: Tech Support (12.5%), IT (12.1%), Performance (9.8%).

- By department: Technical Support, Product Support, Customer Service, and IT Support are the main handlers of performance-related issues.

Insight: Performance issues dominate across multiple teams, pointing to recurring technical instability.


### Text Analysis

Analysis of high-priority tickets shows repeated agent requests for the same customer details:

- Billing system: account numbers, incorrect charges, transaction logs, customer contact details.

- Server load / deployment access: error messages, recent updates, system symptoms.

- Code/data issues: software version, configuration details, API updates, error logs, network status, contact number.

Insight: Lack of structured intake fields forces agents to repeatedly chase for critical details, extending resolution time.


## Recommendations

### Quick Wins (0–4 weeks)

1. Mandatory intake fields → Require account number, software version, error message, and contact phone number at ticket creation.

- Impact: fewer follow-up emails, faster first response.

- Measure: average agent follow-up requests (target -30%).

2. Response templates / macros → Pre-built responses for top recurring issues (password reset, billing, VPN, performance).

- Impact: greater consistency, reduced handling time.

- Measure: first-contact resolution rate (target +15%).

3. Knowledge base “Top 5 Issues” → Self-service articles for most frequent tags.

- Impact: diverts common queries away from support teams.

- Measure: volume reduction in those tags (-20% in 2 months).


### Mid-Term (1–3 months)

4. Cross-train Product Support → Equip Product Support to resolve selected medium-priority incidents directly.

- Impact: reduces Technical Support escalations.

- Measure: % escalations Product → Technical (-25%).

5. Tag standardisation → Merge duplicates/synonyms and implement auto-suggest tagging.

- Impact: cleaner reporting, better routing.

- Measure: reduction in manual tag corrections.

6. Process dashboard → Add Power BI views for workload by priority/type, % high-priority load, and tag trends.

- Impact: improves visibility and planning.

- Measure: manager adoption, frequency of usage.


### Strategic (3–12 months)

7. Service quality metrics → Define targets for high-priority share (<15%), backlog size, and ticket mix.

- Impact: establishes clear service expectations.

- Measure: SLA compliance rate.

8. Performance monitoring integration → Correlate system telemetry with performance-tagged incidents.

- Impact: detect root causes earlier, reduce reactive tickets.

- Measure: % performance-tagged incidents correlated with known system events.


## Implementation Roadmap

Weeks 0–4 (Ops Manager)

- Configure intake form fields.

- Deploy top 5 response templates.

- Publish knowledge base articles.

Weeks 5–12 (Training Lead / IT Ops)

- Deliver Product Support training for medium-priority incidents.

- Begin tag taxonomy clean-up.

- Launch Power BI workload dashboard.

Months 3–12 (Data/Engineering)

- Formalise SLA metrics.

- Explore telemetry → incident correlation.

- Report on ROI of interventions (time saved, cost avoidance).











