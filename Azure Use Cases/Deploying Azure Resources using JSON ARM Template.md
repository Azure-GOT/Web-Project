# Deploying Azure Resources using JSON ARM Template

Create an ARM Template


<ul>
	
<li>In the Visual Studio Code or any other editor you want, create a new file deploy.json</li>
	
	
<li>If you have <b>Azure Resource Manager Tool for Visual Studio Code extension</b> installed, simply write <b>arm!</b> and press enter</li>
	
<img src="Images/arm-snippet.png">
	

<li> Your new file will look like this</li>	
<img src="Images/ARM.png">

</ul>



# Deploy ARM Template to Azure

Make sure you have installed Azure Powershell, and sign in with the same Azure account
<ul>
<li>From the terminal in Visual Studio Code, connect to azure with the following command</li>
	
		Connect-AzAccount
	
<li>Your Account may be associated with multiple subscription, to change the acive subscription that you want get the subcription ID with the following command</li>
		
		Get-AzSubscription
	

	
<li>Now change the active subscription with the following command</li>
	
		$context = Get-AzSubscription -SubscriptionId {Your subscription ID}
		Set-AzContext $context
	
<img src="Images/SubscriptionID.png">

<li>Deploy the template by using Azure Powershell Command</li>
	
<img src="Images/BlankDeployment.png">
	
<li>You will see the succeeded message in the terminal</li>
	
<li>You can see the Deployment in the Resource Group from the Azure Portal as well</li>
	
<img src="Images/Deployment.png">
</ul>

# Add Resource to the ARM Template

<ul>

<li>Enter <b>storage</b> inside the resouces brackets and select <b>arm-storage</b></li>
	
<img src="Images/arm-storage.png">
	
<li>Your new file will look like this:</li>
	
<img src="Images/storage_account.png">
	
<li>Now Deploy the updated template</li>
	
<img src="Images/deploy_storage_account.png">
	
<li>Check your deployment is completed or not from the Azure Portal</li>
	
<img src="Images/Storage_account_from_resource_group.png">

</ul>

# Create parameters for the ARM template

<ul>
	
<li>Create a parameter for <b>Storage Name</b> value</li>
	
<li>In the file, inside the braces in the paramters attribute, write <b>par</b> and choose <b>arm-param</b>. It will look like this:</li>
	
	"parameters": {
    		"parameter1": {
   		"type": "string",
    		"metadata": {
       	 	"description": "description"
    		}
  	   }
	},

	
<li>Now change the required fields and your new file will look like this:</li>
	
<img src="Images/NameParameter.png">
	
<li>Deploy this new parameterized ARM template by using following code</li>
	
<img src="Images/NameParameterTerminal.png">
	
<li>Check your deployment from the Azure Portal</li>
	
<img src="Images/NameParameterPortal.png">

<li>We can add another parameter for the storage SKU to limit allowed values</li>
	
<li>The new parameter will look like this:</li>
	
<img src="Images/StorageSKU.png">
	
<li>Now if we choose the different value other than the allowed values, the deployment will fail. You can see the error</li>
	
<img src="Images/StorageSKUTerminal.png">
	
<img src="Images/StorageSKUFailed.png">
