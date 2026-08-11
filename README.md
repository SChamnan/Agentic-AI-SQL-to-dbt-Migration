# Google Sheet to GitLab Issue Agentic Skill

Below is the verbal documentation on how to create an agentic skill that convert each row in Google Sheet into a GitLab issue.

## Name and Description
- Name: name of the skill. In this case, it's gsheet-sql-issue-creator.
- Description: describe the purpose of the skill being created.

### Step 1: Read Google Sheet
The Google Drive connector is used to locate and read the tracking Goole Sheet. It focus on the columns needed to make decision in creating an issue per row.
- custom_SQL_ID (unique identifier)
- migration_candidate (boolean)
- final_score (numeric score per each query)
- query (text)
- converted (boolean)
- confirm (boolean)

### Step 2: Query Ranking
1. In the tracking Google Sheet, keep rows where the following conditions are met:
    - migration_candidate = TRUE
    - converted = FALSE
    - confirm = TRUE
2. Rank filtered rows by final_score
3. Tie-break by sheet row order position unless specify by users.
4. Rank in a descending order

### Step 3: Deduplicate Existing Issues
- Before creating an issue, check the target repository/project for issues that already exist
- Identify existing custom SQL query using custom_SQL_ID
- Skip any rows that has a matching custom_SQL_ID to prevent creating repeat issue

### Step 4: Confirm with Human before Creating Issue
- Never create issues without explicit user confirmation
- Ask "Create N number of issues for these queries?"
- Allow user to adjust the list before proceeding

### Step 5: Create One Issue per Query
- For each selected query, create an issue
- Loop over the selected rows and issue one per query
- Each issue must follow the pre-designed issue structure
    - Query Metadata
    - Query
### Step 6: Report
- Once issues are created, summarize to the user the following:
    - custom_SQL_ID
    - final_score
    - any skipped duplicates
    - link to each query

### Failture Handling:
High level explanation when encounter error during each session:
- No eligible rows --> report nothing match the condition in step 2
- A single issue creation fails --> continue with the rest and report which query fail and provide explanation of blockers
- Network Block --> explain that the repository is not reachable and show exact error then recommend how user can run themselves.
