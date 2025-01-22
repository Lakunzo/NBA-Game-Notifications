# NBA-Game-Notifications

## Project Overview
This project is an alert system that sends real-time NBA game day score notifications to subscribed users via Email. It leverages Amazon SNS, AWS Lambda and Python, Amazon EvenBridge and NBA APIs to provide up-to-date game information. The project demonstrates cloud computing principles and efficient notification mechanisms.
## Features
* Fetches live NBA game scores using an external API.
* Sends formatted score updates to subscribers via Email using Amazon SNS.
* Scheduled automation for regular updates using Amazon EventBridge.
  
![Architectural Diagram](https://i.postimg.cc/RFLRYRfW/Event-Drivent-API-drawio-1.png)

## Technologies 
* Cloud Provider - AWS
* Services Used - SNS, Lambda, EventBridge, IAM
* External API - NBA Game API (SportsData.io)
* Programming Language - Python 3.x

## Setup Guide
### Clone the Repository
```bash
git clone [https://github.com/Lakunzo/NBA-Game-Notifications.git]
```
### SportsData IO Sign up
1. Sign up on [SportsData.IO](https://sportsdata.io/)
2. Confirm Email
3. Get API Key

### Create an SNS Topic and Add Subscription
1. Open the AWS Management Console
2. Locate the SNS Service
3. Create a Topic using the standard type

### Create SNS Subscription
1. Open the Topic created, anc click Create Subscription
2. Select Email in the protocol list
3. Enter your email address and create the subscription
4. Confirm the subscription

### Create IAM Policy
1. Open IAM, and click policies
2. Create policy and select SNS service. Switch to JSON. Copy and modify the nba_game_role.json file
3. Enter a name for the policy and create the policy

### Create IAM Role
1. Within IAM, click Create role
2. In Trusted entity type, select AWS service. In Use case, select Lambda and click Next
3. Select the IAM policy created, search for the "AWSLambdaBasicExecutionRole", add it and click Next
4. Enter a name for the role and create the role

### Create Lambda Function
1. In Lambda, click Create function
2. Select Author from scratch
3. Enter a function name. In Runtime, select Python 3.13
4. In Change default execution role, use an existing role, and select the IAM role that was created. Create the function
5. Copy the content of the src/nba_game_notification.py file from the repository
6. From the Lambda function, select the Configuration tab, click Environment variables
   * NBA_API_KEY:your_nba_api_key
   * SNS_TOPIC_ARN: The ARN of the SNS topic created earlier
   
### Create an EventBrdige Rule
1. In EventBridge, locate and click Rules in the Buses segment
2. Click Create rule. In Rule detail, enter a name, select Schedule for the rule type, and click continue in Eventbridge scheduler
3. In Schedule pattern, select recurring schedule, and select Cron-based schedule
4. In Cron expression, enter your cron job details
5. In select target, choose AWS Lambda, and select the Lambda function that was created earlier

### Test the System
1. Open the Lambda function
2. In the Code tab, click Test to simulate the function
3. Wait for it to complete and check result in the Test tab
4. Verify that an email was delivered
   
 ![Email](https://i.postimg.cc/0QZrFsv0/Screenshot-2025-01-15-114925.png)   

### Lessons Learned
1. Integrating external API into cloud systems
2. Architecting a notification system using SNS Topic and Lambda
3. Automating system triggers using EventBridge

### Future Enhancements
1. Add S3 bucket as destination for results
2. Dashboard using AWS QuickSight

