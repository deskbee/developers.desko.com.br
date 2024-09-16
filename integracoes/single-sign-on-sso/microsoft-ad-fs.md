# Microsoft AD FS

### Overview <a href="#toc92963874" id="toc92963874"></a>

Active Directory Federation Services (AD FS) is a Windows Server component that allow us manage single sign-on (SSO) access with external applications via Relying Party Trusts (RPT) object. The following procedure will create a RPT object in your AD FS in order to trustily connect _Desko_ app for single sign-on authentication. These instructions also apply to Windows Server 2019, 2016, 2012 R2 and 2008 R2 versions with ADFS v2 and v3, but be aware that there are slight differences in the configuration flow.

Before start, it is necessary to get the _Desko’s_ URLs that is going to be inserted into the proper fields during the RPT object creation, then please follow the steps below:

1. Go to your _Desko_ panel heading over to **https://\<YourCompanyName>.painel.desko.com.br**

**Note: You have to log in using a Master or Admin account.**

![](../../.gitbook/assets/1)

2\. Expand **Integrations** and click on **Authentication**

![](../../.gitbook/assets/2)

3\. Turn on **SSO SAML 2.0 authentication**

![](../../.gitbook/assets/sso8.png)

4\. Go to the bottom of the page at **SAML Basic setup** section and keep it open, you will need these 3 URLs **Identifier (Entity ID), ACS response URL** and **Logout URL** in the next steps

**Note: The image below is for illustrative purposes only, please check on your Desko Panel the URLs matching your account. Each account has its own unique URLs.**

![](<../../.gitbook/assets/sso13 (1).png>)

### Creating Relying Party Trusts (RPT) object <a href="#occ5a3rr1goy" id="occ5a3rr1goy"></a>

5\. Open your **AD FS Management** snap-in, right click on **Relying Party Trusts** e choose **Add Relying Party Trust**

![](../../.gitbook/assets/5)

6\. Keep **Claims aware** option and click on **Start**

![](../../.gitbook/assets/6)

7\. Select **Enter data about the relying party manually** option and click on Next

![](../../.gitbook/assets/7)

8\. Insert a name for the **Display name** field and click on **Next**

![](../../.gitbook/assets/8)

9\. Click on **Next** to skip the token certificate option which is optional

![](../../.gitbook/assets/9)

10\. Choose **Enable support for the SAML 2.0 WebSSO protocol** option, insert the ACS response URL from _Desko_ panel opened in **item 4** as shown below and click on **Next**

![](../../.gitbook/assets/adfs6.png)

11\. In the **Configure Identifiers** step, insert the **Identifier Entity ID** URL from _Desko_ panel as shown below, click on **Add** and then on **Next**

![](../../.gitbook/assets/11)

12\. Keep the default Policy as **Permit Everyone** and click on **Next**

![](../../.gitbook/assets/12)

13\. Review your settings and click on **Next** to add your Relying Party Trust to the AD FS database

![](../../.gitbook/assets/13)

14\. Keep the selected check-box **Configure claims issuance policy for this application** in order to open and configure Claims policies for _Desko_ RPT and click on **Close**

**Note: Once a user is authenticated by SSO, it is mandatory to have claim rules to specify data attributes and its formats such as Name and email. These data attributes will be sent to \_Desko**_\*\* in response to SAML 2.0. As \*\*_**Desko**\_\*\* requires a name identification element that contains the user's email address, in the next section we will create 2 configuration rules.\*\*

![](../../.gitbook/assets/adfs10.png)

### Creating Claim Rules Policies <a href="#toc92963876" id="toc92963876"></a>

15\. In the **Issuance Transform Rules** tab, click on **Add Rule** to start a new rule

![](../../.gitbook/assets/15)

16\. For the first rule, select **Send LDAP Attributes as Claims** option and click on **Next**

![](../../.gitbook/assets/16)

17\. Enter a name for your first rule and select **Active Directory** attribute store. In the table **Mapping of LDAP attributes to outgoing claim types,** select:

_**Display-Name**_\*\* \*\* to \*\* **\_**Name\*\*\_

