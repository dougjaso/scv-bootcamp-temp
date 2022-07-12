# Enable Salesforce as a SAML Identity Provider

Before you can turn on Voice, enable Salesforce as a SAML identity provider. This will allow for single sign-on for your Service Cloud Voice users.

1.  Determine which certificate you want to use to enable your org to communicate with the service provider. You can use the default certificate or create your own. See [Certificates and Keys](https://help.salesforce.com/s/articleView?id=security_keys_about.htm&language=en_US&type=5).
    *  By default, a Salesforce identity provider uses a self-signed certificate generated with the SHA-256 signature algorithm. If you want to use the default certificate, proceed to step 2.
    *  To create a new self-signed certificate, follow the instructions in Generate a Self-Signed Certificate , then proceed to step 2.
    *  To create a CA-signed certificate, follow the instructions in Generate a Certificate Signed by a Certificate Authority, then proceed to step 2.
1.  Login to your Salesforce org as an administrator.
1.  From Setup, in the Quick Find box, enter `Identity Provider`, then select **Identity Provider**.![Enable Identity Provider](/static/01/enable_identity.png)
1.  Choose **Enable Identity Provider**.
1.  Select a certificate from the dropdown menu.
1.  Select **Save**, then confirm by selecting **OK**.

> **_NOTE:_** Salesforce also defines a lifetime for SAML assertions sent to your service provider. A SAML assertion sent by a Salesforce identity provider is valid for 5 minutes after it's issued, with a 30-second buffer to account for clock skew. For example, if the assertion is issued at 12:00:00 GMT, it's valid between 11:59:30 GMT and 12:05:00 GMT. If the service provider receives the SAML response outside of this interval, it typically rejects the assertion.

Once you have enabled Salesforce as an identity provider, you are ready to turn on Voice.

**NEXT STEP: [Turn on voice](prep_04.md)**
