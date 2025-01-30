

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

## Tasks Completed

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


