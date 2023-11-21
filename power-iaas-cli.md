---

copyright:
  years: 2019, 20223
lastupdated: "2023-11-21"

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:preview: .preview}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}

# IBM {{site.data.keyword.powerSys_notm}} CLI Reference
{: #power-iaas-cli-reference}

This document provides a reference of the command-line interface (CLI) commands that are available for the {{site.data.keyword.powerSysFull}}. You can also use application programming interfaces (APIs) to interact with the {{site.data.keyword.powerSys_notm}}. For more information, see [API references](https://cloud.ibm.com/apidocs/power-cloud){: new_window}{: external}.
{: shortdesc}

## Before you begin
{: #power-iaas-cli-before}

1. Install the [{{site.data.keyword.cloud}} CLI](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started){: new_window}{: external}.

2. Install or update the `power-iaas` plug-in.

    **To install:**

    ```
    ibmcloud plugin install power-iaas
    ```
    {: codeblock}

    **To update:**

    ```
    ibmcloud plugin update
    ```
    {: codeblock}

    **To view your installed plug-ins and versions:**

    ```
    ibmcloud plugin list
    ```
    {: codeblock}

3. Log in to the [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login){: new_window}{: external}.

    The power-iaas command-line plug-in uses the region that `ibmcloud login` targets to determine the {{site.data.keyword.powerSys_notm}} endpoint. For example, to use the {{site.data.keyword.powerSys_notm}} endpoint `https://cloud.ibm.com` you must use the `ibmcloud login -a https://cloud.ibm.com` command to target the `us-east` region. If you have a federated account, use the following command:

    ```
    ibmcloud login -a https://cloud.ibm.com -sso
    ```
    {: codeblock}

4. Run the `ibmcloud pi service-list` command to list all of the services under your account. The **Cloud Resource Name** (CRN) under **ID** contains your **Tenant ID** and **Cloud Instance ID**. The following example shows a typical CRN:

    ```
    crn:v1:staging:public:power-iaas:us-east:a/abcdefghijklmnopqrstuvwxyzabcdef:121d5ee5-b87d-4a0e-86b8-aaff422135478::
    ```
    {: screen}

5. Target your service by entering the following command, `ibmcloud pi service-target <crn>`.

```
ibmcloud pi service-target crn:v1:staging:public:power-iaas:us-east:a/abcdefghijklmnopqrstuvwxyzabcdef:121d5ee5-b87d-4a0e-86b8-aaff422135478::
```
{: codeblock}

Power Systems Virtual Server CLI requires a valid IAM token authorization before each use. Use the ibmcloud login command to renew authorization if your token expires.
{: note}

---

## Release notes
{: #release-notes}

Use these release notes to learn about the latest changes to the {{site.data.keyword.powerSysShort}}.
{: shortdesc}

### November 2023
{: nov-2023}

New CLI version `0.6.0` available. Here are the new changes for the new CLI version:
   * New commands - [Create a workspace](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspace-create) and [Delete a workspace](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspace-delete) added.
  

New CLI version `0.5.0` available. Here are the new changes for the new CLI version:
   * New `--user-data` flag added in [instance-create](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-create) command.
   <!-- * New `--mtu` flag added in [network-create-public](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-public) and [network-create-private](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-private) commands.
   * Deprecate `--jumbo` flag in [network-create-public](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-public) and [network-create-private](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-network-create-private) commands. -->
   * New command [datacenter](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-datacenter) and [datacenters](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-datacenters) added.
   * Deprecated `service-list` command in favour of new [workspace](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspace) and [workspaces](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-workspaces) commands.

### September 2023
{: sep-2023}

- Added s1022 in `sys-type value` for [Create a server instance](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-instance-create) and [Create a virtual tape library](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-a-vtl) commands.

### December 2022
{: dec-2022}

- You can now get new error messages for undefined response codes for new service endpoint response codes.
### September 2022
{: sept-2022}

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
{: Jul-2022}

- You can now use [Transit Gateway](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-connection) to interconnect your {{site.data.keyword.powerSys_notm}} to the {{site.data.keyword.cloud_notm}} classic and Virtual Private Cloud (VPC).

### April 2022
{: apr-2022}

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


## Commands
{: #power-iaas-cli-commands}


### `ibmcloud pi connection`
{: #ibmcloud-pi-connection}

#### View details of a cloud Connection.

`ibmcloud pi connection CONNECTION_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi connection-attach-network`
{: #ibmcloud-pi-connection-attach-network}

#### Attach a network to the cloud connection.

`ibmcloud pi connection-attach-network CONNECTION_ID --network NETWORK_ID`

**Options**

- `--network`: The unique identifier (network ID) of the network.
- `--json`: Format output in JSON.

---

### `ibmcloud pi connection-create`
{: #ibmcloud-pi-connection-create}

#### Create a cloud connection.

`ibmcloud pi connection-create CONNECTION_NAME --speed SPEED [--vpc --vpcID "VPC-ID"] ([--classic [--networks "NETWORK_ID1..NETWORK_IDn" [--gre-tunnel "CIDR DEST-IP"]]] | [--networks "NETWORK_ID1..NETWORK_IDn"]) [--global-routing] [--metered] [--json]`

**Options**

- `--speed`: Speed of the cloud connection (speed in megabits per second). Allowed values are 50, 100, 200, 500, 1000, 2000, 5000, 10000.
- `--networks`: Space separated network identifiers.
- `--vpc`: Enable "VPC" cloud connection endpoint.
- `--vpcID`: VPC ID (i.e. crn:v1:..) to add to cloud connection. Use with "--vpc" option.
- `--classic`: Enable "Classic" cloud connection endpoint.
- `--gre-tunnel`: Space separated "cidr" and "destinationIPAddress". Use with "--classic" option. GRE tunnel cannot be configured with speeds above 5000.
- `--metered`: Metered cloud connection flag.
- `--global-routing`: Global routing flag.
- `--transit-enabled`: Enable transit gateway.
- `--json`: Format output in JSON.

---

### `ibmcloud pi connection-delete`
{: #ibmcloud-pi-connection-delete}

#### Delete a cloud Connection.

`ibmcloud pi connection-delete CONNECTION_ID`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi connection-detach-network`
{: #ibmcloud-pi-connection-detach-network}

#### Detach a network from the cloud connection.

`ibmcloud pi connection-detach-network CONNECTION_ID --network NETWORK_ID [--json]`

**Options**

- `--network`: The unique identifier (network ID) of the network.
- `--json`: Format output in JSON.

---

### `ibmcloud pi connection-update`
{: #ibmcloud-pi-connection-update}

#### Update the cloud connection.

`ibmcloud pi connection-update CONNECTION_ID [--speed SPEED] [--vpc=True|False [<--vpcID "VPC-ID">]] [--classic=True|False [--gre-tunnel "CIDR DEST-IP"]] ...`

**Options**

- `--speed`: New speed value for the cloud connection. Allowed values are 50, 100, 200, 500, 1000, 2000, 5000. Speeds currently at 10000 cannot be downgraded lower and speeds cannot be increased to 10000.
- `--vpc`: Enable or disable VPC cloud connection endpoint.
- `--vpcID`: VPC ID to add to the cloud connection for use with "--vpc" option.
- `--classic`: Enable or disable classic cloud connection endpoint.
- `--gre-tunnel`: Space separated "cidr" and "destinationIPAddress" for use with "--classic" option. GRE tunnel cannot be configured with speeds above 5000.
- `--global-routing`: Enable or disable global routing.
- `--metered`: Enable or disable metering.
- `--name`: Name of the cloud connection.
- `--json`: Format output in JSON.

---

### `ibmcloud pi connection-vpcs`
{: #ibmcloud-pi-connection-vpcs}

#### List all virtual private clouds.

`ibmcloud pi connection-vpcs [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi connections`
{: #ibmcloud-pi-connections}

#### List all cloud Connections

`ibmcloud pi connections [--long] [--json]`

**Options**

- `--long`: Retrieve all cloud connections in detail.
- `--json`: Format output in JSON.

---

### `ibmcloud pi datacenter`
{: #ibmcloud-pi-datacenter}

#### View details of a datacenter

`ibmcloud pi datacenter DATACENTER`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi datacenters`
{: #ibmcloud-pi-datacenters}

#### List all datacenter details

`ibmcloud pi dats`

**Options**

- `--long`: Retrieve additional details for datacenters.
- `--json`: Format output in JSON.

---

### `ibmcloud pi disaster-recovery-locations`
{: #ibmcloud-pi-disaster-recovery-locations}

#### List disaster recovery locations for the current region or all regions.

`ibmcloud pi disaster-recovery-locations [--all-regions] [--json]`

**Options**

- `--all-regions`: List disaster recovery locations for all regions.
- `--json`: Format output in JSON.

---

### `ibmcloud pi image`
{: #ibmcloud-pi-image}

#### View details of an image

`ibmcloud pi image IMAGE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-create`
{: #ibmcloud-pi-image-create}

#### Create a copy of an available stock image into this account; stock image names cannot be changed

`ibmcloud pi image-create IMAGE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-delete`
{: #ibmcloud-pi-image-delete}

#### Delete an image from this account

`ibmcloud pi image-delete IMAGE_ID`


---

### `ibmcloud pi image-export`
{: #ibmcloud-pi-image-export}

#### Export an image to IBM Cloud Object Storage

`ibmcloud pi image-export IMAGE_ID --bucket BUCKET_NAME --region REGION_NAME --access-key KEY --secret-key KEY [(--job | --task)] [--json]`

**Options**

- `--bucket`: Cloud Object Storage bucket name.
- `--region`: Cloud Object Storage region (us-south, us-east, eu-gb, eu-de, au-syd, jp-tok, jp-osa, ca-tor, br-sao).
- `--access-key`: Cloud Object Storage HMAC access key.
- `--secret-key`: Cloud Object Storage HMAC secret key.
- `--json`: Format output in JSON.
- `--job`: The operation will be processed as a job.
- `--task`: [DEPRECATED] The operation will be processed as a task. Task processing is deprecated in favor of job processing. Default.

---

### `ibmcloud pi image-export-show`
{: #ibmcloud-pi-image-export-show}

#### View details of an image export job

`ibmcloud pi image-export-show IMAGE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-import`
{: #ibmcloud-pi-image-import}

#### Import an image from IBM Cloud Object Storage

`ibmcloud pi image-import IMAGE_NAME [--bucket-access private] --disk-type DISKTYPE [--os-type OSTYPE] --access-key KEY --secret-key KEY --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME --job [--json]`

**Options**

- `--image-path`: [DEPRECATED] Replaced by image-file-name, region and bucket. Path to image starting with service endpoint and ending with image file name.
- `--os-type`: Operating system contained in the image (rhel, sles, aix, ibmi). Required when importing a raw image.
- `--bucket-access`: Indicates the bucket access type (private or public). Private access requires access and secret keys. Public access requires the --job option. Default is private.
- `--disk-type`: Type of the disk storage (use "ibmcloud pi storage-types" to see available types in the targeted region); required if --affinity-policy and --storage-pool are not provided.
- `--storage-pool`: Storage pool where the image will be imported to (use "ibmcloud pi storage-pools" to see available storage pools). If  is provided then --disk-type and --affinity-policy values cannot be specified.
- `--affinity-policy`: Affinity policy for image. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this cannot be specified.
- `--affinity-instance`: PVM instance identifier or name to base image affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-volume is not provided.
- `--affinity-volume`: Volume identifier or name to base image affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-instance is not provided.
- `--anti-affinity-instances`: Space separated list of instance identifiers or names to base image anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified and --anti-affinity-volumes is not provided.
- `--anti-affinity-volumes`: Space separated list of volume identifiers or names to base image anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified  and --anti-affinity-instances is not provided.
- `--access-key`: Cloud Object Storage HMAC access key.
- `--secret-key`: Cloud Object Storage HMAC secret key.
- `--image-file-name`: The image file name.
- `--bucket`: Cloud Object Storage bucket name.
- `--region`: Cloud Object Storage region (us-south, us-east, eu-gb, eu-de, au-syd, jp-tok, jp-osa, ca-tor, br-sao).
- `--job`: The operation will be processed as a job. image-file-name,region,and bucket is required.
- `--task`: [DEPRECATED] The operation will be processed as a task. Task processing is deprecated in favor of job processing. Default.
- `--json`: Format output in JSON.

---

### `ibmcloud pi image-import-show`
{: #ibmcloud-pi-image-import-show}

#### View details of the last image import job.

`ibmcloud pi image-import-show [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-list-catalog`
{: #ibmcloud-pi-image-list-catalog}

#### List images available in the regional image catalog

`ibmcloud pi image-list-catalog [--long] [--json]`

**Options**

- `--long`: Retrieve all image details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi images`
{: #ibmcloud-pi-images}

#### List all images for this account

`ibmcloud pi images [--long] [--json]`

**Options**

- `--long`: Retrieve all image details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance`
{: #ibmcloud-pi-instance}

#### View details of a server instance

`ibmcloud pi instance INSTANCE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-attach-network`
{: #ibmcloud-pi-instance-attach-network}

#### Attach a network to the server instance

`ibmcloud pi instance-attach-network INSTANCE_NAME --network "NETWORK_ID" [--ip-address "IP_ADDRESS"] [--json]`

**Options**

- `--network`: The network ID.
- `--ip-address`: The requested ip address of this network interface.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-attach-volumes`
{: #ibmcloud-pi-instance-attach-volumes}

#### Attach volumes to an instance.

`ibmcloud pi instance-attach-volumes INSTANCE_ID --volume-ids "VOLUME_ID1 [VOLUME_IDn]"`

**Options**

- `--volume-ids`: Space separated list of volume IDs to the volumes to attach to the instance.

---

### `ibmcloud pi instance-capture`
{: #ibmcloud-pi-instance-capture}

#### Capture a server instance

`ibmcloud pi instance-capture INSTANCE_ID --destination DEST --name NAME [--volumes "VOLUME-ID1 .. VOLUME-IDn"] [--access-key KEY] [--secret-key KEY] [--region REGION] [--image-path PATH] [(--job | --task)]`

**Options**

- `--destination`: Destination for the deployable image (image-catalog, cloud-storage, both).
- `--name`: Name of the deployable image created for the captured instance.
- `--volumes`: Space separated list of identifiers of the volume(s) to capture with the instance. By default, instance capture include all volumes marked as bootable.
- `--access-key`: Cloud Object Storage HMAC access key. Required if destination is cloud-storage.
- `--secret-key`: Cloud Object Storage HMAC secret key. Required if destination is cloud-storage.
- `--region`: Cloud Object Storage region (us-east, us-south, eu-de). Required if destination is cloud-storage.
- `--image-path`: Cloud Object Storage image path. Required if destination is cloud-storage. E.g. bucket-name[/optional/folder].
- `--job`: The operation will be processed as a job.
- `--task`: [DEPRECATED] The operation will be processed as a task. Task processing is deprecated in favor of job processing. Default.

---

### `ibmcloud pi instance-capture-show`
{: #ibmcloud-pi-instance-capture-show}

#### View the job details of the last server instance capture

`ibmcloud pi instance-capture-show INSTANCE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-create`
{: #ibmcloud-pi-instance-create}

#### Create a server instance

`ibmcloud pi instance-create INSTANCE_NAME --image IMAGE [--memory MEMORY] <--network \"NETWORK1 [IP1]\">`

**Options**

- `--image`: Operating system image identifier or name.
- `--memory`: Amount of memory (in GB) to allocate to the instance. Default is 2GB.
- `--networks`: (deprecated - replaced by "network") Space separated list of identifiers or names of the networks to associate with the instance.
- `--network`: Space separated identifier/name of the network and optional IP address to associate with the instance.
- `--processors`: Amount of processors to allocate to the instance. Default is 1 core.
- `--processor-type`: Type of processors: "shared" or "dedicated" or "capped".
- `--volumes`: Space separated list of identifiers or names of the volume(s) to associate with the instance.
- `--key-name`: Name of SSH key.
- `--sys-type`: Name of System Type ("s922", "e880", "e980"). Default is "s922".
- `--storage-type`: Storage type for server deployment when deploying a stock image (use "ibmcloud pi storage-types" to see available storage types in the targeted region).  If --storage-pool or --storage-affinity is provided then this it cannot be specified. When IBM supplied stock images are deployed either  or --storage-pool or --storage-affinity must be specfied. This is not valid when using a custom image (an imported image or an image that is created from a PVMInstance capture) since storage type and pool defaults to the storage type and pool the image was created in.
- `--storage-connection`: The storage connection type. Valid value is "vSCSI".
- `--storage-pool`: Storage pool for server deployment (use "ibmcloud pi storage-pools" to see available storage pools). Only valid when you deploy one of the IBM supplied stock images. Storage type and pool for a custom image (an imported image or an image that is created from a PVMInstance capture) defaults to the storage type and pool the image was created in.
- `--storage-affinity`: Affinity policy for storage pool selection. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this it cannot be specified.
- `--storage-affinity-instance`: PVM instance identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-volume is not provided.
- `--storage-affinity-volume`: Volume identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-instance is not provided.
- `--storage-anti-affinity-instances`: Space separated list of PVM instance identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-volumes is not provided.
- `--storage-anti-affinity-volumes`: Space separated list of volume identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-instances is not provided.
- `--pin-policy`: Pin policy ("none", "soft", "hard"). Default is "none".
- `--replicants`: Number of duplicate instances to create in this request.
- `--replicant-scheme`: Naming scheme to use for duplicate VMs ("suffix", "prefix").
- `--replicant-affinity-policy`: Affinity policy to use when multicreate is used ("affinity", "anti-affinity").
- `--IBMiCSS-license`: IBMi CSS software license associated with the instance.
- `--IBMiDBQ-license`: IBMi DBQ software license associated with the instance.
- `--IBMiPHA-license`: IBMi PHA software license associated with the instance.
- `--IBMiRDS-users`: Number of IBMi RDS users software license associated with the instance, default IBMiRDSUsers=0 (no license).
- `--placement-group`: The placement group ID of the group that the server will be added to.
- `--shared-processor-pool`: The shared processor pool ID of the pool that the server will be in.
- `--deployment-type`: The custom deployment type ("EPIC").
- `--user-data`: The user data passed into the instance.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-delete`
{: #ibmcloud-pi-instance-delete}

#### Delete a server instance

`ibmcloud pi instance-delete INSTANCE_ID [--delete-data-volumes]`

**Options**

- `--delete-data-volumes`: Indicates whether all data volumes attached to the instance must be deleted. Shared data volumes will be deleted if no other instances are attached.

---

### `ibmcloud pi instance-detach-network`
{: #ibmcloud-pi-instance-detach-network}

#### Detach a specific network or mac address from the server instance.

`ibmcloud pi instance-detach-network INSTANCE_NAME --network "NETWORK_ID" [--mac-address "MAC_ADDRESS"]`

**Options**

- `--network`: The network ID.
- `--mac-address`: The mac address of the network interface to be removed. The default is all mac addresses.

---

### `ibmcloud pi instance-get-console`
{: #ibmcloud-pi-instance-get-console}

#### Get the console of an instance

`ibmcloud pi instance-get-console INSTANCE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-hard-reboot`
{: #ibmcloud-pi-instance-hard-reboot}

#### Hard Restart the operating system of an instance

`ibmcloud pi instance-hard-reboot INSTANCE_ID`


---

### `ibmcloud pi instance-immediate-shutdown`
{: #ibmcloud-pi-instance-immediate-shutdown}

#### Immediately Shutdown a server instance

`ibmcloud pi instance-immediate-shutdown INSTANCE_ID`


---

### `ibmcloud pi instance-list-console-languages`
{: #ibmcloud-pi-instance-list-console-languages}

#### List the available console languages for an instance.

`ibmcloud pi instance-list-console-languages INSTANCE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-list-snapshots`
{: #ibmcloud-pi-instance-list-snapshots}

#### List all snapshots for an instance.

`ibmcloud pi instance-list-snapshots INSTANCE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-list-volumes`
{: #ibmcloud-pi-instance-list-volumes}

#### Get a list of volumes attached to an instance

`ibmcloud pi instance-list-volumes INSTANCE [--long] [--json]`

**Options**

- `--long`: Retrieve all volume details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-networks`
{: #ibmcloud-pi-instance-networks}

#### List all the attached networks.

`ibmcloud pi instance-networks INSTANCE_NAME [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-operation`
{: #ibmcloud-pi-instance-operation}

#### Perform an operation on an IBMi server instance.

`ibmcloud pi instance-operation INSTANCE_ID --operation-type TYPE [--boot-mode MODE] [] [--boot-operating-mode MODE] [--job-task TASK]`

**Options**

- `--operation-type`: Name of the operation to execute; allowable values are "job" and "boot".
- `--boot-mode`: Name of the server boot mode; allowable values are "a", "b", "c", and "d".
- `--boot-operating-mode`: Name of the server operating mode; allowable values are "normal" and "manual".
- `--job-task`: Name of the job task to execute; allowable values are "dston", "retrydump", "consoleservice", "iopreset", "remotedstoff", "remotedston", "iopdump", and "dumprestart".

---

### `ibmcloud pi instance-reset-state`
{: #ibmcloud-pi-instance-reset-state}

#### Reset a server instance

`ibmcloud pi instance-reset-state INSTANCE_ID`


---

### `ibmcloud pi instance-soft-reboot`
{: #ibmcloud-pi-instance-soft-reboot}

#### Soft Restart the operating system of an instance

`ibmcloud pi instance-soft-reboot INSTANCE_ID`


---

### `ibmcloud pi instance-start`
{: #ibmcloud-pi-instance-start}

#### Start a server instance

`ibmcloud pi instance-start INSTANCE_ID`


---

### `ibmcloud pi instance-stop`
{: #ibmcloud-pi-instance-stop}

#### Stop a server instance

`ibmcloud pi instance-stop INSTANCE_ID`


---

### `ibmcloud pi instance-update`
{: #ibmcloud-pi-instance-update}

#### Update a server instance

`ibmcloud pi instance-update INSTANCE_ID [--memory AMOUNT] [--name NEW_NAME] [--pin-policy POLICY] [--processors NUMBER] [--processor-type TYPE] [--profile-id SAP_PROFILE_ID] [--storage-pool-affinity=True|False] [--json]`

**Options**

- `--memory`: New amount of memory for the server instance.
- `--name`: New name of the server instance.
- `--pin-policy`: New pin policy for the server instance ("none", "soft", "hard").
- `--processors`: New amount of processors for the server instance.
- `--processor-type`: New processor type for the server instance.
- `--profile-id`: SAP profile ID.
- `--storage-pool-affinity`: Indicates if all volumes attached to the server must reside in the same storage pool. If set to false then volumes from any storage type and pool can be attached to the PVM instance; This impacts PVM instance snapshot,capture,and clone. For capture and clone only data volumes that are of the same storage type and in the same storage pool of the PVM instance's boot volume can be included. For snapshot all data volumes to be included in the snapshot must reside in the same storage type and pool. Once set to false,cannot be set back to true unless all volumes attached reside in the same storage type and pool.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-update-console-language`
{: #ibmcloud-pi-instance-update-console-language}

#### Update the console language of an instance. This update may take some time to take affect.

`ibmcloud pi instance-update-console-language INSTANCE_ID --code CODE`

**Options**

- `--code`: Language code to set. Use 'ibmcloud pi instance-list-console-languages' to see available codes.

---

### `ibmcloud pi instances`
{: #ibmcloud-pi-instances}

#### List all server instances

`ibmcloud pi instances [--long] [--json]`

**Options**

- `--long`: Retrieve all instance details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi job`
{: #ibmcloud-pi-job}

#### View details of a job

`ibmcloud pi job JOB_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi job-delete`
{: #ibmcloud-pi-job-delete}

#### Delete a job

`ibmcloud pi job-delete JOB_ID`


---

### `ibmcloud pi jobs`
{: #ibmcloud-pi-jobs}

#### List all jobs

`ibmcloud pi jobs [--operation-action ACTION] [--operation-id ID] [--operation-target TARGET] [--json]`

**Options**

- `--operation-action`: Operation action to filter returned jobs. Valid values are vmCapture, imageExport, imageImport, storage.
- `--operation-id`: Operation ID to filter returned jobs.
- `--operation-target`: Operation target to filter returned jobs. Valid values are cloudConnection, pvmInstance, image.
- `--json`: Format output in JSON.

---

### `ibmcloud pi key`
{: #ibmcloud-pi-key}

#### View details of a key

`ibmcloud pi key KEY_NAME [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi key-create`
{: #ibmcloud-pi-key-create}

#### Create a key with imported RSA public key

`ibmcloud pi key-create KEY_NAME --key KEY [--json]`

**Options**

- `--key`: SSH RSA key string within a double quotation marks. For example, "ssh-rsa AAA... ".
- `--json`: Format output in JSON.

---

### `ibmcloud pi key-delete`
{: #ibmcloud-pi-key-delete}

#### Delete a key

`ibmcloud pi key-delete KEY_NAME`


---

### `ibmcloud pi key-update`
{: #ibmcloud-pi-key-update}

#### Update the name and the value of a SSH key

`ibmcloud pi key-update KEY_NAME --new-name NEW_NAME --new-key NEW_KEY [--json]`

**Options**

- `--new-name`: SSH key name.
- `--new-key`: SSH RSA key string.
- `--json`: Format output in JSON.

---

### `ibmcloud pi keys`
{: #ibmcloud-pi-keys}

#### List all keys

`ibmcloud pi keys [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi network`
{: #ibmcloud-pi-network}

#### View details of a network

`ibmcloud pi network NETWORK_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi network-create-private`
{: #ibmcloud-pi-network-create-private}

#### Create a private network

`ibmcloud pi network-create-private NETWORK_NAME --cidr-block CIDR --ip-range "startIP-endIP[,startIP-endIP]" [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--jumbo] [--json]`

**Options**

- `--cidr-block`: Network in CIDR notation (192.168.0.0/24).
- `--dns-servers`: Space separated list of DNS Servers to use for this network. 127.0.0.1 by default if DNS server is not specified. A maximum of one DNS server can be specified in Power Edge Router workspaces.
- `--gateway`: Gateway to use for this network.
- `--ip-range`: IP Addresses range(s) for this network, format: startIP-endIP[,startIP-endIP].
- `--json`: Format output in JSON.
- `--jumbo`: Enable MTU Jumbo Network.

---

### `ibmcloud pi network-create-public`
{: #ibmcloud-pi-network-create-public}

#### Create a public network

`ibmcloud pi network-create-public NETWORK_NAME [--dns-servers "DNS1 DNS2"] [--jumbo] [--json]`

**Options**

- `--dns-servers`: Space separated list of DNS Servers to use for this network. 9.9.9.9 by default if DNS server is not specified.
- `--jumbo`: Enable MTU Jumbo Network.
- `--json`: Format output in JSON.

---

### `ibmcloud pi network-delete`
{: #ibmcloud-pi-network-delete}

#### Delete a network

`ibmcloud pi network-delete NETWORK_ID`


---

### `ibmcloud pi network-update`
{: #ibmcloud-pi-network-update}

#### Update a network

`ibmcloud pi network-update NETWORK_ID [--name NETWORK_NAME] [--ip-range "startIP-endIP[,startIP-endIP]"] [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--json]`

**Options**

- `--name`: New name of the network.
- `--dns-servers`: Space separated list of new DNS servers to use for this network.
- `--gateway`: New gateway to use for this network.
- `--ip-range`: New IP address range(s) for this network.
- `--json`: Format output in JSON.

---

### `ibmcloud pi networks`
{: #ibmcloud-pi-networks}

#### List all networks

`ibmcloud pi networks [--long] [--json]`

**Options**

- `--long`: Retrieve all network details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi placement-group`
{: #ibmcloud-pi-placement-group}

#### View details of a server placement group.

`ibmcloud pi placement-group PLACEMENT_GROUP_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi placement-group-create`
{: #ibmcloud-pi-placement-group-create}

#### Create a server placement group.

`ibmcloud pi placement-group-create PLACEMENT_GROUP_NAME --policy POLICY [--json]`

**Options**

- `--policy`: Affinity policy for placement group being created. Valid values are affinity and anti-affinity.
- `--json`: Format output in JSON.

---

### `ibmcloud pi placement-group-delete`
{: #ibmcloud-pi-placement-group-delete}

#### Delete a server placement group.

`ibmcloud pi placement-group-delete PLACEMENT_GROUP_ID`


---

### `ibmcloud pi placement-group-server-add`
{: #ibmcloud-pi-placement-group-server-add}

#### Add a server to the server placement group.

`ibmcloud pi placement-group-server-add PLACEMENT_GROUP_ID --server INSTANCE_ID [--json]`

**Options**

- `--server`: The server instance ID of the server to add to the placement group.
- `--json`: Format output in JSON.

---

### `ibmcloud pi placement-group-server-remove`
{: #ibmcloud-pi-placement-group-server-remove}

#### Remove a server from a server placement group.

`ibmcloud pi placement-group-server-remove PLACEMENT_GROUP_ID --server INSTANCE_ID [--json]`

**Options**

- `--server`: The server instance ID of the server to remove from the placement group.
- `--json`: Format output in JSON.

---

### `ibmcloud pi placement-groups`
{: #ibmcloud-pi-placement-groups}

#### List all server placement groups.

`ibmcloud pi placement-groups [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi sap-create-instance`
{: #ibmcloud-pi-sap-create-instance}

#### Create a new SAP PVM Instance. This command is for use with Linux for SAP (HANA) images.

`ibmcloud pi sap-create-instance SAP_INSTANCE_NAME --image IMAGE --profile-id PROFILE_ID --networks "NETWORK1 [IP1]" [--pin-policy POLICY] [--volumes "VOLUME1 VOLUME2"]`

**Options**

- `--image`: Linux for SAP (HANA) operating system image identifier or name.
- `--profile-id`: The unique identifier of the SAP profile.
- `--networks`: Space separated identifier/name of the network and optional IP address to associate with the instance.
- `--pin-policy`: Pin policy ("none", "soft", "hard"). Default is "none".
- `--volumes`: Space separated list of identifiers or names of the volume(s) to associate with the instance.
- `--storage-type`: Storage type for SAP PVM instance deployment when deploying a stock image (use "ibmcloud pi storage-types" to see available storage types in the targeted region).  If --storage-pool or --storage-affinity is provided then this it cannot be specified. Only valid when one of the IBM supplied stock images is deployed.
- `--storage-pool`: Storage pool for SAP PVM instance deployment. Only valid when you deploy one of the IBM supplied stock images.
- `--storage-affinity`: Affinity policy for storage pool selection. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this it cannot be specified.
- `--storage-affinity-instance`: PVM instance identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-volume is not provided.
- `--storage-affinity-volume`: Volume identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-instance is not provided.
- `--storage-anti-affinity-instances`: Space separated list of PVM instance identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-volumes is not provided.
- `--storage-anti-affinity-volumes`: Space separated list of volume identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-instances is not provided.
- `--key-name`: Name of SSH key.
- `--sys-type`: Name of system type ("e880", "e980"). Default is "e980".
- `--placement-group`: The placement group ID of the group that the server will be added to.
- `--json`: Format output in JSON.

---

### `ibmcloud pi sap-list`
{: #ibmcloud-pi-sap-list}

#### List all SAP profiles for the targeted region

`ibmcloud pi sap-list [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi sap-profile`
{: #ibmcloud-pi-sap-profile}

#### Get the information on a SAP profile

`ibmcloud pi sap-profile SAP_PROFILE_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi service-list`
{: #ibmcloud-pi-service-list}

#### [DEPRECATED] Replaced by "ibmcloud pi workspaces" command. List all services for this account and region

`ibmcloud pi service-list [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi service-target`
{: #ibmcloud-pi-service-target}

#### Target a service

`ibmcloud pi service-target SERVICE_ID`


---

### `ibmcloud pi shared-processor-pool`
{: #ibmcloud-pi-shared-processor-pool}

#### View details of a shared processor pool.

`ibmcloud pi shared-processor-pool SHARED_PROCESSOR_POOL_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi shared-processor-pool-create`
{: #ibmcloud-pi-shared-processor-pool-create}

#### Create a shared processor pool.

`ibmcloud pi shared-processor-pool-create SHARED_PROCESSOR_POOL_NAME --host-group HOST_GROUP --reserved-cores NUMBER_OF_CORES [--placement-group-id PLACEMENT_GROUP_ID] [--json]`

**Options**

- `--host-group`: The host group where the host will be chosen if not provided. Valid values are 's922', or 'e980'.
- `--reserved-cores`: The integer amount of reserved processor cores for the shared processor pool.
- `--placement-group-id`: The identifier of the shared processor pool placement group the pool will be added to.
- `--json`: Format output in JSON.

---

### `ibmcloud pi shared-processor-pool-delete`
{: #ibmcloud-pi-shared-processor-pool-delete}

#### Delete a shared processor pool.

`ibmcloud pi shared-processor-pool-delete SHARED_PROCESSOR_POOL_ID`


---

### `ibmcloud pi shared-processor-pool-update`
{: #ibmcloud-pi-shared-processor-pool-update}

#### Update a shared processor pool.

`ibmcloud pi shared-processor-pool-update SHARED_PROCESSOR_POOL_ID [--name SHARED_PROCESSOR_POOL_NAME] [--reserved-cores NUMBER_OF_CORES] [--json]`

**Options**

- `--name`: New name of the shared processor pool. A minimum of 2 characters and a maximum of 12 are allowed. The only special character allowed is the underscore '_'.
- `--reserved-cores`: The integer amount of reserved processor cores for the shared processor pool.
- `--json`: Format output in JSON.

---

### `ibmcloud pi shared-processor-pools`
{: #ibmcloud-pi-shared-processor-pools}

#### List all shared processor pools.

`ibmcloud pi shared-processor-pools [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi snapshot`
{: #ibmcloud-pi-snapshot}

#### Get the detail of a snapshot.

`ibmcloud pi snapshot SNAPSHOT_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi snapshot-create`
{: #ibmcloud-pi-snapshot-create}

#### Create a PVM instance snapshot

`ibmcloud pi snapshot-create INSTANCE_ID --name SNAPSHOT_NAME [--volumes "VOLUME-ID1 .. VOLUME-IDn"] [--description DESCRIPTION] [--json]`

**Options**

- `--name`: Name of the snapshot.
- `--volumes`: Space separated list of volumes to include in the PVM instance snapshot.
- `This`: parameter is optional. If you do not specify this parameter or if the volumes list is empty,.
- `all`: the volumes that are attached to the PVM instance are included in the snapshot.
- `--description`: Snapshot description.
- `--json`: Format output in JSON.

---

### `ibmcloud pi snapshot-delete`
{: #ibmcloud-pi-snapshot-delete}

#### Delete a snapshot.

`ibmcloud pi snapshot-delete SNAPSHOT_ID`


---

### `ibmcloud pi snapshot-restore`
{: #ibmcloud-pi-snapshot-restore}

#### Restore a PVM instance snapshot

`ibmcloud pi snapshot-restore INSTANCE_ID --snapshot SNAPSHOT_ID [--force] [--restore VALUE]`

**Options**

- `--snapshot`: The unique identifier of the snapshot.
- `--force`: By default the VM must be shutoff during a snapshot restore,force set to true will relax the VM shutoff pre-condition.
- `--restore`: Action to take on a failed snapshot restore - allowable values: ["retry","rollback"].

---

### `ibmcloud pi snapshots`
{: #ibmcloud-pi-snapshots}

#### List all snapshots

`ibmcloud pi snapshots [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi spp-placement-group`
{: #ibmcloud-pi-spp-placement-group}

#### View details of a shared processor pool placement group.

`ibmcloud pi spp-placement-group PLACEMENT_GROUP_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi spp-placement-group-create`
{: #ibmcloud-pi-spp-placement-group-create}

#### Create a shared processor pool placement group.

`ibmcloud pi spp-placement-group-create PLACEMENT_GROUP_NAME --policy POLICY [--json]`

**Options**

- `--policy`: Affinity policy for placement group being created. Valid values are affinity and anti-affinity.
- `--json`: Format output in JSON.

---

### `ibmcloud pi spp-placement-group-delete`
{: #ibmcloud-pi-spp-placement-group-delete}

#### Delete a shared processor pool placement group.

`ibmcloud pi spp-placement-group-delete PLACEMENT_GROUP_ID`


---

### `ibmcloud pi spp-placement-group-member-add`
{: #ibmcloud-pi-spp-placement-group-member-add}

#### Add a shared processor pool to the placement group.

`ibmcloud pi spp-placement-group-member-add PLACEMENT_GROUP_ID --shared-processor-pool POOL_ID [--json]`

**Options**

- `--shared-processor-pool`: The shared processor pool ID of the pool to add to the placement group.
- `--json`: Format output in JSON.

---

### `ibmcloud pi spp-placement-group-member-remove`
{: #ibmcloud-pi-spp-placement-group-member-remove}

#### Remove a shared processor pool from the placement group.

`ibmcloud pi spp-placement-group-member-remove PLACEMENT_GROUP_ID --shared-processor-pool POOL_ID [--json]`

**Options**

- `--shared-processor-pool`: The shared processor pool ID of the pool to remove from the placement group.
- `--json`: Format output in JSON.

---

### `ibmcloud pi spp-placement-groups`
{: #ibmcloud-pi-spp-placement-groups}

#### List all shared processor pool placement groups.

`ibmcloud pi spp-placement-groups [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi storage-pools`
{: #ibmcloud-pi-storage-pools}

#### List all storage pools for the targeted region

`ibmcloud pi storage-pools [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi storage-types`
{: #ibmcloud-pi-storage-types}

#### List all storage types for the targeted region

`ibmcloud pi storage-types [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi system-pool`
{: #ibmcloud-pi-system-pool}

#### List of available system pools within a particular data center

`ibmcloud pi system-pool [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi task`
{: #ibmcloud-pi-task}

#### View details of a task.

`ibmcloud pi task TASK_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi task-delete`
{: #ibmcloud-pi-task-delete}

#### Delete a task.

`ibmcloud pi task-delete TASK_ID [--json]`


---

### `ibmcloud pi virtual-tape-libraries`
{: #ibmcloud-pi-virtual-tape-libraries}

#### List all virtual tape libraries

`ibmcloud pi virtual-tape-libraries [--long] [--json]`

**Options**

- `--long`: Retrieve all virtual tape library details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi virtual-tape-library`
{: #ibmcloud-pi-virtual-tape-library}

#### View details of a virtual tape library

`ibmcloud pi virtual-tape-library TAPE_LIBRARY_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi virtual-tape-library-attach-network`
{: #ibmcloud-pi-virtual-tape-library-attach-network}

#### Attach a network to the virtual tape library.

`ibmcloud pi virtual-tape-library-attach-network TAPE_LIBRARY_NAME --network "NETWORK_ID" [--ip-address "IP_ADDRESS"] [--json]`

**Options**

- `--network`: The network ID.
- `--ip-address`: The requested ip address of this network interface.
- `--json`: Format output in JSON.

---

### `ibmcloud pi virtual-tape-library-create`
{: #ibmcloud-pi-virtual-tape-library-create}

#### Create a virtual tape library

`ibmcloud pi virtual-tape-library-create TAPE_LIBRARY_NAME --image IMAGE --capacity LICENSED_CAPACITY [--memory MEMORY] <--network \"NETWORK1 [IP1]\">`

**Options**

- `--image`: Operating system image identifier or name.
- `--capacity`: Amount of licensed repository capacity (in TB).
- `--memory`: Amount of memory (in GB) to allocate to the virtual tape library. Memory needs to be at least 16 GB + (2 GB x the licensed repository capacity value).
- `--network`: Space separated identifier/name of the network and optional IP address to associate with the virtual tape library.
- `--processors`: Amount of processors to allocate to the virtual tape library. 1-12 TB of licensed repository capacity needs at least 2 processors...
- `13`: - 72 TB of licensed repository capacity needs at least 4 processors. Greater than 72 TB of licensed repository capacity needs at least 8 processors.
- `--processor-type`: Type of processors: 'shared' or 'dedicated' or 'capped'.
- `--volumes`: Space separated list of identifiers or names of the volumes to associate with the virtual tape library. A minimum of 3 volumes is required.
- `--key-name`: Name of SSH key.
- `--sys-type`: Name of System Type ("s922", "e880", "e980"). Default is "s922".
- `--storage-type`: Storage type for virtual tape library deployment when deploying a stock image (use "ibmcloud pi storage-types" to see available storage types in the targeted region).  If --storage-pool or --storage-affinity is provided then this it cannot be specified. Only valid when one of the IBM supplied stock images is deployed.
- `--storage-pool`: Storage pool for virtual tape library deployment. Only valid when you deploy one of the IBM supplied stock images.
- `--storage-affinity`: Affinity policy for storage pool selection. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this it cannot be specified.
- `--storage-affinity-instance`: PVM instance or VTL identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-volume is not provided.
- `--storage-affinity-volume`: Volume identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-instance is not provided.
- `--storage-anti-affinity-instances`: Space separated list of PVM instance or VTL identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-volumes is not provided.
- `--storage-anti-affinity-volumes`: Space separated list of volume identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-instances is not provided.
- `--pin-policy`: Pin policy ("none", "soft", "hard"). Default is "none".
- `--placement-group`: The placement group ID of the group that the virtual tape library will be added to.
- `--shared-processor-pool`: The shared processor pool ID of the pool that the virtual tape library will be in.
- `--json`: Format output in JSON.

---

### `ibmcloud pi virtual-tape-library-delete`
{: #ibmcloud-pi-virtual-tape-library-delete}

#### Delete a virtual tape library

`ibmcloud pi virtual-tape-library-delete TAPE_LIBRARY_ID [--delete-data-volumes]`

**Options**

- `--delete-data-volumes`: Indicates whether all data volumes attached to the virtual tape library must be deleted. Shared data volumes will be deleted if no other virtual tape libraries are attached.

---

### `ibmcloud pi virtual-tape-library-detach-network`
{: #ibmcloud-pi-virtual-tape-library-detach-network}

#### Detach all or a specific network from the virtual tape library.

`ibmcloud pi virtual-tape-library-detach-network TAPE_LIBRARY_NAME --network "NETWORK_ID" [--mac-address "MAC_ADDRESS"]`

**Options**

- `--network`: The network ID.
- `--mac-address`: The mac address of the network interface to be removed. The default is all mac addresses.

---

### `ibmcloud pi virtual-tape-library-get-console`
{: #ibmcloud-pi-virtual-tape-library-get-console}

#### Get the console of a virtual tape library.

`ibmcloud pi virtual-tape-library-get-console TAPE_LIBRARY_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi virtual-tape-library-hard-reboot`
{: #ibmcloud-pi-virtual-tape-library-hard-reboot}

#### Hard restart the operating system of a virtual tape library.

`ibmcloud pi virtual-tape-library-hard-reboot TAPE_LIBRARY_ID`


---

### `ibmcloud pi virtual-tape-library-immediate-shutdown`
{: #ibmcloud-pi-virtual-tape-library-immediate-shutdown}

#### Immediately shutdown a virtual tape library

`ibmcloud pi virtual-tape-library-immediate-shutdown TAPE_LIBRARY_ID`


---

### `ibmcloud pi virtual-tape-library-networks`
{: #ibmcloud-pi-virtual-tape-library-networks}

#### List all the attached networks.

`ibmcloud pi virtual-tape-library-networks TAPE_LIBRARY_NAME [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi virtual-tape-library-reset-state`
{: #ibmcloud-pi-virtual-tape-library-reset-state}

#### Reset a virtual tape library

`ibmcloud pi virtual-tape-library-reset-state TAPE_LIBRARY_ID`


---

### `ibmcloud pi virtual-tape-library-soft-reboot`
{: #ibmcloud-pi-virtual-tape-library-soft-reboot}

#### Soft restart the operating system of a virtual tape library.

`ibmcloud pi virtual-tape-library-soft-reboot TAPE_LIBRARY_ID`


---

### `ibmcloud pi virtual-tape-library-start`
{: #ibmcloud-pi-virtual-tape-library-start}

#### Start a virtual tape library

`ibmcloud pi virtual-tape-library-start TAPE_LIBRARY_ID`


---

### `ibmcloud pi virtual-tape-library-stop`
{: #ibmcloud-pi-virtual-tape-library-stop}

#### Stop a virtual tape library.

`ibmcloud pi virtual-tape-library-stop TAPE_LIBRARY_ID`


---

### `ibmcloud pi virtual-tape-library-update`
{: #ibmcloud-pi-virtual-tape-library-update}

#### Update a virtual tape library.

`ibmcloud pi virtual-tape-library-update TAPE_LIBRARY_ID [--capacity LICENSED_CAPACITY] [--memory AMOUNT] [--name NEW_NAME] [--pin-policy POLICY] [--processors NUMBER] [--processor-type TYPE] [--storage-pool-affinity=True|False] [--json]`

**Options**

- `--capacity`: New amount of licensed repository capacity (in TB). This value can only be increased.
- `--memory`: New amount of memory for the virtual tape library. Memory needs to be at least 16 GB + (2 GB x the licensed repository capacity value).
- `--name`: New name of the virtual tape library.
- `--pin-policy`: New pin policy for the virtual tape library ("none", "soft", "hard").
- `--processors`: New amount of processors for the virtual tape library. 1-12 TB of licensed repository capacity needs at least 2 processors...
- `13`: - 72 TB of licensed repository capacity needs at least 4 processors. Greater than 72 TB of licensed repository capacity needs at least 8 processors.
- `--processor-type`: New processor type for the virtual tape library.
- `--storage-pool-affinity`: Indicates if all volumes attached to the virtual tape library must reside in the same storage pool. If set to false then volumes from any storage type and pool can be attached to the virtual tape library. Once set to false,cannot be set back to true unless all volumes attached reside in the same storage type and pool.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume`
{: #ibmcloud-pi-volume}

#### View details of a volume

`ibmcloud pi volume VOLUME_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-action`
{: #ibmcloud-pi-volume-action}

#### Perform an action on a volume.

`ibmcloud pi volume-action VOLUME_ID [--replication-enabled=True|False]`

**Options**

- `--replication-enabled`: Enables or disables storage replication on the volume.

---

### `ibmcloud pi volume-attach`
{: #ibmcloud-pi-volume-attach}

#### Attach a volume to an instance

`ibmcloud pi volume-attach VOLUME_ID --instance INSTANCE [--json]`

**Options**

- `--instance`: Instance to attach the volume to.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-clone`
{: #ibmcloud-pi-volume-clone}

#### Get the status of a clone request for the specified clone task ID.

`ibmcloud pi volume-clone CLONE_TASK_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-create`
{: #ibmcloud-pi-volume-create}

#### Create a volume

`ibmcloud pi volume-create VOLUME_NAME --type TYPE --size SIZE [--shareable] [--replication-enabled] [--json]`

**Options**

- `--type`: Type of the volume (use "ibmcloud pi storage-types" to see available storage types in the targeted region).
- `--size`: Size of the volume (in GB).
- `--shareable`: Whether volume can be attached to multiple VMs.
- `--storage-pool`: Volume pool where the volume will be created (use "ibmcloud pi storage-pools" to see available storage pools). If  is provided then --type and --affinity-policy values cannot be specified.
- `--affinity-policy`: Affinity policy for data volume being created. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this cannot be specified.
- `--affinity-instance`: PVM instance identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-volume is not provided.
- `--affinity-volume`: Volume identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-instance is not provided.
- `--anti-affinity-instances`: Space separated list of instance identifiers or names to base volume anit-affinity policy against; required if "--affinity-policy anti-affinity" is specified and --anti-affinity-volumes is not provided.
- `--anti-affinity-volumes`: Space separated list of volume identifiers or names to base volume anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified  and --anti-affinity-instances is not provided.
- `--replication-enabled`: Enables storage replication on the volume. False by default.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-create-clone`
{: #ibmcloud-pi-volume-create-clone}

#### Create a volume clone for specific volumes.

`ibmcloud pi volume-create-clone CLONE_NAME --volumes "VOLUME1 ..VOLUMEn" [--json]`

**Options**

- `--volumes`: Space separated list of identifiers the volume(s) to be cloned.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-delete`
{: #ibmcloud-pi-volume-delete}

#### Delete a volume

`ibmcloud pi volume-delete VOLUME_ID`


---

### `ibmcloud pi volume-detach`
{: #ibmcloud-pi-volume-detach}

#### Detach a volume from an instance

`ibmcloud pi volume-detach VOLUME_ID --instance INSTANCE [--json]`

**Options**

- `--instance`: Instance to detach the volume from.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-flash-copy-mapping`
{: #ibmcloud-pi-volume-flash-copy-mapping}

#### Get a list of flash copy mappings of a volume directly from primary storage host.

`ibmcloud pi volume-flash-copy-mapping VOLUME_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-group`
{: #ibmcloud-pi-volume-group}

#### View details of a volume group.

`ibmcloud pi volume-group VOLUME_GROUP_ID [--long] [--json]`

**Options**

- `--long`: Retrieve additional details for the volume group.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-group-create`
{: #ibmcloud-pi-volume-group-create}

#### Create a volume group.

`ibmcloud pi volume-group-create (--volume-group-name VOLUME_GROUP_NAME | --consistency-group-name CONSISTENCY_GROUP_NAME) --member-volume-ids "VOLUME_ID_1 [VOLUME_ID_N]" [--json]`

**Options**

- `--volume-group-name`: Storage volume group name. This is required for the creation of new volume group.
- `--consistency-group-name`: Storage volume group name. This is required to onboard existing volume group on the target site for DR set up.
- `--member-volume-ids`: Space separated member volume identifiers.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-group-delete`
{: #ibmcloud-pi-volume-group-delete}

#### Delete a volume group.

`ibmcloud pi volume-group-delete VOLUME_GROUP_ID`


---

### `ibmcloud pi volume-group-remote-copy-relationships`
{: #ibmcloud-pi-volume-group-remote-copy-relationships}

#### Get all remote copy relationships for each volume in a volume group.

`ibmcloud pi volume-group-remote-copy-relationships VOLUME_GROUP_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-group-reset`
{: #ibmcloud-pi-volume-group-reset}

#### Reset a volume group to update its status value.

`ibmcloud pi volume-group-reset VOLUME_GROUP_ID [--status STATUS]`

**Options**

- `--status`: New status to be set for a volume group. Default is "available".

---

### `ibmcloud pi volume-group-start`
{: #ibmcloud-pi-volume-group-start}

#### Start a volume group.

`ibmcloud pi volume-group-start VOLUME_GROUP_ID [--source SOURCE]`

**Options**

- `--source`: The copying volume source. Allowed values are master or auxiliary. Default is master.

---

### `ibmcloud pi volume-group-stop`
{: #ibmcloud-pi-volume-group-stop}

#### Stop a volume group.

`ibmcloud pi volume-group-stop VOLUME_GROUP_ID [--allow-read-access]`

**Options**

- `--allow-read-access`: Allow the auxiliary volume to be accessible after stopping the volume group. Default is false.

---

### `ibmcloud pi volume-group-storage-details`
{: #ibmcloud-pi-volume-group-storage-details}

#### View storage details of a volume group.

`ibmcloud pi volume-group-storage-details VOLUME_GROUP_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-group-update`
{: #ibmcloud-pi-volume-group-update}

#### Update a volume group.

`ibmcloud pi volume-group-update VOLUME_GROUP_ID [--add-member-volume-ids "VOLUME_ID_1 [VOLUME_ID_N]"] [--remove-member-volume-ids "VOLUME_ID_1 [VOLUME_ID_N]"]`

**Options**

- `--add-member-volume-ids`: Space separated volume identifiers to add as members of the volume group.
- `--remove-member-volume-ids`: Space separated volume identifiers to remove as members of the volume group.

---

### `ibmcloud pi volume-groups`
{: #ibmcloud-pi-volume-groups}

#### List all volume groups.

`ibmcloud pi volume-groups [--long] [--json]`

**Options**

- `--long`: Retrieve additional details for all volume groups.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-multi-create`
{: #ibmcloud-pi-volume-multi-create}

#### Create multiple volume.

`ibmcloud pi volume-multi-create VOLUME_BASE_NAME --type TYPE --volume-count COUNT --size SIZE [--shareable] [--replication-enabled] [--json]`

**Options**

- `--type`: Type of the volume (use "ibmcloud pi storage-types" to see available storage types in the targeted region); required if --affinity-policy and --storage-pool are not provided.
- `--volume-count`: Number of volumes to create.
- `--size`: Size of the volume (in GB).
- `--shareable`: Whether the volumes can be attached to multiple VMs.
- `--storage-pool`: Volume pool where the volume will be created. If  is provided then --type and --affinity-policy values cannot be specified.
- `--affinity-policy`: Affinity policy for data volume being created. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this cannot be specified.
- `--affinity-instance`: PVM instance identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-volume is not provided.
- `--affinity-volume`: Volume identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-instance is not provided.
- `--anti-affinity-instances`: Space separated list of instance identifiers or names to base volume anit-affinity policy against; required if "--affinity-policy anti-affinity" is specified and --anti-affinity-volumes is not provided.
- `--anti-affinity-volumes`: Space separated list of volume identifiers or names to base volume anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified  and --anti-affinity-instances is not provided.
- `--replication-enabled`: Enables storage replication on the volume. False by default.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-onboarding`
{: #ibmcloud-pi-volume-onboarding}

#### Get the information of volume onboarding operation.

`ibmcloud pi volume-onboarding VOLUME_ONBOARDING_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-onboarding-create`
{: #ibmcloud-pi-volume-onboarding-create}

#### Create a volume onboarding operation.

`ibmcloud pi volume-onboarding-create --source-crn SOURCE_CRN <--auxiliary-volume "AUXVOLUMENAME1 [NAME1]"--> [--description] [--json]`

**Options**

- `--source-crn`: CRN of source ServiceBroker instance from where auxiliary volumes need to be onboarded.
- `--auxiliary-volume`: Space separated list of identifiers of the volume(s) at storage host level. Repeat this option to add more auxiliary volumes.
- `--description`: Volume onboarding description.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-onboardings`
{: #ibmcloud-pi-volume-onboardings}

#### List all volume onboarding operations.

`ibmcloud pi volume-onboardings [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-remote-copy-relationship`
{: #ibmcloud-pi-volume-remote-copy-relationship}

#### Get the remote copy relationship information of a volume.

`ibmcloud pi volume-remote-copy-relationship VOLUME_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-update`
{: #ibmcloud-pi-volume-update}

#### Update a volume

`ibmcloud pi volume-update VOLUME_ID [--bootable=True|False] [--name NEW_NAME] [--size NEW_SIZE] [--shareable=True|False] [--json]`

**Options**

- `--bootable`: New  for whether the volume can be booted.
- `--name`: New name of the volume.
- `--size`: New size of the volume.
- `--shareable`: New  for whether the volume can be attached to multiple VMs.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volumes`
{: #ibmcloud-pi-volumes}

#### List all volumes

`ibmcloud pi volumes [--long] [--json] [--replication-enabled=True|False] [--auxiliary=True|False]`

**Options**

- `--long`: Retrieve all volume details.
- `--json`: Format output in JSON.
- `--replication-enabled`: Filter replication-enabled volumes if set to True or non-replication-enabled volumes if False. True by default.
- `--auxiliary`: Filter auxiliary volumes if set to True or non-auxiliary volumes if False. True by default.

---

### `ibmcloud pi vpn-connection`
{: #ibmcloud-pi-vpn-connection}

#### View details of a VPN connection.

`ibmcloud pi vpn-connection VPN_CONNECTION_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connection-create`
{: #ibmcloud-pi-vpn-connection-create}

#### Create a VPN connection.

`ibmcloud pi vpn-connection-create VPN_CONNECTION_NAME --mode MODE --peer-gateway-address PEER_GATEWAY --peer-subnet-cidrs "CIDR1 [CIDRn]" --ike-policy-id IKE_POLICY_ID --ipsec-policy-id IPSEC_POLICY_ID --network-ids "ID1 [IDn]" [--json]`

**Options**

- `--mode`: Mode to be used by the VPN connection and cannot be updated later. Valid values are 'route' and 'policy'.
- `--peer-gateway-address`: IP address of the peer gateway attached to this VPN connection.
- `--peer-subnet-cidrs`: Space separated list of peer subnet CIDRs.
- `--ike-policy-id`: Unique ID of IKE policy selected for this VPN connection.
- `--ipsec-policy-id`: Unique ID of IPSec policy selected for this VPN connection.
- `--network-ids`: Space separated list of network IDs attached to this VPN connection.
- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connection-delete`
{: #ibmcloud-pi-vpn-connection-delete}

#### Delete a VPN connection.

`ibmcloud pi vpn-connection-delete VPN_CONNECTION_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connection-network-attach`
{: #ibmcloud-pi-vpn-connection-network-attach}

#### Attach a network to a specific VPN connection

`ibmcloud pi vpn-connection-network-attach VPN_CONNECTION_ID --network-id ID [--json]`

**Options**

- `--network-id`: Network ID to attach to the VPN connection.
- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connection-network-detach`
{: #ibmcloud-pi-vpn-connection-network-detach}

#### Detach a network from a specific VPN connection.

`ibmcloud pi vpn-connection-network-detach VPN_CONNECTION_ID --network-id ID`

**Options**

- `--network-id`: Network ID to detach from the VPN connection.

---

### `ibmcloud pi vpn-connection-networks`
{: #ibmcloud-pi-vpn-connection-networks}

#### Get a list of networks attached to a specific VPN connection.

`ibmcloud pi vpn-connection-networks VPN_CONNECTION_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connection-peer-subnet-attach`
{: #ibmcloud-pi-vpn-connection-peer-subnet-attach}

#### Attach a peer subnet to a specific VPN connection.

`ibmcloud pi vpn-connection-peer-subnet-attach VPN_CONNECTION_ID --peer-subnet-cidr CIDR [--json]`

**Options**

- `--peer-subnet-cidr`: Peer subnet CIDR to attach to the VPN connection.
- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connection-peer-subnet-detach`
{: #ibmcloud-pi-vpn-connection-peer-subnet-detach}

#### Detach a peer subnet from a specific VPN connection.

`ibmcloud pi vpn-connection-peer-subnet-detach VPN_CONNECTION_ID --peer-subnet-cidr CIDR`

**Options**

- `--peer-subnet-cidr`: Peer subnet CIDR to detach from this VPN connection.

---

### `ibmcloud pi vpn-connection-peer-subnets`
{: #ibmcloud-pi-vpn-connection-peer-subnets}

#### Get a list of peer subnets attached to a specific VPN connection.

`ibmcloud pi vpn-connection-peer-subnets VPN_CONNECTION_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connection-update`
{: #ibmcloud-pi-vpn-connection-update}

#### Update a VPN connection.

`ibmcloud pi vpn-connection-update VPN_CONNECTION_ID [--name VPN_CONNECTION_NAME] [--peer-gateway-address PEER_GATEWAY] [--ike-policy-id IKE_POLICY_ID] [--ipsec-policy-id IPSEC_POLICY_ID] [--json]`

**Options**

- `--name`: New unique name of this VPN connection.
- `--peer-gateway-address`: New IP address of the peer gateway attached to this VPN connection.
- `--ike-policy-id`: New ID of IKE policy selected for this VPN connection.
- `--ipsec-policy-id`: New ID of IPSec policy selected for this VPN connection.
- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-connections`
{: #ibmcloud-pi-vpn-connections}

#### List all VPN connections.

`ibmcloud pi vpn-connections [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ike-policies`
{: #ibmcloud-pi-vpn-ike-policies}

#### List all VPN IKE policies.

`ibmcloud pi vpn-ike-policies [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ike-policy`
{: #ibmcloud-pi-vpn-ike-policy}

#### View details of a VPN IKE policy.

`ibmcloud pi vpn-ike-policy IKE_POLICY_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ike-policy-add`
{: #ibmcloud-pi-vpn-ike-policy-add}

#### Add a VPN IKE policy.

`ibmcloud pi vpn-ike-policy-add IKE_POLICY_NAME --version VERSION --authentication AUTHENTICATION --encryption ENCRYPTION --dh-group DH_GROUP --preshared-key KEY --key-lifetime SECONDS [--json]`

**Options**

- `--version`: Version number of the IKE policy. Valid values are '2', '1'.
- `--authentication`: Authentication algorithm of the IKE policy. Valid values are 'sha-256', 'sha-384', 'sha1', 'none'.
- `--encryption`: Encryption algorithm of the IKE policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
- `--dh-group`: DH group number of the IKE policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
- `--preshared-key`: Preshared key used in this VPN connection. The key length must be even.
- `--key-lifetime`: Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ike-policy-delete`
{: #ibmcloud-pi-vpn-ike-policy-delete}

#### Delete a VPN IKE policy.

`ibmcloud pi vpn-ike-policy-delete IKE_POLICY_ID`


---

### `ibmcloud pi vpn-ike-policy-update`
{: #ibmcloud-pi-vpn-ike-policy-update}

#### Update a VPN IKE policy.

`ibmcloud pi vpn-ike-policy-update IKE_POLICY_ID  [--name NEW_NAME] [--version VERSION] [--authentication AUTHENTICATION] [--encryption ENCRYPTION] [--dh-group DH_GROUP] [--preshared-key KEY] [--key-lifetime SECONDS] [--json]`

**Options**

- `--name`: New unique name of the IKE Policy. The maximum name length is 47 characters.
- `--version`: Version number of the IKE Policy. Valid values are '2', '1'.
- `--authentication`: Authentication algorithm of the IKE Policy. Valid values are 'sha-256', 'sha-384', 'sha1', 'none'.
- `--encryption`: Encryption algorithm of the IKE Policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
- `--dh-group`: DH group number of the IKE Policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
- `--preshared-key`: Preshared key used in this VPN connection. The key length must be even.
- `--key-lifetime`: Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ipsec-policies`
{: #ibmcloud-pi-vpn-ipsec-policies}

#### List all IPSec policies.

`ibmcloud pi vpn-ipsec-policies [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ipsec-policy`
{: #ibmcloud-pi-vpn-ipsec-policy}

#### View details of a VPN IPSec policy.

`ibmcloud pi vpn-ipsec-policy IPSEC_POLICY_ID [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ipsec-policy-add`
{: #ibmcloud-pi-vpn-ipsec-policy-add}

#### Add a VPN IPSec policy.

`ibmcloud pi vpn-ipsec-policy-add IPSEC_POLICY_NAME --authentication AUTHENTICATION --encryption ENCRYPTION --dh-group DH_GROUP --key-lifetime SECONDS [--pfs] [--json]`

**Options**

- `--authentication`: Authentication encryption type of the IPSec policy. Valid values are 'hmac-sha-256-128', 'hmac-sha1-96', 'none'.
- `--encryption`: Connection encryption policy of the IPSec policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-192-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm', 'aes-192-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
- `--dh-group`: DH group number of the IPSec policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
- `--key-lifetime`: Key lifetime of the IPSec policy in seconds. Valid range is 180 to 86400 seconds.
- `--pfs`: Enable perfect forward secrecy. Disabled if not specified.
- `--json`: Format output in JSON.

---

### `ibmcloud pi vpn-ipsec-policy-delete`
{: #ibmcloud-pi-vpn-ipsec-policy-delete}

#### Delete a VPN IPSec policy.

`ibmcloud pi vpn-ipsec-policy-delete IPSEC_POLICY_ID`


---

### `ibmcloud pi vpn-ipsec-policy-update`
{: #ibmcloud-pi-vpn-ipsec-policy-update}

#### Update a VPN IPSec policy.

`ibmcloud pi vpn-ipsec-policy-update IPSEC_POLICY_ID  [--name NEW_NAME] [--authentication AUTHENTICATION] [--encryption ENCRYPTION] [--dh-group DH_GROUP] [--key-lifetime SECONDS] [--pfs=True|False] [--json]`

**Options**

- `--name`: New unique name of the IPSec policy. The maximum name length is 47 characters.
- `--authentication`: Authentication algorithm of the IPSec policy. Valid values are 'hmac-sha-256-128', 'hmac-sha1-96', 'none'.
- `--encryption`: Encryption algorithm of the IPSec policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-192-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm', 'aes-192-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
- `--dh-group`: DH group number of the IPSec policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
- `--key-lifetime`: Key lifetime of the IPSec policy in seconds. Valid range is 180 to 86400 seconds.
- `--pfs`: Enable or disable perfect forward secrecy.
- `--json`: Format output in JSON.

---

### `ibmcloud pi workspace`
{: #ibmcloud-pi-workspace}

#### View details of a workspace

`ibmcloud pi workspace WORKSPACE_ID`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi workspace-create`
{: #ibmcloud-pi-workspace-create}

#### Create a workspace

`ibmcloud pi workspace-create WORKSPACE_NAME --datacenter DATACENTER --group RESOURCE_GROUP --plan PLAN [--json]`

**Options**

- `--datacenter`: The datacenter location where the instance should be hosted. Use the "datacenters" command to see possible values.
- `--group`: The ID of the resource group. Use the "ibmcloud resource groups" command to see possible values.
- `--plan`: Plan associated with the offering. Valid values are "public" or "private".
- `--json`: Format output in JSON.

---

### `ibmcloud pi workspace-delete`
{: #ibmcloud-pi-workspace-delete}

#### Delete a workspace

`ibmcloud pi workspace-delete WORKSPACE_ID`

---

### `ibmcloud pi workspaces`
{: #ibmcloud-pi-workspaces}

#### List workspaces for this account

`ibmcloud pi wss`

**Options**

- `--long`: Retrieve all workspace details.
- `--json`: Format output in JSON.

---