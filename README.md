# Prepare for deploying ESLZ
## 1. Set up workstation

1.1 Install PowerShell 7.1.x

https://github.com/PowerShell/PowerShell/releases/tag/v7.1.3

1.2 Update the Execution Policy.

````powershell
# Get the Execution Policy on the system, and make note of it before making changes
Get-ExecutionPolicy
# Set the Execution Policy for this process only
if ((Get-ExecutionPolicy) -ne "RemoteSigned") { Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process -Force }
````

1.3 Update the Execution Policy.

````powershell
# Install latest NuGet provider
Install-PackageProvider -Name NuGet -Force
# Check if the AzureRM PowerShell modules are installed - if so, present a warning
if ($PSVersionTable.PSEdition -eq 'Desktop' -and (Get-Module -Name AzureRM -ListAvailable)) {
    Write-Warning -Message ('Az module not installed. Having both the AzureRM and ' +
        'Az modules installed at the same time is not supported.')
} else {
    # If no AzureRM PowerShell modules are detected, install the Azure PowerShell modules
    Install-Module -Name Az -AllowClobber -Scope CurrentUser
}
````

## Optional

1. Install Visual Studio Code

https://code.visualstudio.com/

2. Install GitHub Desktop

https://desktop.github.com/

## 2. Set up GitHub account