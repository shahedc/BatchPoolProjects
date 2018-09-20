# BatchPoolProjects
Azure Batch .NET projects to spin up VMs

Derived from Microsoft's Azure Batch Samples:
- Sample Code: https://github.com/Azure/azure-batch-samples/tree/master/CSharp/ArticleProjects/DotNetTutorial
- Article: https://docs.microsoft.com/en-us/azure/batch/batch-dotnet-get-started 
- 3D Toolkit Implementation Sample (in branch): https://github.com/3DStreamingToolkit/cloud-deploy/tree/function-batch/function-batch/BatchPoolWebApp
- 3D Toolkit Iplementation (in master): https://github.com/3DStreamingToolkit/cloud-deploy/tree/master/web-api


# Steps to run the BatchPoolApp project

1. Create a new Batch account in Azure.

    - Tutorial: https://docs.microsoft.com/en-us/azure/batch/quick-create-portal

2. Register your Batch app with Azure AD
    - Tutorial: https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#adding-an-application

3. Create a config file using the template provided.
    - _(see instructions in Config File section)_

4. In the *CreatePoolIfNotExistAsync()* method of the *Program.cs* file, edit the call to *PoolOperations.CreatePool()* to use either a *cloudServiceConfiguration* or *virtualMachineConfiguration*. Note that VM images must be located in the same Region and Subscription as the Batch account.

4. Build the Solution in Visual Studio (2017).

5. Run the "BatchPoolApp" project (console app).

# Config File

Make a copy of the config file template "AppSettingsSecrets.config.txt" and remove the .txt extension. Replace the placeholder values with your own settings.

```xml
<appSettings>
  <!-- Azure AD + integrated auth credentials -->
  <add key="AuthorityUri" value="https://login.microsoftonline.com/REPLACE-TenantId-DirId" />
  <add key="BatchResourceUri" value="https://batch.core.windows.net/" />
  <add key="ClientId" value="REPLACE-App-ClientId" />
  <add key="RedirectUri" value="REPLACE-AnyValidUri" />
  
  <!-- Batch account credentials -->
  <add key="BatchAccountName" value="REPLACE-BatchAccountName" />
  <add key="BatchAccountKey" value="REPLACE-BatchAccountKey" />
  <add key="BatchAccountUrl" value="REPLACE-BatchAccountUrl" />
  
  <!-- Storage account credentials-->
  <add key="StorageAccountName" value="REPLACE-StorageAccountName" />
  <add key="StorageAccountKey" value="REPLACE-StorageAccountKey" />
  
  <!-- Custom Pool/Job settings -->
  <add key="PoolId" value="REPLACE-PoolId" />
  <add key="JobId" value="REPLACE-JobId" />
  
  <!-- VM image settings -->
  <add key="VirtualMachineImageId" value="REPLACE-VirtualMachineImageId" />
</appSettings>

```

# Further Documentation

- Create pool: https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.batch.pooloperations.createpool?view=azure-dotnet

- Cloud Service Configuration: https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.batch.cloudserviceconfiguration?view=azure-dotnet

- Virtual Machine Configuration: https://docs.microsoft.com/en-us/dotnet/api/microsoft.azure.batch.virtualmachineconfiguration?view=azure-dotnet

- Create pool with custom images: https://docs.microsoft.com/en-us/azure/batch/batch-custom-images
