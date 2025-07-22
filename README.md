# Serverless application to send emails
This is a simple serverless application using S3, API Gateway, Lambda, Step Functions, SNS & SES.
The steps I followed to build this:
1) Configure Simple Email service
2) Add a email lambda function to use SES to send emails for the serverless application
3) Implement and configure the state machine, the core of the application
4) Implement the API Gateway, API and supporting lambda function
5) Implement the static frontend application and test functionality

* Configure Simple Email Service (SES):
   ![Creating identities](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/added%20emails%20as%20verified%20identities.png)
   This application is going to send reminder messages Email. It will use the simple email service or SES. In production, it could be configured to allow sending from the application email, to any users of the       application. For this project I will verify the sender address and the receiver address.

   Added 2 emails in the SES console as identities and verified them. 1 identity for the sender and the other for the receiver.

* Add a email lambda function to use SES to send emails for the serverless application
    ![Create lambda function](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/email%20reminder%20lambda.png)
   We first need to create an IAM execution role in order to give out lambda functions the ability to interact with the other services. Then create the the lambda function which will will be used by the serverless application to create an email and then send it using SES.
   ![Create lambda function](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/email%20reminder%20lambda%20code.png)

* Implement and configure the state machine, the core of the application
  ![Create state machine](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/state%20machine%20definition.png)
Create an IAM role which the state machine will use to interact with other AWS services. Then move into the statemachine console and enter the code to define the stages for the state machine.

![Create state machine](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/State%20machine%20stages.png)

* Implement the API Gateway, API and supporting lambda function
  ![Create state machine](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/Created%20restAPI.png)
  ![Create state machine](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/Created%20POST%20method%20for%20resource.png)
  Make an API gateway endpoint and in the resouce we then make a POST methid suing the API gateway

* Implement the static frontend application and test functionality
  ![Upload files into the S3 bucket](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/Files%20in%20the%20S3%20bucket.png)
  Upload the javascript and html files into S3. 
   ![Create state machine](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/Enabled%20static%20file%20hosting%20on%20S3%20bucket.png)
  Upload the frontend files to S3 and enable static webhosting
  Test the app by providing inputs and the email app is working
  ![Test](https://github.com/Abdullakhan110100100/PetCuddleOTron/blob/main/images%202/Success.png)
