# Enable Omni-Channel

Before you can turn on Voice, enable Omni-Channel so your agents can make and receive calls. Service Cloud Voice agents use the Omni-Channel widget to handle all contact types, including voice. There is no additional soft phone required, and agents do not use the standard Amazon Connect Contact Control Panel (CCP). 

>**_IMPORTANT:_** Salesforce uses your My Domain subdomain name to configure single sign-on for Service Cloud Voice. Don’t change the My Domain name after you turn on Voice. Otherwise, you have to restart your Voice implementation.

1.  Login to Salesforce as an administrator
1.  From Setup, enter `Omni-Channel Settings` in the Quick Find box, then select **Omni-Channel Settings**.
1.  Select **Enable Omni-Channel**.
1.  Select **Omni-Channel settings** to enable features.
1.  Choose **Save**. 
![Enable Omni-Channel](/static/01/enable_omni.png)

Once you have enabled Omni-Channel, you need to enable Salesforce as an identity provider.

**NEXT STEP: [CEnable Salesforce as a SAML Identity Provider](prep_03.md)**
