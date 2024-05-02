# Commands for creating an Unlocked Package
## Authorize DevHub
sfdx force:auth:web:login -d -a DevHub <br/>
here **DevHub** is an alias of Salesforce instance where we enable "DevHub and Unlocked Packages and Second-Generation Managed Packages"
## Check sfdx-project.json
{
   "packageDirectories": [
      {
         "path": "force-app",
         "default": true
      }
   ], 
   "namespace": "", 
   "sfdcLoginUrl": "https://login.salesforce.com", 
   "sourceApiVersion": "50.0" 
} 
## Create the Package
sfdx force:<zero-width space>package:create --name testunlocked  --description "testunlocked package" --packagetype Unlocked --path force-app --nonamespace --targetdevhubusername DevHub <br/>
## Create the Package Version
sfdx force:<zero-width space>package:version:create -p testunlocked -d force-app -k test1234 --wait 10 -v DevHub --codecoverage
--codecoverage
Calculate and store the code coverage percentage by running the Apex tests included in this package version.
Before you can promote and release a managed or unlocked package version, the Apex code must meet a minimum 75% code coverage requirement.
Without this it is not possible to promote.
## Promote 
sfdx force:<zero-width space>package:version:promote -p testunlocked@0.1.0-1 -v DevHub
## Intall the package
sfdx force:<zero-width space>package:install --wait 10 --publishwait 10 --package testunlocked@0.1.0-1 -k test1234 -r -u PackageDemoOrg

here **PackageDemoOrg** is alias of Salesforce instace where we want to install our package
# Salesforce DX Project: Next Steps

Now that you’ve created a Salesforce DX project, what’s next? Here are some documentation resources to get you started.

## How Do You Plan to Deploy Your Changes?

Do you want to deploy a set of changes, or create a self-contained application? Choose a [development model](https://developer.salesforce.com/tools/vscode/en/user-guide/development-models).

## Configure Your Salesforce DX Project

The `sfdx-project.json` file contains useful configuration information for your project. See [Salesforce DX Project Configuration](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_ws_config.htm) in the _Salesforce DX Developer Guide_ for details about this file.

## Read All About It

- [Salesforce Extensions Documentation](https://developer.salesforce.com/tools/vscode/)
- [Salesforce CLI Setup Guide](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_intro.htm)
- [Salesforce DX Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_intro.htm)
- [Salesforce CLI Command Reference](https://developer.salesforce.com/docs/atlas.en-us.sfdx_cli_reference.meta/sfdx_cli_reference/cli_reference.htm)
