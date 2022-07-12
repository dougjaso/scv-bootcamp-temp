# Create and Validate your contact center

Set up your contact center for Service Cloud Voice with Amazon Connect. When you create a contact center in Voice, Salesforce creates an Amazon Connect instance and two Salesforce connected apps for you. Before starting this task, assign the Contact Center Admin permission set to at least one user and find out where your contact center is physically located.

## Assign the Contact Center Administrator Permission Set

Salesforce uses permission sets to control access to your Service Cloud Voice with Amazon Connect contact center. You need at least one user, likely your main developer account, with the Contact Center Admin permission set so they can set up the contact center. A deeper review of permission sets for Service Cloud Voice will come in a later module.

1.  Login to your Salesforce org as an administrator.
1.  From Setup, enter `Amazon Setup` in the Quick Find box, then select **Amazon Setup**.
1.  In the Set Up Your Contact Center section, choose **Assign Permissions**. The Permission Sets page opens. ![Assign Permissions](/static/01/assign_permissions.png)
1.  Select **Contact Center Admin**.
1.  Choose **Manage Assignments**.
1.  Select **Add Assignments**.
1.  Select the users that you want to assign the permission set to.
1.  Choose **Assign**.

After assigning the permission set, create your contact center. Single sign-on (SSO) for the contact center is handled by a connected app that Salesforce automatically creates and assigns to your contact center users.

## Create your contact center
Set up your contact center for Service Cloud Voice with Amazon Connect. When you create a contact center in Voice, Salesforce creates an Amazon Connect instance and two Salesforce connected apps for you. Before starting this task, assign the Contact Center Admin permission set to at least one user and find out where your contact center is physically located.

> **NOTE:_** The Amazon Connect instance can be located in data centers around the world. Select a region that is closest to where you’re located geographically. For information about AWS regions that support Amazon Connect, see [Region Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) in the AWS documentation.

1.  Login to your Salesforce org as an administrator.
1.  From Setup, in the Quick Find box, enter `Amazon Setup`, then select **Amazon Setup**.
1.  In the Set Up Your Contact Center section, choose **Create Contact Center**. The Create Contact Center wizard opens. ![Creat contact center](/static/01/create_cc.png)
1.  Enter a display name for your contact center.
1.  Complete the form 
    *  Enter a display name for your contact center
    *  Enter an internal name for your contact center. The internal name is how other objects recognize your call center, similar to an API name. The internal name must be unique to your org, contain fewer than 20 characters, start with a letter, and contain only alphanumeric characters.
    *  Select the region that’s closest to where your contact center is located. The list is populated with the AWS regions that support Amazon Connect.

![Complete the form](/static/01/create_cc_form.png)

6.  Select **Next**.
6.  Choose at least one administrator for the contact center. The list is populated with users who already have the Contact Center Admin permission set.
6.  Select **Done**. The window closes. It can take a few minutes to create the contact center.

![Creat contact center](/static/01/create_cc_in_progress.png)

## Validate your contact center
Once your contact center is created, you can validate basic telephony operation by connecting to the Amazon Connect administrative interface, claiming a phone number, launching the built-in phone panel, and placing a test call.

### Access the Amazon Connect administrative interface
The Amazon Connect administrative interface can be accessed from Salesforce. Since Service Cloud Voice uses the Identity Provider that you setup pereviously, you will not need to login to Amazon Connect seperately, and your user account should already be provisioned.

1.  Login to your Salesforce org as the user that you assigned to the Contact Center Administrator permission set.
1.  From Setup, in the Quick Find box, enter `Amazon Contact Centers`, then select **Amazon Contact Centers**.
1.  In the line for your contact center, select **Telephony Provider Settings**.
1.  A new tab will open and, after a moment, you should be logged into the Amazon Connect administrative interface.

### Claim a phone number

To receive or make calls, you need a phone number. Amazon Connect provides several options, including claiming an available number and porting an existing number, among other options. For more details, see [Set up phone numbers for your contact center](https://docs.aws.amazon.com/connect/latest/adminguide/contact-center-phone-number.html) in the Amazon Connect Administrator Guide.

To claim a phone number in Amazon Connect, log in to your Amazon Connect instance as described above, and follow these steps:

1.  Choose Channels and select **Phone numbers**.
1.  Select **Claim a number**.
1.  Select **DID (Direct Inward Dialing)**.
1.  In the country menu, select your country. 
1.  Select a number from the list of available phone numbers.
1.  Provide a brief description, such as `Test number`
1.  In the Contact flow/IVR menu, select **Sample_SCV_Inbound_With_Transcription**.
1.  Choose **Save**

This will claim the phone number from AWS and assign it to your Amazon Connect instance. This process usally takes ~1 minute to activate. While the number is provisioned, update the sample queue to use this number for outbound calls.

### Assign a default outbound number
Any queue that will be used to place outbound calls, whether manual, API-driven, our click-to-call, must have a phone number associated to it. This number will be presented as the caller id when placing calls.

1.  Choose Routing and select **Queues**.
1.  Select **BasicQueue**
1.  In the Outbound caller ID number menu, select the phone number that you claimed.
1.  In the Outbound whisper flow menu, select **Sample_SCV_Outbound_Flow_With_Transcription**.
1.  Choose **Save**

### Test basic telephony routing
Now that you have claimed a phone number and assigned it to your queue, you are ready to test basic telephony routing. You will perform this validation from the Amazon Connect administrative interface.

1.  In the upper right, select the **phone icon** to open the Amazon Connect contact control panel (CCP) in a new window. ![Open the CCP](/static/01/connect_admin_ccp_icon.png)
1.  As the window opens, allow access to the microphone and notifications as requested.
1.  Change your agent status by selecting **Offline** and choosing **Available**. ![Change agent status](/static/01/ccp_change_state.png)
1.  Select **Number pad** top open the dial pad and enter a direct dial phone number, such as your mobile phone, that you have access to. 
> **_IMPORTANT:_** **UK numbers** with the following prefixes are not allowed by default: +447, +44111, +44118, +44119, +448, +44826, +449. **Japan mobile numbers** with the following prefixes are not allowed by default: +8170, 8180, and 8190. Before you can dial these numbers, you must submit a service quota increase request. If you only have access to a number that begins with one of these prefixes. Skip to the inbound call test that begins at step 10.
5.  Select **Call**. ![Outbound call](/static/01/ccp_outbound.png)
5.  Answer the call on your mobile phone when it arrives
5.  After brief messages on both the customer and agent sides, the call should connect. ![Call connected](/static/01/ccp_connected.png)
5.  Once it does, you can end the call by selecting **End call**.
5.  Select **Close contact** to clear the agent from the After call work state.
5.  Now, from your mobile phone, call the number that you claimed earlier. It should be the same as the caller ID from the call you just received.
5.  After a couple short messages, the call should arrive at the agent's CCP. ![Incoming](/static/01/ccp_incoming.png)
5.  Accept the call by selecting the **green checkmark button**.
5.  Once the call has connected, you can end it by selecting **End call**.
5.  Select **Close contact** to clear the agent from the After call work state.
5.  Close the Contact Control Panel window

**NEXT STEP: [Configure Salesforce REST API access](prep_07.md)**