_**E-Mail-Addresses**_\*\* \*\* to \*\* **\_**E-Mail Address\*\*\_

Just like shown below and click on **Finish**

![](../../.gitbook/assets/17)

18\. Click on **Add rule** to add and start the second rule

![](../../.gitbook/assets/18)

19\. For the second rule, select **Transform an Income Claim** option and click on **Next**

![](../../.gitbook/assets/19)

20\. Enter a name for your second rule and select:

_**E-Mail**_\*\* \*\* for \*\* **\_**Incoming claim type\*\*\_

_**Name ID**_\*\* \*\* for \*\* **\_**Outgoing claim type\*\*\_

_**Persistent Identifier**_\*\* \*\* for \*\* **\_**Outgoing name ID format\*\*\_

Just like shown below and click on **Finish**

![](../../.gitbook/assets/20)

21\. Click on Apply in order to commit the new rules

![](../../.gitbook/assets/adfs17.png)

22\. After commit and close the Claim dialog, go to your Relying Party Trusts list, right-click on the object you just created and click on **Properties**

![](../../.gitbook/assets/adfs18.png)

23\. Go to **Endpoints** tab and click on **Add SAML**

![](../../.gitbook/assets/adfs19.png)

24\. Select _**SAML Logout**_ for _**Endpoint type**_ option and _**Redirect**_ for _**Binding**_ option. Insert the _**Logout URL**_ from _Desko_ panel into the _**Trusted URL**_ field just like shown below and click on **OK**

![](../../.gitbook/assets/adfs20.png)

25\. Go to **Advanced** tab and make sure that _**Secure hash algorithm**_ is set to **SHA-256**. Click on **Ok** to close the object properties

![](../../.gitbook/assets/adfs22.png)

### Getting the Token Signing Certificate <a href="#toc92963877" id="toc92963877"></a>

26\. In your **AD FS Management**, expand **Service**, go to **Certificates**, right-click on your **Token-signing** certificate and choose **View Certificate**

![](../../.gitbook/assets/adfs23.png)

27\. Go to **Details** tab and click on **Copy to File**

![](../../.gitbook/assets/adfs24.png)

28\. Choose Base-64 encoded X.509 (.CER) option and click on Next

![](../../.gitbook/assets/adfs25.png)

29\. Specify a name and a location to export the CER file and click on **Next.** You will need to upload the CER file on _Desko_ panel later on

![](../../.gitbook/assets/adfs26.png)

### Getting the AD FS Federation Metadata <a href="#toc92963878" id="toc92963878"></a>

30\. In this step, it is necessary to get the AD FS Federation Metadata in order to obtain the URLs from your AD FS to insert on _Desko_ panel. For that, open a web-browser, head over to [https://adfshelp.microsoft.com/MetadataExplorer/GetFederationMetadata](https://adfshelp.microsoft.com/MetadataExplorer/GetFederationMetadata) insert your federation service name and click on **Get federation metadata** as shown below

![](../../.gitbook/assets/adfs27.png)

31\. Once you get your federation metadata, it’s time configure your _Desko_ panel. First of all give a name to your connection, then insert the _**Entity ID**_ URL from federation metadata into _**Identity ID**_ field on _Desko_ panel and _**Federation Passive Endpoint**_ URL into _**Login URL**_, just like shown below (The Logout URL is optional)

![](../../.gitbook/assets/adfs28.png)

32\. Upload the certificate file you exported and converted in the item **29**. Click on **Update Certificate**, select the CER file and click on **Open**

![](../../.gitbook/assets/adfs29.png)

33\. Scroll down to the bottom of the page, click on **Save** button and it’s done!

![](<../../.gitbook/assets/okta19 (1).png>)

34\. To access your _Desko_ app, just head over to **https://\<YourCompanyName>.desko.com.br** and click on the button you named for your login method.

![](../../.gitbook/assets/Capture.PNG)

### Versioning: <a href="#toc92963879" id="toc92963879"></a>

| **Version** | **Author**          | **Date**   |
| ----------- | ------------------- | ---------- |
| v1.0        | Eduardo de Oliveira | 01/13/2022 |
