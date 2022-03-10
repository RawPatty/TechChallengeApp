### Prerequisite Resources

This workflow is designed to be used with Azure Cloud
You will need a directory and a subscription of your own to deploy resources into.
You will need access to this github repo's resources

### Permissions, Accounts, and Secrets

To run this workflow, you will need to set up a service principle.
In the Azure Cli, when you have the role of "Application Administrator" or higher and Owner permissions on the subscription, run:
az ad sp create-for-rbac --name "githubactions" --role contributor --sdk-auth

This will create a set of credentials which will need to be entered into the github secrets area
The response you get from the above command will look like

{
   "clientId": "0000-0de0-0000-0000-0000",
   "clientSecret": "0000000000000000000000000000",
   "subscriptionId": "0000000000000000000000000000",
   "tenantId": "000000000000000000000000",
   "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
   "resourceManagerEndpointUrl": "https://management.azure.com/",
   "activeDirectoryGraphResourceId": "https://graph.windows.net/",
   "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
   "galleryEndpointUrl": "https://gallery.azure.com/",
   "managementEndpointUrl": "https://management.core.windows.net/"
}

You will need the following secret names
ACR_USERNAME - Use the value of clientID 
ACR_PASSWORD - Use the value of clientSecret
AZURE_CREDENTIALS - The value should be the whole response block (lines 15-26)
AZURE_SUB_ID - Use the subscriptionID of your Azure subscription

### How to get started
After setting up the above secrets, the workflows should be run

This github workflow requires the "run-once-setup.yaml" workflow to be run first to set up resources that the second workflow will deploy to.

Run the "docker-image.yml" workflow to deploy to container instance.


### Overview of the workflows 

Both workflows can be manually triggered
The Run-once workflow sets up the resources for a fresh subscription
Any updates to master branch or merged pull-requests will trigger the docker pipeline to deploy the latest contents to Azure

### Notes

Unfortunately I was unable to debug why the applicaiton was crashing post-deployment, in a working environment, I would get in touch with the developers/app support to go through it together.

This was my first time using Github actions, so it was very interesting to learn how to get the workflow working via the modules rather than coding it all in Azure Powershell.
