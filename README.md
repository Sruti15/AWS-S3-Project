# AWS-S3-Project

Creating an Amazon S3 bucket and loading the sample files
**1) Step 1 :
**
- Login to your AWS account
 - Goto Services and select storage ->S3
   or Under services search 
   
![Screenshot 2024-09-22 at 5 18 46 PM](https://github.com/user-attachments/assets/c55031aa-a3a8-4bd4-a29a-12621c23e57f)


**2) Step 2 :
**
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

**3) Step 3:
**
Upload all the downloaded data files into the respective folders.

