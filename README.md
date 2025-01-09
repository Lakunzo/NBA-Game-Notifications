# NBA-Game-Notifications

## Project Overview
This project is an alert system that sends real-time NBA game day score notifications to subscribed users via SMS/Email. It leverages Amazon SNS, AWS Lambda and Python, Amazon EvenBridge and NBA APIs to provide sports fans with up-to-date game information. The project demonstrates cloud computing principles and efficient notification mechanisms.
## Features
* Fetches live NBA game scores using an external API.
* Sends formatted score updates to subscribers via SMS/Email using Amazon SNS.
* Scheduled automation for regular updates using Amazon EventBridge.
* Designed with security in mind, following the principle of least privilege for IAM roles.
  
![Architectural Diagram](https://i.postimg.cc/RFLRYRfW/Event-Drivent-API-drawio-1.png)

## Technologies 
* Cloud Provider - AWS
* Services Used - SNS, Lambda, EventBridge, IAM
* External API - NBA Game API (SportsData.io)
* Programming Language - Python 3.x

## Setup Guide
### Clone the Repository

git clone [https://github.com/Lakunzo/NBA-Game-Notifications.git]

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
2. Create policy and select SNS service. Switch to JSON. Copy and modify the nba_
