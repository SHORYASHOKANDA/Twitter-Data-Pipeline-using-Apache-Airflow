🚀 Twitter Data Pipeline using Apache Airflow

This project demonstrates a complete end-to-end data pipeline that extracts data from the Twitter (X) API, transforms it using Python, and orchestrates the workflow using Apache Airflow. The processed data is stored in Amazon S3, making it ready for further analytics or reporting.

📌 Features

🔗 Extract tweets using the Twitter API

🧹 Transform and clean tweet data

☁️ Store raw & processed data in Amazon S3

🗂️ Orchestrate & schedule ETL workflow using Apache Airflow

📊 Ready for analytics, dashboards & ML use-cases

🏗️ Architecture
Twitter API → Extract (Python) → Transform (Python/Pandas) 
→ Load to Amazon S3 → Orchestrated by Airflow (DAG)


Technologies Used

Python

Tweepy / Requests

Apache Airflow

Pandas

Amazon S3

Docker (optional for Airflow setup)

🔄 Pipeline Workflow
1️⃣ Extract

Connects to the Twitter API

Fetches tweets based on keywords, hashtags, or user handles

Stores raw JSON data

2️⃣ Transform

Converts JSON → DataFrame

Cleans text, formats timestamps

Selects meaningful fields (tweet, user, metrics)

Saves processed data as CSV or Parquet

3️⃣ Load

Uploads raw and processed data to S3

s3://twitter-data-landing/ (raw)

s3://twitter-data-processed/ (cleaned)

4️⃣ Orchestration

Airflow DAG controls execution

Tasks:

extract_tweets

transform_tweets

load_to_s3

Execution chain:

extract_tweets >> transform_tweets >> load_to_s3


🚀 How to Run the Project
1. Clone the repository
git clone https://github.com/<your-username>/twitter-airflow-pipeline.git
cd twitter-airflow-pipeline

2. Start Airflow (Docker recommended)
docker-compose up -d

3. Add DAG

Place twitter_dag.py inside the dags/ directory.

4. Add Twitter API credentials

Save your keys inside:

config/twitter_credentials.json

5. Access Airflow UI

Open in your browser:

👉 http://localhost:8080

Activate the DAG → Trigger Run

🧪 Sample DAG Code Structure
extract = PythonOperator(
    task_id='extract_tweets',
    python_callable=extract_function
)

transform = PythonOperator(
    task_id='transform_tweets',
    python_callable=transform_function
)

load = PythonOperator(
    task_id='load_to_s3',
    python_callable=load_function
)

extract >> transform >> load

📊 Use Cases

Trend & hashtag analysis

Social media analytics

Sentiment analysis

Marketing insights

Real-time monitoring (extendable via Kafka)

🛠️ Future Enhancements

Load transformed data into Snowflake / Redshift

Add Spark / Databricks for heavy processing

Add Airflow Sensors for real-time triggers

Integrate dashboards using Power BI / Tableau

Apply NLP sentiment analysis on tweets

🤝 Contributions

Contributions, issues, and feature requests are welcome!
Feel free to open a PR.

⭐ Support

If you like this project, give the repository a star ⭐ to support the developer.
