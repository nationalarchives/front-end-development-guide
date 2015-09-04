# Deploying to Azure 

These instructions describe the process for deploying HTML prototypes to an Azure website for testing and review. Please remember that Azure websites are public. While this is unlikely to present any issues for most development activity, developers should consider - on a case-by-case basis - whether Azure is the best option for hosting the prototype. In all cases, it is important to:
* turn the site off when it's not being used, and delete it when it is no longer needed. 
* consider obfuscating the url. One option for doing this is to create a SHA hash on the command line and use this as the site name (see instructions below).

These instructions are accurate at the time of creation but, ***if you find the process has changed when you come to use them, please update the instuctions for the benefit of others***. 

## Step 1: Sign in to Azure

Create an account for your TNA development at [http://azure.microsoft.com](http://azure.microsoft.com). This uses a Microsoft ID, but it's a good idea to keep this separate from any account you may have already. 
 
## Step 2: Open your Azure Management Portal

Having created an account, click the 'portal' menu link (at the time of writing this is at the top-left of the screen) and sign in. Having done this, you should see a screen similar to this 

![Azure management portal](https://raw.githubusercontent.com/nationalarchives/development-guide-and-peer-reviews/master/images/azure-management-portal.png?token=ACfFGbixqP4O1tOqW5Lu0ZUb9vIt0HvEks5V8wNIwA%3D%3D)

At this point you should: 

* Click the 'New' button (bottom left of screen)
* Select COMPUTE > WEB APP > CUSTOM CREATE, at which point you'll be prompted for a URL. The text that you enter here will be used as subdomain for the site on azurewebsites.net. If you'd like to create an obfuscated URL, typing ```echo 'tna-business-plan' | openssl sha1 | pbcopy``` (with tna-business-plan replaced with your chosen string) will **copy a SHA1 hash to your clipboard**. You can then paste this into the form field. 
* Ignore the APP SERVICE PLAN and DATABASE fields
* Check the option to **publish from source control** at which point you can proceed to the next step
* Choose GitHub as the answer to the 'Where is your source code?' question and proceed. If you have not yet authorised Azure to access your GitHub account, you will be prompted to do so at this point. 
* You can then select the **repository** AND **branch** that will be used for automated deployments. 

From this point forward, any code pushed that the selected branch on GitHub will be immediately deployed to the Azure site. 




