---
title: AzureRmWebAppDeployment@2 - Azure App Service Deploy v2 task
description: Update Azure App Service using Web Deploy / Kudu REST APIs (task version 2).
ms.date: 09/01/2022
monikerRange: "<=azure-pipelines"
---

# AzureRmWebAppDeployment@2 - Azure App Service Deploy v2 task

<!-- :::description::: -->
:::moniker range="<=azure-pipelines"

<!-- :::editable-content name="description"::: -->
Update Azure App Service using Web Deploy / Kudu REST APIs.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::description-end::: -->

<!-- :::syntax::: -->
## Syntax

:::moniker range=">=azure-pipelines-2019"

```yaml
# Azure App Service Deploy v2
# Update Azure App Service using Web Deploy / Kudu REST APIs.
- task: AzureRmWebAppDeployment@2
  inputs:
    ConnectedServiceName: # string. Required. Azure Subscription. 
    WebAppName: # string. Required. App Service name. 
    #DeployToSlotFlag: false # boolean. Deploy to slot. Default: false.
    #ResourceGroupName: # string. Required when DeployToSlotFlag = true. Resource group. 
    #SlotName: # string. Required when DeployToSlotFlag = true. Slot. 
    #VirtualApplication: # string. Virtual Application. 
    Package: '$(System.DefaultWorkingDirectory)/**/*.zip' # string. Required. Package or Folder. Default: '$(System.DefaultWorkingDirectory)/**/*.zip'.
  # Output
    #WebAppUri: # string. App Service URL. 
  # Additional Deployment Options
    #UseWebDeploy: true # boolean. Publish using Web Deploy. Default: true.
    #SetParametersFile: # string. Optional. Use when UseWebDeploy == true. SetParameters File. 
    #RemoveAdditionalFilesFlag: false # boolean. Optional. Use when UseWebDeploy == true. Remove Additional Files at Destination. Default: false.
    #ExcludeFilesFromAppDataFlag: false # boolean. Optional. Use when UseWebDeploy == true. Exclude Files from the App_Data Folder. Default: false.
    #AdditionalArguments: # string. Optional. Use when UseWebDeploy == true. Additional Arguments. 
    #TakeAppOfflineFlag: false # boolean. Take App Offline. Default: false.
```

:::moniker-end

:::moniker range="=azure-pipelines-2018"

```yaml
# YAML Syntax is not supported in TFS 2018.
# Use the classic designer to add and configure tasks.
# See the following Inputs section for details on the inputs that this task supports.
```

:::moniker-end
<!-- :::syntax-end::: -->

<!-- :::inputs::: -->
## Inputs

<!-- :::item name="ConnectedServiceName"::: -->
:::moniker range="<=azure-pipelines"

**`ConnectedServiceName`** - **Azure Subscription**<br>
Type: string. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the Azure Resource Manager subscription for the deployment.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="WebAppName"::: -->
:::moniker range="<=azure-pipelines"

**`WebAppName`** - **App Service name**<br>
Type: string. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Enter or Select the name of an existing Azure App Service.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="DeployToSlotFlag"::: -->
:::moniker range="<=azure-pipelines"

**`DeployToSlotFlag`** - **Deploy to slot**<br>
Type: boolean. Default value: false.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the option to deploy to an existing slot other than the Production slot.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="ResourceGroupName"::: -->
:::moniker range="<=azure-pipelines"

**`ResourceGroupName`** - **Resource group**<br>
Type: string. Required when DeployToSlotFlag = true.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Enter or Select the Azure Resource group that contains the Azure App Service specified above.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SlotName"::: -->
:::moniker range="<=azure-pipelines"

**`SlotName`** - **Slot**<br>
Type: string. Required when DeployToSlotFlag = true.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Enter or Select an existing Slot other than the Production slot.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="VirtualApplication"::: -->
:::moniker range="<=azure-pipelines"

**`VirtualApplication`** - **Virtual Application**<br>
Type: string.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the name of the Virtual Application that has been configured in the Azure portal. The option is not required for deployments to the App Service root.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="Package"::: -->
:::moniker range="<=azure-pipelines"

