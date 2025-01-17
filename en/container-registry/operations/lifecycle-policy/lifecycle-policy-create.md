# Creating a lifecycle policy

You can only set a [lifecycle policy](../../concepts/lifecycle-policy.md) for a [repository](../../concepts/repository.md). To find out the name of a repository, request a [list of repositories in the registry](../repository/repository-list.md#repository-get).

{% list tabs group=instructions %}

- Management console {#console}

  1. In the [management console]({{ link-console-main }}), select the [folder](../../../resource-manager/concepts/resources-hierarchy.md#folder) where the [registry](../../concepts/registry.md) was created.
  1. In the list of services, select **{{ ui-key.yacloud.iam.folder.dashboard.label_container-registry }}**.
  1. Select the registry and click the row with its name.
  1. Select the repository and click the row with its name.
  1. In the left-hand panel, click ![lifecycle](../../../_assets/console-icons/arrows-rotate-right.svg) **{{ ui-key.yacloud.cr.registry.label_lifecycle }}**.
  1. In the top-right corner, click **{{ ui-key.yacloud.common.create }}**.
  1. Set the lifecycle policy parameters:
     * (Optional) **{{ ui-key.yacloud.common.name }}**.
     * (Optional) **{{ ui-key.yacloud.common.description }}**.
     * **{{ ui-key.yacloud.common.label_status }}**: Lifecycle policy status after its creation. We do not recommend creating an `ACTIVE` policy right away.
     * Under **{{ ui-key.yacloud.cr.registry.label_lifecycle-rules }}**, add rules:
       1. Click **{{ ui-key.yacloud.common.add }}**.
       1. Set the rule parameters:

          {% include [lifecycle-rules-console](../../../_includes/container-registry/lifecycle-rules-console.md) %}

          * (Optional) **{{ ui-key.yacloud.common.description }}**.
  1. Click **{{ ui-key.yacloud.common.create }}**.

- CLI {#cli}

  {% include [cli-install](../../../_includes/cli-install.md) %}

  1. Prepare [policy rules](../../concepts/lifecycle-policy.md#lifecycle-rules) and save them to a file named `rules.json`.

     {% include [lifecycle-rules](../../../_includes/container-registry/lifecycle-rules.md) %}

  1. Create a lifecycle policy by running the command:

     ```bash
     yc container repository lifecycle-policy create \
       --repository-name crp3cpm16edq********/ubuntu \
       --name test-policy \
       --description "disabled lifecycle-policy for tests" \
       --rules ./rules.json
     ```

     Where:
     * `--repository-name`: Repository name.
     * `--rules`: Path to the policy description file.
     * `--description` (optional): Lifecycle policy description.
     * `--name` (optional): Policy name. The naming requirements are as follows:

       {% include [name-format](../../../_includes/name-format.md) %}

     {% note info %}

     The default policy is created disabled (`DISABLED` status). We do not recommend creating an active policy (`--active` flag) right away.

     {% endnote %}

     Result:

     ```text
     id: crp6lg1868p3********
     name: test-policy
     repository_id: crp3cpm16edq********
     ...
     - description: delete all untagged Docker images older than 48 hours
       expire_period: 172800s
       untagged: true
     ```

     The `expired_period` parameter value in the response is displayed in seconds. This is a technical constraint, the format will be changed.
  1. Make sure that the policy is created by running the command:

     ```bash
     yc container repository lifecycle-policy list --repository-name crp3cpm16edq********/ubuntu
     ```

     Where `repository-name` is the repository name.

     Result:

     ```text
     +----------------------+-------------+----------------------+----------+---------------------+-------------------------------+
     |          ID          |    NAME     |    REPOSITORY ID     |  STATUS  |       CREATED       |          DESCRIPTION          |
     +----------------------+-------------+----------------------+----------+---------------------+-------------------------------+
     | crp6lg1868p3******** | test-policy | crp3cpm16edq******** | DISABLED | 2020-05-28 15:05:58 | disabled lifecycle-policy for |
     |                      |             |                      |          |                     | tests                         |
     +----------------------+-------------+----------------------+----------+---------------------+-------------------------------+
     ```

- {{ TF }} {#tf}

  {% include [terraform-install](../../../_includes/terraform-install.md) %}

  1. In the configuration file, describe the parameters of the resources you want to create:

     ```hcl
     resource "yandex_container_repository_lifecycle_policy" "my_lifecycle_policy" {
       name          = "<policy_name>"
       status        = "<policy_status>"
       repository_id = "<repository_ID>"

       rule {
         description   = "<rule_description>"
         untagged      = true
         tag_regexp    = ".*"
         retained_top  = 1
         expire_period = "48h"
       }
     }
     ```

     Where:
     * `name`: Policy name.
     * `status`: Policy status. It can either be `true` or `false`.
     * `repository_id`: Repository ID.
     * `rule`: Section with the policy rule. Contains the following parameters:
       * `description`: Rule description.
       * `untagged`: If the parameter is set to `true`, the rule applies to all [Docker images](../../concepts/docker-image.md) that do not have a [tag](../../concepts/docker-image.md#version).
       * `tag_regexp`: Docker image tag for filtering. Java regular expressions are supported. For example, the `test.*` regular expression retrieves all images with tags starting with `test`.
       * `retained_top`: Number of Docker images that will not be deleted even if they match the lifecycle policy rules.
       * `expire_period`: Time after which the lifecycle policy applies to the Docker image. This parameter comes as a number followed by a unit of measurement: `s`, `m`, `h`, or `d` (seconds, minutes, hours, or days). `expire_period` must be a multiple of 24 hours.

     For more information about the `yandex_container_repository_lifecycle_policy` resource parameters in {{ TF }}, see the [relevant provider documentation]({{ tf-provider-resources-link }}/container_repository_lifecycle_policy).
  1. Create resources:

     {% include [terraform-validate-plan-apply](../../../_tutorials/_tutorials_includes/terraform-validate-plan-apply.md) %}

  This will create a lifecycle policy in the specified repository. You can check the new policy and its settings using the [management console]({{ link-console-main }}) or this [CLI](../../../cli/) command:

  ```bash
   yc container repository lifecycle-policy list --registry-id <registry_ID>
  ```

- API {#api}

  To create a lifecycle policy, use the [Create](../../api-ref/grpc/LifecyclePolicy/create.md) method for the [LifecyclePolicyService](../../api-ref/grpc/LifecyclePolicy/index.md) resource.

{% endlist %}

{% note tip %}

You can [test the lifecycle policy](lifecycle-policy-dry-run.md) to check what [Docker images](../../concepts/docker-image.md) comply with the policy rules. Docker images are not actually deleted during dry runs.

{% endnote %}