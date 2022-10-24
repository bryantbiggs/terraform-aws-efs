# AWS EFS Terraform module

Terraform module which creates AWS EFS (elastic file system) resources.

## Usage

See [`examples`](https://github.com/terraform-aws-modules/terraform-aws-efs/tree/master/examples) directory for working examples to reference:

```hcl
module "efs" {
  source = "terraform-aws-modules/efs/aws"

  tags = {
    Terraform   = "true"
    Environment = "dev"
  }
}
```

## Examples

Examples codified under the [`examples`](https://github.com/terraform-aws-modules/terraform-aws-efs/tree/master/examples) are intended to give users references for how to use the module(s) as well as testing/validating changes to the source code of the module. If contributing to the project, please be sure to make any appropriate updates to the relevant examples to allow maintainers to test your changes and to keep the examples up to date for users. Thank you!

- [Complete](https://github.com/terraform-aws-modules/terraform-aws-efs/tree/master/examples/complete)

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 4.16 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 4.16 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_efs_file_system.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/efs_file_system) | resource |
| [aws_efs_file_system_policy.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/efs_file_system_policy) | resource |
| [aws_efs_mount_target.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/efs_mount_target) | resource |
| [aws_security_group.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_security_group_rule.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group_rule) | resource |
| [aws_iam_policy_document.policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_attach_policy"></a> [attach\_policy](#input\_attach\_policy) | Determines whether a policy is attached to the file system | `bool` | `true` | no |
| <a name="input_availability_zone_name"></a> [availability\_zone\_name](#input\_availability\_zone\_name) | The AWS Availability Zone in which to create the file system. Used to create a file system that uses One Zone storage classes | `string` | `null` | no |
| <a name="input_bypass_policy_lockout_safety_check"></a> [bypass\_policy\_lockout\_safety\_check](#input\_bypass\_policy\_lockout\_safety\_check) | A flag to indicate whether to bypass the `aws_efs_file_system_policy` lockout safety check. Defaults to `false` | `bool` | `null` | no |
| <a name="input_create"></a> [create](#input\_create) | Determines whether resources will be created (affects all resources) | `bool` | `true` | no |
| <a name="input_create_security_group"></a> [create\_security\_group](#input\_create\_security\_group) | Determines whether a security group is created | `bool` | `true` | no |
| <a name="input_creation_token"></a> [creation\_token](#input\_creation\_token) | A unique name (a maximum of 64 characters are allowed) used as reference when creating the Elastic File System to ensure idempotent file system creation. By default generated by Terraform | `string` | `null` | no |
| <a name="input_encrypted"></a> [encrypted](#input\_encrypted) | If `true`, the disk will be encrypted | `bool` | `true` | no |
| <a name="input_kms_key_id"></a> [kms\_key\_id](#input\_kms\_key\_id) | The ARN for the KMS encryption key. When specifying `kms_key_id`, encrypted needs to be set to `true` | `string` | `null` | no |
| <a name="input_lifecycle_policy"></a> [lifecycle\_policy](#input\_lifecycle\_policy) | A file system [lifecycle policy](https://docs.aws.amazon.com/efs/latest/ug/API_LifecyclePolicy.html) object | `any` | `{}` | no |
| <a name="input_mount_targets"></a> [mount\_targets](#input\_mount\_targets) | A map of mount target definitions to create | `any` | `{}` | no |
| <a name="input_override_policy_documents"></a> [override\_policy\_documents](#input\_override\_policy\_documents) | List of IAM policy documents that are merged together into the exported document. In merging, statements with non-blank `sid`s will override statements with the same `sid` | `list(string)` | `[]` | no |
| <a name="input_performance_mode"></a> [performance\_mode](#input\_performance\_mode) | The file system performance mode. Can be either `generalPurpose` or `maxIO`. Default is `generalPurpose` | `string` | `null` | no |
| <a name="input_policy_statements"></a> [policy\_statements](#input\_policy\_statements) | A map of IAM policy [statements](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document#statement) for custom permission usage | `any` | `{}` | no |
| <a name="input_provisioned_throughput_in_mibps"></a> [provisioned\_throughput\_in\_mibps](#input\_provisioned\_throughput\_in\_mibps) | The throughput, measured in MiB/s, that you want to provision for the file system. Only applicable with `throughput_mode` set to `provisioned` | `number` | `null` | no |
| <a name="input_security_group_description"></a> [security\_group\_description](#input\_security\_group\_description) | Security group description. Defaults to Managed by Terraform | `string` | `null` | no |
| <a name="input_security_group_name"></a> [security\_group\_name](#input\_security\_group\_name) | Name to assign to the security group. If omitted, Terraform will assign a random, unique name | `string` | `null` | no |
| <a name="input_security_group_rules"></a> [security\_group\_rules](#input\_security\_group\_rules) | Map of security group rule definitions to create | `any` | `{}` | no |
| <a name="input_security_group_use_name_prefix"></a> [security\_group\_use\_name\_prefix](#input\_security\_group\_use\_name\_prefix) | Determines whether to use a name prefix for the security group. If `true`, the `security_group_name` value will be used as a prefix | `bool` | `false` | no |
| <a name="input_security_group_vpc_id"></a> [security\_group\_vpc\_id](#input\_security\_group\_vpc\_id) | The VPC ID where the security group will be created | `string` | `null` | no |
| <a name="input_source_policy_documents"></a> [source\_policy\_documents](#input\_source\_policy\_documents) | List of IAM policy documents that are merged together into the exported document. Statements must have unique `sid`s | `list(string)` | `[]` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | A map of tags to add to all resources | `map(string)` | `{}` | no |
| <a name="input_throughput_mode"></a> [throughput\_mode](#input\_throughput\_mode) | Throughput mode for the file system. Defaults to `bursting`. Valid values: `bursting`, `provisioned`. When using `provisioned`, also set `provisioned_throughput_in_mibps` | `string` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_arn"></a> [arn](#output\_arn) | Amazon Resource Name of the file system |
| <a name="output_dns_name"></a> [dns\_name](#output\_dns\_name) | The DNS name for the filesystem per [documented convention](http://docs.aws.amazon.com/efs/latest/ug/mounting-fs-mount-cmd-dns-name.html) |
| <a name="output_id"></a> [id](#output\_id) | The ID that identifies the file system (e.g., `fs-ccfc0d65`) |
| <a name="output_mount_targets"></a> [mount\_targets](#output\_mount\_targets) | Map of mount targets created and their attributes |
| <a name="output_security_group_arn"></a> [security\_group\_arn](#output\_security\_group\_arn) | ARN of the security group |
| <a name="output_security_group_id"></a> [security\_group\_id](#output\_security\_group\_id) | ID of the security group |
| <a name="output_size_in_bytes"></a> [size\_in\_bytes](#output\_size\_in\_bytes) | The latest known metered size (in bytes) of data stored in the file system, the value is not the exact size that the file system was at any point in time |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## License

Apache-2.0 Licensed. See [LICENSE](https://github.com/terraform-aws-modules/terraform-aws-efs/blob/master/LICENSE).
