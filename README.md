# Zoho-Books-Custom-Connections
Tutorial for creating custom connections in Zoho Books.

Weirdly enough, Zoho Books does not have a default Connection for using Zoho APIs. Also to note, the Zoho APIs have more capabilites than the standard Deluge functions. 

For example's sake let's walk through how to connect to the Zoho Books API in...Zoho Books. So meta, right? Actually we can use this same process for all Zoho APIs that use OAuth 2.0:
* Zoho Books
* Zoho CRM
* Zoho Desk
* Zoho Projects
* Zoho Invoice
* Zoho Inventory
* Zoho Sign
* and then some...


## Tutorial
### Create API Credentials:
#### Connecting to an external REST API:
It is very common to want to import data from another software provider. Before you make a Custom Connection in Books, make sure you have taken a look at the list of ready-to-go connections.

You will need to generate some authentication credentials from your API. This tutorial assumes this API will be using OAuth 2.0. If the API does not use OAuth 2.0, reach out to us at https://theworkflowacademy.com/get-help/ and we may be able to help.

**IMPORTANT:** When creating a Custom Connection in Zoho Books or CRM, you must register the following URL as an approved Redirect URI:   

      https://deluge.zoho.com/delugeauth/callback
      
Zoho Books will use this when completing the OAuth 2.0 workflow.

#### Connecting to a Zoho REST API:
It's very easy to register our "app" with Zoho to get OAuth 2.0 permissions:
1. Go to the [Zoho API Console](https://api-console.zoho.com/)
2. Click **Add Client** and select **Server-based Applications**
3. Fill in the following fields:
   * **Client Name** -> `Zoho Books API`
   * **Homepage URL** -> `https://books.zoho.com`
   * **Authorized Redirect URIs** -> `https://deluge.zoho.com/delugeauth/callback`
4. Click **Update**
5. Notice the *Client ID* and *Client Secret* here. You will need these in the next step, so keep this tab open.
  
### Create Custom Connection
Now, we're going to actually create the Connection in Zoho Books.
1. Visit [Zoho Books](https://books.zoho.com)
2. Click **Settings** > **Automation** > **Custom Functions**
3. Select **+ New Custom Function** and give it a random name and module. We will only use this function for a simple test.
4. Choose **Connections** on the right hand side, then **Go To Connections**.
5. Click **Add Connection**. Choose **Custom Service**.
6. Fill in the following fields (This has to be very exact):
   * **Service Name** -> `Zoho Books`
   * **Service LinkName** -> `zoho_books`
   * **Authentication Type** -> `oAuth2`
   * **Param Type** -> `Header`
   * **Grant Type** -> `Authorization Code`
   * **Client ID** -> `[YOUR_CLIENT_ID]`
   * **Client Secret** -> `[YOUR_CLIENT_SECRET]`
   * **Authorize URL** -> `https://accounts.zoho.com/oauth/v2/auth?`
   * **Access Token URL** -> `https://accounts.zoho.com/oauth/v2/token?`
   * **Refresh Token URL** -> `https://accounts.zoho.com/oauth/v2/token?`
   * **Connection Name** -> `Zoho Books`
   * **Connection LinkName** -> `zoho_books`
   * **Scope** -> `ZohoBooks.fullaccess.all` or [YOUR_SCOPE_HERE] (Note: Be sure to click the **'+'** to add the scope. You can also add multiple scopes.)
   * **Use credentials of login user** -> `UNCHECKED`
7. Click **Create and Connect**. If asked to authenticate, enter your login details.

This should have created the connection. If it was unable to connection, please verify you data inputs. If you continue to face issues, please reach out to us at https://theworkflowacademy.com/get-help/.

Happy workflowing!
