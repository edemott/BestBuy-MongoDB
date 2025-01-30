

# MongoDB Learning with BestBuy Data

This repository contains a series of tasks designed to help learn MongoDB by working with a dataset of search queries submitted to BestBuy’s website. The dataset contains user search queries and related data, which has been stored in a MongoDB database for further analysis.

Project Overview

In this project, we perform a series of tasks to:
	1.	Import data from a CSV file into a MongoDB database.
	2.	Query and manipulate the data using MongoDB’s aggregation framework.
	3.	Use Python to interact with MongoDB and perform data analysis.

The tasks completed include:
	•	Importing data into MongoDB.
	•	Querying the database to count records.
	•	Aggregating the most frequently searched product SKUs.

Project Setup
	1.	Prerequisites
	•	Python 3.x
	•	MongoDB installed and running
	•	MongoDB Compass (for graphical interface)
	•	pymongo library for interacting with MongoDB in Python
	2.	Install Required Python Libraries
You can install the required libraries using pip:

pip install pymongo pandas


	3.	Starting MongoDB
If you’re running MongoDB locally, make sure it is started:

sudo mongod --dbpath /path/to/your/mongodb


	4.	Database Setup
	•	The dataset is imported into a MongoDB collection named bestbuy within the database bestbuy_database.
	•	Ensure that the MongoDB server is running, and you can access it via the MongoDB Compass GUI or through Python scripts.

Files
	•	bestbuy.csv: The dataset containing user search queries from the BestBuy website.
	•	q1.ipynb: An IPython notebook that performs the following tasks:
	•	Loads the CSV data into MongoDB.
	•	Executes queries to analyze the data.

Tasks Completed

(a) Importing Data into MongoDB
	•	Task: Read the data from bestbuy.csv and insert it into the bestbuy collection in MongoDB.
	•	Approach:
	•	The dataset is loaded using pandas.
	•	A connection to MongoDB is established using pymongo.
	•	Data is inserted into MongoDB in the required schema: User, sku, category, query, click time, query time.

(b) Counting Records
	•	Task: Execute a query to count the number of records in the database.
	•	Approach:
	•	A simple count query is executed using MongoDB’s count_documents() function.

(c) Top-5 Most Frequently Searched Product SKUs
	•	Task: Find the top-5 most frequently searched product SKUs.
	•	Approach:
	•	An aggregation query is run to group the data by SKU and count the occurrences.
	•	The results are sorted by frequency and the top 5 SKUs are returned.

Code Explanation

MongoDB Connection

from pymongo import MongoClient

# Establish a connection to the MongoDB server
client = MongoClient('mongodb://localhost:27017/')
db = client.bestbuy_database  # Replace with your actual database name
collection = db.bestbuy  # Replace with your collection name

Task (a) - Importing Data into MongoDB

import pandas as pd

# Load the CSV file into a pandas DataFrame
df = pd.read_csv('bestbuy.csv')

# Insert data into MongoDB
data = df.to_dict(orient='records')
collection.insert_many(data)

Task (b) - Counting Records

# Count the total number of records in the collection
record_count = collection.count_documents({})
print(f"Total number of records: {record_count}")

Task (c) - Top-5 Most Frequently Searched Product SKUs

# Aggregation pipeline to find the top-5 most frequent SKUs
pipeline = [
    {"$group": {"_id": "$sku", "count": {"$sum": 1}}},
    {"$sort": {"count": -1}},
    {"$limit": 5}
]

# Execute the aggregation query
top_skus = collection.aggregate(pipeline)

# Print the results
for sku in top_skus:
    print(f"SKU: {sku['_id']}, Count: {sku['count']}")

Usage
	1.	Running the Python Script:
	•	Ensure MongoDB is running on your local machine or on a remote server.
	•	Execute the Python script to load the data, run the queries, and analyze the results.
	2.	Viewing Results in MongoDB Compass:
	•	Open MongoDB Compass and connect to the MongoDB server.
	•	Browse the bestbuy_database and bestbuy collection to view the data and the results of the queries.

Conclusion

This project helped solidify understanding of MongoDB’s core concepts, including data import, aggregation, and querying. By working with the BestBuy search query dataset, I gained hands-on experience in handling and analyzing large datasets using MongoDB.

Future Work
	•	Further explore advanced MongoDB queries like joins using $lookup.
	•	Implement more complex aggregation pipelines for deeper insights.
	•	Set up MongoDB clusters for scalability and redundancy.

Feel free to adjust the README as per your preferences, such as including additional instructions or modifying descriptions based on how you’ve approached the tasks!
