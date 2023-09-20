# Prime
A simple Python Flask app that checks if a given number is prime, and if not, finds the closest prime number.

You could just run this locally using "flask run", or follow one of the options below to either deploy directly to the Azure cloud, or create it as a container image to deploy anywhere.

### Option 1: Deploy as an Azure Container App  

The Azure Container Apps service supports directly deploying a web app using the "az containerapp up" CLI command.  

This command automatically converts a web app app to a container image and deploys it. Here's an example using the Azure Cloud Shell (which comes with the Azure CLI pre-installed):

1. Connect to Azure Cloud shell (https://shell.azure.com)
2. Clone this repo:  
   `git clone https://github.com/gbowerman/prime`
3. `cd prime`
4. `az containerapp up --name prime --source . --ingress external --target-port 5000 --resource-group prime-group `

Note: The first time you run "az containerapp up" you'll be prompted to install an Azure CLI extension.

### Option 2: Create and run a Docker container image  
Note: If running on Windows, first install Docker Desktop, and make sure you have git installed.  

Change the image tag _"prime-app"_ in the commands below to any name you want to give it.  

1. Clone this repo locally (e.g. using git command line or VS Code etc.)
2. cd to the prime directory  
3. Build a container image:  
   `docker buildx build . -t prime-app:latest`

4. Test locally:  
   `docker run -d --name prime-app-container -p 80:5000 prime-app:latest`
5. Connect to the running app at localhost:80   
  
  
  
__Acknowledgements__  
Credit to Rahul Upadhyaya (@kavishavi) for the inspiration. (see [PrimeContainerapp](https://github.com/kavishavi/PrimeContainerApp) for the latest version of his project)

__License__  
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.