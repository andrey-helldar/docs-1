---
editable: false
sourcePath: en/_api-ref-grpc/mdb/mongodb/v1/api-ref/grpc/User/list.md
---

# Managed Service for MongoDB API, gRPC: UserService.List {#List}

Retrieves the list of MongoDB User resources in the specified cluster.

## gRPC request

**rpc List ([ListUsersRequest](#yandex.cloud.mdb.mongodb.v1.ListUsersRequest)) returns ([ListUsersResponse](#yandex.cloud.mdb.mongodb.v1.ListUsersResponse))**

## ListUsersRequest {#yandex.cloud.mdb.mongodb.v1.ListUsersRequest}

```json
{
  "clusterId": "string",
  "pageSize": "int64",
  "pageToken": "string"
}
```

#|
||Field | Description ||
|| clusterId | **string**

Required field. ID of the cluster to list MongoDB users in.
To get the cluster ID, use a [ClusterService.List](/docs/managed-mongodb/api-ref/grpc/Cluster/list#List) request. ||
|| pageSize | **int64**

The maximum number of results per page to return. If the number of available
results is larger than `pageSize`, the service returns a [ListUsersResponse.nextPageToken](#yandex.cloud.mdb.mongodb.v1.ListUsersResponse)
that can be used to get the next page of results in subsequent list requests. ||
|| pageToken | **string**

Page token. To get the next page of results, set `pageToken` to the
[ListUsersResponse.nextPageToken](#yandex.cloud.mdb.mongodb.v1.ListUsersResponse) returned by the previous list request. ||
|#

## ListUsersResponse {#yandex.cloud.mdb.mongodb.v1.ListUsersResponse}

```json
{
  "users": [
    {
      "name": "string",
      "clusterId": "string",
      "permissions": [
        {
          "databaseName": "string",
          "roles": [
            "string"
          ]
        }
      ]
    }
  ],
  "nextPageToken": "string"
}
```

#|
||Field | Description ||
|| users[] | **[User](#yandex.cloud.mdb.mongodb.v1.User)**

List of MongoDB User resources. ||
|| nextPageToken | **string**

This token allows you to get the next page of results for list requests. If the number of results
is larger than [ListUsersRequest.pageSize](#yandex.cloud.mdb.mongodb.v1.ListUsersRequest), use the `nextPageToken` as the value
for the [ListUsersRequest.pageToken](#yandex.cloud.mdb.mongodb.v1.ListUsersRequest) parameter in the next list request. Each subsequent
list request will have its own `nextPageToken` to continue paging through the results. ||
|#

## User {#yandex.cloud.mdb.mongodb.v1.User}

A MongoDB User resource. For more information, see the
[Developer's Guide](/docs/managed-mongodb/concepts).

#|
||Field | Description ||
|| name | **string**

Name of the MongoDB user. ||
|| clusterId | **string**

ID of the MongoDB cluster the user belongs to. ||
|| permissions[] | **[Permission](#yandex.cloud.mdb.mongodb.v1.Permission)**

Set of permissions granted to the user. ||
|#

## Permission {#yandex.cloud.mdb.mongodb.v1.Permission}

#|
||Field | Description ||
|| databaseName | **string**

Name of the database that the permission grants access to. ||
|| roles[] | **string**

MongoDB roles for the `databaseName` database that the permission grants. ||
|#