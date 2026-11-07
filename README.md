# Elementary + dbt Data Quality Monitoring with ClickHouse

## 1. Project Overview

This project demonstrates an end-to-end data quality monitoring workflow using **dbt, Elementary, ClickHouse, and SQL**.

The project builds dbt models, executes data quality tests, identifies data quality issues, and generates an Elementary observability dashboard.

The sample dataset intentionally contains a NULL value to demonstrate how data quality tests detect invalid records.

## 2. Project Objectives

- Configure a dbt project with ClickHouse.
- Build and execute SQL-based dbt models.
- Implement data quality tests.
- Detect NULL values using dbt tests.
- Monitor model execution and test results with Elementary.
- Generate a local data observability report.

## 3. Technologies Used

| Technology | Version / Purpose |
|---|---|
| Python | 3.12.10 |
| dbt Core | 1.12.6 |
| dbt ClickHouse | 1.10.3 |
| Elementary | 0.26.1 |
| ClickHouse | Database |
| SQL | Data transformation and testing |
| Git and GitHub | Version control |

## 4. Prerequisites

Before running this project, install:

- Python 3.12
- Docker Desktop
- Git
- ClickHouse Server
- PowerShell or a terminal

The ClickHouse server must be accessible using the connection settings in your dbt profile.

## 5. Project Setup

### Step 1: Clone the repository

```bash
git clone https://github.com/nagendrasiddi95-max/elementary-dbt-data-quality-monitoring-v2.git
```

Replace the placeholder with the actual repository URL.

### Step 2: Open the project directory

```bash
cd elementary-dbt-data-quality-monitoring-v2
```

### Step 3: Create a virtual environment

```powershell
py -3.12 -m venv .venv
```

### Step 4: Activate the virtual environment

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, run:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

Then activate the environment again.

### Step 5: Install dependencies

```bash
python -m pip install "elementary-data[dbt1-clickhouse]==0.26.1"
```

### Step 6: Install dbt packages

```bash
dbt deps
```

## 6. ClickHouse Configuration

Configure your dbt connection in:

```text
~/.dbt/profiles.yml
```

Use the `elementary_alert_demo` profile and configure the ClickHouse connection with your own credentials.

Do not upload your actual database password or private credentials to GitHub.

## 7. Running the Project

Run these commands from the directory containing `dbt_project.yml`.

### Validate the connection

```bash
dbt debug
```

### Install project packages

```bash
dbt deps
```

### Execute dbt models

```bash
dbt run
```

### Execute data quality tests

```bash
dbt test
```

### Generate the Elementary dashboard

```bash
edr report --file-path elementary_report.html --open-browser true
```

The report is saved as an HTML file and can be opened in a web browser.

## 8. Data Quality Testing

The project includes tests for:

- Unique IDs
- NOT NULL constraints
- Custom SQL assertions

The sample model deliberately contains one NULL ID:

```sql
select 1 as id
union all
select null as id
```

This allows the project to demonstrate how data quality checks identify invalid records.

The custom test `assert_no_null_ids` also checks for NULL IDs.

## 9. Verified Execution Results

The following results were observed during project execution:

| Operation | Verified Result |
|---|---|
| `dbt debug` | Connection successful |
| `dbt deps` | Packages installed |
| `dbt run` | 36 passed |
| `dbt test` | 7 passed, 2 failed |
| `edr --version` | Elementary 0.26.1 |
| Elementary report | Generated and opened in browser |

**Note:** The two dbt test failures are intentional in this demonstration. Both detect the NULL ID deliberately inserted into the sample model. They demonstrate data quality issue detection rather than a failed database connection or model build.

## 10. Project Structure

```text
elementary-dbt-data-quality-monitoring-v2/
│
├── models/
│   └── example/
│       ├── my_first_dbt_model.sql
│       ├── my_second_dbt_model.sql
│       └── schema.yml
│
├── tests/
│   └── assert_no_null_ids.sql
│
├── macros/
├── analyses/
├── seeds/
├── snapshots/
│
├── .env.example
├── .gitignore
├── dbt_project.yml
├── packages.yml
├── package-lock.yml
├── README.md
└── elementary_report.html
```

Generated folders such as `target`, `logs`, and `dbt_packages` are excluded from version control where configured in `.gitignore`.

## 11. Project Output

The Elementary dashboard provides visibility into:

- Test results and failures
- Monitored tables
- Model execution history
- Data test results
- Data quality monitoring metrics

## 12. Documentation

- dbt: https://docs.getdbt.com/
- Elementary: https://docs.elementary-data.com/
- ClickHouse: https://clickhouse.com/docs