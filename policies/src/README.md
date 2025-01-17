
---

# NBA Data Lake: A Comprehensive Guide to NBA Analytics with AWS

Welcome to the **NBA Data Lake** repository! This project is designed to streamline the creation of a robust data lake for NBA analytics using the power of AWS services. With just a few steps, you can set up a system that integrates **Amazon S3**, **AWS Glue**, and **Amazon Athena** to store and query NBA-related data effortlessly.

---

## 📖 Overview

The `setup_nba_data_lake.py` script simplifies the process of building an NBA data lake by automating the following tasks:

1. **Amazon S3 Setup**: Creates a bucket to store raw and processed NBA data.
2. **Data Upload**: Uploads sample NBA data (in JSON format) to the S3 bucket.
3. **AWS Glue Configuration**: Establishes a database and external tables to enable querying.
4. **Amazon Athena Integration**: Configures resources for querying data directly from S3.

---

## 🔑 Prerequisites

Before running the script, ensure you have the following:

### 1. **SportsData.io Account**
- Sign up for a free account at [SportsData.io](https://sportsdata.io).
- Navigate to **Developers** > **API Resources** > **Introduction & Testing**.
- Select the **SportsDataIO API Free Trial** and complete the setup, ensuring you choose **NBA** for this tutorial.
- Once registered, you’ll receive an API key via email. Save this key for later use.

### 2. **IAM Role/Permissions**
Ensure your AWS user or role has the following permissions:
- **Amazon S3**: `s3:CreateBucket`, `s3:PutObject`, `s3:DeleteBucket`, `s3:ListBucket`
- **AWS Glue**: `glue:CreateDatabase`, `glue:CreateTable`, `glue:DeleteDatabase`, `glue:DeleteTable`
- **Amazon Athena**: `athena:StartQueryExecution`, `athena:GetQueryResults`

---

## 🚀 Getting Started

Follow these steps to set up the NBA Data Lake:

### **Step 1: Open AWS CloudShell**
1. Log in to your AWS account at [aws.amazon.com](https://aws.amazon.com).
2. In the top navigation bar, click the CloudShell icon (a square with `>_` inside).

---

### **Step 2: Create the Python Script**
1. In CloudShell, create a new file by typing:
   ```bash
   nano setup_nba_data_lake.py
   ```
2. Visit the [NBA Data Lake Repository](https://github.com/alahl1/NBADataLake) and copy the contents of the `setup_nba_data_lake.py` file.
3. Paste the contents into the newly created file in CloudShell.
4. Locate the line under **#Sportsdata.io configurations** that says:
   ```python
   api_key = ""
   ```
   Replace the empty string with your API key.
5. Save and exit:
   - Press `Ctrl + X` to exit.
   - Press `Y` to confirm saving changes.
   - Hit `Enter` to finalize the file name.

---

### **Step 3: Create the `.env` File**
1. In CloudShell, create another file:
   ```bash
   nano .env
   ```
2. Add the following lines, replacing `your_sportsdata_api_key` with your actual API key:
   ```bash
   SPORTS_DATA_API_KEY=your_sportsdata_api_key
   NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
   ```
3. Save and exit using the same steps as above.

---

### **Step 4: Run the Script**
1. Execute the script by typing:
   ```bash
   python3 setup_nba_data_lake.py
   ```
2. If everything is set up correctly, you should see messages confirming:
   - Successful creation of resources.
   - Successful upload of sample data.
   - Completion of the data lake setup.

---

### **Step 5: Verify the Setup**
1. **Check S3 Resources**:
   - In the AWS Management Console, search for **S3** and open the service.
   - Locate a bucket named `Sports-analytics-data-lake`.
   - Inside the bucket, check for a folder named `raw-data` containing `nba_player_data.json`.
2. **Test with Amazon Athena**:
   - Open Amazon Athena in the AWS Management Console.
   - Use the following sample query to retrieve player data:
     ```sql
     SELECT FirstName, LastName, Position, Team
     FROM nba_players
     WHERE Position = 'PG';
     ```
   - Click **Run** and view the query results.

---

## 🎓 Key Learnings
By completing this project, you’ll gain hands-on experience in:
1. **AWS Security**: Applying least privilege IAM policies.
2. **Automation**: Using scripts to configure cloud infrastructure.
3. **API Integration**: Leveraging external APIs in data workflows.

---

## 🔮 Future Enhancements
Consider expanding the project with these features:
1. Automating data ingestion using **AWS Lambda**.
2. Adding a data transformation layer with **AWS Glue ETL**.
3. Enhancing analytics with visualizations in **AWS QuickSight**.

---

Enjoy building your NBA Data Lake! If you have any questions or suggestions, feel free to contribute or raise an issue. 🏀

--- 
