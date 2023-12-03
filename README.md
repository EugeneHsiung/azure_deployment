# azure_deployment

Deploy Application via Azure:
In the Google Shell terminal, you will need to install AZURE CLI with this: curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash. Copy and paste the line in and enter.

Then type in az. Type in az login --use-device-code and wait for a link and a code to appear in the terminal. Copy the code and press the link to log in to your Azure account. This will help connect your Google Shell with your Azure account.

Log in to your Azure account. Navigate to Resource Group and create a new Resource Group with a unique name. Press Review and Create.

Head back to Google Shell and in the terminal, type in az account list --output table to make sure you have the correct subscription for your Azure account. Make sure your subscription is correct. In my case, the subscription is Azure for Students. If the subscription has not defaulted to the desired one, type in az account set --subscription <paste the desired SubscriptionId here>.

Now type in az group list.

Type in az webapp up --name <replace with what you would like to name the webapp> --runtime PYTHON:3.9 --sku B1. Once entered, the Azure app service will create the web app for you. This step may take a while to load.

Once the service completes the deployment, you can go to App Service in the Azure site to deploy the web app. Choose the appropriate web app. Then you will be redirected to the overview of the web app. The link for your application will be found at the Default domain. Click on the link and you will now be redirected to your web application.








# flask_6_api_management

# Flask-based RESTful API
Using the [templates](https://github.com/hantswilliams/HHA_504_2023/tree/main/WK6/code/flask) provided, I created flask examples named `app_basic.p` and `app_flasgger.py` inside this [folder](https://github.com/EugeneHsiung/flask_6_api_management/tree/main/examples.py). I combined both templates and created an `app.py` flask template for this assignment. By running this application, type in `python app.py` in the shell terminal. The output would be a json file. For example: replace everything after the .dev with `/home?name=John&lastname=Smith` and the output should result in `{
  "message": "Hello JOHN SMITH!"
}`

# Azure API deployment and Flassger 
Follow this [guide](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt) and this [guide](https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-cli-python?tabs=linux%2Cbash%2Cazure-cli&pivots=python-mode-decorators)
1. In order to install Azure CLI, type in `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`
2. Type in `az login --use-device-code` and follow instructructins by clicking the link provided and typing in the password provided/
3. Type in `sudo apt-get install azure-functions-core-tools-4` to install Azure Functions Core Tools for Linux
4. Type `func init LocalFunctionProj --python -m V2` to create Azure Functions project folder
5. Open `local.settings.json` folder and verify that `AzureWebJobsFeatureFlags` is equal to `EnableWorkerIndexing`
6. Go to Azure and search storage. Create a new storage. Access the storage and go to `Acess keys`. Copy the connection string under any of the keys.
7. Go back to the folder in the shell enviorment and find `AzureWebJobsStorage`. Paste the connection string after.
8. In your `function_app.py` under the `LocalFunctionProj` replace contents with the chosen code and reformat it following the guide. For example, for mine I inserted this [code](https://github.com/EugeneHsiung/flask_6_api_management/blob/main/LocalFunctionProj/function_app.py) 
9. In the terminal, cd into the `LocalFunctionProj` then type `func start`.
10. Type `az functionapp create --resource-group <resource group name> --consumption-plan-location eastus --runtime python --runtime-version 3.9 --functions-version 4 --name <app name> --os-type linux --storage-account <storage account name>`. Replace with your resource group name, a chosen app name, and the storage account name created in Azure. This will create the API connection. 
11. Type: `func azure functionapp publish <app name>` and replace the app name with the chosen app name from the prior step.
12. Images of the API and flassger can be seen in the screenshots [folder](https://github.com/EugeneHsiung/flask_6_api_management/tree/main/Screenshots)
