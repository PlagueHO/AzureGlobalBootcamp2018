# Containerize Your World using Azure Container Services

This session will show you how to get started with Azure Container Service (ACS), one of the most powerful ways of running containerized applications in Azure. You'll learn how to set up a Kubernetes cluster using the Azure Cloud Shell and deploy a highly available and scalable web application with only a few commands. We'll then show how easy it is to scale up, reconfigure or update your application without any incurring any downtime to users.

## Content

- [Part 1 - Opening a Cloud Shell](#Part-1---Opening-a-Cloud-Shell)
- [Part 2 - Create an Azure Container Service](#Part-2---Create-the-Azure-Container-Service)

## Part 1 - Opening a Cloud Shell

Azure Cloud Shell is an interactive, browser-accessible shell for managing Azure resources. It provides the flexibility of choosing the shell experience that best suits the way you work. Linux users can opt for a Bash experience, while Windows users can opt for PowerShell.

1. Open Cloud Shell by clicking the Cloud Shell icon:
   ![Open Cloud Shell](images/opencloudshell.png "Open Cloud Shell")

> If you have **not** previously used Azure Cloud Shell:

![Welcome to Cloud Shell](images/welcometocloudshell.png "Welcome to Cloud Shell")

1. Click **Bash (Linux)**

   _When you first create a Cloud Shell a storage account will get created for you to store your settings, scripts and other files you might create. This enables you to have access to your
   own environment no matter what device you're using._

   ![Create Cloud Shell Storage](images/createcloudshellstorage.png "Create Cloud Shell Storage")

1. Select the **subscription** to create the Storage Account in and click
   **Create storage**.
1. The Storage Account will be created and the Cloud Shell will be started:

   ![Cloud Shell Started](images/cloudshellstarted.png "Cloud Shell Started")

> If you have previously used Azure Cloud Shell:

1. Select **Bash** from the shell drop down:

   ![Select Bash Cloud Shell](images/selectbashcloudshell.png "Select Bash Cloud Shell")

## Part 2 - Create an Azure Container Service

1. Run this command in CloudShell, but change 'myacs' to the name that your container
   service will be created as. Thist must be unique.

```powershell
name="myacs"
```

2. Run this command in CloudShell to create a resource group:

```powershell
az group create --name $name-rgp --location EastUS
```

3. Run this command in CloudShell to create a kubernetes cluster:

```bash
az acs create --name $name --resource-group $name-rgp --location EastUS --dns-prefix $name --orchestrator-type kubernetes --generate-ssh-keys --agent-count 2
```