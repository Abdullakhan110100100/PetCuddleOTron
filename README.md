# Serverless application to send emails
This is a simple serverless application using S3, API Gateway, Lambda, Step Functions, SNS & SES.
The steps I followed to build this:
1) Configure Simple Email service
2) Add a email lambda function to use SES to send emails for the serverless application
3) Implement and configure the state machine, the core of the application
4) Implement the API Gateway, API and supporting lambda function
5) Implement the static frontend application and test functionality

1) Configure Simple Email Service (SES):
   ![Creating identities](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/added%20emails%20as%20verified%20identities.png)
   This application is going to send reminder messages Email. It will use the simple email service or SES. In production, it could be configured to allow sending from the application email, to any users of the       application. For this project I will verify the sender address and the receiver address.

   Added 2 emails in the SES console as identities and verified them. 1 identity for the sender and the other for the receiver.

2) Add a email lambda function to use SES to send emails for the serverless application
    ![Create lambda function](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/email%20reminder%20lambda.png)
   We first need to create an IAM execution role in order to give out lambda functions the ability to interact with the other services. Then create the the lambda function which will will be used by the serverless application to create an email and then send it using SES.
   ![Create lambda function](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/email%20reminder%20lambda%20code.png)

3) Implement and configure the state machine, the core of the application
Create an IAM role which the state machine will use to interact with other AWS services. Then move into the statemachine console and 
