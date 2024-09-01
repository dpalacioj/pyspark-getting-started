# Getting Started with PySpark and Colab
This repository is a beginner's guide to using PySpark with Google Colab. It demonstrates the most common methods used in PySpark and is designed to be simple and intuitive, similar to the use of Pandas.

**Disclaimer:** When using the MLlib library of Apache Spark, there are opportunities to improve feature engineering before making predictions. This guide is intended to quickly introduce students and learners to these concepts within the context of data science.

# Setting Up PySpark in Google Colab
To use PySpark in Google Colab, you'll need to configure your environment to run Spark. Execute the following commands in your Colab notebook:

```python
%%time
# Install OpenJDK 8, which is required for running Apache Spark
!apt-get install openjdk-8-jdk-headless -qq > /dev/null

# Download Apache Spark (version 3.5.1 with Hadoop 3) from the official archive
!wget -q http://archive.apache.org/dist/spark/spark-3.5.1/spark-3.5.1-bin-hadoop3.tgz

# Extract the downloaded Spark archive
!tar xf spark-3.5.1-bin-hadoop3.tgz

# Install the 'findspark' package, which simplifies the integration of PySpark with Jupyter notebooks
!pip install -q findspark

# Set environment variables for Java and Spark
import os
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-8-openjdk-amd64"  # Set the path to the Java installation
os.environ["SPARK_HOME"] = "/content/spark-3.5.1-bin-hadoop3"  # Set the path to the Spark installation

# Initialize findspark to make sure Spark is correctly set up
import findspark
findspark.init()

# Import the necessary module to create a Spark session
from pyspark.sql import SparkSession

# Create a Spark session; this is the entry point for working with DataFrames in Spark
spark = SparkSession.builder.master("local[*]").getOrCreate()

# Set a configuration to improve the formatting of DataFrame outputs in the notebook
spark.conf.set("spark.sql.repl.eagerEval.enabled", True)

# Display the Spark session information
spark
```

This setup installs Java, Spark, and the findspark package, then configures the environment variables needed for PySpark to run in Colab. Finally, a Spark session is created, which is necessary for running PySpark commands.

# Data Used in the Tutorial
The data used in this tutorial is located in the data/ folder. You can directly use the files df_natural_disasters.parquet and df_health_income.parquet as they were created within the notebook. These files contain the datasets processed and used throughout the guide.

# Note on Paths
Please ensure you adjust any absolute paths to match your specific Google Drive structure if you are running this notebook in Google Colab. The notebook assumes the data is stored relative to the project directory, but paths may need to be modified according to your setup.

# Additional Notes
This guide is a quick start to familiarize new users with PySpark in a Colab environment. While it covers basic operations and provides an introduction to using PySpark's MLlib for regression, it is not exhaustive. For a production environment, further tuning and more sophisticated feature engineering would be necessary.
The code examples are designed to be easily understandable, mirroring Pandas-like syntax where possible to ease the learning curve.
We hope this guide helps you get started with PySpark and gives you a solid foundation for exploring the powerful capabilities of Spark in big data processing.</br>


+ _To dive deeper into the official documentation, visit:_
https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/index.html

+ _This tutorial was also based on this YouTube Channel_
https://www.youtube.com/watch?v=_C8kWso4ne4&ab_channel=freeCodeCamp.org