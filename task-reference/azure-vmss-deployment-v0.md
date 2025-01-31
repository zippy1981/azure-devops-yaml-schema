---
title: AzureVmssDeployment@0 - Azure VM scale set deployment v0 task
description: Deploy a virtual machine scale set image.
ms.date: 09/01/2022
monikerRange: "<=azure-pipelines"
---

# AzureVmssDeployment@0 - Azure VM scale set deployment v0 task

<!-- :::description::: -->
:::moniker range=">=azure-pipelines-2019.1"

<!-- :::editable-content name="description"::: -->
Deploy a virtual machine scale set image.
<!-- :::editable-content-end::: -->

:::moniker-end

:::moniker range="<=azure-pipelines-2019"

<!-- :::editable-content name="description"::: -->
Deploy Virtual Machine scale set image.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::description-end::: -->

<!-- :::syntax::: -->
## Syntax

:::moniker range=">=azure-pipelines-2019.1"

```yaml
# Azure VM scale set deployment v0
# Deploy a virtual machine scale set image.
- task: AzureVmssDeployment@0
  inputs:
  # Azure Details
    azureSubscription: # string. Required. Azure subscription. 
    action: 'Update image' # 'Update image' | 'Configure application startup'. Required. Action. Default: 'Update image'.
    vmssName: # string. Required. Virtual Machine scale set name. 
    vmssOsType: # 'Windows' | 'Linux'. Required. OS type. 
  # Image Details
    imageUrl: # string. Required. Image URL. 
  # Configure start-up
    #customScriptsDirectory: # string. Custom script directory. 
    #customScript: # string. Command. 
    #customScriptArguments: # string. Arguments. 
    #customScriptsStorageAccount: # string. Azure storage account where custom scripts will be uploaded. 
  # Advanced
    #skipArchivingCustomScripts: false # boolean. Skip Archiving custom scripts. Default: false.
```

:::moniker-end

:::moniker range="=azure-pipelines-2019"

