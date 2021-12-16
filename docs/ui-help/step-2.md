In the **VPC for AWS** section, do one of the following:

* To create a new VPC, select **Create new VPC on AWS**, check that the pre-filled CIDR block is available, and click **Next**. If the recommended CIDR block is not available, enter a new IP range in CIDR format for the management cluster to use. The recommended CIDR block for **VPC CIDR** is 10.0.0.0/16.
* To use an existing VPC, select **Select an existing VPC** and select the **VPC ID** from the drop-down menu. The **VPC CIDR** block is filled in automatically when you select the VPC.

For more information about VPC, see [Virtual Private Clouds and NAT Gateway Limits](https://tanzucommunityedition.io/docs/latest/ref-aws/#vpc).

## Step 3: Management Cluster Settings

1. In the **Management Cluster Settings** section, select an instance size for either **Development** or **Production**. If you select **Development**, the installer deploys a management cluster with a single control plane node. If you select **Production**, the installer deploys a highly available management cluster with three control plane nodes. Use the **Instance type** drop-down menu to select from different combinations of CPU, RAM, and storage for the control plane node VM or VMs.  Choices are listed alphabetically, not by size. The minimum configuration is 2 CPUs and 8 GB memory. The list of compatible instance types varies in different regions. For information about the configuration of the different sizes of instances, see [Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/).

1. (Optional) Enter a name for your management cluster. If you do not specify a name, the installer generates a unique name. If you do specify a name, the name must end with a letter, not a numeric character, and must be compliant with DNS hostname requirements as outlined in [RFC 952](https://tools.ietf.org/html/rfc952) and amended in [RFC 1123](https://tools.ietf.org/html/rfc1123).
1. Under **Worker Node Instance Type**, select the configuration for the worker node VM.  If you select an instance type in the **Production** tile, the instance type that you select is automatically selected for the **Worker Node Instance Type**. If necessary, you can change this.
1. [`MachineHealthCheck`](https://cluster-api.sigs.k8s.io/developer/architecture/controllers/machine-health-check.html#machinehealthcheck) is selected by default. `MachineHealthCheck` provides node health monitoring and node auto-repair on the clusters that you deploy with this management cluster. You can activate or deactivate `MachineHealthCheck` on clusters after deployment by using the CLI.
1. (Optional) Disable the **Bastion Host** checkbox if a bastion host already exists in the availability zone(s) in which you are deploying the management cluster.
1. Configure Availability Zones. From the **Availability Zone 1** drop-down menu, select an availability zone for the management cluster. You can select only one availability zone in the **Development** tile.  If you selected the **Production** tile, use the **Availability Zone 1**, **Availability Zone 2**, and **Availability Zone 3** drop-down menus to select three unique availability zones for the management cluster. When Tanzu deploys the management cluster, which includes three control plane nodes, it distributes the control plane nodes across these availability zones.

1. To complete the configuration of the **Management Cluster Settings** section, do one of the following:
   * If you created a new VPC in the **VPC for AWS** section, click **Next**.
   * If you selected an existing VPC in the **VPC for AWS** section, use the **VPC public subnet** and **VPC private subnet** drop-down menus to select existing subnets on the VPC and click **Next**.