# azure_deployment

Deploy Application via Azure:
In the Google Shell terminal, you will need to install AZURE CLI with this: curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash. Copy and paste the line in and enter.

Then type in az. Type in az login --use-device-code and wait for a link and a code to appear in the terminal. Copy the code and press the link to log in to your Azure account. This will help connect your Google Shell with your Azure account.

Log in to your Azure account. Navigate to Resource Group and create a new Resource Group with a unique name. Press Review and Create.

Head back to Google Shell and in the terminal, type in az account list --output table to make sure you have the correct subscription for your Azure account. Make sure your subscription is correct. In my case, the subscription is Azure for Students. If the subscription has not defaulted to the desired one, type in az account set --subscription <paste the desired SubscriptionId here>.

Now type in az group list.

Type in az webapp up --name <replace with what you would like to name the webapp> --runtime PYTHON:3.9 --sku B1. Once entered, the Azure app service will create the web app for you. This step may take a while to load.

Once the service completes the deployment, you can go to App Service in the Azure site to deploy the web app. Choose the appropriate web app. Then you will be redirected to the overview of the web app. The link for your application will be found at the Default domain. Click on the link and you will now be redirected to your web application.
