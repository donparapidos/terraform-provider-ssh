### terraform-provider-ssh

This provider enables SSH port forwarding in Terraform. It is intended as a
bandaid [until it is supported in Terraform itself](https://github.com/hashicorp/terraform/issues/8367).

#### Example

See [main.tf](main.tf).

#### Installation

On Linux:

```shell
mkdir -p terraform.d/plugins/linux_amd64
wget https://github.com/stefansundin/terraform-provider-ssh/releases/download/v0.0.2/terraform-provider-ssh_v0.0.2_linux_amd64.zip
unzip terraform-provider-ssh_v0.0.2_linux_amd64.zip -d terraform.d/plugins/linux_amd64
rm terraform-provider-ssh_v0.0.2_linux_amd64.zip
terraform init
```

On Mac:

```shell
mkdir -p terraform.d/plugins/darwin_amd64
wget https://github.com/stefansundin/terraform-provider-ssh/releases/download/v0.0.2/terraform-provider-ssh_v0.0.2_darwin_amd64.zip
unzip terraform-provider-ssh_v0.0.2_darwin_amd64.zip -d terraform.d/plugins/darwin_amd64
rm terraform-provider-ssh_v0.0.2_darwin_amd64.zip
terraform init
```

#### Applying an output file

Note that there is a gotcha when trying to apply a generated plan output file (see [issue #1](https://github.com/stefansundin/terraform-provider-ssh/issues/1)). In this case, the SSH tunnels will not be automatically opened.

As a workaround, before you apply, run the companion program `terraform-open-ssh-tunnels` on the plan file first in order to reopen the SSH tunnels. [Download from the releases.](https://github.com/stefansundin/terraform-provider-ssh/releases/latest)

#### TODO

- Support another hop (ProxyJump-like behavior)
- Note that the Windows binary is completely untested!
