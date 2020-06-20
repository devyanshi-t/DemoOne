# Azure Resource Manager (ARM) template deployment of Windows Vitrtual Machine

## Azure Resource Manager (ARM) Templates
<p align="center">
<img src="./az.png">
<br />
</p>


1.The way of  deploying infrastructure-as-code to Azure is  Azure Resource Manager (ARM) Templates  which are the obvious way of doing it simply and repeatedly. They define the objects you want, their types, names and properties in a JSON file which can be understood by the ARM API.<br/>
2. This demo shows how to deploy an windows VM using an  ARM templates .<br/>
3. Also it contains the three ways of deploying ARM Templates to Azure.<br/> 


# Deployment Details
1. To deploy a VM we need to aasign it to a Virtual Network First.<br/>
2. The azuredeploy template above first creates a Virtual Network with two subnets- Frontend and Backend Subnet.<br/>
3. It also assignd Network Security Groups (NSG) to each of the subnets.<br/>
4. The template defines the security rules for both of the subnets.<br/>
5. It assigns Storage account, Network interface, Disks, Public IP address to the VM.<br/>
6. It deploys the VM in the frontend subnet for demonstration purposes and enbles RDP connection for the VM.<br/>


