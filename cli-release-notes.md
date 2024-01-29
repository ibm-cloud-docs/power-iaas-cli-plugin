---

copyright:
  years: 2019, 2024
lastupdated: "2024-01-10"

---

{{site.data.keyword.attribute-definition-list}}


## Release notes
{: #release-notes}

Use these release notes to learn about the latest changes to the {{site.data.keyword.powerSysShort}}.
{: shortdesc}

### January 2024
{: #jan-2024}


New CLI version `0.7.1` available. Here are the changes for the new CLI version:

**New flags**

* "list-catalog": `--sap` Include SAP images.
* "list-catalog": `--vtl` Include VTL images.

**What's Changed**

Removed `--IBMiDBQ-license` flag from `instance-create` command.

**Bug Fixes**

Fixed issue in `instance-update` command when `--virtual-optical-device` flag is not used.

### December 2023
{: dec-2023}

New CLI version `0.7.0` available. Here are the changes for the new CLI version:

**New command**

- [List all storage tiers for the targeted region](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-storage-tiers): List all storage tiers for the targeted region.

**New flags**

- A `--virtual-optical-device` flag is added in [Update a server instance](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-update) command: Use this to attach a virtual optical device to this instance. Valid values is "attach".
- A `--mtu` flag is added in [Create a private network](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-private) command: Use this is to define the Maximum Transmission Unit. The default value is 1450.
- A `--mtu` flag is added in [Create a public network](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-public) command: Use this is to define the Maximum Transmission Unit. The default value is 1450.
- A `--target-tier` flag is added in [Perform an action on a volume](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-action) command:  Use this to change the storage tier of the volume (use [List all storage tiers for the targeted region](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-storage-tiers) to see available storage tiers in the targeted region). `Tier5k` volumes cannot exceed 200 GB.
 

**What's Changed**

- New custom deployment type - `VMNoStorage` for [Create a server instance](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-create) command.
- Deprecate `--jumbo` flag in [Create a public network](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-public) and [Create a private network](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-private) commands.
- New Power Edge Router (PER) details field when using the `workspace` command.

### November 2023
{: #nov-2023}

New CLI version `0.6.0` available. Here are the new changes for the new CLI version:
   * New commands - [Create a workspace](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspace-create) and [Delete a workspace](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspace-delete) added.
  

New CLI version `0.5.0` available. Here are the new changes for the new CLI version:
   * New `--user-data` flag added in [instance-create](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-create) command.
   <!-- * New `--mtu` flag added in [network-create-public](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-public) and [network-create-private](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-private) commands.
   * Deprecate `--jumbo` flag in [network-create-public](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-public) and [network-create-private](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-private) commands. -->
   * New command [datacenter](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-datacenter) and [datacenters](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-datacenters) added.
   * Deprecated `service-list` command in favour of new [workspace](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspace) and [workspaces](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspaces) commands.

### September 2023
{: #sep-2023}

- Added s1022 in `sys-type value` for [Create a server instance](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-create) and [Create a virtual tape library](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-a-vtl) commands.

### December 2022
{: #dec-2022}

- You can now get new error messages for undefined response codes for new service endpoint response codes.
### September 2022
{: #sept-2022}

- You can now use shared processor pool using CLI. The following are new commands for shared processor pools:
    - [View details of a shared processor pool](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool)
    - [Create a shared processor pool](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-create)
    - [Delete a shared processor pool](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-delete)
    - [Update a shared processor pool](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-update)
    - [List all shared processor pools](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pools)
    - [View details of a shared processor pool placement group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-placement-group)
    - [Create a shared processor pool placement group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-placement-group-create)
    - [Delete a shared processor pool placement group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-placement-group-delete)
    - [Add a shared processor pool to the placement group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-placement-group-member-add)
    - [Remove a shared processor pool from the placement group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#remove-from-shared-processor-pool-placement-group)
    - [List all shared processor pool placement groups](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-shared-processor-pool-placement-groups)

- The command [Create a server instance](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-create) is updated to include following new options for SPP and Epic:
    - *shared-processor-pool value*
    - *deployment-type value*

- You can now use global replication service using CLI. The following commands are added new for global replication service:
    - [List disaster recovery locations for the current region or all regions](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-disaster-recovery-loc)
    - [Perform an action on a volume](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-action)
    - [Get a list of flash copy mappings of a volume directly from primary storage host.](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-flash-copy-map)
    - [View details of a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-details)
    - [Create a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-create)
    - [Delete a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-delete)
    - [Get all remote copy relationships for each volume in a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-remote-copy-rel)
    - [Reset a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-reset)
    - [List all volume groups](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-groups)
    - [Start a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-start)
    - [Stop a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-stop)
    - [View storage details of a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-storage-details)
    - [Update a volume group](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-group-update)
    - [Get the information of volume onboarding operation](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-onboarding-info)
    - [Create a volume onboarding operation](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-onboarding-create)
    - [List all volume onboarding operations](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-onboarding-list)
    - [Get the remote copy relationship information of a volume](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-volume-remote-copy-rel)

- The command [Create a volume](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud) is updated to include a new option *replication-enabled*.

- The description of [Create a new SAP PVM Instance](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-sap-instance) is changed for HANA images. 
    

### July 2022
{: #Jul-2022}

- You can now use [Transit Gateway](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-connection) to interconnect your {{site.data.keyword.powerSys_notm}} to the {{site.data.keyword.cloud_notm}} classic and Virtual Private Cloud (VPC).

### April 2022
{: #apr-2022}

- Provisioning VTL instances is temporarily disabled.

### December 2021
{: #dec-2021}

- You can now use [Storage pools](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-create) to set affinity policies by using CLI.
- You can now use [Create connection](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-connection) to set 10 Gbps speed for your Cloud connection by using CLI.
- You can now use [Placement Groups](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#vpn-ipsec-policies) to create placement groups and add VMs to set policies by using CLI.


### October 2021
{: #oct-2021}

- You can now use [VPN](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#vpn-connections) to create VPN connection by using CLI.
- You can now use [VPN IKE policies](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#vpn-ike-policies) to create an IKE policy for the VPN connection by using CLI.
- You can now use [VPN IKE policies](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#vpn-ipsec-policies) to create an IPsec policy for the VPN connection by using CLI.


### September 2021
{: #sep-2021}

- You can now use [Import Image](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-image-import) to Import an image from IBM Cloud Object Storage by using CLI.
- You can now use [Jobs](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-job) to View details of a job by using CLI.
- You can now use [Console language](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-update-console-language) to update Language to Japanese.

### May 2021
{: #may-2021}

- You can now use [Cloud connection](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-connection) to automate the way you connect your Power Systems Virtual Server instances to the IBM Cloud resources by using CLI.

### March 2021
{: #mar-2021}

- You can now manage [snapshots](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#snapshot-id) of a cloud instance by using the CLI.
- You can create and list [SAP profiles](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#sapprofile-info) by using CLI.
- You can [list of available system pools](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#system-pools-support) within a particular data center by using CLI.
- You can [attach](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#attach-network), [detach](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#detach-network), or [list all the attached networks](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#list-networks) to an instance.
- Added image-import progress (task) monitoring.