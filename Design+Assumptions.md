# Project Notes

## Setup and Running
- Detailed setup and running instructions can be found in the `README.md` file.
- If you want to see the results of the analytics queries, you need to add logic to print the results. I didn’t include this by default as I wasn’t sure if you wanted the results printed.
- The SQL queries are located under the `sql` folder, as requested.

## Question About Data
- **How to Calculate Launch Delays**: 
  I couldn’t find any clear information on how to calculate delays in the launches. If there’s a way to calculate it, I’d be happy to try implementing it. Let me know if you have any ideas or data points related to this.

## Design and Assumptions

### Design
- You provided the local data environment tools: **Postgres** and **Trino**. These are used as the primary data tools for this project.
- There only way to use trime tavel(like in iceberg) is to save the aggregated data with is_current value.
- The code should be runnable this scheduler like Airflow or any other scheduler.
- The code should be easy to add more logic and tables and need to be clear how to do that.

### Assumptions
1. **Ingestion**:
   - The ingestion process is implemented in Python and uses **Postgres** exclusively.
   - This separation ensures that ingestion and analytics are handled independently and for easy conrol on new devlopment features.

2. **Analytics**:
   - The analytics process uses **Trino** for executing queries, leveraging its strengths for analytics workloads and in memmpry calculations.
   - NOTE: I didng know if i should create tables or something from the analytics resaults.


### ETL Design
- The ETL process is designed with main tables:
  1. **Launches**: 
     - This table is appended with new rows on every run.
     - NOTE: history data can be insert using commented code for testing perposes.
  2. **Payloads**:
     - Contains payload-specific data to support analytics queries.
  3. **Launchpad**:
     - Stores launchpad-related data to enrich the analytics process.
  4. **Aggregation Table**:
     - The aggregation table is updated on every run.
     - It includes a column `is_current` to indicate whether a value is up-to-date or not.

## Additional Notes
- I didn’t want to send an email on Shavuot, so I included this information here instead. Let me know if you need further clarification or additional details.
