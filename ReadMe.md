# Azure Resource Manager (ARM) template deployment of Windows Vitrtual Machine

## Azure Resource Manager (ARM) Templates -An Introduction 
<p align="center">
<img src="./az.png">
<br />
</p>


 The way of  deploying infrastructure-as-code (IaC) to Azure is  Azure Resource Manager (ARM) Templates  which are the obvious way of doing it simply and repeatedly. They define the objects you want, their types, names and properties in a JSON file which can be understood by the ARM API.<br/>
 An ARM template usually has following sections:<br/>
 1. Parameters
 2. Variables
 3. User Defined Function
 4. Resources
 5. Outputs
 
[ For further details  on ARM templates refer to this link ]( https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/overview)
# Context
This demo shows how to deploy an windows VM using an  ARM templates .<br/>  We would be deploying the ARM template to Azure using Powershell.<br/> 

# Key Terms
1. Virtual Network(VNet) - It is fundamental building block of a private network in Azure which allows various resources to securely communicate with one another.<br/>
     [For details on Virtual Network refe to this linkr](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
2.   Subnets  - Subnets or Subnetwork are the logical isolation within a VNet.  <br/> It is done using Classless InterDomain Routing (CIDR).<br/>
3.   Network Security groups (NSG) - It contains security rules for inblound and outbound network traffics which helps in filtering the traffic and ensure security.<br/>
    [For details on Network Security Groups in Azure refer to this link](https://docs.microsoft.com/en-us/azure/virtual-network/security-overview)
4.  Virtual Machine(VM) - It is an emulation of the computer system.They provide functionality of a physical computer. <br/> Azure supports all Windows server versions as well as all major Linux Distributions like Ubuntu, RedHat etc.<br/>


# Deployment Details
1. To deploy a VM we need to aasign it to a Virtual Network First.<br/>
2. The azuredeploy template above first creates a Virtual Network with two subnets- Frontend and Backend Subnet.<br/>
3. It also assignd Network Security Groups (NSG) to each of the subnets.<br/>
4. The template defines the security rules for both of the subnets.<br/>
5. It assigns Storage account, Network interface, Disks, Public IP address to the VM.<br/>
6. It deploys the VM in the frontend subnet for demonstration purposes and enbles RDP connection for the VM.<br/>



# Demonstration
The ARM template created is going to be deployed by using Powershell. <br/>
 PowerShell is a cross-platform task automation and configuration management framework by Microsoft which consists  of a command-line shell and scripting language. <br/>
 PowerShell is built on top of the .NET Common Language Runtime (CLR).<br/>
 [For details on Powershell refer to this link](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7)
 
 First we are going to run a Powershell to test that the ARM template is valid.
 ``` bash
 Test-AzResourceGroupDeployment -ResourceGroupName "name of the resource group" -TemplateFile "yourtemplatefilename".json -Mode incremental -TemplateParameterFile "yourparametersfilename".json
```
After the template is validated we are going to actually deploy the template by the Powershell script
```bash 
New-AzResourceGroupDeployment -ResourceGroupName "name of the resource group" -TemplateFile "yourtemplatefilename".json -Mode incremental -TemplateParameterFile "yourparametersfilename".json
```
Note: All deployments of templates here is in incremental mode.<br/>
In incremental mode, Resource Manager leaves unchanged resources that exist in the resource group but aren't specified in the template. Resources in the template are added to the resource group.<br/>
[For details on modes of ARM template deployments refer to this link](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/deployment-modes)
# Result
After the template is succesfully deployed the Powershell will show the details of the deployments.<br/>
<p align="center">
<img src="./1.png">
<br />
</p>
You can go to Azure portal to further verify that all deployments were successful.

<p align="center">
<img src="./2.png">
<br />
</p>

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


# Author
``` Devyanshi Tiwari```

