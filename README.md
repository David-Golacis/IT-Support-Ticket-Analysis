# Customer IT Support Analysis

## Background and Overview

An open-source customer IT support dataset for a global brand has been obtained from Kaggle. Please find the dataset linked here: [Customer IT Support - Ticket Dataset](https://www.kaggle.com/datasets/tobiasbueck/multilingual-customer-support-tickets).

The fictitious company has significant amounts of data for its application across various departments, including priority of issues, types of tickets, assigned tags/categories, and queries' subjects, bodies, and answers. This project thoroughly analyses and synthesises this data to uncover critical insights that will improve the business's quality of responses.

Insights and recommendations are provided on the following key areas:
- Evaluation of departmental workload distribution
- An analysis of the highest priority issues
- An assessment of the most frequent tags used
- Identification of commonly requested details in ticket responses

An interactive Power BI dashboard can be downloaded [here](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/IT%20Support%20Dashboard.pbix).

The dataset used can be found [here](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Dataset/aa_dataset-tickets-multi-lang-5-2-50-version.csv).


## Data Structure Overview

The Customer IT Support dataset consists of one table with 28,587 records. Shown below is the structure of the database.

| Field    | Description                                                                   | Data Type |
|----------|-------------------------------------------------------------------------------|-----------|
| Queue    | Specifies the department to which the email ticket is routed                  | String    |
| Priority | Indicates the urgency and importance of the issue                             | String    |
| Language | Indicates the language in which the email is written                          | String    |
| Version  | Designates the version of the application used                                | Number    |
| Subject  | Subject of the customer's email                                               | String    |
| Body     | Body of the customer's email                                                  | String    |
| Answer   | The response provided by the helpdesk agent                                   | String    |
| Type     | The type of ticket as picked by the agent                                     | String    |
| Tags     | Tags/categories assigned to the ticket, split into ten columns in the dataset | String    |

For this analysis, the following amendments were made:
- The language column was filtered for English-only responses
- From the queries' bodies and answers, the linebreak code, \n\n, was removed

This helped clarify the information, ensuring that all data points were clear and readable. This reduced the number of records to 16,338, a reduction of 42.85%.


## Executive Summary

Key performance indicators show that the Technical Support department handles the majority of tickets by volume, 4,737, of the 16,338 total tickets raised, equating to 28.99%. From the total number of issues, 38.84% have been marked as high-priority incidents, indicating urgency and importance to the business. Additionally, 40.22% of problems have been assigned the incident type by an agent, showing that issues were related to unplanned interruption or a reduction in the quality of an IT service that directly impacts users' ability to perform their jobs. To further support this, the top 3 tags across all records signify concerns with the application's usability: Tech Support, IT, and Performance.

Below is the overview page from the Power BI dashboard, and more examples are included throughout the report.

![Executive overview](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Executive%20Overview.png)


## Insights Deep Dive

The second page of the dashboard shows a workload breakdown by department for priorities, incident types, and assigned tags. This page would be helpful for an IT manager to review the allocation of tasks for their various teams, ensuring each team has a balanced workload to avoid one particular team being burdened with too many urgent, critical problems all at once.

![Workload](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Workload.png)

The third page of the dashboard shows further supporting information relating to the assigned tags. Here, the IT manager can view the total number of a specific tag used, the number of live application versions in use, the correspondence between incident types and priorities, and example responses from their staff. 

![Tags & Themes](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Tags%20%26%20Themes.png)


### Priority Breakdown

The Technical Support department accounted for 43.51% (2,761) of all high-priority issues, with the next most significant number of responses coming from IT Support and Product Support at 14.78% (938) and 14.17% (899), respectively. These high-priority issues made up 58.29% of the Technical Support team's responses, indicating potential bottlenecks for the business if resources were suddenly strained.

![Dept vs Priority](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Dept%20vs%20Priority.png)

The IT Support team actioned the second greatest number of high-priority requests, contributing to 30.52% of their workload. This shows that the IT Support team has a more balanced distribution of load across its three priority queues compared to the Technical Support team. If the number of their issues were to increase, the team would have the capacity to take the burden and succeed, as there is room for growth.

Although the Product Support department handles the third-highest number of high-priority tickets, it acts on the most medium-priority requests, totalling 1,575 tickets. These medium requests equate to 51.25% of their load. In contrast, the Technical Support team handles 1,442 medium tickets, resulting in 30.44% of their workload being of 2nd order priority. These figures may indicate the Product Support team's immaturity, as they are handling 1.75 times more medium-priority tasks compared to their high-priority tickets.

Digging deeper into the middle of the table figures, the Customer Service team shows that they responded to 1,121 medium tickets, equalling 46.51% of their workload, giving them the third longest queue of items to action of this priority. This is in addition to the Customer Service department actioning the largest number of low-priority tickets at 837, accounting for 34.73% of their responses. However, despite this imbalance of actions, it does make sense that the Customer Service team responds more frequently to lower-priority issues due to the nature of the role and how they tie in with the other departments. They are expected to handle simpler queries, enabling the more technical teams to spend the majority of their time and effort in resolving urgent problems for end-users.


### Incident Types Analysis

The incidents column in this dataset features four attributes: change, incident, problem, and request. These types correlate to both the severity and type of issue the end-user is experiencing.

![Incidents by Dept & Type](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Incidents%20by%20Dept%20%26%20Type.png)

The Technical Support department responded to 2,460 Incident tickets, accounting for 51.93% of their total responses. This indicates that the team's primary focus is on resolving unplanned interruptions or reductions in IT service quality. Filtering by priority reveals that this team actioned 1,444 high-priority Incident tickets, resulting in 30.48% of their total workload and 52.30% of their critical actions.

![Technical Support Incidents](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Technical%20Support%20Incidents.png)

The next largest number of Incident tickets, 1,383, was responded to by the Product Support department, making up 45.00% of their total responses. Investigating this figure further unveiled that the majority of responses came under medium priority, equating to 49.53% of their Incident tickets. This is in contrast to the Technical Support team, which handled medium-priority tickets of Incident type 29.72% of the time.

![Product Support Incidents](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Product%20Support%20Incidents.png)

One can conclude from this that issues escalate from the Product Support team to the Technical Support team, as there are apparent differences in what each team prioritises. A similar story is present within the Problem-type tickets, where the Technical Support team actioned 1,023 requests, while the Product Support team followed with the next highest number at 666. Looking further into these two figures showed that the Technical Support team responded to 596 high-priority Problem tickets, making up 58.26% of their responses for this incident type, while the Product Support team resolved 327 medium-priority tickets of the same type, taking up 49.10% of their effort with Problem requests.

![Problem Tickets](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Problem%20Tickets.png)


### Tags per Department

Sifting through the assigned categories reveals that the three most common tags used across all tickets were Tech Support (9,597; 12.50%), IT (9,320; 12.14%), and Performance (7,536; 9.82%). This reveals that the end-users are experiencing a significant number of issues with the application's performance.

![Total Tags](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Total%20Tags.png)

Grouping these tags by department reveals that the Technical Support, Product Support, Customer Service, and IT Support departments primarily address these concerns.

![Tags per Department](https://github.com/David-Golacis/IT-Support-Dashboard/blob/main/Visuals/Tags%20per%20Department.png)


## Recommendations

































