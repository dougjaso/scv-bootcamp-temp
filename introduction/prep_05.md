# Initial AWS setup

After Voice is turned on, you will need to create a password for your AWS account and confirm your tax registration number to make Service Cloud Voice available in your org.. 

## Set the password for your root account in the AWS console
Go to AWS and complete the password reset flow. Basic instructions are below, for detailed instructions, see [Resetting a Lost or Forgotten Root User Password](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys_retrieve.html#reset-root-password).

> **_NOTE:_** We strongly recommend that you do not use the root user for your everyday tasks, even the administrative ones. Instead, adhere to the best practice of using the root user only to create your first IAM user. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks. To view the tasks that require you to sign in as the root user, see [AWS Tasks That Require Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html). The **Create your IAM user** section further below walks you through this process.

1.  Open a broswer and navigate to the [AWS Console](https://console.aws.amazon.com/).
1.  Select **Root user** as the sign in type.

![Login as Root](/static/01/aws_login.png)

3.  Provide the email address you used to turn on voice and select **Next**.
4.  Choose **Forgot password?**.
5.  Complete the CAPTCHA. Once completed successfully, an password reset link will be sent to the root email address.
6.  Follow the link to the **Reset password** page.
7.  Provide and confirm a new password. 
8.  Once you have reset your password, sign in by selecting **Sign in** on the "Password reset successful!" page.
9.  Select **Root user** as the sign in type.
10.  Provide the email address you used to turn on voice and select **Next**.
11.  Provide your password and select **Sign in**.
12.  You are not logged into the AWS Console.

## Create your first IAM user
As mentioned above, AWS strongly recommends that you do not use the root user for your everyday tasks, even the administrative ones. In order to provide your account with full administrative access, while still protecting your root credentials, create an admin user in Identity and Access Management and use that user account for AWS Console access after you complete these prerequisite steps.

1.  In the AWS console, navigate to the [IAM Console](https://console.aws.amazon.com/iamv2/)
2.  From the side menu, select **Users**
3.  Choose **Add users**
4.  Provide a username, such as **WorkshopAdmin** (feel free to use whatever you like), and select the **Password - AWS Management Console access**. You can choose to specify a password, or let IAM autogenerate one for you.
![IAM user setup step 1](/static/01/iam_step_1.png)
5.  Select **Next: Permissions**
6.  Choose **Attach existing policies directly**, then select the checkbox next to **AdministratorAccess** in the policies list.
![IAM attach policies](/static/01/iam_step_2.png)
7.  Select **Next: Tags**, then select **Next: Review**
8.  Verify the information is correct, then choose **Create user**
9.  After a moment, your user will be created. Note the AWS console login URL, as it will allow for login without needing to know the AWS account number or name. 
![IAM user created](/static/01/iam_step_5.png)
10. Select **Show** to see the password. Copy the password to a safe location. If you lose it, you can login as root to reset the password if needed.
Your user has been created. You do not need to switch users now. Feel free to complete the rest of the prerequistes, then begin using the IAM user from that point forward.

## Confirm your tax registration number
After your Amazon Web Services subaccount is created, confirm your company’s tax registration number for the subaccount. Complete this step so that Service Cloud Voice can be turned on in your org.

> **_CRITICAL:_** The configuration and security of the Amazon Web Services subaccount and the Amazon Connect instance is the your responsibility.

The steps differ depending on whether your company is located in the United States or outside the United States.

### United States customers
1.  Login to your Salesforce org as an administrator.
1.  From Setup, enter `Amazon Setup` in the Quick Find box, then select **Amazon Setup**.
1.  In the Register Tax Information section, choose **Confirm Settings**. ![Login as Root](/static/01/confirm_tax.png)
1.  Select **Acknowledge**.

> **_IMPORTANT:_** Salesforce uses its address for US-based customers. Clicking Acknowledge means that you’ve read the tax registration notice.

### Customers outside of the United States:

1.  Login to the [AWS Console](https://console.aws.amazon.com/)
1.  Navigate to the [AWS Tax Settings](https://console.aws.amazon.com/billing/home?#/tax) page 
1.  Enter your tax registration number. 
1.  When you’re done, login to your Salesforce org as an administrator.
1.  From Setup, enter `Amazon Setup` in the Quick Find box, then select **Amazon Setup**.
1.  In the Register Tax Information section, choose **Confirm Settings**.
1.  Select **Acknowledge**.

> **_NOTE:_** After you acknowledge the notice, Voice is turned on in your org. An email notification is sent to the Salesforce admin when Voice is successfully turned on. The email will be from support@salesforce.com and the subject will be "Salesforce Service Cloud Voice is turned on" or something similar.

After Voice is turned on, create your contact center and assign an administrator.

**NEXT STEP: [Create and Validate your contact center](prep_06.md)**
