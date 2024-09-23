# AWS-S3-Project
# 1. Learning to create and store files S3 bucket 

Creating an Amazon S3 bucket and loading the sample files
1) Step 1 :
- Login to your AWS account
 - Goto Services and select storage ->S3
   or Under services search 
   
![Screenshot 2024-09-22 at 5 18 46 PM](https://github.com/user-attachments/assets/c55031aa-a3a8-4bd4-a29a-12621c23e57f)


2) Step 2 :
To create a bucket :
- Click on create bucket
- Give unique name to the bucket (names must be unique across all regions in aws)
- navigate to the end of the form keeping all values default and click on create bucket.

- Bucket with "demo-glue-studio-da-project" is created.
- Click on the bucket and start creating three folders:
	1) datafiles ---> customers and sales
	2) profile -output
	3) shared

ALl the folders will help us to create and maintain easily during ETL steps.

3) Step 3:
Upload all the downloaded data files into the respective folders.


With conclusion of the above steps, we learnt to load data into s3 buckets. S3 buckets can be used to store raw files so that other analytical services can consume. Data here isn't compressed.

In the next section, we will use AWS Glue to crawl, catalog, transform and optimize the data for analytical services.

# 2. Using AWS Glue to crawl and catalog data 

Step 1- Search for AWS glue under Services->analytics ->AWS glue 

![Screenshot 2024-09-22 at 5 55 16 PM](https://github.com/user-attachments/assets/aa3c2b66-e444-4369-bac6-4c40198b543e)

Step 2-  Locate 'Data Catalog'-> Crawlers  ( to create a crawler )

![Screenshot 2024-09-22 at 5 56 19 PM](https://github.com/user-attachments/assets/c1e67157-7879-497e-9760-256a004aaa19)

Step 3- 
- Enter the name of the crawler 
- Add the data sources
- Provide the path of S3 bucket/ datafiles that we have created earlier.
- Enter the configuration details in the next step , choose to create a new IAM role
- Choose the output and scheduling of the crawler and a database for new Data catalog that will store source.
- Create the new database
- Provide these details and schedule as on demand.
- Review all the details and create crawler.

Step 4 - 
Run the crawler

![Screenshot 2024-09-22 at 7 20 28 PM](https://github.com/user-attachments/assets/f2d4995c-41ea-494f-972e-cc7fcf09914d)

-  This will initiate an interrogation of the source data that will populate the sales_data database in the Data Catalog with source schema and data types

Step 5- 
On successful completion of the crawler, two tables are created.

![Screenshot 2024-09-22 at 7 22 47 PM](https://github.com/user-attachments/assets/e6df74b3-e9c1-4492-adce-306583750103)

Step 6- 

In the left navigation bar, under Data Catalog , we will have the databases created and both the tables (sales and customer) are present inside the database folder.  

Step 7 - 
To see the metadata information about the table, schemas, data type , click on the tables:

![Screenshot 2024-09-22 at 7 26 32 PM](https://github.com/user-attachments/assets/71ce3873-6dc1-4ff0-b5e6-f087a2539830)

# 3. AWS Glue ( ETL on Data ) 

In this section, we will use default transformation provided by the AWS glue studio on the datasets loaded. 

Step 1- 
- Data catalog is already populated in the previous step/
- Data Integration & ETL -> visual ETL
- Create the ETL job by entering all the details for Source - Transform- Target 

![Screenshot 2024-09-22 at 11 11 55 PM](https://github.com/user-attachments/assets/ecada2b3-1d11-4431-b37c-3f4553f1bbad)

- The visual for  the ETL job with all the necessary transformations looks like below:
![Screenshot 2024-09-22 at 11 13 47 PM](https://github.com/user-attachments/assets/22d066bb-e7ff-49a1-8ab4-b0ee08478cb6)

- We can add necessary transformations as provided by AWS Glue. Here, for this project I renamed the columns in the target , dropped few columns from the source table, aggregated the datasets on basis of some columns.

- Once the entire set up is complete, you can run the jobs and data will be loaded in the destination folders in the S3 buckets.

- ![Screenshot 2024-09-22 at 11 19 43 PM](https://github.com/user-attachments/assets/0a85d40e-cda1-4a11-9886-00f5751bfda3)
