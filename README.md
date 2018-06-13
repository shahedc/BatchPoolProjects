# BatchPoolProjects
Azure Batch .NET projects to spin up VMs

# Steps to run the project

1. Create a new Batch account in Azure.

    - Tutorial: https://docs.microsoft.com/en-us/azure/batch/quick-create-portal

2. Register your Batch app with Azure AD
    - Tutorial: https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#adding-an-application

3. Create a config file using the template provided.
    - _(see instructions in Config File section)_

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
</appSettings>
```
