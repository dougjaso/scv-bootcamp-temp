# Turn on voice

Turn on Service Cloud Voice so you can start setting up a contact center. When you turn on Service Cloud Voice with Amazon Connect, Salesforce creates an Amazon Web Services (AWS) account that’s used to create your Amazon Connect instance.

> **_IMPORTANT:_** The configuration and security of the Amazon Web Services subaccount and the Amazon Connect instance is the customer’s responsibility.

1.  Select an email address to use as the root user for your AWS subaccount. Salesforce uses this email address to create the root user in Amazon Web Services. The root email address must be unique and cannot be used with another AWS service. Write down this email address, because you need it later to set the AWS account password and to configure your Amazon Connect instance. To access Amazon Web Services documentation, go to [https://docs.aws.amazon.com](https://docs.aws.amazon.com). For details, see [AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html). 
1.  Login to Salesforce as an administrator
1.  From Setup, enter `Amazon Setup` in the Quick Find box, then select **Amazon Setup**.
1.  Select **Turn On Service Cloud Voice**.
1.  Enter the root email address two times.
1.  Select **Turn On Voice**. ![Turn on voice](/static/01/turn_on_voice.png)

> **_NOTE:_** It can take a while for Voice to be turned on. You can see whether the process is completed by refreshing the Amazon Setup page. When the process is complete, or if an error occurs, Salesforce sends a notification email to the Salesforce admin. When the Amazon Web Services account is enabled, AWS sends an email to the root user email address.

**NEXT STEP: [Initial AWS setup](prep_05.md)**
