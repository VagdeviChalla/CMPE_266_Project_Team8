# CMPE_266 - Project Team 8
1. University Name: [San Jose State University](http://www.sjsu.edu/)
2. Course         : [Big Data Engineering and Analytics](http://info.sjsu.edu/web-dbgen/catalog/courses/CMPE266.html)
3. Professor      : [Sanjay Garje](https://www.linkedin.com/in/sanjaygarje/)
4. Students       : <br/>
			[Sayali Patil](https://www.linkedin.com/in/sayali-patil-7b041078/) <br/>
			[Vagdevi Challa](https://www.linkedin.com/in/vagdevi-challa-bbb46161/) <br/>
		    	[Mohinish Daswani](https://www.linkedin.com/in/mohinish-daswani-0318a6110/) <br/>
			[Kavina Desai](https://www.linkedin.com/in/kavina-desai)<br/>
			[Sai Supraja Malla](https://www.linkedin.com/in/saisuprajamalla/) <br/>
        

	            

## Project Introduction :

Twitter is one of the eminent social media platform that gets a tremendous amounts of tweets everyday. This huge amount of information can be used for financial,government or social approaches by organizing and examining the tweets. Since the volume of data generated by Twitter is enormous, storage and processing of this data is a serious issue.

In order to extract useful information from data generated via twitter tweets, we used
various readily available cloud services from AWS. Services that are used in this project includes
Kinesis data fire hose, Amazon S3, AWS Lambda, AWS Translate, AWS Comprehend, Athena
and Amazon Quick sight. Following gives the overview of how tweets are analyzed to extract
useful information out of it.

1) In this project, we used Kinesis data fire hose to get real time data from twitter. In
order to extract real time data from twitter, Consumer key, Consumer secret key, access
token and access secret token is needed to connect to twitter. Once an app is created in
twitter, all these keys will be available and data can be extracted. Once the data is
extracted from twitter, it can be stored on various storage services like data stores, data
warehouses and data lakes. For this project, we used Amazon S3 to store the data generated from twitter.
2) Then, we used AWS Lambda that uses two fully managed services, AWS Translate
and AWS Comprehend to analyze tweets. These two services helped to perform NLP
(Natural language processing) on tweets.
3) a. Positive and Negative Sentiment polarity scores of 10 selected players are produced by analysing the data generated by AWS comprehend.
   b. The data values that has sentiment column as POSITIVE or NEGATIVE are considered.
   c. Search on the tweets is performed using the String values assigned for each player.
   d. The tweets are then grouped by Sentiment and then by Player to get the Sentiment Polarity Scores for each player. 
4) Separate Kinesis data delivery streams within kinesis fire hose service is used in order to write back data to s3 bucket.
5) Once the enriched data is stored on S3, we used Athena to query the data that is
stored on S3. 
6) Then, used Amazon quick sight to visualize analyzed data.

## Sample Demo Screenshots : 
1. Twitter App to collect data:

<img width="960" alt="Twitter_tokens" src="https://user-images.githubusercontent.com/38084886/57042183-daf4c500-6c18-11e9-8ba2-a0cdab146596.PNG">

2. Amazon Kinesis Data Firehose :

<img width="960" alt="Kinesis_firehose_streams" src="https://user-images.githubusercontent.com/4371600/57039638-0de78a80-6c12-11e9-8b5e-128985b02425.PNG">

3. Amazon S3 :

<img width="960" alt="S3_dashboard" src="https://user-images.githubusercontent.com/4371600/57039276-0e335600-6c11-11e9-8749-f757804e755a.PNG">

<img width="960" alt="s3_bucket_folders" src="https://user-images.githubusercontent.com/4371600/57039512-a8939980-6c11-11e9-8b27-36b4f210a81c.PNG">

4. IAM roles  :

<img width="960" alt="IAM_roles" src="https://user-images.githubusercontent.com/4371600/57039688-2b1c5900-6c12-11e9-84bd-d408e9ff19ea.PNG">

5. EC2 Instance :

<img width="960" alt="EC2-instance" src="https://user-images.githubusercontent.com/4371600/57040396-22c51d80-6c14-11e9-8614-891f91947791.PNG">

6. Athena Database :

<img width="237" alt="Athena_database" src="https://user-images.githubusercontent.com/4371600/57040224-9adf1380-6c13-11e9-9a4f-59639ecd1e5d.PNG">

7.Amazon QuickSight :



## Pre-requisites Set Up :

Below is the list of resources to be configured for this project:

  #### **Amazon S3** <br/>
  Amazon Simple Storage Service (Amazon S3) is an object storage service offering scalability, data availability, security,    	 and performance. It is designed for 99.999999999% of durability, and storing the data for millions of applications for      
  organizations all around the world. <br/> Below are the steps to create S3 bucket : <br/> 
  	
	1. Open Amazon S3 console at https://console.aws.amazon.com/s3/.
	2. Choose Create bucket.
	3. Enter the bucket name and region where you want the bucket to reside. (here region is N. Virginia)
	4. Choose Create. 
	
	
 
  #### **Amazon Kinesis Data Firehose** <br/>
  Amazon Kinesis Data Firehose is used for reliably loading streaming data into data stores and analytics tools. It captures, 	transforms, and loads streaming data into Amazon S3, Amazon Redshift, Amazon Elasticsearch Service, Splunk and enables near   real-time analytics with existing business intelligence tools and dashboards. <br/>
  In this project, we are capturing real time Twitter data in Amazon Kinesis Data firehose for the analysis.<br/>
  
  
  #### **Amazon Athena** <br/>
  Amazon Athena is an interactive query service making it easy for analyzing data in Amazon S3 using standard SQL. Athena is     serverless, so there is no infrastructure to manage, and you pay only for the queries that you run. <br/>

  Amazon QuickSight <br/>
  Amazon QuickSight is a fully managed service that lets you easily create and publish interactive dashboards including ML     	 Insights. Dashboards can then be accessed from any device, and embedded into your applications, portals, and websites. <br/>
  

  #### **Amazon IAM** <br/>
  AWS Identity and Access Management (IAM) enables you to manage access to AWS services and resources securely. Using IAM, you can create and manage AWS users and groups, and use permissions to allow and deny their access to AWS resources. You can use roles to delegate access to users, applications, or services that don't normally have access to your AWS resources.

	1. Sign in to the AWS Management Console and open the IAM console at https://console.aws.amazon.com/iam/.
	2.In the navigation pane of the console, choose Roles and then choose Create role.
	3.Select Lambda as the AWS service for that role 
	4.In permissions, add the access permissions of other AWS Services such as AWS CloudWatch, AWS Comprehend, Firehose, S3.
	5.Enter the role name and role description and click Create Role.

Similarly IAM roles are created for the EC2 instance and AWS firehose streams as well.

  
  #### **Amazon Lambda** <br/>
  AWS Lambda is an event-driven, serverless computing platform provided by Amazon as a part of the Amazon Web Services. It is a computing service that runs code in response to events and automatically manages the computing resources required by that code.
  
 	1. Sign in to the AWS Management Console and open the AWS Lambda console athttps://console.aws.amazon.com/lambda/.  
	2. Choose Create function.
	3. Enter the function name and choose the runtime environment as Python 3.6
	4. Attach an already existing IAM role created in the previous step that will give this lambda function access to other AWS services
	5. After all the configuration is done, click Create Function

  #### **Amazon EC2** <br/>
  Amazon Elastic Compute Cloud (Amazon EC2) is a web service providing secure, resizable compute capacity in the cloud. It is 	designed to make web-scale cloud computing easier for developers. <br/>
  Below are the steps for creating AWS EC2 instance for this project : <br/>
  
  	Create VPC and subnets with below configuration :
	Select this option (to avoid charges to your account):
    	In "Specify the details of your NAT gateway" Section, Select "Use NAT Instance Instead".  
	
	    NAT Instance Type:          t2.micro
	    NAT Instance Keypair:       

	    CIDR block                  10.0.0.0/16 
	    Public Subnet:              10.193.10.0/24
 	
	Launch a new EC2 Instance into your new VPC as follows:

	T2 Micro Instance
	VPC: Twitter_Data
	Public Subnet
	Auto Assign Public IP
	Security Group: (create new) with ports 22 open
	Select Key Pair: 
	AWS Instance Name: Twitter_data

 

## How to run the project

**Step1** : Log in into the AWS console and go to the EC2 dashboard.

**Step2** : SSH into the created linux instance. After logging in the instance run the following command
```
node twitter_stream_producer_app.js
```
This command will call config file which has details to access twitter and starts extracting data from the Twitter and put it into Amazon S3 through kinesis firehose. As the data comes in the S3 bucket, lambda function is triggered which fetches the twitter data, performs analysis on it and pushes back to the S3 bucket



**Step3** : Go to Athena dashboard and create external table in Athena. After creating the table, write SQL queries. The query output will be stored in a new S3 bucket.

**Step4** : Go to Amazon Quicksight console and create a new data set in it and choose the tables created in Amazon Athena. After that, run a query in the Quicksight console and you can see graphs generated from the results of the query.