```yaml
# Azure VM scale set Deployment v0
# Deploy Virtual Machine scale set image.
- task: AzureVmssDeployment@0
  inputs:
  # Azure Details
    azureSubscription: # string. Required. Azure subscription. 
    action: 'Update image' # 'Update image' | 'Configure application startup'. Required. Action. Default: 'Update image'.
    vmssName: # string. Required. Virtual Machine scale set name. 
    vmssOsType: # 'Windows' | 'Linux'. Required. OS type. 
  # Image Details
    imageUrl: # string. Required. Image URL. 
  # Configure start-up
    #customScriptsDirectory: # string. Custom script directory. 
    #customScript: # string. Command. 
    #customScriptArguments: # string. Arguments. 
    #customScriptsStorageAccount: # string. Azure storage account where custom scripts will be uploaded. 
  # Advanced
    #skipArchivingCustomScripts: false # boolean. Skip Archiving custom scripts. Default: false.
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

<!-- :::item name="azureSubscription"::: -->
:::moniker range="<=azure-pipelines"

**`azureSubscription`** - **Azure subscription**<br>
Input alias: `ConnectedServiceName`. Type: string. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the Azure Resource Manager subscription for the scale set.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="action"::: -->
:::moniker range="<=azure-pipelines"

**`action`** - **Action**<br>
Type: string. Required. Allowed values: 'Update image', 'Configure application startup'. Default value: 'Update image'.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Choose between updating a VM scale set by using a VHD image and/or by running deployment/install scripts using Custom Script VM extension.<br/>The VHD image approach is better for scaling quickly and doing rollback. The extension approach is useful for post deployment configuration, software installation, or any other configuration / management task.<br/>You can use a VHD image to update a VM scale set only when it was created by using a custom image, the update will fail if the VM Scale set was created by using a platform/gallery image available in Azure.<br/>The Custom script VM extension approach can be used for VM scale set created by using either custom image or platform/gallery image.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="vmssName"::: -->
:::moniker range="<=azure-pipelines"

**`vmssName`** - **Virtual Machine scale set name**<br>
Type: string. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Name of VM scale set which you want to update by using either a VHD image or by using Custom script VM extension.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="vmssOsType"::: -->
:::moniker range="<=azure-pipelines"

**`vmssOsType`** - **OS type**<br>
Type: string. Required. Allowed values: 'Windows', 'Linux'.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Select the operating system type of VM scale set.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="imageUrl"::: -->
:::moniker range=">=azure-pipelines-2019"

**`imageUrl`** - **Image URL**<br>
Type: string. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the URL of VHD image. If it is an Azure storage blob URL, the storage account location should be same as scale set location.
<!-- :::editable-content-end::: -->

:::moniker-end

:::moniker range="=azure-pipelines-2018"

**`imageUrl`** - **Image url**<br>
Type: string. Required.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Specify the URL of VHD image. If it is an Azure storage blob URL, the storage account location should be same as scale set location.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="customScriptsDirectory"::: -->
:::moniker range="<=azure-pipelines"

**`customScriptsDirectory`** - **Custom script directory**<br>
Type: string.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
Path to directory containing custom script(s) that will be run by using Custom Script VM extension. The extension approach is useful for post deployment configuration, application/software installation, or any other application configuration/management task. For example: the script can set a machine level environment variable which the application uses, like database connection string.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="customScript"::: -->
:::moniker range="<=azure-pipelines"

**`customScript`** - **Command**<br>
Type: string.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The script that will be run by using Custom Script VM extension. This script can invoke other scripts in the directory. The script will be invoked with arguments passed below.<br/>This script in conjugation with such arguments can be used to execute commands. For example:<br/>1. Update-DatabaseConnectionStrings.ps1 -clusterType dev -user $(dbUser) -password $(dbUserPwd) will update connection string in web.config of web application.<br/>2. install-secrets.sh --key-vault-type prod -key serviceprincipalkey will create an encrypted file containing service principal key.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="customScriptArguments"::: -->
:::moniker range="<=azure-pipelines"

**`customScriptArguments`** - **Arguments**<br>
Type: string.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The custom script will be invoked with arguments passed. Build/Release variables can be used which makes it easy to use secrets.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="customScriptsStorageAccount"::: -->
:::moniker range="<=azure-pipelines"

**`customScriptsStorageAccount`** - **Azure storage account where custom scripts will be uploaded**<br>
Type: string.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
The Custom Script Extension downloads and executes scripts provided by you on each virtual machines in the VM scale set. These scripts will be stored in the storage account specified here. Specify a pre-existing ARM storage account.
<!-- :::editable-content-end::: -->

:::moniker-end
<!-- :::item-end::: -->
<!-- :::item name="skipArchivingCustomScripts"::: -->
:::moniker range="<=azure-pipelines"

**`skipArchivingCustomScripts`** - **Skip Archiving custom scripts**<br>
Type: boolean. Default value: false.<br>
<!-- :::editable-content name="helpMarkDown"::: -->
By default, this task creates a compressed archive of directory containing custom scripts. This improves performance and reliability while uploading to azure storage. If not selected, archiving will not be done and all files will be inidividually uploaded.
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
## Remarks

- Updates Azure Virtual Machine scale set with a custom machine image.
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
| Runs on | Agent, DeploymentGroup |
| [Demands](/azure/devops/pipelines/process/demands) | None |
| [Capabilities](/azure/devops/pipelines/agents/agents#capabilities) | This task does not satisfy any demands for subsequent tasks in the job. |
| [Command restrictions](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| [Settable variables](/azure/devops/pipelines/security/templates#agent-logging-command-restrictions) | Any |
| Agent version |  2.0.0 or greater |
| Task category | Deploy |

:::moniker-end
<!-- :::properties-end::: -->

<!-- :::see-also::: -->
<!-- :::editable-content name="seeAlso"::: -->
<!-- :::editable-content-end::: -->
<!-- :::see-also-end::: -->