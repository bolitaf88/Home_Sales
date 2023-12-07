# Home_Sales

### N/B The task was accomplished on Google Colab due to challenges encountered with installing PySpark on the local machine. 
Initially, we installed `PySpark` for `Google Colab` using the following code. `Tip:` It's essential to ensure compatibility by selecting the version that aligns with your local machine's Python version. For instance, in my case, the Python version was `3.5.0.`

import os
# Find the latest version of Spark 3.x from http://www.apache.org/dist/spark/ and enter as the spark version
# For example:
# spark_version = 'spark-3.5.0'
spark_version = 'spark-3.5.0'
os.environ['SPARK_VERSION'] = spark_version

# Install Spark and Java
!apt-get update
!apt-get install openjdk-11-jdk-headless -qq > /dev/null
!wget -q http://www.apache.org/dist/spark/$SPARK_VERSION/$SPARK_VERSION-bin-hadoop3.tgz
!tar xf $SPARK_VERSION-bin-hadoop3.tgz
!pip install -q findspark

# Set Environment Variables
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-11-openjdk-amd64"
os.environ["SPARK_HOME"] = f"/content/{spark_version}-bin-hadoop3"

# Start a SparkSession
import findspark
findspark.init()


# Credit Risk Analysis Project

## Assignment Execution

This assignment aimed to conduct data analysis using Spark DataFrames, focusing on querying and processing a dataset of home sales information. The following steps outline the completion of the assignment:

### Step 1: Creating Spark DataFrame

- The dataset was loaded into a Spark DataFrame using Spark's data manipulation capabilities.

### Step 2: Creating Temporary Table

- A temporary table named "home_sales" was created from the original DataFrame, enabling SQL-like queries on the data.

### Step 3: Query for Average Price of Four-Bedroom Houses Sold Each Year

- A SQL query was written to extract and compute the average price of four-bedroom houses sold in each year, rounded to two decimal places.

### Step 4: Query for Average Price of Homes with Three Bedrooms and Three Bathrooms

- Another SQL query was formulated to calculate the average price of homes with three bedrooms and three bathrooms, rounded to two decimal places.

### Step 5: Query for Average Price of Specific Home Criteria by Year Built

- A SQL query was designed to determine the average price of homes meeting specific criteria (three bedrooms, three bathrooms, two floors, at least 2,000 square feet) for each year built, rounded to two decimal places.

### Step 6: Query for View Rating based on Price Threshold

- A query was developed to derive the view rating for homes priced at or above $350,000, rounded to two decimal places. The runtime for this query was recorded.

### Step 7: Creating and Validating Cached Table

- A cached version of the "home_sales" temporary table was created to enhance query performance. The integrity and existence of the cached table were verified.

### Step 8: Running Cached Query and Recording Runtime

- The query from Step 6 was executed on the cached "home_sales" table, and the runtime was computed to evaluate the performance improvement gained from caching.

### Step 9: Creating Partitioned Parquet Data

- The home sales dataset was partitioned by the "date_built" field and stored in Parquet format.

### Step 10: Creating Temporary Table for Parquet Data

- A temporary table was established from the Parquet-formatted data, allowing SQL-like querying on this dataset.

### Step 11: Running Query on Parquet Table and Recording Runtime

- The query from Step 6 was executed on the temporary Parquet table, and the runtime was recorded to assess the efficiency of querying Parquet-formatted data.

### Step 12: Uncaching and Verification of "home_sales" Table

- The "home_sales" temporary table was uncached, and its integrity was verified to ensure proper management of cached data.

## Tools Used

- Apache Spark: Used for loading, processing, and querying large datasets.
- SQL: Employed for formulating queries on Spark DataFrames.
- Parquet: Leveraged for optimized storage and querying of partitioned data.

## Aknowledgements 
**Justin Bisal** - TA
**James NewMan** - TA
**Liang Yam** - TA

