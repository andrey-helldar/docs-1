---
editable: false
---

# yc compute image create

Create an image

#### Command Usage

Syntax: 

`yc compute image create <IMAGE-NAME> [Flags...] [Global Flags...]`

#### Flags

| Flag | Description |
|----|----|
|`--name`|<b>`string`</b><br/>A name of the image.|
|`--description`|<b>`string`</b><br/>Specifies a textual description of the image.|
|`--labels`|<b>`key=value[,key=value...]`</b><br/>A list of label KEY=VALUE pairs to add. For example, to add two labels named 'foo' and 'bar', both with the value 'baz', use '--labels foo=baz,bar=baz'.|
|`--family`|<b>`string`</b><br/>The family of the image.|
|`--min-disk-size`|<b>`byteSize`</b><br/>Specify minimum size of the disk which will be created from this image.|
|`--product-ids`|<b>`value[,value]`</b><br/>A list of product license IDs. Used for billing purposes.|
|`--pooled`|Create image pool for this image.|
|`--os-type`|<b>`string`</b><br/>OS type (optional). Values: 'linux', 'windows'|
|`--source-image-name`|<b>`string`</b><br/>A source image used to create the image.|
|`--source-image-id`|<b>`string`</b><br/>An ID of the source image used to create the image.|
|`--source-family`|<b>`string`</b><br/>The family of the source image.|
|`--source-snapshot-name`|<b>`string`</b><br/>A source snapshot to create the image from.|
|`--source-snapshot-id`|<b>`string`</b><br/>An ID of the source snapshot to create the image from.|
|`--source-disk-name`|<b>`string`</b><br/>A source disk to create the image from.|
|`--source-disk-id`|<b>`string`</b><br/>An ID of the source disk to create the image from.|
|`--source-uri`|<b>`string`</b><br/>The full Yandex Object Storage URI where the disk image is stored.|
|`--source-image-folder-id`|<b>`string`</b><br/>The folder ID against which all image and image family references will be resolved.|
|`--hardware-generation-id`|<b>`string`</b><br/>Specify an instance hardware generation ID to override the inherited or default one.|
|`--hardware-features`|<b>`key=value[,key=value...]`</b><br/>Specify features of the instance hardware generation to override. Use together with --hardware-generation-id. This is a list of KEY=VALUE pairs, for example '--hardware-features pci_topology=v2,other_feature=some-id'.|
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