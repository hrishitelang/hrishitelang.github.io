---
layout: project
title: AWS ETL Pipeline Manager for YouTube User Data Analysis
subtitle: "Scalable Data Pipeline for YouTube Insights and Advertising Success"
---
## **Problem Statement**  
With the goal of launching a data-driven advertising campaign on YouTube, the customer needed insights to categorize videos based on comments and statistics and to identify factors affecting video popularity. Key metrics like views, likes, shares, and comments were crucial for analyzing user engagement. The dataset, sourced from Kaggle, included structured (CSV) and semi-structured (JSON) data on top trending YouTube videos and their categories. The challenge lay in building an efficient pipeline to process, clean, and analyze this data for actionable insights.

---

## **Project Objectives**  
- Build a **data lake** to store and manage large volumes of structured and semi-structured data.
- Develop a lightweight ETL pipeline for data transformation and cleaning.
- Perform SQL-based data integration to create a unified dataset.
- Build interactive BI dashboards to visualize insights for decision-making.
- Enable the customer to identify trends and launch a successful ad campaign.

---

## **Methodology and Steps**

### **1. Data Lake Setup**
- Configured **Amazon S3** to serve as the foundation for the data lake.
  - A **landing bucket** was created to store raw datasets, including:
    - A CSV file containing video statistics (views, likes, shares, etc.).
    - A JSON file defining video categories.
  - Ensured S3 bucket permissions and structure followed best practices for scalability and security.

### **2. Data Processing**
- Utilized **AWS Glue** to create a **Data Catalog**, organizing metadata for seamless querying.
- Developed a **light ETL pipeline** using **AWS Lambda**:
  - Converted nested JSON files to Parquet format for optimized storage and querying.
  - Addressed challenges in nested JSON structure by parsing complex data fields.

### **3. Data Transformation**
- Used **AWS Athena** to perform SQL joins on the cleaned Parquet files.
  - Integrated data from JSON and CSV files into a unified dataset.
  - Generated intermediate datasets containing key metrics like:
    - Total views, likes, and dislikes by genre.
    - Engagement patterns by channel and category.
- Stored the transformed data in a new **S3 reporting bucket**.

### **4. Visualization**
- Built an interactive BI dashboard using **AWS QuickSight**:
  - **Bar Graphs**:
    - Sum of likes and dislikes by genre.
    - Sum of views by genre.
  - **Donut Charts**:
    - Distribution of views by genre.
    - Distribution of views by channel titles.
  - Configured dynamic filters for drill-down analysis by regions and genres.

---

## **Tools and Technologies**
- **Amazon S3**: For data storage and lake creation.
- **AWS Glue**: For data cataloging and metadata management.
- **AWS Lambda**: For serverless ETL processing and JSON to Parquet conversion.
- **AWS Athena**: For SQL querying and data integration.
- **AWS QuickSight**: For building dashboards and visualizing insights.
- **IAM**: For creating secure roles and policies to manage access across AWS services.

---

## **Challenges Faced**
1. **Handling Nested JSON Files**:
   - Directly querying nested JSON structures was infeasible. This required implementing a custom ETL step using **AWS Lambda** to flatten and convert JSON to Parquet.
2. **Data Cleansing**:
   - Identifying and resolving issues with join keys between the JSON and CSV datasets was critical for successful integration.
3. **Optimization**:
   - Ensuring that the data pipeline minimized latency and optimized storage without compromising query performance.

---

## **Outcome**
- The pipeline processed and analyzed large volumes of YouTube data efficiently.
- Key insights provided through dashboards:
  - Top genres by views, likes, and dislikes.
  - Leading channels driving engagement in specific regions.
  - Factors influencing video popularity, such as comment patterns and interaction rates.
- The customer launched a targeted advertising campaign on YouTube, leveraging these insights to maximize user engagement and ROI.

---

## **What I Learned**
This project was a significant learning experience in:
1. **Data Engineering**:
   - Designing and implementing a scalable data lake.
   - Building ETL pipelines to process and transform large datasets.
2. **AWS Services**:
   - Leveraging **S3**, **Glue**, **Lambda**, **Athena**, and **QuickSight** for end-to-end data management and visualization.
3. **Data Integration**:
   - Handling structured and semi-structured data to create a unified dataset.
4. **Visualization**:
   - Creating interactive BI dashboards to communicate key insights effectively.

While the BI dashboard was an outcome, the focus was on mastering the ETL pipeline and data warehousing techniques, making this an excellent portfolio project for roles in **Data Engineering**, **Data Analytics**, and **Data Science**.

---

## **Future Enhancements**
- Expand the pipeline to handle real-time streaming data from YouTube APIs.
- Incorporate advanced analytics, such as sentiment analysis of comments using **AWS Comprehend**.
- Enhance dashboards with predictive modeling insights using Amazon SageMaker.

---
