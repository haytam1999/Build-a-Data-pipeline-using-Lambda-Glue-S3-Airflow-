# Build-a-Data-pipeline-using-Lambda-Glue-S3-Airflow

This project consists of building a data pipeline using AWS tools (Lambda, Glue and S3), and Airflow to orchestrate the tasks.

1) Tools used:

	-AWS Lambda- is a compute service that allows you to run code without provisioning or managing servers. 
					Lambda functions are small pieces of code that can be triggered by specific events, 
					such as changes to data in an Amazon S3 bucket or updates to a database.
	
	-AWS Glue- is a fully managed extract, transform, and load (ETL) service that makes it easy to move
					data between data stores.
					
	-S3- is AWS’ blob storage. 
	
	-Airflow- is a workflow orchestrator based on Python. Used to develop, organize, order, schedule, 
					and monitor tasks using a structure called DAG — Direct Acyclic Graph.
					
2) Data Source:

I used data from the Brazillian ENEM (National Exam of High School, on literal translation).
The goal will be to extract the exams questions, which are available as PDFs 
on the MEC (Ministry of Education) website [CC BY-ND 3.0].

3) Schema:

Here is the schema I followed to build the pipeline:

![alt text](https://github.com/haytam1999/Build-a-Data-pipeline-using-Lambda-Glue-S3-Airflow-/blob/master/Schema.png?raw=true)

4) Scripts:

docker-compose.yml: this file will help you run airflow using docker.

download_files.py: this script will download files and place them in a s3 bucket.

lambda_function.py: this is the script of the lambda function (if a pdf file is added to s3 bucket, this lambda function 
					will be triggered and extract the questions from the pdf file to a json format).
					
glue_job_processPDF.py: this script will Read the text, split the questions and save the results in CSV.

pipeline_dag.py: this is the main DAG script that will orchestrate all of that.
