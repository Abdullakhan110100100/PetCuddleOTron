# Serverless application to send emails
This is a simple serverless application using S3, API Gateway, Lambda, Step Functions, SNS & SES.
The steps I followed to build this:
1) Configure Simple Email service
2) Add a email lambda function to use SES to send emails for the serverless application
3) Implement and configure the state machine, the core of the application
4) Implement the API Gateway, API and supporting lambda function
5) Implement the static frontend application and test functionality

1) Configure Simple Email Service (SES):
   This application is going to send reminder messages Email. It will use the simple email service or SES. In production, it could be configured to allow sending from the application email, to any users of the application. For this project I will verify the sender address and the receiver address.

Move to the SES console https://console.aws.amazon.com/ses/home?region=us-east-1#
Click on Verified Identities under Configuration Click Create Identity
Check the 'Email Address' checkbox
Ideally you will need a sending email address for the application and a receiving email address for your test customer. But you can use the same email for both.

For my application email ... the email the app will send from i'm going to use adrian+cuddleotron@cantrill.io
Enter whatever email you want to use to send in the box (it needs to be a valid address as it will be checked)
Click Create Identity
You will receive an email to this address containing a link to click
Click that link
You should see a Congratulations! message
Return to the SES console and Refresh your browser, the verification status should now be verified
Record this address somewhere save as the PetCuddleOTron Sending Address

STAGE 1B - VERIFY SES APPLICATION CUSTOMER EMAIL ADDRESS
If you want to use a different email address for the test customer (recommended), follow the steps below
Click Create Identity
Check the 'Email Address' checkbox For my application email ... the email for my test customer is adrian+cuddlecustomer@cantrill.io
Enter whatever email you want to use to send in the box (it needs to be a valid address as it will be checked)
Click Create Identity
You will receive an email to this address containing a link to click
Click that link
You should see a Congratulations! message
Return to the SES console and refresh your browser, the verification status should now be verified
Record this address somewhere save as the PetCuddleOTron Customer Address

STAGE 1 - FINISH
At this point you have whitelisted 2 email addresses for use with SES.

the PetCuddleOTron Sending Address.
the PetCuddleOTron Customer Address.
