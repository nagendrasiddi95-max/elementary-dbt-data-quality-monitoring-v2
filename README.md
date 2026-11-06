
# elementary-dbt-data-quality-monitoring-v2

## Project Overview

This project demonstrates data quality monitoring using:

- dbt (Data Build Tool)
- Elementary
- ClickHouse
- SQL

The goal is to build dbt models, execute data quality tests, identify data issues, and demonstrate monitoring and alerting.

## Project Objectives

- Configure a dbt project.
- Connect dbt to ClickHouse.
- Build and execute dbt models.
- Run data quality tests.
- Identify issues such as NULL values.
- Demonstrate Elementary monitoring and alerting.

## Prerequisites

- Python
- dbt
- ClickHouse
- Elementary
- Git

## Project Setup

1. Clone the repository.
2. Open the project directory.
3. Create and activate a Python virtual environment.
4. Install the dependencies required by the project.
5. Configure the dbt profile for ClickHouse.

## Execution

Run these commands from the dbt project directory:

```bash
dbt debug
dbt deps
dbt run
dbt test
```

## Expected Results

- dbt connection validation completes successfully.
- Project dependencies are installed.
- dbt models execute successfully.
- Configured data quality tests report their results.
- Data quality issues can be investigated through test results.

## Project Structure

The project includes dbt model files, test configurations, Elementary package configuration, and monitoring-related settings.

## Resources

- dbt documentation: https://docs.getdbt.com/
- Elementary documentation: https://docs.elementary-data.com/
- ClickHouse documentation: https://clickhouse.com/docs
