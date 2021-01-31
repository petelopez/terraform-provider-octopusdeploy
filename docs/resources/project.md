---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "octopusdeploy_project Resource - terraform-provider-octopusdeploy"
subcategory: ""
description: |-
  This resource manages projects in Octopus Deploy.
---

# Resource `octopusdeploy_project`

This resource manages projects in Octopus Deploy.

## Example Usage

```terraform
resource "octopusdeploy_project" "example" {
  auto_create_release                  = false
  default_guided_failure_mode          = "EnvironmentDefault"
  default_to_skip_if_already_installed = false
  description                          = "The development project."
  discrete_channel_release             = false
  is_disabled                          = false
  is_discrete_channel_release          = false
  is_version_controlled                = false
  lifecycle_id                         = "Lifecycles-123"
  name                                 = "Development Project (OK to Delete)"
  project_group_id                     = "ProjectGroups-123"
  tenanted_deployment_participation    = "TenantedOrUntenanted"

  connectivity_policy {
    allow_deployments_to_no_targets = false
    exclude_unhealthy_targets       = false
    skip_machine_behavior           = "SkipUnavailableMachines"
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **lifecycle_id** (String) The lifecycle ID associated with this project.
- **name** (String) The name of this resource.

### Optional

- **allow_deployments_to_no_targets** (Boolean, Deprecated)
- **auto_create_release** (Boolean)
- **auto_deploy_release_overrides** (List of String)
- **cloned_from_project_id** (String)
- **connectivity_policy** (Block List) (see [below for nested schema](#nestedblock--connectivity_policy))
- **default_guided_failure_mode** (String)
- **default_to_skip_if_already_installed** (Boolean)
- **deployment_changes_template** (String)
- **description** (String) The description of this resource.
- **discrete_channel_release** (Boolean) Treats releases of different channels to the same environment as a separate deployment dimension
- **id** (String) The unique ID for this resource.
- **included_library_variable_sets** (List of String)
- **is_disabled** (Boolean)
- **is_discrete_channel_release** (Boolean) Treats releases of different channels to the same environment as a separate deployment dimension
- **is_version_controlled** (Boolean)
- **project_group_id** (String)
- **release_creation_strategy** (Block List, Max: 1) (see [below for nested schema](#nestedblock--release_creation_strategy))
- **release_notes_template** (String)
- **space_id** (String) The space ID associated with this resource.
- **templates** (Block List) (see [below for nested schema](#nestedblock--templates))
- **tenanted_deployment_participation** (String) The tenanted deployment mode of the resource. Valid account types are `Untenanted`, `TenantedOrUntenanted`, or `Tenanted`.
- **version_control_settings** (Block Set) (see [below for nested schema](#nestedblock--version_control_settings))

### Read-only

- **deployment_process_id** (String)
- **extension_settings** (Block Set) (see [below for nested schema](#nestedblock--extension_settings))
- **slug** (String)
- **variable_set_id** (String)
- **versioning_strategy** (Block Set) (see [below for nested schema](#nestedblock--versioning_strategy))

<a id="nestedblock--connectivity_policy"></a>
### Nested Schema for `connectivity_policy`

Optional:

- **allow_deployments_to_no_targets** (Boolean)
- **exclude_unhealthy_targets** (Boolean)
- **skip_machine_behavior** (String)
- **target_roles** (List of String)


<a id="nestedblock--release_creation_strategy"></a>
### Nested Schema for `release_creation_strategy`

Optional:

- **channel_id** (String)
- **release_creation_package** (Block List, Max: 1) (see [below for nested schema](#nestedblock--release_creation_strategy--release_creation_package))
- **release_creation_package_step_id** (String)

<a id="nestedblock--release_creation_strategy--release_creation_package"></a>
### Nested Schema for `release_creation_strategy.release_creation_package`

Optional:

- **deployment_action** (String)
- **package_reference** (String)



<a id="nestedblock--templates"></a>
### Nested Schema for `templates`

Required:

- **name** (String) The name of the variable set by the parameter. The name can contain letters, digits, dashes and periods. Example: `ServerName`.

Optional:

- **default_value** (String) A default value for the parameter, if applicable. This can be a hard-coded value or a variable reference.
- **display_settings** (Map of String) The display settings for the parameter.
- **help_text** (String) The help presented alongside the parameter input.
- **id** (String) The unique ID for this resource.
- **label** (String) The label shown beside the parameter when presented in the deployment process. Example: `Server name`.


<a id="nestedblock--version_control_settings"></a>
### Nested Schema for `version_control_settings`

Optional:

- **password** (String, Sensitive) The password associated with this resource.
- **username** (String, Sensitive) The username associated with this resource.

Read-only:

- **default_branch** (String)
- **url** (String)


<a id="nestedblock--extension_settings"></a>
### Nested Schema for `extension_settings`

Read-only:

- **extension_id** (String)
- **values** (List of String)


<a id="nestedblock--versioning_strategy"></a>
### Nested Schema for `versioning_strategy`

Read-only:

- **donor_package** (List of Object) (see [below for nested schema](#nestedatt--versioning_strategy--donor_package))
- **donor_package_step_id** (String)
- **template** (String)

<a id="nestedatt--versioning_strategy--donor_package"></a>
### Nested Schema for `versioning_strategy.donor_package`

Read-only:

- **deployment_action** (String)
- **package_reference** (String)

## Import

Import is supported using the following syntax:

```shell
terraform import [options] octopusdeploy_project.<name> <project-id>
```