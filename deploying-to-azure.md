# Deploying to Azure 

These instructions describe the process for deploying HTML prototypes to an Azure website for testing and review. Please remember that Azure websites are public. While this is unlikely to present any issues for most development activity, developers should consider - on a case-by-case basis - whether Azure is the best option for hosting the prototype. In all cases, it is important to:
* turn the site off when it's not being used, and delete it when it is no longer needed. 
* consider obfuscating the url. One option for doing this is to create a SHA hash on the command line and use this as the site name (see instructions below).

These instructions are accurate at the time of creation but, ***if you find the process has changed when you come to use them, please update the instuctions for the benefit of others***. 

## Step 1: Sign in to Azure

Create an account for your TNA development at [http://azure.microsoft.com](http://azure.microsoft.com). This uses a Microsoft ID, but it's a good idea to keep this separate from any account you may have already. 
 
## Step 2: Open your Azure Management Portal

Having created an account, click the 'portal' menu link (at the time of writing this is at the top-left of the screen) and sign in. Having done this, you should see a screen similar to this 

![Azure management portal](https://raw.githubusercontent.com/nationalarchives/development-guide-and-peer-reviews/master/azure-management-portal.png)


