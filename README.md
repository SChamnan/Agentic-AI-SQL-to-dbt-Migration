# GitLab Business Intelligence: Centralizing Enterprise Logic
**Summary:** Migrating Tableau custom SQL into version-controlled dbt model via an agentic-AI workflow with customer Claude Skills.
## **Overview**
Hundreds of custom SQL queries live on Tableau, each in their respective workbook. The problem is these queries cannot be tracked and monitored, making any upstream source changes silently break downstream queries. Ultimately, creating either outdated or inaccurate dashboards and reports both at department and company levels. Therefore, our goal in the first phase is to dbt-tized high value customer SQL to dbt models which can be tracked monitored and reconfigured whenever needed.
## **Objectives**
- **Identify** and **prioritize** the highest-value custom SQL for migration
- **Design** a repeatable custom SQL to dbt conversion pipeline
- **Repoint** Tableau workbooks to certified dbt source
## **Data and Tools**
Hundreds of custom SQL queries embedded across Tableau workbooks, some with multiple queries per workbook, supporting critical reports and dashboards used across departments
Tools:
- Claude Skills
- OpenCode
- Excel
- Tableau
- GitLab
- SQL
- dbt
## **Methodology**
- Evaluated and scored custom SQL queries using weighted model
- Created a non-duplicated GitLab issue per each eligible custom SQL query
- Triggered two agents to convert each custom SQL query in each GitLab issue to dbt code model and generate a merge request to be reviewed and approved by human (keeping human in the loop for final approval)
## **Key Insights**
- Our workflow was adopted by the data team and serves as a single, reusable pipeline that many developers can build on at once.
- By moving custom SQL queries to dbt models, duplicates issue is eliminated
- Migration effort dropped by 80%
- Created a centralized source of truth that everyone can reference from and trace back
## **Business Value**
- **Reliability:** Upstream changes no longer silently break dashboards and reports because each SQL query now lives in dbt model which can tracked, monitored instead of hidden inside each workbook
- **A single source of truth:** teams across departments reference the same certified models, so metrics stay consistent and accurate
- **Faster, scalable migration:** a reusable pipeline allows the data team to covert queries in parallel, reducing migration effort by 80%
- **Safe use of AI:** agents do the repetitive conversion work while human review and approve final change in each merge request.
## **Team**
**Faculty Advisor:** Mohannad Elhamod

Chamnan Suon **|** 
Mokhinur Talibzhanova **|** 
Quency Ye
