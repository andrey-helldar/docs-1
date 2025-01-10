---
editable: false
sourcePath: en/_cli-ref/cli-ref/managed-kubernetes/cli-ref/marketplace/helm-release/update.md
---

# yc managed-kubernetes marketplace helm-release update

Update a Helm Release from marketplace on the cluster.

#### Command Usage

Syntax: 

`yc managed-kubernetes marketplace helm-release update <HELM_RELEASE-ID> --product-version-id <PRODUCT-VERSION-ID> --values <KEY>=<VALUE>[,<KEY>=<VALUE>...] [Global Flags...]`

#### Flags

| Flag | Description |
|----|----|
|`--id`|<b>`string`</b><br/>ID of the Helm Release.|
|`--name`|<b>`string`</b><br/>|
|`--product-version-id`|<b>`string`</b><br/>ID of the Marketplace Product Version.|
|`--values`|<b>`key=value[,key=value...]`</b><br/>Values to pass to the Helm Release.|
|`--async`|Display information about the operation in progress, without waiting for the operation to complete.|

#### Global Flags

| Flag | Description |
|----|----|
|`--profile`|<b>`string`</b><br/>Set the custom configuration file.|
|`--debug`|Debug logging.|
|`--debug-grpc`|Debug gRPC logging. Very verbose, used for debugging connection problems.|
|`--no-user-output`|Disable printing user intended output to stderr.|
|`--retry`|<b>`int`</b><br/>Enable gRPC retries. By default, retries are enabled with maximum 5 attempts.<br/>Pass 0 to disable retries. Pass any negative value for infinite retries.<br/>Even infinite retries are capped with 2 minutes timeout.|
|`--cloud-id`|<b>`string`</b><br/>Set the ID of the cloud to use.|
|`--folder-id`|<b>`string`</b><br/>Set the ID of the folder to use.|
|`--folder-name`|<b>`string`</b><br/>Set the name of the folder to use (will be resolved to id).|
|`--endpoint`|<b>`string`</b><br/>Set the Cloud API endpoint (host:port).|
|`--token`|<b>`string`</b><br/>Set the OAuth token to use.|
|`--impersonate-service-account-id`|<b>`string`</b><br/>Set the ID of the service account to impersonate.|
|`--no-browser`|Disable opening browser for authentication.|
|`--format`|<b>`string`</b><br/>Set the output format: text (default), yaml, json, json-rest.|
|`--jq`|<b>`string`</b><br/>Query to select values from the response using jq syntax|
|`-h`,`--help`|Display help for the command.|