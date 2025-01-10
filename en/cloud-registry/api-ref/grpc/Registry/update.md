---
editable: false
sourcePath: en/_api-ref-grpc/cloudregistry/v1/api-ref/grpc/Registry/update.md
---

# Yandex Cloud Registry API, gRPC: RegistryService.Update

Updates the specified registry.

## gRPC request

**rpc Update ([UpdateRegistryRequest](#yandex.cloud.cloudregistry.v1.UpdateRegistryRequest)) returns ([operation.Operation](#yandex.cloud.operation.Operation))**

## UpdateRegistryRequest {#yandex.cloud.cloudregistry.v1.UpdateRegistryRequest}

```json
{
  "registry_id": "string",
  "update_mask": "google.protobuf.FieldMask",
  "name": "string",
  "labels": "map<string, string>",
  "description": "string",
  "properties": "map<string, string>"
}
```

#|
||Field | Description ||
|| registry_id | **string**

Required field. ID of the Registry resource to update.

To get the registry ID use a [RegistryService.List](/docs/cloud-registry/api-ref/grpc/Registry/list#List) request. ||
|| update_mask | **[google.protobuf.FieldMask](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/field-mask)**

Field mask that specifies which fields of the Registry resource are going to be updated. ||
|| name | **string**

Name of the registry.

There may be only one registry per folder. ||
|| labels | **object** (map<**string**, **string**>)

Resource labels as `key:value` pairs.

Existing set of `labels` is completely replaced by the provided set. ||
|| description | **string**

Description of the registry. 0-1024 characters long. ||
|| properties | **object** (map<**string**, **string**>)

Property names and values. ||
|#

## operation.Operation {#yandex.cloud.operation.Operation}

```json
{
  "id": "string",
  "description": "string",
  "created_at": "google.protobuf.Timestamp",
  "created_by": "string",
  "modified_at": "google.protobuf.Timestamp",
  "done": "bool",
  "metadata": {
    "registry_id": "string"
  },
  // Includes only one of the fields `error`, `response`
  "error": "google.rpc.Status",
  "response": {
    "id": "string",
    "folder_id": "string",
    "name": "string",
    "kind": "Kind",
    "type": "Type",
    "status": "Status",
    "description": "string",
    "labels": "map<string, string>",
    "properties": "map<string, string>",
    "created_at": "google.protobuf.Timestamp",
    "modified_at": "google.protobuf.Timestamp"
  }
  // end of the list of possible fields
}
```

An Operation resource. For more information, see [Operation](/docs/api-design-guide/concepts/operation).

#|
||Field | Description ||
|| id | **string**

ID of the operation. ||
|| description | **string**

Description of the operation. 0-256 characters long. ||
|| created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Creation timestamp. ||
|| created_by | **string**

ID of the user or service account who initiated the operation. ||
|| modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

The time when the Operation resource was last modified. ||
|| done | **bool**

If the value is `false`, it means the operation is still in progress.
If `true`, the operation is completed, and either `error` or `response` is available. ||
|| metadata | **[UpdateRegistryMetadata](#yandex.cloud.cloudregistry.v1.UpdateRegistryMetadata)**

Service-specific metadata associated with the operation.
It typically contains the ID of the target resource that the operation is performed on.
Any method that returns a long-running operation should document the metadata type, if any. ||
|| error | **[google.rpc.Status](https://cloud.google.com/tasks/docs/reference/rpc/google.rpc#status)**

The error result of the operation in case of failure or cancellation.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|| response | **[Registry](#yandex.cloud.cloudregistry.v1.Registry)**

The normal response of the operation in case of success.
If the original method returns no data on success, such as Delete,
the response is [google.protobuf.Empty](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#google.protobuf.Empty).
If the original method is the standard Create/Update,
the response should be the target resource of the operation.
Any method that returns a long-running operation should document the response type, if any.

Includes only one of the fields `error`, `response`.

The operation result.
If `done == false` and there was no failure detected, neither `error` nor `response` is set.
If `done == false` and there was a failure detected, `error` is set.
If `done == true`, exactly one of `error` or `response` is set. ||
|#

## UpdateRegistryMetadata {#yandex.cloud.cloudregistry.v1.UpdateRegistryMetadata}

#|
||Field | Description ||
|| registry_id | **string**

ID of the Registry resource that is being updated. ||
|#

## Registry {#yandex.cloud.cloudregistry.v1.Registry}

A Registry resource.

#|
||Field | Description ||
|| id | **string**

Output only. ID of the registry. ||
|| folder_id | **string**

ID of the folder that the registry belongs to. ||
|| name | **string**

Name of the registry. ||
|| kind | enum **Kind**

Kind of the registry.

- `KIND_UNSPECIFIED`
- `MAVEN`: Registry kind is maven.
- `NPM`: Registry kind is npm.
- `DOCKER`: Registry kind is docker. ||
|| type | enum **Type**

Type of the registry.

- `TYPE_UNSPECIFIED`
- `LOCAL`: Registry type is local. ||
|| status | enum **Status**

Output only. Status of the registry.

- `STATUS_UNSPECIFIED`
- `CREATING`: Registry is being created.
- `ACTIVE`: Registry is ready to use.
- `DELETING`: Registry is being deleted. ||
|| description | **string**

Description of the registry. ||
|| labels | **object** (map<**string**, **string**>)

Resource labels as `key:value` pairs. Maximum of 64 per resource. ||
|| properties | **object** (map<**string**, **string**>)

Resource properties as `key:value` pairs. Maximum of 64 per resource. ||
|| created_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Output only. Creation timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. ||
|| modified_at | **[google.protobuf.Timestamp](https://developers.google.com/protocol-buffers/docs/reference/google.protobuf#timestamp)**

Output only. Modification timestamp in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. ||
|#