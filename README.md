# NBA Data Lake

This repository contains the `setup_nba_data_lake.py` script, which automates the creation of a data lake for NBA analytics using AWS services. The script integrates Amazon S3, AWS Glue, and Amazon Athena, setting up the infrastructure for storing and querying NBA-related data.

## Overview
The `setup_nba_data_lake.py` script performs the following actions:
- Creates an Amazon S3 bucket to store raw and processed data.
- Uploads sample NBA data (JSON format) to the S3 bucket.
- Sets up an AWS Glue database and an external table for querying the data.
- Configures Amazon Athena for SQL-based queries.

## Prerequisites
1. **SportsData.io Account**: 
   - Sign up for a free account at [SportsData.io](https://sportsdata.io).
   - Obtain your NBA API key from the "Standings" section.
   
2. **IAM Permissions**:
   - S3: `s3:CreateBucket`, `s3:PutObject`, `s3:DeleteBucket`, `s3:ListBucket`
   - Glue: `glue:CreateDatabase`, `glue:CreateTable`, `glue:DeleteDatabase`, `glue:DeleteTable`
   - Athena: `athena:StartQueryExecution`, `athena:GetQueryResults`

## Getting Started

### Step 1: Open CloudShell Console
1. Go to [AWS Console](https://aws.amazon.com) and log in.
2. Open CloudShell by clicking the square icon with `>_` next to the search bar.

### Step 2: Create the `setup_nba_data_lake.py` File
1. In CloudShell, type:
   ```bash
   nano setup_nba_data_lake.py



2. Copy the script from GitHub and paste it into the file.
3. Replace api_key under #Sportsdata.io configurations with your SportsData.io API key.
4. Save and exit (^X, then Y, then Enter).


## Step 3: Create .env File
In CloudShell, type:
```bash
nano .env
```




Paste the following code and replace with your API key:

```bash
SPORTS_DATA_API_KEY=your_sportsdata_api_key
NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
```

Save and exit.
Step 4: Run the Script
Run the script to set up the data lake:

```bash
python3 setup_nba_data_lake.py
```

You should see messages confirming successful resource creation.

## Step 5: Verify Resources
Amazon S3:
Check for a bucket named sports-analytics-data-lake with sample data in the raw-data folder.
Amazon Athena:
Use the following query to verify data:
```bash
SELECT FirstName, LastName, Position, Team
FROM nba_players
WHERE Position = 'PG';
```
Click Run to see the results.

## What We Learned
1. Securing AWS services with least privilege IAM policies.
2. Automating service creation with Python scripts.
3. Integrating external APIs into cloud workflows.

## Future Enhancements
1. Automate data ingestion using AWS Lambda.
2. Add a data transformation layer with AWS Glue ETL.
3. Incorporate advanced analytics and visualizations with AWS QuickSight.


