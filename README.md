# Silly Little Site On Azure

This is a getting started with .Net MVC and azure challange. 

You are going to make a simple website deploy it to azure and make some small midifications. 


The goal of this challenge is:

 - Create a new .NET MVC solution
 - Setting up Continuous Deployment (CD) to Azure
 - Editing the _layout.cshtml file to personalise the site a little
 - Setting up a database connection in Azure
 - Enabling OAuth logins

 -------------------------------


##New MVC Site
 - Create a new github repository to put this solution into. We will be building on the foundations in later challanges
 - Make sure you create the git hub repo with the Visual Studio .gitignore file (VERY IMPORTANT if you dont want to waid thor lots of unnessary diffs)
 - Open Visual Studio
 - Click File -> New -> Project
 - Follow directions below
 - <image>
 - Follow Directions in image
 - <image>
 - Git commit changes (Very important!)
 - Git push origin
 - In visual studio press F5
 
So at this point you will have a new site open itself in your default browser
Woot Go you!!


 ##Continuous Deployment (CD) to Azure
 
  - Signup to azure [https://azure.microsoft.com/en-us/pricing/free-trial/](https://azure.microsoft.com/en-us/pricing/free-trial/) 
   - You will need a credit card, but you wont need to spend anything ($250 credit free trial)
  - Click New
  - Go through the wizard to create a new site ( See here for a full guide [https://azure.microsoft.com/en-in/documentation/articles/web-sites-publish-source-control/](https://azure.microsoft.com/en-in/documentation/articles/web-sites-publish-source-control/)
   - Connect up your github repo
  - You should now see your published site live on the internet (So cool!)
  
## Small personalisations

In .Net MVC there is a file views/shared/_layout.cshtml This is the (default) master page.
Open it up and have a look around. This file uses the razor view templating syntax. You will notice it has html mised up with a lot of `@` When a page is renedred the `@` parts will get replaced with content.
 
 - Find where it says `@Html.ActionLink("Application name", "Index", "Home", new { area = "" }, new { @class = "navbar-brand" })` on line 20
  - Change `Application name` to something more interesting
 - Find where it says `<p>&copy; @DateTime.Now.Year - My ASP.NET Application</p>` on line 36
  - Change `My ASP.NET Application` to something more interesting
  - Save changes (Ctrl+S)
  - Go back to your browser and press F5 to refresh
  - Have a look for your changes
  - View source (Ctrl+U)
  - See how `@Html.ActionLink("Application name", "Index", "Home", new { area = "" }, new { @class = "navbar-brand" })` has converted into an `<a>` (line 23) and `@DateTime.Now.Year` into the current year (line 72)
 - Have a look at line 33 of _layout.cshtml `@RenderBody()`
  - This is where the content from the view (so far from: `/views/Home/Index.cshtml`) gets injected in.
 
##Publishing personalisations

We are going to take the personalisations made before and publish them. 
 - git commit 
 - git push origin
 - Go to the url of your page hosted on azure
  - Keep refreshing the page after a few seconds your changes should have been deployed and the site updated
  - 
  
##Add DataBase on Azure

Now a website is all fine and dandy. However we want to put some stuff in a database to make things a little bit more interesting. Out of the box .net MVC uses something called LocalDB. This is all good for development; but is no good when we are running on Azure. LocalDB is not designed for concurrent access (lots of users at one time), also once a site is deployed to Azure you only have read access to the file system. (There are good technical reasons for this.) So we need to setup a database on Azure and then fixup the config to point to that db when deployed


 - Follow this guide to setup a db on azure [https://azure.microsoft.com/en-us/documentation/articles/sql-database-get-started](https://azure.microsoft.com/en-us/documentation/articles/sql-database-get-started/)
 - Once the database is setup grab the connectionsting <image>
 - Find the Azure website you created before
 - Go to the settings <image>
 - Find the connections string settings 
 - Add the connections string (you may need to replace the password part)
 - Save

Sweet you've got yourself a sweet database talking to your live site. Go you!
You can now register as a user on the site and login.

We have put the connection string setting for production (Azure) in the azure settings. We want to do it this way, rather than saving it in the config files (web.config, config.json), because we dont want our production db password saved into git where anyone (with access) to the code base can find it. This may sound a little paranoid but you will find it really is not.

##Add OAuth access



##Add an Authorised access page
 




  
  
 


  


 
