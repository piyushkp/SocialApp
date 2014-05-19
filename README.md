SocialApp
=========

C# Application Integration with Facebook,Twitter and LinkeIn


  1.  Setting a Facebook status through a C# application
  2.  Sending a Tweet through a C# application
  3.  Setting LinkedIn Status through a C# application
  
FACEBOOK:  

Let's start by first doing the Facebook part of this article. 

To set a status on Facebook using your C# application, first of all you will need to create an application by going to the following link:

https://developers.facebook.com/apps

    Click on the CREATE NEW APP button.

    Fill in the required information and click Continue

    Now your application has been created. There are 2 things that you need to take note of; The App ID & AppSecret. We will be using them later on.

   

    Now let us move on to the coding. Make a new Windows Forms Project. We will add a WebBrowser to our main form.
    The App.config of your project should look something like this:

Collapse | Copy Code

<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="EnableSqlDependency" value="true" />
    <add key="ApplicationId" value="<YOUR APP ID GOES HERE>" />
    <add key="ApplicationUrl" value="" />
    <add key="ApiKey" value="" />
    <add key="ApplicationSecret" value="<YOUR APP SECRET GOES HERE>" />
    <add key="ExtendedPermissions" value="offline_access" />
  </appSettings>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0" />
  </startup>
</configuration>

    Now we'll move on to authorizing the application. For this you'll have to login to your Facebook account when the application prompts. This will give you the access token that you would need to communicate. 
    We'll be using the Facebook C# SDK (http://csharpsdk.org/) You can get it from the mentioned link
    Now we are ready to post our status:

Collapse | Copy Code

var fb = new FacebookClient(this.AccessToken);
dynamic result = fb.Post("me/feed", new { message = "My second wall post using Facebook C# SDK" });

    The complete project is attached with the article, All you have to do to make it work is to enter your App ID & App secret in the app.config.

