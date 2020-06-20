# Azure Resource Manager (ARM) template deployment of Windows Vitrtual Machine

## Azure Resource Manager (ARM) Templates
<p align="center">
<img src="./az.png">
<br />
</p>


1. The way of  deploying infrastructure-as-code to Azure is  Azure Resource Manager (ARM) Templates  which are the obvious way of doing it simply and repeatedly. They define the objects you want, their types, names and properties in a JSON file which can be understood by the ARM API.<br/>
2. This demo shows how to deploy an windows VM using an  ARM templates .<br/>
3. Also it contains the three ways of deploying ARM Templates to Azure.<br/> 


# Deployment Details
1. To deploy a VM we need to aasign it to a Virtual Network First.<br/>
2. The azuredeploy template above first creates a Virtual Network with two subnets- Frontend and Backend Subnet.<br/>
3. It also assignd Network Security Groups (NSG) to each of the subnets.<br/>
4. The template defines the security rules for both of the subnets.<br/>
5. It assigns Storage account, Network interface, Disks, Public IP address to the VM.<br/>
6. It deploys the VM in the frontend subnet for demonstration purposes and enbles RDP connection for the VM.<br/>

# Template Details

# There are three ways to deploy an ARM template in Azure:
### 1.  Deploy to Portal

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fdevyanshi-t%2FDemoOne%2Fmaster%2Fazuredeploy.json"  target="_blank">
<img src="http://azuredeploy.net/deploybutton.png"/> 
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-AAD-DomainServices%2Fazuredeploy.json" target="_blank">
<img src="http://armviz.io/visualizebutton.png"/> 
</a></br>
Click on the deploy button above, you will be redirected  to Azure where you can fill in all the parameters in ARM template to create a Virtual Network.<br/>

###    2. Azure Command Line Interface(CLI)
<a href="https://shell.azure.com" target="_blank">
<img name="launch-cloud-shell" src="https://docs.microsoft.com/azure/includes/media/cloud-shell-try-it/launchcloudshell.png" data-linktype="external">
</a>
</br>

```bash
az group deployment create --resource-group Resource group name --template-file file name
```
###  3. PowerShell 

<a href="https://shell.azure.com" target="_blank">
<img name="launch-cloud-shell" src="https://docs.microsoft.com/azure/includes/media/cloud-shell-try-it/launchcloudshell.png" data-linktype="external">
</a>
</br>

```bash 
New-AzResourceGroupDeployment -ResourceGroupName resource-group-name -TemplateFile path-to-template 
```
Note: Do change the directory to home before executing the command.
<br/>Refer to the parameter.json file to see the default values for the parameters .






