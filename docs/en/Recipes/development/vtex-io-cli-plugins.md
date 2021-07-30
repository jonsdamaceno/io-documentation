---
title: VTEX IO CLI Plugins
description: "Any development in VTEX IO begins and ends with the Toolbelt, our CLI (Command Line Interface). Learn all the necessary plugins to develop in the platform."
date: "2020-07-28"
tags: ["toolbelt", "cli", "command-line-interface", "plugins", "reference"]
version: "3.x"
git: " "
---


# VTEX IO's CLI Plugins

D️ifferent from the previous version, VTEX IO's CLI 3.x has a plugin-based architecture. With this improvement, the commands are detached from the CLI code, 
each command will have his own repository in the format `cli-plugin-comand_name` and will be hosted by [Github](https://github.com/) on VTEX org.

See the [CLI plugin template documentation](https://github.com/vtex/cli-plugin-template) and check how to create and mantain a plugin.

## VTEX plugins settings

<details>
  <summary><span class="fa fa-lplugins">&nbsp;</span>Listing all VTEX plugins</summary>
  <br>

  To list all VTEX supported plugins, run the following command in your command line:

  ```sh
  vtex plugins source
  ```
  ![cli plugins](https://user-images.githubusercontent.com/67270558/127198123-7c5777f3-0ab2-4c2e-b5a5-188665951646.png)

  > ℹ️ If you already have downloaded a plugin, it will be highlighted in green.

  <br>
</details>

<details>
  <summary><span class="fa fa-lplugins">&nbsp;</span>Listing all downloaded plugins</summary>
  <br>

  To list all downloaded plugins, run the following command in your command line:

  ```sh
  vtex plugins list
  ```

  <br>
</details>

<details>
  <summary><span class="fa fa-iplugin">&nbsp;</span>Installing a plugin</summary>
  <br>

  To install a new plugin, run the following command in your command line:
  ```sh
  vtex plugins install plugin_name
  ```

  > in `plugin_name` insert, the name of the plugin you want to install, which has two types of format: **VTEX** and **third parties** plugins. For VTEX commands, only use the command name from `plugins source`, i.e., `vtex plugins install infra`. 
  That way, the CLI will look for `@vtex/cli-plugin-infra` in `NPM` registry. For third parties plugins, you type `@org/plugin_name`.


  ![install-plugin](https://user-images.githubusercontent.com/67270558/127199329-914dcea3-4068-4e4f-ba89-7a2f1d43b2ad.png)

  <br>
</details>

<details>
  <summary><span class="fa fa-uplugin">&nbsp;</span>Updating all plugins</summary>
  <br>

  To update all plugins, run the following command in your command line:
  ```sh
  vtex plugins update
  ```

  ![update-plugins](https://user-images.githubusercontent.com/67270558/127201651-d44f6cb3-421f-466f-a09d-649cd1ab74b7.png)
  <br>
</details>

<details>
  <summary><span class="fa fa-dplugin">&nbsp;</span>Deleting a plugin</summary>
  <br>

  To delete a plugin, run the following command in your command line:
  ```sh
  vtex plugins delete plugin_name
  ```
  > in `plugin_name` insert, the name of the plugin you want to install, which has two types of format: **VTEX** and **third parties** plugins. For VTEX commands, only use the command name from `plugins source`, i.e., `vtex plugins install infra`. 
  That way, the CLI will look for `@vtex/cli-plugin-infra` in `NPM` registry. For third parties plugins, you type `@org/plugin_name`.
  <br>
</details>


## Overview

Check in the following a brief description of the main plugins of VTEX IO's CLI.

|Plugin Name|Functionality|
|------------|-------------|
| [`vtex add`](#add) |Add app(s) to the manifest dependencies.|
| [`vtex autoupdate`](#autoupdate) | Update the VTEX IO'S CLI.|
| [`vtex congif get`](#config-get) |Gets the current value for the requested configuration.|
| [`vtex congif reset`](#config-reset) |Reset the requested configuration to the default value.|
| [`vtex congif set`](#config-set) |Sets the current value for the given configuration.|
| [`vtex debug dotnet`](#debug-donet) | Debug .NET applications (IDEs only).| 
| [`vtex infra install`](#infra-install) |Installs an infra service.|
| [`vtex infra list`](#infra-list) |Lists installed infra services.|
| [`vtex infra update`](#infra-update) |Updates all installed infra services.|
| [`vtex lighthouse audit`](#lighthouse-audit) |Runs a Lighthouse audit over the specified URL.|
| [`vtex lighthouse show`](#lighthouse-show) |Shows a previous audit report, filtering by app and/or URL.|
| [`vtex logs`](#logs) |Shows logs of an app (only apps in production).|
| [`vtex plugins install`](#plugins-install) |Installs a plugin into the CLI.|
| [`vtex plugins link`](#plugins-link) |Links a plugin into the CLI for development.|
| [`vtex plugins:list`](#plugins-list) |Lists all plugins installed on your machine.|
| [`vtex plugins source`](#plugins-source) |Lists all plugins supported by VTEX.|
| [`vtex plugins uninstall`](#plugins-uninstall) |Removes a plugin from the CLI.|
| [`vtex plugins:update`](#plugins-update) |Updates all plugins installed on your machine.|
| [`vtex redirects delete`](#redirects-delete) |Deletes redirects from the current account and workspace.|
| [`vtex redirects export`](#redirects-export) |Exports all redirects defined in the current account and workspace to a CSV file.|
| [`vtex redirects import`](#redirects-import) |Imports redirects from a CSV file to the current account and workspace.|
| [`vtex settings get`](#settings-get) |Prints the settings of the specified app.|
| [`vtex settings set`](#settings-set) |Sets value to the specified setting of an app.|
| [`vtex settings unset`](#settings-unset) |Disables the specified setting of an app.|
| [`vtex submit`](#submit) |Submits the current app, or an specified one, to validation from VTEX App Store team.|
| [`vtex support`](#support) |Logs in as support to another VTEX account.|
| [`vtex test e2e`](#test-e2e) |Runs E2E integration tests for the app in the current directory.|
| [`vtex test unit`](#test-unit) |Runs unit tests for the app in the current directory.|
| [`vtex url`](#url) |Prints base URL for the current account and workspace.|
| [`vtex workspace abtest finish`](#workspace-abtest-finish) |Stops all A/B tests from running on the current account.|
| [`vtex workspace abtest start`](#workspace-abtest-start) |Starts a new A/B test on the current workspace.|
| [`vtex workspace abtest status`](#workspace-abtest-status) |Displays the results of the active A/B tests.|

> The following plugins are native to the VTEX IO'S CLI. Thus you do not need to install them:  `vtex autoupdate`, `vtex deploy`, `vtex workspace abtest finish`, `vtex workspace abtest start`, `vtex workspace abtest status`, `vtex deps diff`, `vtex deps list`, `vtex deps update`, `edition get`, `edition set`, `vtex plugins install`, `vtex plugins link`, `vtex plugins:list`, `vtex plugins source`, `vtex plugins unistall`, `vtex plugins:update`, `vtex whoami`, `vtex workspace delete`, `vtex workspace list`, `vtex workspace promote`, `vtex workspace reset`, `vtex workspace status`, `vtex workspace use`.

## Detailed reference

Check in the following the help texts for each plugin of VTEX IO's CLI. 

### Add
Add app(s) to the manifest dependencies.

#### Usage
  
```shell
$ vtex add APPID [ITHAPPID]
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**APPID**|Name and version (`{vendor}.{appname}@{x.x.x}`) of the dependency to include in the manifest.json file.|
|**ITHAPPID** (optional)|Names and versions (`{vendor}.{appname}@{x.x.x}`) of the multiple dependencies to include in the manifest.json file.|

#### Example

```shell
vtex add vtex.service-example@0.x
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Autoupdate

Update the VTEX IO'S CLI.

#### Usage

```shell
  $ vtex autoupdate [CHANNEL]
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**CHANNEL** (optional)|.|

<div align="right"> 🔼 <a href="#overview">Back</a></div>


### Config get
Gets the current value for the requested configuration.

#### Usage
  
```shell
$ vtex config get CONFIGNAME
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**CONFIGNAME**|Configuration to retrieve the value from.|


#### Example

```shell
 vtex config get env
 vtex config get cluster
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Config reset
Reset the requested configuration to the default value.

#### Usage
  
```shell
$ vtex config reset CONFIGNAME
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**CONFIGNAME**|Name of the configuration to reset.|


#### Example

```shell
 vtex config reset env
 vtex config reset cluster
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Config set
Sets the current value for the given configuration.

#### Usage
  
```shell
$ vtex config set CONFIGNAME VALUE
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**CONFIGNAME**|Name of the configuration.|
|**VALUE**|New value of the specified configuration.|


#### Example

```shell
  vtex config set env envValue
  vtex config set cluster clusterValue
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Debug donet

#### Usage

```shell
  $ vtex debug dotnet DEBUGINST
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**DEBUGINST**|Name of the .NET application to debug.|

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Infra install
Install an infra service.

#### Usage

```shell
  $ vtex infra install SERVICEID
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**SERVICEID**|Name and version of the service (`{vendor}.{servicename}@{x.x.x}`) to install.|

#### Examples

```shell
  vtex infra install infra-service
  vtex infra install infra-service@0.0.1
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Infra list
List installed infra services.

#### Usage

```shell
  $ vtex infra list [NAME]
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**NAME** (optional)|Service name.|

#### Options

|Option|Alias|Description|
|-------|-----|-----------|
|**--available**|-a|Lists services that are available to install.|
|**--filter=filter**|-f|Lists services that contain the specified word.|
  
#### Aliases

```shell
  $ vtex infra ls
```

#### Examples

```shell
  vtex infra list
  vtex infra ls
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Infra update
Update all installed infra services.

#### Usage

```shell
  $ vtex infra update
```

#### Example

```shell
  vtex infra update
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Lighthouse audit
Run lighthouse audit over a specific URL.

#### Usage

```shell
  $ vtex lighthouse audit URL
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**URL**|URL to audit.|

#### Options

|Option|Alias|Description|
|------|-----|-----------|
|**--json**|-j|Returns the report as a json on stdout.|

#### Aliases

```shell
  $ vtex lh audit
```

#### Examples

```shell
  vtex lighthouse audit my.url.com
  vtex lh audit my.url.com
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Lighthouse show
Show previous saved audit reports, filtering by app and/or URL.

#### Usage

```shell
  $ vtex lighthouse show
```

#### Options

|Option|Alias|Description|
|-------|-----|-----------|
|**--app=app**|-a|Filters by app name.|
|**--url=url**|-u|Filters by URL.|
  
#### Aliases

```shell
  $ vtex lh show
```

#### Examples

```shell
  vtex lighthouse show --app=vtex.awesome-app
  vtex lighthouse show -u https://awesome.store.com
  vtex lighthouse show -a vtex.awesome-app --url=https://awesome.store.com
  vtex lh show --app=vtex.awesome-app
  vtex lh show -u https://awesome.store.com
  vtex lh show -a vtex.awesome-app --url=https://awesome.store.com
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Logs
Show apps production logs.

#### Usage

```shell
  $ vtex logs [APP]
```
#### Arguments

|Argument|Description|
|--------|-----------|
|**APP** (optional)|Name of the app to show logs.|

#### Options

|Option|Alias|Description|
|-------|-----|-----------|
|**--all**|-a|Shows logs of every app installed on the current account.|
|**--past**|-p|Shows previous logs of the specified app.|
  
#### Examples

```shell
  vtex logs
  vtex logs appName
  vtex logs --all
  vtex logs appName --past
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Plugins install
Installs a plugin into the CLI.

#### Usage

```shell
  $ vtex plugins install PLUGIN
```
#### Arguments

|Argument|Description|
|--------|-----------|
| **PLUGIN** | Plugin to install.|

#### Options

|Option|Alias|Description|
|-------|-----|-----------|
|**--force**| -f| Refetches all packages, even the ones that were previously installed.|
  
#### Aliases

```shell
  $ vtex plugins:add
```

#### Examples

```shell
  vtex plugins install lighthouse
  vtex plugins install https://github.com/vtex/cli-plugin-someplugin
  vtex plugins install @vtex/cli-plugin-someplugin
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Plugins link
Links a plugin into the CLI for development.

#### Usage

```shell
  $ vtex plugins link PLUGIN
```

#### Arguments

|Argument|Description|
|--------|-----------|
| **PLUGIN** | Plugin to link.|
|**PATH [default: .]** |Plugin path.|

#### Examples

```shell
   vtex plugins link myplugin
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Plugins list
Lists all plugins installed on your machine.

#### Usage

```shell
  $ vtex plugins:list
```

#### Options

|Option|Description|
|-------|-----------|
|**--core**| Shows core plugins.|

#### Examples

```shell
  vtex plugins list
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Plugins source
Lists all plugins supported by VTEX.
#### Usage

```shell
  $ vtex plugins source PLUGIN
```

#### Arguments

|Argument|Description|
|--------|-----------|
| **PLUGIN** | Plugin name.|
|**PATH [default: .]** |Plugin path.|

#### Examples

```shell
  vtex plugins source myplugin
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Plugins uninstall
Removes a plugin from the CLI.

#### Usage

```shell
  $ vtex plugins uninstall PLUGIN
```

#### Arguments

|Argument|Description|
|--------|-----------|
| **PLUGIN** | Plugin to uninstall.|

#### Aliases

```shell
  $ vtex plugins:unlink
  $ vtex plugins:remove
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Plugins update

Updates all plugins installed on your machine.

#### Usage

```shell
  $ vtex plugins:update
```

### Redirects delete
Delete redirects in the current account and workspace.

#### Usage

```shell
  $ vtex redirects delete CSVPATH
```
#### Arguments

|Argument|Description|
|--------|-----------|
|**CSVPATH**|CSV file containing the URL paths to be deleted.|

#### Example

```shell
  vtex redirects delete csvPath
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Redirects export
Export all redirects in the current account and workspace

#### Usage

```shell
  $ vtex redirects export CSVPATH
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**CSVPATH**|Name of the CSV file.|

#### Example

```shell
  vtex redirects export csvPath
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Redirects import
Import redirects for the current account and workspace.

#### Usage

```shell
  $ vtex redirects import CSVPATH
```

#### Options

|Option|Alias|Description|
|-------|-----|-----------|
|**--reset**|-r|Removes all redirects previously defined.|
  
#### Example

```shell
  vtex redirects import csvPath
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Settings get
Get app settings.

#### Usage

```shell
  $ vtex settings get APPNAME [FIELD]
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**APNAME**| Name of the app to check the available settings.|
|**FIELD** (optional)|Name of the setting.|

#### Aliases

```shell
  $ vtex settings
```

#### Example

```shell
  vtex settings get vtex.service-example
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Settings set
Set app settings.

#### Usage

```shell
  $ vtex settings set APPNAME FIELD VALUE 
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**APPNAME** |Name of the app.|
|**FIELD**|Name of the setting.|
|**VALUE**|Value of the setting.|

#### Example

```shell
  vtex settings set vtex.store enableCriticalCSS true
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>


### Settings unset
Unset app settings.

#### Usage

```shell
  $ vtex settings unset APPNAME FIELD
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**APPNAME**|Name of the app.|
|**FIELD**|Name of the setting.|

#### Example

```shell
  vtex settings unset vtex.service-example fieldName
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Submit
Submits the current app, or an specified one, to validation from VTEX App Store team.

#### Usage

```shell
  $ vtex submit [APPID]
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**APPID** (optional)|Name of the app to be validated.|

#### Examples

```shell
  vtex submit
  vtex submit myvendor.myapp@1.2.3
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Support
Login as support into another VTEX account.

#### Usage

```shell
  $ vtex support ACCOUNT
```

#### Arguments

|Argument|Description|
|--------|-----------|
|**ACCOUNT**|Name of the account to give support.|

#### Example

```shell
  vtex support storecomponents
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Test e2e
Run your VTEX app's integration tests.

#### Usage

```shell
  $ vtex test e2e
```

#### Options

|Option|Alias|Description|
|-------|-----|-----------|
|**--report=report**|-r|Displays the results and state of the specified test ID.|
|**--token**|-t|(Not recommended.) Sends your personal authorization token to your testing session, making it available during the tests. It can be dangerous since it exposes your token via the 'authToken' environment variable.|
|**--workspace**|-w|Runs tests for the apps installed on the specified workspace.|

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Test unit
Run your VTEX app unit tests.

#### Usage

```shell
  $ vtex test unit
```

#### Options

|Option|Alias|Description|
|-------|-----|-----------|
|**--unsafe**|-u|Ignores Typescript errors|

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### URL
Prints base URL for current account, workspace and environment.

#### Usage

```shell
  $ vtex url
```

#### Example

```shell
  vtex url
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Workspace abtest finish
Stop all AB testing in current account.

#### Usage

```shell
  $ vtex workspace abtest finish
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Workspace abtest start
Start AB testing with current workspace.

#### Usage

```shell
  $ vtex workspace abtest start
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>

### Workspace abtest status
Display currently running AB tests results.

#### Usage

```shell
  $ vtex workspace abtest status
```

<div align="right"> 🔼 <a href="#overview">Back</a></div>