**`Package`** - **Package or Folder**<br>
Type: string. Required. Default value: '$(System.DefaultWorkingDirectory)/**/*.zip'.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Folder or file path to the App Service package or folder. Variables ( [Build](https://www.visualstudio.com/docs/build/define/variables) | [Release](https://www.visualstudio.com/docs/release/author-release-definition/understanding-tasks#predefvariables)), wild cards are supported. <br/> For example, $(System.DefaultWorkingDirectory)/\*\*/\*.zip.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="WebAppUri"::: -->
:::moniker range="<=azure-pipelines"

**`WebAppUri`** - **App Service URL**<br>
Type: string.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify a name for the output variable that is generated for the URL of the App Service. The variable can be consumed in subsequent tasks.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="UseWebDeploy"::: -->
:::moniker range="<=azure-pipelines"

**`UseWebDeploy`** - **Publish using Web Deploy**<br>
Type: boolean. Default value: true.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Publish using web deploy options are supported only when using Windows agent. On other platforms, the task relies on [Kudu REST APIs](https://github.com/projectkudu/kudu/wiki/REST-API) to deploy the App Service, and following options are not supported.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="SetParametersFile"::: -->
:::moniker range="<=azure-pipelines"

**`SetParametersFile`** - **SetParameters File**<br>
Type: string. Optional. Use when UseWebDeploy == true.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Optional: location of the SetParameters.xml file to use.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="RemoveAdditionalFilesFlag"::: -->
:::moniker range="<=azure-pipelines"

**`RemoveAdditionalFilesFlag`** - **Remove Additional Files at Destination**<br>
Type: boolean. Optional. Use when UseWebDeploy == true. Default value: false.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the option to delete files on the Azure App Service that have no matching files in the App Service package or folder.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="ExcludeFilesFromAppDataFlag"::: -->
:::moniker range="<=azure-pipelines"

**`ExcludeFilesFromAppDataFlag`** - **Exclude Files from the App_Data Folder**<br>
Type: boolean. Optional. Use when UseWebDeploy == true. Default value: false.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the option to prevent files in the App_Data folder from being deployed to the Azure App Service.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="AdditionalArguments"::: -->
:::moniker range="<=azure-pipelines"

**`AdditionalArguments`** - **Additional Arguments**<br>
Type: string. Optional. Use when UseWebDeploy == true.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Additional Web Deploy arguments following the syntax -key:value.<br />These will be applied when deploying the Azure App Service. Example: -disableLink:AppPoolExtension -disableLink:ContentExtension.<br />For more examples of Web Deploy operation settings, refer to  [this](https://go.microsoft.com/fwlink/?linkid=838471).
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="TakeAppOfflineFlag"::: -->
:::moniker range="<=azure-pipelines"

**`TakeAppOfflineFlag`** - **Take App Offline**<br>
Type: boolean. Default value: false.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the option to take the Azure App Service offline by placing an app_offline.htm file in the root directory of the App Service before the sync operation begins. The file will be removed after the sync operation completes successfully.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->

### Task control options

All tasks have control options in addition to their task inputs. For more information, see [Control options and common task properties](/azure/devops/pipelines/yaml-schema/steps-task#common-task-properties).
<!-- :::inputs-end::: -->

<!-- :::outputVariables::: -->
## Output variables

:::moniker range="<=azure-pipelines"

None.

:::moniker-end
<!-- :::outputVariables-end::: -->

<!-- :::remarks::: -->
<!-- :::editable-content name="remarks"::: -->
<!-- :::editable-content-end::: -->
<!-- :::remarks-end::: -->

<!-- :::examples::: -->
<!-- :::editable-content name="examples"::: -->
<!-- :::editable-content-end::: -->
<!-- :::examples-end::: -->

<!-- :::properties::: -->
## Requirements

:::moniker range="<=azure-pipelines"

| Requirement | Description |
|-------------|-------------|
| Pipeline types | YAML, Classic build, Classic release |
| Runs on | Agent |
| [Demands](/azure/devops/pipelines/process/demands) | None |
| [Capabilities](/azure/devops/pipelines/agents/agents#capabilities) | This task does not satisfy any demands for subsequent tasks in the job. |
| [Command restrictions](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| [Settable variables](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| Agent version |  1.102.0 or greater |
| Task category | Deploy |

:::moniker-end
<!-- :::properties-end::: -->

<!-- :::see-also::: -->
<!-- :::editable-content name="seeAlso"::: -->
<!-- :::editable-content-end::: -->
<!-- :::see-also-end::: -->