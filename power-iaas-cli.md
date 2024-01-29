---

copyright:
  years: 2019, 2024
lastupdated: "2024-01-29"

---

{{site.data.keyword.attribute-definition-list}}

# IBM {{site.data.keyword.powerSys_notm}} CLI Reference v 0.7.1
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

## Commands V0.7.1

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

`ibmcloud pi image-import IMAGE_NAME [--bucket-access private] [--disk-type STORAGE_TIER] [--os-type OSTYPE] --access-key KEY --secret-key KEY --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME --job [--json]`

**Options**

- `--image-path`: [DEPRECATED] Replaced by image-file-name, region and bucket. Path to image starting with service endpoint and ending with image file name.
- `--os-type`: Operating system contained in the image (rhel, sles, aix, ibmi). Required when importing a raw image.
- `--bucket-access`: Indicates the bucket access type (private or public). Private access requires access and secret keys. Public access requires the --job option. Default is private.
- `--disk-type`: Tier of the disk storage (use "ibmcloud pi storage-tiers" to see available tiers in the targeted region); Default to tier3 if not provided.
- `--storage-pool`: Storage pool where the image will be imported to (use "ibmcloud pi storage-pools" to see available storage pools). If  is provided then --affinity-policy values cannot be specified.
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

`ibmcloud pi image-list-catalog [--sap] [--vtl] [--long] [--json]`

**Options**

- `--sap`: Include SAP images.
- `--vtl`: Include VTL images.
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
- `--storage-type`: Storage tier for server deployment when deploying a stock image (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region). Default to tier3 if not provided.
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
- `--IBMiPHA-license`: IBMi PHA software license associated with the instance.
- `--IBMiRDS-users`: Number of IBMi RDS users software license associated with the instance, default IBMiRDSUsers=0 (no license).
- `--placement-group`: The placement group ID of the group that the server will be added to.
- `--shared-processor-pool`: The shared processor pool ID of the pool that the server will be in.
- `--deployment-type`: The custom deployment type ("EPIC" or "VMNoStorage").
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
- `--virtual-optical-device`: Attach or Detach a Virtual Optical Device to this instance. Valid values are "attach" and "detach".
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

`ibmcloud pi network-create-private NETWORK_NAME --cidr-block CIDR --ip-range "startIP-endIP[,startIP-endIP]" [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--jumbo] [--mtu] [--json]`

**Options**

- `--cidr-block`: Network in CIDR notation (192.168.0.0/24).
- `--dns-servers`: Space separated list of DNS Servers to use for this network. 127.0.0.1 by default if DNS server is not specified. A maximum of one DNS server can be specified in Power Edge Router workspaces.
- `--gateway`: Gateway to use for this network.
- `--ip-range`: IP Addresses range(s) for this network, format: startIP-endIP[,startIP-endIP].
- `--json`: Format output in JSON.
- `--jumbo`: (deprecated - replaced by "mtu") Enable MTU Jumbo Network.
- `--mtu`: Maximum Transmission Unit. The default value is 1450.

---

### `ibmcloud pi network-create-public`
{: #ibmcloud-pi-network-create-public}

#### Create a public network

`ibmcloud pi network-create-public NETWORK_NAME [--dns-servers "DNS1 DNS2"] [--jumbo] [--mtu] [--json]`

**Options**

- `--dns-servers`: Space separated list of DNS Servers to use for this network. 9.9.9.9 by default if DNS server is not specified.
- `--jumbo`: (deprecated - replaced by "mtu") Enable MTU Jumbo Network.
- `--mtu`: Maximum Transmission Unit. The default value is 1450.
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
- `--storage-type`: Storage tier for server deployment when deploying a stock image (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region). Default to tier3 if not provided.
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

#### [DEPRECATED] Replaced by "ibmcloud pi workspaces" command. List all services for this account

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

### `ibmcloud pi storage-tiers`
{: #ibmcloud-pi-storage-tiers}

#### List all storage tiers for the targeted region

`ibmcloud pi storage-tiers [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi storage-types`
{: #ibmcloud-pi-storage-types}

#### [DEPRECATED] Replaced by "ibmcloud pi storage-tiers" command. List all storage types for the targeted region.

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

`ibmcloud pi volume-action VOLUME_ID [--replication-enabled=True|False] [--target-tier STORAGE_TIER]`

**Options**

- `--replication-enabled`: Enables or disables storage replication on the volume.
- `--target-tier`: Change the storage tier of the volume (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region). "Tier5k" volumes cannot exceed 200GB.

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

`ibmcloud pi volume-create VOLUME_NAME --size SIZE [--type STORAGE_TIER] [--shareable] [--replication-enabled] [--json]`

**Options**

- `--type`: Tier of the volume (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region); Default to tier3 if not provided.
- `--size`: Size of the volume (in GB). "Tier5k" volumes cannot exceed 200GB.
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

`ibmcloud pi volume-create-clone CLONE_NAME --volumes "VOLUME1 ..VOLUMEn" [--replication-enabled=True|False] [--target-tier STORAGE_TIER] [--json]`

**Options**

- `--replication-enabled`: Enables replication for the cloned volume. If no value is provided, it will default to the replication status of the source volume.
- `--target-tier`: Target storage tier for the cloned volumes (use "ibmcloud storage-tiers" to see available tiers in the targeted region). Default to the storage tier of the original volume(s) if not specified.
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

`ibmcloud pi volume-multi-create VOLUME_BASE_NAME --volume-count COUNT --size SIZE [--type STORAGE_TIER] [--shareable] [--replication-enabled] [--json]`

**Options**

- `--type`: Tier of the volume (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region); Default to tier3 if not provided.
- `--volume-count`: Number of volumes to create.
- `--size`: Size of the volume (in GB). "Tier5k" volumes cannot exceed 200GB.
- `--shareable`: Whether the volumes can be attached to multiple VMs.
- `--storage-pool`: Volume pool where the volume will be created. If  is provided then --affinity-policy values cannot be specified.
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
- `--size`: New size of the volume. "Tier5k" volumes cannot exceed 200GB.
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

#### List all workspaces for this account

`ibmcloud pi wss`

**Options**

- `--long`: Retrieve all workspace details.
- `--json`: Format output in JSON.

---

## Commands V1.0.0
{: #pvs-cli-commands-v1}

Following are the V1.0.0 commands. For more information on what have changed, see [What’s new in IBM Power Virtual Server CLI V 1.0.0](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-whats-new-v1).

## `ibmcloud pi`
{: #ibmcloud-pi}
**Alias**: `pi`
**Description**: Manage IBM Cloud Power Virtual Server service.
**Usage**: `pi`
**Available Commands**:
- `cloud-connection`:    IBM Cloud Power Virtual Server Cloud Connections.
- `datacenter`:    IBM Cloud Power Virtual Server Datacenters.
- `disaster-recovery`:    List disaster recovery locations for the current region or all regions.
- `ike-policy`:    IBM Cloud Power Virtual Server Internet Key Exchange policies.
- `image`:    IBM Cloud Power Virtual Server Images.
- `instance`:    IBM Cloud Power Virtual Server Instances.
- `ipsec-policy`:    IBM Cloud Power Virtual Server Internet Protocol Security policies.
- `job`:    IBM Cloud Power Virtual Server Jobs.
- `placement-group`:    IBM Cloud Power Virtual Server Placement Groups.
- `shared-processor-pool`:    IBM Cloud Power Virtual Shared Processor Pools.
- `snapshot`:    IBM Cloud Power Virtual Server Snapshots.
- `ssh-key`:    IBM Cloud Power Virtual Server SSH-Keys.
- `storage-pools`:    List all storage pools for the targeted region.
- `storage-tiers`:    List all storage tiers for the targeted region.
- `subnet`:    IBM Cloud Power Virtual Server Subnets.
- `system-pools`:    List of available system pools within a particular data center.
- `volume`:    IBM Cloud Power Virtual Server Volumes.
- `volume-group`:    IBM Cloud Power Virtual Server Volume Groups.
- `vpn`:    IBM Cloud Power Virtual Server Virtual Private Networking.
- `workspace`:    IBM Cloud Power Virtual Server Workspaces.

---

### `ibmcloud pi cloud-connection`
{: #ibmcloud-pi-cloud-connection}
**Alias**: `cloud-connection, cc`
**Description**: IBM Cloud Power Virtual Server Cloud Connections.
**Usage**: `cloud-connection`
**Available Commands**:
- `create`:    Create a cloud connection.
- `delete`:    Delete a cloud Connection.
- `get`:    View details of a cloud Connection.
- `list`:    List all Cloud Connections.
- `subnet`:    IBM Cloud Power Virtual Server Virtual Cloud Connection Subnets.
- `update`:    Update the cloud connection.

---

#### `ibmcloud pi cloud-connection create`
{: #ibmcloud-pi-cloud-connection-create}
**Alias**: `create, cr`
**Description**: Create a cloud connection.
**Usage**: 
```
create CONNECTION_NAME --speed SPEED
		([--classic [--subnets "SUBNET_ID1..SUBNET_IDn" --gre-tunnel "CIDR DEST-IP"]] | [--subnets "SUBNET_ID1..SUBNET_IDn"])
		[--global-routing] [--metered] [--vpc --vpcIDs "VPC-ID"]

  CONNECTION_NAME: The unique name of the cloud connection.
```
**Available Flags**:
```
  -c, --classic             Enable "Classic" cloud connection endpoint.
  -g, --global-routing      Global routing flag.
  -t, --gre-tunnel string   Space separated "cidr" and "destinationIPAddress". Use with "--classic" option. GRE tunnel cannot be configured with speeds above 5000.
  -m, --metered             Metered cloud connection flag.
  -s, --speed int           Speed of the cloud connection (speed in megabits per second). Allowed values are 50, 100, 200, 500, 1000, 2000, 5000, 10000.
  -n, --subnets strings     Comma separated subnet identifiers.
  -r, --transit-enabled     Enable transit gateway.
  -v, --vpc                 Enable "VPC" cloud connection endpoint.
  -p, --vpcIDs strings      VPC ID (i.e. crn:v1:..) to add to cloud connection. Use with "--vpc" option.
```

---

#### `ibmcloud pi cloud-connection delete`
{: #ibmcloud-pi-cloud-connection-delete}
**Alias**: `delete, del`
**Description**: Delete a cloud Connection.
**Usage**: 
```
delete CONNECTION_ID

  CONNECTION_ID: The unique identifier of the cloud connection.
```

---

#### `ibmcloud pi cloud-connection get`
{: #ibmcloud-pi-cloud-connection-get}
**Alias**: `get`
**Description**: View details of a cloud Connection.
**Usage**: 
```
get CONNECTION_ID

  CONNECTION_ID: The unique identifier of the cloud connection.
```

---

#### `ibmcloud pi cloud-connection list`
{: #ibmcloud-pi-cloud-connection-list}
**Alias**: `list, ls`
**Description**: List all Cloud Connections.
**Usage**: `list`

---

#### `ibmcloud pi cloud-connection subnet`
{: #ibmcloud-pi-cloud-connection-subnet}
**Alias**: `subnet, snet`
**Description**: IBM Cloud Power Virtual Server Virtual Cloud Connection Subnets.
**Usage**: `subnet`
**Available Commands**:
- `attach`:    Attach a network to the cloud connection.
- `detach`:    Detach a subnet from the cloud connection.

---

##### `ibmcloud pi cloud-connection subnet attach`
{: #ibmcloud-pi-cloud-connection-subnet-attach}
**Alias**: `attach, att`
**Description**: Attach a network to the cloud connection.
**Usage**: 
```
attach CONNECTION_ID --subnet SUBNET_ID

  CONNECTION_ID: The unique identifier of the cloud connection.
```
**Available Flags**:
```
  -s, --subnet string   Subnet ID to attach to the cloud connection.
```

---

##### `ibmcloud pi cloud-connection subnet detach`
{: #ibmcloud-pi-cloud-connection-subnet-detach}
**Alias**: `detach, det`
**Description**: Detach a subnet from the cloud connection.
**Usage**: 
```
detach CONNECTION_ID --subnet ID

  CONNECTION_ID: The unique identifier of the cloud connection.
```
**Available Flags**:
```
  -s, --subnet string   Subnet ID to detach from the cloud connection.
```

---

#### `ibmcloud pi cloud-connection update`
{: #ibmcloud-pi-cloud-connection-update}
**Alias**: `update, upd`
**Description**: Update the cloud connection.
**Usage**: 
```
update CONNECTION_ID [--classic [--gre-tunnel "CIDR DEST-IP"]] [--global-routing]
		[--metered] [--name NAME] [--speed SPEED] [--vpc [<--vpcIDs "VPC-ID">]]

  CONNECTION_ID: The unique identifier of the cloud connection.
```
**Available Flags**:
```
  -c, --classic             Enable "Classic" cloud connection endpoint.
  -g, --global-routing      Global routing flag.
  -t, --gre-tunnel string   Space separated "cidr" and "destinationIPAddress". Use with "--classic" option. GRE tunnel cannot be configured with speeds above 5000.
  -m, --metered             Metered cloud connection flag.
  -n, --name string         Name of the cloud connection.
  -s, --speed int           New speed value for the cloud connection. Allowed values are 50, 100, 200, 500, 1000, 2000, 5000. Speeds currently at 10000 cannot be downgraded lower and speeds cannot be increased to 10000.
  -v, --vpc                 Enable "VPC" cloud connection endpoint.
  -p, --vpcIDs strings      VPC ID (i.e. crn:v1:..) to add to cloud connection. Use with "--vpc" option.
```

---

### `ibmcloud pi datacenter`
{: #ibmcloud-pi-datacenter}
**Alias**: `datacenter, dat`
**Description**: IBM Cloud Power Virtual Server Datacenters.
**Usage**: `datacenter`
**Available Commands**:
- `get`:    View details of a datacenter.
- `list`:    List all datacenter details.

---

#### `ibmcloud pi datacenter get`
{: #ibmcloud-pi-datacenter-get}
**Alias**: `get`
**Description**: View details of a datacenter.
**Usage**: 
```
get DATACENTER

  DATACENTER: The name of the datacenter
```

---

#### `ibmcloud pi datacenter list`
{: #ibmcloud-pi-datacenter-list}
**Alias**: `list, ls`
**Description**: List all datacenter details.
**Usage**: `list [--long]`
**Available Flags**:
```
  -l, --long   Retrieve additional details for datacenters.
```

---

### `ibmcloud pi disaster-recovery`
{: #ibmcloud-pi-disaster-recovery}
**Alias**: `disaster-recovery, drl`
**Description**: List disaster recovery locations for the current region or all regions.
**Usage**: `disaster-recovery [--all-regions]`
**Available Flags**:
```
  -a, --all-regions   List disaster recovery locations for all regions.
```

---

### `ibmcloud pi ike-policy`
{: #ibmcloud-pi-ike-policy}
**Alias**: `ike-policy, ike`
**Description**: IBM Cloud Power Virtual Server Internet Key Exchange policies.
**Usage**: `ike-policy`
**Available Commands**:
- `create`:    Create a VPN IKE policy.
- `delete`:    Delete a VPN IKE policy.
- `get`:    View details of a VPN IKE policy.
- `list`:    List all VPN IKE policies.
- `update`:    Update a VPN IKE policy.

---

#### `ibmcloud pi ike-policy create`
{: #ibmcloud-pi-ike-policy-create}
**Alias**: `create, cr`
**Description**: Create a VPN IKE policy.
**Usage**: 
```
create IKE_POLICY_NAME --version VERSION --authentication AUTHENTICATION --encryption ENCRYPTION --dh-group DH_GROUP --preshared-key KEY --key-lifetime SECONDS

  IKE_POLICY_NAME: A unique name of the VPN IKE policy. The maximum name length is 47 characters.
```
**Available Flags**:
```
  -a, --authentication string   Authentication algorithm of the IKE policy. Valid values are 'sha-256', 'sha-384', 'sha1', 'none'.
  -d, --dh-group int            DH group number of the IKE policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
  -e, --encryption string       Encryption algorithm of the IKE policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
  -k, --key-lifetime int        Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
  -p, --preshared-key string    Preshared key used in this VPN connection. The key length must be even.
  -v, --version int             Version number of the IKE policy. Valid values are '2', '1'.
```

---

#### `ibmcloud pi ike-policy delete`
{: #ibmcloud-pi-ike-policy-delete}
**Alias**: `delete, del`
**Description**: Delete a VPN IKE policy.
**Usage**: 
```
delete IKE_POLICY_ID

  IKE_POLICY_ID: The unique identifier of the VPN IKE policy.
```

---

#### `ibmcloud pi ike-policy get`
{: #ibmcloud-pi-ike-policy-get}
**Alias**: `get`
**Description**: View details of a VPN IKE policy.
**Usage**: 
```
get IKE_POLICY_ID

  IKE_POLICY_ID: The unique identifier of the VPN IKE policy.
```

---

#### `ibmcloud pi ike-policy list`
{: #ibmcloud-pi-ike-policy-list}
**Alias**: `list, ls`
**Description**: List all VPN IKE policies.
**Usage**: `list`

---

#### `ibmcloud pi ike-policy update`
{: #ibmcloud-pi-ike-policy-update}
**Alias**: `update, upd`
**Description**: Update a VPN IKE policy.
**Usage**: 
```
update IKE_POLICY_ID [--name NEW_NAME] [--version VERSION] [--authentication AUTHENTICATION] [--encryption ENCRYPTION] [--dh-group DH_GROUP] [--preshared-key KEY] [--key-lifetime SECONDS]

  IKE_POLICY_ID: The unique identifier of the VPN IKE policy.
```
**Available Flags**:
```
  -a, --authentication string   Authentication algorithm of the IKE policy. Valid values are 'sha-256', 'sha-384', 'sha1', 'none'.
  -d, --dh-group int            DH group number of the IKE policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
  -e, --encryption string       Encryption algorithm of the IKE policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
  -k, --key-lifetime int        Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
  -n, --name string             New unique name of the IKE Policy. The maximum name length is 47 characters.
  -p, --preshared-key string    Preshared key used in this VPN connection. The key length must be even.
  -v, --version int             Version number of the IKE policy. Valid values are '2', '1'.
```

---

### `ibmcloud pi image`
{: #ibmcloud-pi-image}
**Alias**: `image, img`
**Description**: IBM Cloud Power Virtual Server Images.
**Usage**: `image`
**Available Commands**:
- `create`:    Create a copy of an available stock image into this account; stock image names cannot be changed.
- `delete`:    Delete an image.
- `export`:    Export an image to IBM Cloud Object Storage.
- `export-show`:    View details of the last image export job.
- `get`:    View details of an image.
- `import`:    Import an image to IBM Cloud Object Storage.
- `import-show`:    View details of the last image import job.
- `list`:    List all images in a workspace.
- `list-catalog`:    List images available in the regional image catalog.

---

#### `ibmcloud pi image create`
{: #ibmcloud-pi-image-create}
**Alias**: `create, cr`
**Description**: Create a copy of an available stock image into this account; stock image names cannot be changed.
**Usage**: 
```
create IMAGE_ID

  IMAGE_ID: The unique identifier or name of the image
```

---

#### `ibmcloud pi image delete`
{: #ibmcloud-pi-image-delete}
**Alias**: `delete, del`
**Description**: Delete an image.
**Usage**: 
```
delete IMAGE_ID

  IMAGE_ID: The unique identifier or name of the image
```

---

#### `ibmcloud pi image export`
{: #ibmcloud-pi-image-export}
**Alias**: `export, ex`
**Description**: Export an image to IBM Cloud Object Storage.
**Usage**: 
```
export IMAGE_ID --bucket BUCKET_NAME --region REGION_NAME --access-key KEY --secret-key KEY

  IMAGE_ID: The unique identifier or name of the image
```
**Available Flags**:
```
  -a, --access-key string   Cloud Object Storage HMAC access key.
  -b, --bucket string       Cloud Object Storage bucket name.
  -r, --region string       Cloud Object Storage region (au-syd, br-sao, ca-tor, eu-de, eu-gb, jp-osa, jp-tok, us-east, us-south).
  -s, --secret-key string   Cloud Object Storage HMAC secret key.
```

---

#### `ibmcloud pi image export-show`
{: #ibmcloud-pi-image-export-show}
**Alias**: `export-show, exs`
**Description**: View details of the last image export job.
**Usage**: 
```
export-show IMAGE_ID

  IMAGE_ID: The unique identifier or name of the image
```

---

#### `ibmcloud pi image get`
{: #ibmcloud-pi-image-get}
**Alias**: `get`
**Description**: View details of an image.
**Usage**: 
```
get IMAGE_ID

  IMAGE_ID: The unique identifier or name of the image
```

---

#### `ibmcloud pi image import`
{: #ibmcloud-pi-image-import}
**Alias**: `import, im`
**Description**: Import an image to IBM Cloud Object Storage.
**Usage**: 
```
import IMAGE_NAME [--bucket-access private] [--storage-tier STORAGE_TIER] [--os-type OSTYPE] --access-key KEY --secret-key KEY --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME
  pi image import IMAGE_NAME [--bucket-access private] [--storage-tier STORAGE_TIER] --storage-pool POOL [--os-type OSTYPE] --access-key KEY --secret-key KEY --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME
  pi image import IMAGE_NAME [--bucket-access private] [--storage-tier STORAGE_TIER] --affinity-policy affinity (--affinity-instance INSTANCE | --affinity-volume VOLUME) [--os-type OSTYPE] --access-key KEY --secret-key KEY --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME
  pi image import IMAGE_NAME [--bucket-access private] [--storage-tier STORAGE_TIER] --affinity-policy anti-affinity (--anti-affinity-instances "INSTANCE1 [INSTANCEn]" | --anti-affinity-volumes "VOLUME1 [VOLUMEn]") [--os-type OSTYPE] --access-key KEY --secret-key KEY --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME
  pi image import IMAGE_NAME --bucket-access public [--storage-tier STORAGE_TIER] [--os-type OSTYPE] --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME
  pi image import IMAGE_NAME --bucket-access public [--storage-tier STORAGE_TIER] --storage-pool POOL [--os-type OSTYPE] --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME
  pi image import IMAGE_NAME --bucket-access public [--storage-tier STORAGE_TIER] --affinity-policy affinity (--affinity-instance INSTANCE | --affinity-volume VOLUME) [--os-type OSTYPE] --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME
  pi image import IMAGE_NAME --bucket-access public [--storage-tier STORAGE_TIER] --affinity-policy anti-affinity (--anti-affinity-instances "INSTANCE1 [INSTANCEn]" | --anti-affinity-volumes "VOLUME1 [VOLUMEn]") [--os-type OSTYPE] --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME

  IMAGE_NAME: The desired name of the image
```
**Available Flags**:
```
  -k, --access-key string                 Cloud Object Storage HMAC access key.
  -i, --affinity-instance string          PVM instance identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-volume is not provided.
  -a, --affinity-policy string            Affinity policy for data volume being created. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this cannot be specified.
  -v, --affinity-volume string            Volume identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-instance is not provided.
  -j, --anti-affinity-instances strings   Comma separated list of instance identifiers or names to base volume anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified and --anti-affinity-volumes is not provided.
  -w, --anti-affinity-volumes strings     Comma separated list of volume identifiers or names to base volume anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified  and --anti-affinity-instances is not provided.
  -b, --bucket string                     Cloud Object Storage bucket name.
  -u, --bucket-access string              Indicates the bucket access type (private or public). Private access requires access and secret keys. Public access requires the --job option. Default is private. (default "private")
  -n, --image-file-name string            The image file name.
  -o, --os-type string                    Operating system contained in the image (rhel, sles, aix, ibmi). Required when importing a raw image.
  -r, --region string                     Cloud Object Storage region (au-syd, br-sao, ca-tor, eu-de, eu-gb, jp-osa, jp-tok, us-east, us-south).
  -s, --secret-key string                 Cloud Object Storage HMAC secret key.
  -p, --storage-pool string               Storage pool where the image will be imported to (use "ibmcloud pi storage-pools" to see available storage pools). If --storage-pool is provided then --affinity-policy cannot be specified.
  -t, --storage-tier string               Tier of the disk storage (use "ibmcloud pi storage-tiers" to see available tiers in the targeted region). Default to tier3 if not provided.
```

---

#### `ibmcloud pi image import-show`
{: #ibmcloud-pi-image-import-show}
**Alias**: `import-show, ims`
**Description**: View details of the last image import job.
**Usage**: `import-show`

---

#### `ibmcloud pi image list`
{: #ibmcloud-pi-image-list}
**Alias**: `list, ls`
**Description**: List all images in a workspace.
**Usage**: `list`

---

#### `ibmcloud pi image list-catalog`
{: #ibmcloud-pi-image-list-catalog}
**Alias**: `list-catalog, lc`
**Description**: List images available in the regional image catalog.
**Usage**: `list-catalog [--sap] [--vtl]`
**Available Flags**:
```
  -s, --sap   Include SAP images.
  -v, --vtl   Include VTL images.
```

---

### `ibmcloud pi instance`
{: #ibmcloud-pi-instance}
**Alias**: `instance, ins`
**Description**: IBM Cloud Power Virtual Server Instances.
**Usage**: `instance`
**Available Commands**:
- `action`:    Perform an operation in a PVM server instance.
- `capture`:    IBM Cloud Power Virtual Server Instance Capture.
- `console`:    IBM Cloud Power Virtual Server Instance Console.
- `create`:    Create a server instance.
- `delete`:    Delete a server instance.
- `get`:    View details of a server instance.
- `list`:    List all server instances.
- `operation`:    Perform an operation on an IBMi server instance.
- `sap`:    IBM Cloud Power Virtual Server Instance SAP.
- `snapshot`:    IBM Cloud Power Virtual Server Instance Snapshots.
- `subnet`:    IBM Cloud Power Virtual Server Instance Subnets.
- `update`:    Update a server instance.
- `volume`:    IBM Cloud Power Virtual Server Instance Volumes.

---

#### `ibmcloud pi instance action`
{: #ibmcloud-pi-instance-action}
**Alias**: `action, act`
**Description**: Perform an operation in a PVM server instance.
**Usage**: 
```
action INSTANCE_ID --operation op

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -o, --operation string   Operation to be done in a PVM server instance. Valid values are "hard-reboot", "immediate-shutdown", "reset-state", "soft-reboot", "start", and "stop".
```

---

#### `ibmcloud pi instance capture`
{: #ibmcloud-pi-instance-capture}
**Alias**: `capture, cap`
**Description**: IBM Cloud Power Virtual Server Instance Capture.
**Usage**: `capture`
**Available Commands**:
- `create`:    Create a capture of a server instance.
- `show`:    View the job details of the last server instance capture.

---

##### `ibmcloud pi instance capture create`
{: #ibmcloud-pi-instance-capture-create}
**Alias**: `create, cr`
**Description**: Create a capture of a server instance.
**Usage**: 
```
create INSTANCE_ID --destination DEST --name NAME [--volumes VOLUME1,VOLUMEn] [--access-key KEY] [--image-path PATH] [--region REGION] [--secret-key KEY]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -a, --access-key string    Cloud Object Storage HMAC access key. Required if destination is cloud-storage.
  -d, --destination string   Destination for the deployable image (image-catalog, cloud-storage, both).
  -i, --image-path string    Cloud Object Storage image path. Required if destination is cloud-storage. E.g. bucket-name[/optional/folder].
  -n, --name string          Name of the deployable image created for the captured instance.
  -r, --region string        Cloud Object Storage region (us-south, us-east, eu-gb, eu-de, au-syd, jp-tok, jp-osa, ca-tor, br-sao). Required if destination is cloud-storage.
  -s, --secret-key string    Cloud Object Storage HMAC secret key. Required if destination is cloud-storage.
  -v, --volumes strings      Comma separated list of volume identifiers or names to associate with the instance.
```

---

##### `ibmcloud pi instance capture show`
{: #ibmcloud-pi-instance-capture-show}
**Alias**: `show, sh`
**Description**: View the job details of the last server instance capture.
**Usage**: 
```
show INSTANCE_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```

---

#### `ibmcloud pi instance console`
{: #ibmcloud-pi-instance-console}
**Alias**: `console, con`
**Description**: IBM Cloud Power Virtual Server Instance Console.
**Usage**: `console`
**Available Commands**:
- `get`:    Get the console of an instance.
- `list`:    List the available console languages for an instance.
- `update`:    Update the console language of an instance. This update may take some time to take affect.

---

##### `ibmcloud pi instance console get`
{: #ibmcloud-pi-instance-console-get}
**Alias**: `get`
**Description**: Get the console of an instance.
**Usage**: 
```
get INSTANCE_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```

---

##### `ibmcloud pi instance console list`
{: #ibmcloud-pi-instance-console-list}
**Alias**: `list, ls`
**Description**: List the available console languages for an instance.
**Usage**: 
```
list INSTANCE_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```

---

##### `ibmcloud pi instance console update`
{: #ibmcloud-pi-instance-console-update}
**Alias**: `update, upd`
**Description**: Update the console language of an instance. This update may take some time to take affect.
**Usage**: 
```
update INSTANCE_ID --code CODE

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -c, --code string   Language code to set. Use 'ibmcloud pi instance console list' to see available codes.
```

---

#### `ibmcloud pi instance create`
{: #ibmcloud-pi-instance-create}
**Alias**: `create, cr`
**Description**: Create a server instance.
**Usage**: 
```
create INSTANCE_NAME --image IMAGE --subnets "SUBNET1 [IP1]"[,"SUBNETn [IPn]"]
		[--memory MEMORY] [--processors PROCESSORS] [--processor-type PROC_TYPE] [--volumes VOLUME1[,VOLUMEn]]
		[--key-name NAME] [--sys-type TYPE] [--storage-connection STORAGE_CONNECTION] [--storage-pool STORAGE_POOL]
		[--storage-affinity STORAGE_AFFINITY_POLICY] [--storage-affinity-instance INSTANCE] [--storage-affinity-volume VOLUME]
		[--storage-anti-affinity-instances INSTANCE1[,INSTANCEn]] [--storage-anti-affinity-volumes VOLUME1[,VOLUMEn]]
		[--replicants NUMBER] [--replicant-scheme SCHEME] [--replicant-affinity-policy AFFINITY_POLICY] [--pin-policy POLICY]
		[--IBMiCSS-license] [--IBMiPHA-license] [--IBMiRDS-users NUMBER-USERS] [--placement-group GROUP_ID]
		[--shared-processor-pool SHARED_PROCESSOR_POOL] [--deployment-type TYPE] [--storage-tier STORAGE_TIER] [--user-data USER_DATA]

  INSTANCE_NAME: The name of the instance.
```
**Available Flags**:
```
      --IBMiCSS-license                           IBMi CSS software license associated with the instance.
      --IBMiPHA-license                           IBMi PHA software license associated with the instance.
      --IBMiRDS-users int                         Number of IBMi RDS users software license associated with the instance, default IBMiRDSUsers=0 (no license).
      --deployment-type string                    The custom deployment type ("EPIC" or "VMNoStorage").
  -i, --image string                              Operating system image identifier or name.
  -k, --key-name string                           Name of SSH key.
  -m, --memory float                              Amount of memory (in GB) to allocate to the instance. Default is 2GB. (default 2)
      --pin-policy string                         Pin policy ("none", "soft", "hard"). Default is "none".
      --placement-group string                    The placement group ID of the group that the server will be added to.
  -r, --processor-type string                     Type of processors: "shared" or "dedicated" or "capped". Default is "dedicated". (default "dedicated")
  -p, --processors float                          Amount of processors to allocate to the instance. Default is 1 core. (default 1)
      --replicant-affinity-policy string          Affinity policy to use when multicreate is used ("affinity", "anti-affinity")
      --replicant-scheme string                   Naming scheme to use for duplicate VMs ("suffix", "prefix").
      --replicants float                          Number of duplicate instances to create in this request.
      --shared-processor-pool string              The shared processor pool ID of the pool that the server will be in.
      --storage-affinity string                   Affinity policy for storage pool selection. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided, then this it cannot be specified.
      --storage-affinity-instance string          PVM instance identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-volume is not provided.
      --storage-affinity-volume string            Volume identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-instance is not provided.
      --storage-anti-affinity-instances strings   Comma separated list of PVM instance identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-volumes is not provided.
      --storage-anti-affinity-volumes strings     Comma separated list of volume identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-instances is not provided.
      --storage-connection string                 The storage connection type. Valid value is "vSCSI".
      --storage-pool string                       Storage pool for server deployment (use "ibmcloud pi storage-pools" to see available storage pools). Only valid when you deploy one of the IBM supplied stock images. Storage tier and pool for a custom image (an imported image or an image that is created from a PVMInstance capture) defaults to the storage tier and pool the image was created in.
  -t, --storage-tier string                       Storage tier for server deployment when deploying a stock or custom image (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region). Default to tier3 if not provided.
  -n, --subnets strings                           Comma separated list of subnet identifiers or names and optional IP address to associate with the instance.
  -s, --sys-type string                           Name of System Type ('s922', 's1022', 'e980', 'e1080'). Default is "s922". (default "s922")
      --user-data string                          The user data passed into the instance.
  -v, --volumes strings                           Comma separated list of volume identifiers or names to associate with the instance.
```

---

#### `ibmcloud pi instance delete`
{: #ibmcloud-pi-instance-delete}
**Alias**: `delete, del`
**Description**: Delete a server instance.
**Usage**: 
```
delete INSTANCE_ID [--delete-data-volumes]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -d, --delete-data-volumes   Indicates whether all data volumes attached to the instance must be deleted. Shared data volumes will be deleted if no other instances are attached.
```

---

#### `ibmcloud pi instance get`
{: #ibmcloud-pi-instance-get}
**Alias**: `get`
**Description**: View details of a server instance.
**Usage**: 
```
get INSTANCE_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```

---

#### `ibmcloud pi instance list`
{: #ibmcloud-pi-instance-list}
**Alias**: `list, ls`
**Description**: List all server instances.
**Usage**: `list`

---

#### `ibmcloud pi instance operation`
{: #ibmcloud-pi-instance-operation}
**Alias**: `operation, op`
**Description**: Perform an operation on an IBMi server instance.
**Usage**: 
```
operation INSTANCE_ID --operation-type TYPE [--boot-mode MODE] [--boot-operating-mode MODE] [--job-task TASK]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -b, --boot-mode string             Name of the server boot mode; allowable values are "a", "b", "c", and "d".
  -m, --boot-operating-mode string   Name of the server operating mode; allowable values are "normal" and "manual".
  -j, --job-task string              Name of the job task to execute; allowable values are "dston", "retrydump", "consoleservice", "iopreset", "remotedstoff", "remotedston", "iopdump", and "dumprestart".
  -o, --operation-type string        Name of the operation to execute; allowable values are "job" and "boot".
```

---

#### `ibmcloud pi instance sap`
{: #ibmcloud-pi-instance-sap}
**Alias**: `sap`
**Description**: IBM Cloud Power Virtual Server Instance SAP.
**Usage**: `sap`
**Available Commands**:
- `create`:    Create a new SAP PVM Instance. This command is for use with Linux for SAP (HANA) images.
- `list`:    List all SAP profiles for the targeted region.
- `profile`:    Get the information on a SAP profile.

---

##### `ibmcloud pi instance sap create`
{: #ibmcloud-pi-instance-sap-create}
**Alias**: `create, cr`
**Description**: Create a new SAP PVM Instance. This command is for use with Linux for SAP (HANA) images.
**Usage**: 
```
create SAP_INSTANCE_NAME --image IMAGE --profile-id PROFILE_ID --subnets "SUBNET1 [IP1]"[,"SUBNETn [IPn]"]
		[--storage-tier STORAGE_TIER] [--pin-policy POLICY] [--volumes VOLUME1[,VOLUMEn]] [--storage-pool STORAGE_POOL]
		[--storage-affinity STORAGE_AFFINITY_POLICY] [--storage-affinity-instance INSTANCE] [--storage-affinity-volume VOLUME]
		[--storage-anti-affinity-instances INSTANCE1[,INSTANCEn]] [--storage-anti-affinity-volumes VOLUME1[,VOLUMEn]]
		[--key-name KEY-NAME] [--sys-type TYPE] [--placement-group PLACEMENT_GROUP_ID]

  SAP_INSTANCE_NAME: The name of the SAP instance.
```
**Available Flags**:
```
  -i, --image string                              Operating system image identifier or name.
  -k, --key-name string                           Name of SSH key.
      --pin-policy string                         Pin policy ("none", "soft", "hard"). Default is "none".
      --placement-group string                    The placement group ID of the group that the server will be added to.
  -p, --profile-id string                         The unique identifier of the SAP profile.
      --storage-affinity string                   Affinity policy for storage pool selection. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided, then this it cannot be specified.
      --storage-affinity-instance string          PVM instance identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-volume is not provided.
      --storage-affinity-volume string            Volume identifier or name to base storage affinity policy against; required if "--storage-affinity affinity" is specified and --storage-affinity-instance is not provided.
      --storage-anti-affinity-instances strings   Comma separated list of PVM instance identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-volumes is not provided.
      --storage-anti-affinity-volumes strings     Comma separated list of volume identifiers or names to base storage affinity policy against; required if "--storage-affinity anti-affinity" is specified and --storage-anti-affinity-instances is not provided.
      --storage-pool string                       Storage pool for SAP PVM instance deployment. Only valid when you deploy one of the IBM supplied stock images.
  -t, --storage-tier string                       Storage tiers for SAP PVM instance deployment when deploying a stock or custom image (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region). Default to tier3 if not provided.
  -n, --subnets strings                           Comma separated list of subnet identifiers or names and optional IP address to associate with the instance.
  -s, --sys-type string                           Name of system type ('e880', 'e980', 'e1080'). Default is "e980". (default "e980")
  -v, --volumes strings                           Comma separated list of volume identifiers or names to associate with the instance.
```

---

##### `ibmcloud pi instance sap list`
{: #ibmcloud-pi-instance-sap-list}
**Alias**: `list, ls`
**Description**: List all SAP profiles for the targeted region.
**Usage**: `list`

---

##### `ibmcloud pi instance sap profile`
{: #ibmcloud-pi-instance-sap-profile}
**Alias**: `profile, prof`
**Description**: Get the information on a SAP profile.
**Usage**: 
```
profile SAP_PROFILE_ID

  SAP_INSTANCE_NAME: The name of the SAP instance.
```

---

#### `ibmcloud pi instance snapshot`
{: #ibmcloud-pi-instance-snapshot}
**Alias**: `snapshot, snap`
**Description**: IBM Cloud Power Virtual Server Instance Snapshots.
**Usage**: `snapshot`
**Available Commands**:
- `list`:    List all snapshots for an instance.

---

##### `ibmcloud pi instance snapshot list`
{: #ibmcloud-pi-instance-snapshot-list}
**Alias**: `list, ls`
**Description**: List all snapshots for an instance.
**Usage**: 
```
list INSTANCE_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```

---

#### `ibmcloud pi instance subnet`
{: #ibmcloud-pi-instance-subnet}
**Alias**: `subnet, snet`
**Description**: IBM Cloud Power Virtual Server Instance Subnets.
**Usage**: `subnet`
**Available Commands**:
- `attach`:    Attach a subnet to the server instance.
- `detach`:    Detach a specific subnet or mac address from the server instance.
- `list`:    List all the attached subnets.

---

##### `ibmcloud pi instance subnet attach`
{: #ibmcloud-pi-instance-subnet-attach}
**Alias**: `attach, att`
**Description**: Attach a subnet to the server instance.
**Usage**: 
```
attach INSTANCE_ID --subnet "SUBNET_ID" [--ip-address "IP_ADDRESS"]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -i, --ip-address string   The requested ip address of this subnet interface.
  -n, --subnet string       The subnet ID.
```

---

##### `ibmcloud pi instance subnet detach`
{: #ibmcloud-pi-instance-subnet-detach}
**Alias**: `detach, det`
**Description**: Detach a specific subnet or mac address from the server instance.
**Usage**: 
```
detach INSTANCE_ID --subnet "SUBNET_ID" [--mac-address "MAC_ADDRESS"]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -m, --mac-address string   The mac address of the subnet interface to be removed. The default is all mac addresses.
  -n, --subnet string        The subnet ID.
```

---

##### `ibmcloud pi instance subnet list`
{: #ibmcloud-pi-instance-subnet-list}
**Alias**: `list, ls`
**Description**: List all the attached subnets.
**Usage**: 
```
list INSTANCE_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```

---

#### `ibmcloud pi instance update`
{: #ibmcloud-pi-instance-update}
**Alias**: `update, upd`
**Description**: Update a server instance.
**Usage**: 
```
update INSTANCE_ID [--memory AMOUNT] [--name NEW_NAME] [--pin-policy POLICY] [--processors NUMBER] [--processor-type TYPE] [--profile-id SAP_PROFILE_ID] [--storage-pool-affinity=True|False]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -m, --memory float                    New amount of memory for the server instance.
  -n, --name string                     New name of the server instance.
      --pin-policy string               New pin policy for the server instance ("none", "soft", "hard").
      --processor-type string           New processor type for the server instance.
      --processors float                New amount of processors for the server instance.
      --profile-id string               SAP profile ID.
      --storage-pool-affinity           Indicates if all volumes attached to the server must reside in the same storage pool. If set to false, then volumes from any storage tier and pool can be attached to the PVM instance; This impacts PVM instance snapshot, capture, and clone. For capture and clone only data volumes that are of the same storage tier and in the same storage pool of the PVM instance's boot volume can be included. For snapshot all data volumes to be included in the snapshot must reside in the same storage tier and pool. Once set to false, cannot be set back to true unless all volumes attached reside in the same storage tier and pool.
      --virtual-optical-device string   Attach or Detach a Virtual Optical Device to this instance. Valid values are "attach" and "detach".
```

---

#### `ibmcloud pi instance volume`
{: #ibmcloud-pi-instance-volume}
**Alias**: `volume, vol`
**Description**: IBM Cloud Power Virtual Server Instance Volumes.
**Usage**: `volume`
**Available Commands**:
- `attach`:    Attach one or more volumes to an instance.
- `detach`:    Detach a volume from an instance.
- `list`:    List all the attached volumes.

---

##### `ibmcloud pi instance volume attach`
{: #ibmcloud-pi-instance-volume-attach}
**Alias**: `attach, att`
**Description**: Attach one or more volumes to an instance.
**Usage**: 
```
attach INSTANCE_ID --volumes VOLUME1[,VOLUMEn]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -v, --volumes strings   Comma separated list of volume identifiers or names to associate with the instance.
```

---

##### `ibmcloud pi instance volume detach`
{: #ibmcloud-pi-instance-volume-detach}
**Alias**: `detach, det`
**Description**: Detach a volume from an instance.
**Usage**: 
```
detach INSTANCE_ID --volume VOLUME_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -v, --volume string   Volume to detach from the instance.
```

---

##### `ibmcloud pi instance volume list`
{: #ibmcloud-pi-instance-volume-list}
**Alias**: `list, ls`
**Description**: List all the attached volumes.
**Usage**: 
```
list INSTANCE_ID

  INSTANCE_ID: The unique identifier or name of the instance.
```

---

### `ibmcloud pi ipsec-policy`
{: #ibmcloud-pi-ipsec-policy}
**Alias**: `ipsec-policy, ips`
**Description**: IBM Cloud Power Virtual Server Internet Protocol Security policies.
**Usage**: `ipsec-policy`
**Available Commands**:
- `create`:    Create a VPN IPSec policy.
- `delete`:    Delete a VPN IPSec policy.
- `get`:    View details of a VPN IPSec policy.
- `list`:    List all IPSec policies.
- `update`:    Update a VPN IPSec policy.

---

#### `ibmcloud pi ipsec-policy create`
{: #ibmcloud-pi-ipsec-policy-create}
**Alias**: `create, cr`
**Description**: Create a VPN IPSec policy.
**Usage**: 
```
create IPSEC_POLICY_NAME --authentication AUTHENTICATION --dh-group DH_GROUP --encryption ENCRYPTION --key-lifetime SECONDS [--pfs]

  IPSEC_POLICY_NAME: A unique name of the VPN IPSec policy. The maximum name length is 47 characters.
```
**Available Flags**:
```
  -a, --authentication string   Authentication encryption type of the IPSec policy. Valid values are 'hmac-sha-256-128', 'hmac-sha1-96', 'none'.
  -d, --dh-group int            DH group number of the IPSec policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
  -e, --encryption string       Connection encryption policy of the IPSec policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-192-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm', 'aes-192-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
  -k, --key-lifetime int        Key lifetime of the IPSec policy in seconds. Valid range is 180 to 86400 seconds.
  -p, --pfs                     Enable perfect forward secrecy. Disabled if not specified.
```

---

#### `ibmcloud pi ipsec-policy delete`
{: #ibmcloud-pi-ipsec-policy-delete}
**Alias**: `delete, del`
**Description**: Delete a VPN IPSec policy.
**Usage**: 
```
delete IPSEC_POLICY_ID

  IPSEC_POLICY_ID: The unique identifier of the VPN IPSec policy.
```

---

#### `ibmcloud pi ipsec-policy get`
{: #ibmcloud-pi-ipsec-policy-get}
**Alias**: `get`
**Description**: View details of a VPN IPSec policy.
**Usage**: 
```
get IPSEC_POLICY_ID

  IPSEC_POLICY_ID: The unique identifier of the VPN IPSec policy.
```

---

#### `ibmcloud pi ipsec-policy list`
{: #ibmcloud-pi-ipsec-policy-list}
**Alias**: `list, ls`
**Description**: List all IPSec policies.
**Usage**: `list`

---

#### `ibmcloud pi ipsec-policy update`
{: #ibmcloud-pi-ipsec-policy-update}
**Alias**: `update, upd`
**Description**: Update a VPN IPSec policy.
**Usage**: 
```
update IPSEC_POLICY_ID  [--name NEW_NAME] [--authentication AUTHENTICATION] [--encryption ENCRYPTION] [--dh-group DH_GROUP] [--key-lifetime SECONDS] [--pfs=True|False]]

  IPSEC_POLICY_ID: The unique identifier of the VPN IPSec policy.
```
**Available Flags**:
```
  -a, --authentication string   Authentication encryption type of the IPSec policy. Valid values are 'hmac-sha-256-128', 'hmac-sha1-96', 'none'.
  -d, --dh-group int            DH group number of the IPSec policy. Valid values are '2', '14', '19', '20', '24', '5', '1'.
  -e, --encryption string       Connection encryption policy of the IPSec policy. Valid values are 'aes-256-cbc', 'aes-192-cbc', 'aes-128-cbc', 'aes-256-gcm', 'aes-192-gcm', 'aes-128-gcm', '3des-cbc'. When using 'aes-128-gcm', 'aes-192-gcm' or 'aes-256-gcm' authentication should be set to 'none'.
  -k, --key-lifetime int        Key lifetime of the IPSec policy in seconds. Valid range is 180 to 86400 seconds.
  -n, --name string             New unique name of the IPSec policy. The maximum name length is 47 characters.
  -p, --pfs                     Enable perfect forward secrecy. Disabled if not specified.
```

---

### `ibmcloud pi job`
{: #ibmcloud-pi-job}
**Alias**: `job`
**Description**: IBM Cloud Power Virtual Server Jobs.
**Usage**: `job`
**Available Commands**:
- `delete`:    Delete a job.
- `get`:    View details of a job.
- `list`:    List all jobs in a workspace.

---

#### `ibmcloud pi job delete`
{: #ibmcloud-pi-job-delete}
**Alias**: `delete, del`
**Description**: Delete a job.
**Usage**: 
```
delete JOB_ID

  JOB_ID: The unique identifier of the job.
```

---

#### `ibmcloud pi job get`
{: #ibmcloud-pi-job-get}
**Alias**: `get`
**Description**: View details of a job.
**Usage**: 
```
get JOB_ID

  JOB_ID: The unique identifier of the job.
```

---

#### `ibmcloud pi job list`
{: #ibmcloud-pi-job-list}
**Alias**: `list, ls`
**Description**: List all jobs in a workspace.
**Usage**: `list [--operation-action ACTION] [--operation-id ID] [--operation-target TARGET]`
**Available Flags**:
```
  -a, --operation-action string   Operation action to filter returned jobs. Valid values are vmCapture, imageExport, imageImport, storage.
  -i, --operation-id string       Operation ID to filter returned jobs.
  -t, --operation-target string   Operation target to filter returned jobs. Valid values are cloudConnection, pvmInstance, image.
```

---

### `ibmcloud pi placement-group`
{: #ibmcloud-pi-placement-group}
**Alias**: `placement-group, pg`
**Description**: IBM Cloud Power Virtual Server Placement Groups.
**Usage**: `placement-group`
**Available Commands**:
- `create`:    Create a server placement group.
- `delete`:    Delete a server placement group.
- `get`:    View details of a server placement group.
- `list`:    List all server placement groups.
- `server-add`:    Add a server to the server placement group.
- `server-remove`:    Remove a server from a server placement group.

---

#### `ibmcloud pi placement-group create`
{: #ibmcloud-pi-placement-group-create}
**Alias**: `create, cr`
**Description**: Create a server placement group.
**Usage**: 
```
create PLACEMENT_GROUP_NAME --policy POLICY

  PLACEMENT_GROUP_NAME: A unique name of the placement group.
```
**Available Flags**:
```
  -p, --policy string   Affinity policy for placement group being created. Valid values are affinity and anti-affinity.
```

---

#### `ibmcloud pi placement-group delete`
{: #ibmcloud-pi-placement-group-delete}
**Alias**: `delete, del`
**Description**: Delete a server placement group.
**Usage**: 
```
delete PLACEMENT_GROUP_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```

---

#### `ibmcloud pi placement-group get`
{: #ibmcloud-pi-placement-group-get}
**Alias**: `get`
**Description**: View details of a server placement group.
**Usage**: 
```
get PLACEMENT_GROUP_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```

---

#### `ibmcloud pi placement-group list`
{: #ibmcloud-pi-placement-group-list}
**Alias**: `list, ls`
**Description**: List all server placement groups.
**Usage**: `list`

---

#### `ibmcloud pi placement-group server-add`
{: #ibmcloud-pi-placement-group-server-add}
**Alias**: `server-add, sa`
**Description**: Add a server to the server placement group.
**Usage**: 
```
server-add PLACEMENT_GROUP_ID --server INSTANCE_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```
**Available Flags**:
```
  -s, --server string   The server instance ID of the server to add to the placement group.
```

---

#### `ibmcloud pi placement-group server-remove`
{: #ibmcloud-pi-placement-group-server-remove}
**Alias**: `server-remove, sr`
**Description**: Remove a server from a server placement group.
**Usage**: 
```
server-remove PLACEMENT_GROUP_ID --server INSTANCE_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```
**Available Flags**:
```
  -s, --server string   The server instance ID of the server to add to the placement group.
```

---

### `ibmcloud pi shared-processor-pool`
{: #ibmcloud-pi-shared-processor-pool}
**Alias**: `shared-processor-pool, spp`
**Description**: IBM Cloud Power Virtual Shared Processor Pools.
**Usage**: `shared-processor-pool`
**Available Commands**:
- `create`:    Create a shared processor pool.
- `delete`:    Delete a shared processor pool.
- `get`:    View details of a shared processor pool.
- `list`:    List all shared processor pools.
- `placement-group`:    IBM Cloud Power Virtual Server Placement Groups.
- `update`:    Update a shared processor pool.

---

#### `ibmcloud pi shared-processor-pool create`
{: #ibmcloud-pi-shared-processor-pool-create}
**Alias**: `create, cr`
**Description**: Create a shared processor pool.
**Usage**: 
```
create SHARED_PROCESSOR_POOL_NAME --host-group HOST_GROUP --reserved-cores NUMBER_OF_CORES [--placement-group-id PLACEMENT_GROUP_ID]

  SHARED_PROCESSOR_POOL_NAME: A unique name of the shared processor pool. A minimum of 2 characters and a maximum of 12 are allowed. The only special character allowed is the underscore '_'.
```
**Available Flags**:
```
  -g, --host-group string           The host group where the host will be chosen if not provided. Valid values are: 's922', 's1022', 'e980', 'e1080'.
  -p, --placement-group-id string   The identifier of the shared processor pool placement group the pool will be added to.
  -r, --reserved-cores int          The integer amount of reserved processor cores for the shared processor pool.
```

---

#### `ibmcloud pi shared-processor-pool delete`
{: #ibmcloud-pi-shared-processor-pool-delete}
**Alias**: `delete, del`
**Description**: Delete a shared processor pool.
**Usage**: 
```
delete SHARED_PROCESSOR_POOL_ID

  SHARED_PROCESSOR_POOL_ID: The unique identifier or name of the shared processor pool.
```

---

#### `ibmcloud pi shared-processor-pool get`
{: #ibmcloud-pi-shared-processor-pool-get}
**Alias**: `get`
**Description**: View details of a shared processor pool.
**Usage**: 
```
get SHARED_PROCESSOR_POOL_ID

  SHARED_PROCESSOR_POOL_ID: The unique identifier or name of the shared processor pool.
```

---

#### `ibmcloud pi shared-processor-pool list`
{: #ibmcloud-pi-shared-processor-pool-list}
**Alias**: `list, ls`
**Description**: List all shared processor pools.
**Usage**: `list`

---

#### `ibmcloud pi shared-processor-pool placement-group`
{: #ibmcloud-pi-shared-processor-pool-placement-group}
**Alias**: `placement-group, pg`
**Description**: IBM Cloud Power Virtual Server Placement Groups.
**Usage**: `placement-group`
**Available Commands**:
- `create`:    Create a shared processor pool placement group.
- `delete`:    Delete a shared processor pool placement group.
- `get`:    View details of a shared processor pool placement group.
- `list`:    List all shared processor pool placement groups.
- `member-add`:    Add a shared processor pool to the placement group.
- `member-remove`:    Remove a shared processor pool to the placement group.

---

##### `ibmcloud pi shared-processor-pool placement-group create`
{: #ibmcloud-pi-shared-processor-pool-placement-group-create}
**Alias**: `create, cr`
**Description**: Create a shared processor pool placement group.
**Usage**: 
```
create PLACEMENT_GROUP_NAME --policy POLICY

  PLACEMENT_GROUP_NAME: A unique name of the placement group.
```
**Available Flags**:
```
  -p, --policy string   Affinity policy for placement group being created. Valid values are affinity and anti-affinity.
```

---

##### `ibmcloud pi shared-processor-pool placement-group delete`
{: #ibmcloud-pi-shared-processor-pool-placement-group-delete}
**Alias**: `delete, del`
**Description**: Delete a shared processor pool placement group.
**Usage**: 
```
delete PLACEMENT_GROUP_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```

---

##### `ibmcloud pi shared-processor-pool placement-group get`
{: #ibmcloud-pi-shared-processor-pool-placement-group-get}
**Alias**: `get`
**Description**: View details of a shared processor pool placement group.
**Usage**: 
```
get PLACEMENT_GROUP_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```

---

##### `ibmcloud pi shared-processor-pool placement-group list`
{: #ibmcloud-pi-shared-processor-pool-placement-group-list}
**Alias**: `list, ls`
**Description**: List all shared processor pool placement groups.
**Usage**: `list`

---

##### `ibmcloud pi shared-processor-pool placement-group member-add`
{: #ibmcloud-pi-shared-processor-pool-placement-group-member-add}
**Alias**: `member-add, ma`
**Description**: Add a shared processor pool to the placement group.
**Usage**: 
```
member-add PLACEMENT_GROUP_ID --shared-processor-pool POOL_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```
**Available Flags**:
```
  -s, --shared-processor-pool string   The shared processor pool ID of the pool to add to the placement group.
```

---

##### `ibmcloud pi shared-processor-pool placement-group member-remove`
{: #ibmcloud-pi-shared-processor-pool-placement-group-member-remove}
**Alias**: `member-remove, mr`
**Description**: Remove a shared processor pool to the placement group.
**Usage**: 
```
member-remove PLACEMENT_GROUP_ID --shared-processor-pool POOL_ID

  PLACEMENT_GROUP_ID: The unique identifier of the placement group.
```
**Available Flags**:
```
  -s, --shared-processor-pool string   The shared processor pool ID of the pool to remove from the placement group.
```

---

#### `ibmcloud pi shared-processor-pool update`
{: #ibmcloud-pi-shared-processor-pool-update}
**Alias**: `update, upd`
**Description**: Update a shared processor pool.
**Usage**: 
```
update SHARED_PROCESSOR_POOL_ID [--name SHARED_PROCESSOR_POOL_NAME] [--reserved-cores NUMBER_OF_CORES] 

  SHARED_PROCESSOR_POOL_ID: The unique identifier or name of the shared processor pool.
```
**Available Flags**:
```
  -n, --name string          New name of the shared processor pool. A minimum of 2 characters and a maximum of 12 are allowed. The only special character allowed is the underscore '_'.
  -r, --reserved-cores int   The integer amount of reserved processor cores for the shared processor pool.
```

---

### `ibmcloud pi snapshot`
{: #ibmcloud-pi-snapshot}
**Alias**: `snapshot, snap`
**Description**: IBM Cloud Power Virtual Server Snapshots.
**Usage**: `snapshot`
**Available Commands**:
- `create`:    Create a PVM instance snapshot.
- `delete`:    Delete a snapshot.
- `get`:    Get the detail of a snapshot.
- `list`:    List all snapshots.
- `restore`:    Restore a PVM instance snapshot.

---

#### `ibmcloud pi snapshot create`
{: #ibmcloud-pi-snapshot-create}
**Alias**: `create, cr`
**Description**: Create a PVM instance snapshot.
**Usage**: 
```
create INSTANCE_ID --name SNAPSHOT_NAME [--description DESCRIPTION] [--volumes VOLUME1[,VOLUMEn]]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -d, --description string   Snapshot description.
  -n, --name string          Name of the snapshot.
  -v, --volumes strings      Comma separated list
                             of volume identifiers or names to include in the PVM instance snapshot. This parameter is optional. If
                             you do not specify this parameter or if the volumes list is empty, all the volumes that are attached
                             to the PVM instance are included in the snapshot.
```

---

#### `ibmcloud pi snapshot delete`
{: #ibmcloud-pi-snapshot-delete}
**Alias**: `delete, del`
**Description**: Delete a snapshot.
**Usage**: 
```
delete SNAPSHOT_ID

  SNAPSHOT_ID: The unique identifier of the snapshot.
```

---

#### `ibmcloud pi snapshot get`
{: #ibmcloud-pi-snapshot-get}
**Alias**: `get`
**Description**: Get the detail of a snapshot.
**Usage**: 
```
get SNAPSHOT_ID

  SNAPSHOT_ID: The unique identifier of the snapshot.
```

---

#### `ibmcloud pi snapshot list`
{: #ibmcloud-pi-snapshot-list}
**Alias**: `list, ls`
**Description**: List all snapshots.
**Usage**: `list`

---

#### `ibmcloud pi snapshot restore`
{: #ibmcloud-pi-snapshot-restore}
**Alias**: `restore, res`
**Description**: Restore a PVM instance snapshot.
**Usage**: 
```
restore INSTANCE_ID --snapshot SNAPSHOT_ID [--force] [--restore VALUE]

  INSTANCE_ID: The unique identifier or name of the instance.
```
**Available Flags**:
```
  -f, --force             By default the VM must be shutoff during a snapshot restore, force set to true will relax the VM shutoff pre-condition.
  -r, --restore string    Action to take on a failed snapshot restore - allowable values: ["retry","rollback"].
  -s, --snapshot string   The unique identifier of the snapshot.
```

---

### `ibmcloud pi ssh-key`
{: #ibmcloud-pi-ssh-key}
**Alias**: `ssh-key, ssh`
**Description**: IBM Cloud Power Virtual Server SSH-Keys.
**Usage**: `ssh-key`
**Available Commands**:
- `create`:    Create an SSH-Key with an imported RSA public key.
- `delete`:    Delete an SSH-Key.
- `get`:    View details of an SSH-Key.
- `list`:    List all SSH-Keys.
- `update`:    Update the name and the value of an SSH-Key.

---

#### `ibmcloud pi ssh-key create`
{: #ibmcloud-pi-ssh-key-create}
**Alias**: `create, cr`
**Description**: Create an SSH-Key with an imported RSA public key.
**Usage**: 
```
create KEY_NAME --key KEY

  KEY_NAME: The name of the key.
```
**Available Flags**:
```
  -k, --key string   SSH RSA key string within a double quotation marks. For example, "ssh-rsa AAA... "
```

---

#### `ibmcloud pi ssh-key delete`
{: #ibmcloud-pi-ssh-key-delete}
**Alias**: `delete, del`
**Description**: Delete an SSH-Key.
**Usage**: 
```
delete KEY_NAME

  KEY_NAME: The name of the key.
```

---

#### `ibmcloud pi ssh-key get`
{: #ibmcloud-pi-ssh-key-get}
**Alias**: `get`
**Description**: View details of an SSH-Key.
**Usage**: 
```
get KEY_NAME

  KEY_NAME: The name of the key.
```

---

#### `ibmcloud pi ssh-key list`
{: #ibmcloud-pi-ssh-key-list}
**Alias**: `list, ls`
**Description**: List all SSH-Keys.
**Usage**: `list`

---

#### `ibmcloud pi ssh-key update`
{: #ibmcloud-pi-ssh-key-update}
**Alias**: `update, upd`
**Description**: Update the name and the value of an SSH-Key.
**Usage**: 
```
update KEY_NAME --new-name NEW_NAME --new-key NEW_KEY

  KEY_NAME: The name of the key.
```
**Available Flags**:
```
  -k, --new-key string    SSH RSA key string
  -n, --new-name string   SSH-Key name
```

---

### `ibmcloud pi storage-pools`
{: #ibmcloud-pi-storage-pools}
**Alias**: `storage-pools, spools`
**Description**: List all storage pools for the targeted region.
**Usage**: `storage-pools`

---

### `ibmcloud pi storage-tiers`
{: #ibmcloud-pi-storage-tiers}
**Alias**: `storage-tiers, stiers`
**Description**: List all storage tiers for the targeted region.
**Usage**: `storage-tiers`

---

### `ibmcloud pi subnet`
{: #ibmcloud-pi-subnet}
**Alias**: `subnet, snet`
**Description**: IBM Cloud Power Virtual Server Subnets.
**Usage**: `subnet`
**Available Commands**:
- `create`:    Create a subnet.
- `delete`:    Delete a subnet.
- `get`:    View details of a subnet.
- `list`:    List all subnets in a workspace.
- `update`:    Update a subnet.

---

#### `ibmcloud pi subnet create`
{: #ibmcloud-pi-subnet-create}
**Alias**: `create, cr`
**Description**: Create a subnet.
**Usage**: 
```
create SUBNET_NAME --cidr-block CIDR --net-type private [--dns-servers "DNS1,[DNSn]]"] [--gateway GATEWAY] [--ip-range "startIP-endIP[,startIP-endIP]"] [--jumbo]
  pi subnet create SUBNET_NAME --net-type public [--dns-servers "DNS1 DNS2"] [--jumbo]

  SUBNET_NAME: The name of the subnet.
```
**Available Flags**:
```
  -c, --cidr-block string     Subnet in CIDR notation (192.168.0.0/24).
  -d, --dns-servers strings   Comma separated list of DNS Servers to use for this subnet. 127.0.0.1 by default if DNS server is not specified for private subnet types. 9.9.9.9 by default for public subnet types.
  -g, --gateway string        Gateway to use for this subnet.
  -i, --ip-range string       IP Addresses range(s) for this subnet, format: startIP-endIP[,startIP-endIP].
  -j, --jumbo                 Enable MTU Jumbo Subnet. The default value is false.
  -n, --net-type string       Subnet type. Either "public" or "private".
```

---

#### `ibmcloud pi subnet delete`
{: #ibmcloud-pi-subnet-delete}
**Alias**: `delete, del`
**Description**: Delete a subnet.
**Usage**: 
```
delete SUBNET_ID

  SUBNET_ID: The unique identifier or name of the subnet.
```

---

#### `ibmcloud pi subnet get`
{: #ibmcloud-pi-subnet-get}
**Alias**: `get`
**Description**: View details of a subnet.
**Usage**: 
```
get SUBNET_ID

  SUBNET_ID: The unique identifier or name of the subnet.
```

---

#### `ibmcloud pi subnet list`
{: #ibmcloud-pi-subnet-list}
**Alias**: `list, ls`
**Description**: List all subnets in a workspace.
**Usage**: `list`

---

#### `ibmcloud pi subnet update`
{: #ibmcloud-pi-subnet-update}
**Alias**: `update, upd`
**Description**: Update a subnet.
**Usage**: 
```
update SUBNET_ID [--name SUBNET_NAME] [--ip-range "startIP-endIP[,startIP-endIP]"] [--dns-servers "DNS1,[DNSn]"] [--gateway GATEWAY]

  SUBNET_ID: The unique identifier or name of the subnet.
```
**Available Flags**:
```
  -d, --dns-servers strings   Comma separated list of DNS Servers to use for this subnet.
  -g, --gateway string        Gateway to use for this subnet.
  -i, --ip-range string       IP Addresses range(s) for this subnet, format: startIP-endIP[,startIP-endIP].
  -n, --name string           New name of the subnet.
```

---

### `ibmcloud pi system-pools`
{: #ibmcloud-pi-system-pools}
**Alias**: `system-pools, sysp`
**Description**: List of available system pools within a particular data center.
**Usage**: `system-pools`

---

### `ibmcloud pi volume`
{: #ibmcloud-pi-volume}
**Alias**: `volume, vol`
**Description**: IBM Cloud Power Virtual Server Volumes.
**Usage**: `volume`
**Available Commands**:
- `action`:    Perform an action on a volume.
- `clone`:    IBM Cloud Power Virtual Server Volume Clones.
- `create`:    Create a volume.
- `delete`:    Delete a volume.
- `flash-copy-mapping`:    Get a list of flash copy mappings of a volume directly from primary storage host.
- `get`:    View details of a volume.
- `list`:    List all storage volumes in a workspace.
- `onboarding`:    IBM Cloud Power Virtual Server Volume Onboarding.
- `remote-copy-relationship`:    Get the remote copy relationship information of a volume.
- `update`:    Update a volume.

---

#### `ibmcloud pi volume action`
{: #ibmcloud-pi-volume-action}
**Alias**: `action, act`
**Description**: Perform an action on a volume.
**Usage**: 
```
action VOLUME_ID [--replication-enabled=True|False] [--target-tier STORAGE_TIER]

  VOLUME_ID: The unique identifier or name of the volume.
```
**Available Flags**:
```
  -r, --replication-enabled   Enables storage replication on the volume. False by default.
  -t, --target-tier string    Change the storage tier of the volume (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region). "Tier5k" volumes cannot exceed 200GB.
```

---

#### `ibmcloud pi volume clone`
{: #ibmcloud-pi-volume-clone}
**Alias**: `clone, cl`
**Description**: IBM Cloud Power Virtual Server Volume Clones.
**Usage**: `clone`
**Available Commands**:
- `create`:    Create a volume clone for specific volumes.
- `get`:    Get the status of a clone request for the specified clone task ID.

---

##### `ibmcloud pi volume clone create`
{: #ibmcloud-pi-volume-clone-create}
**Alias**: `create, cr`
**Description**: Create a volume clone for specific volumes.
**Usage**: 
```
create CLONE_NAME --volumes VOLUME1[,VOLUMEn] [--replication-enabled=True|False] [--target-tier STORAGE_TIER]

  CLONE_NAME: The name of a clone.
```
**Available Flags**:
```
  -r, --replication-enabled   Enables replication for the cloned volume. If no value is provided, it will default to the replication status of the source volume.
  -t, --target-tier string    Target storage tier for the cloned volumes (use "ibmcloud pi storage-tiers" to see available tiers in the targeted region). Default to the storage tier of the original volume(s) if not specified.
  -v, --volumes strings       Comma separated list of volume identifiers or names to be cloned.
```

---

##### `ibmcloud pi volume clone get`
{: #ibmcloud-pi-volume-clone-get}
**Alias**: `get`
**Description**: Get the status of a clone request for the specified clone task ID.
**Usage**: 
```
get CLONE_TASK_ID

  CLONE_TASK_ID: The unique identifier of a clone task.
```

---

#### `ibmcloud pi volume create`
{: #ibmcloud-pi-volume-create}
**Alias**: `create, cr`
**Description**: Create a volume.
**Usage**: 
```
create VOLUME_NAME --size SIZE [--count COUNT] [--replication-enabled] [--shareable] [--storage-tier STORAGE_TIER]
  pi volume create VOLUME_NAME --size SIZE --storage-pool POOL [--count COUNT] [--replication-enabled] [--shareable] [--storage-tier STORAGE_TIER]
  pi volume create VOLUME_NAME --affinity-policy affinity (--affinity-volume VOLUME | --affinity-instance INSTANCE) --size SIZE [--count COUNT] [--replication-enabled] [--shareable] [--storage-tier STORAGE_TIER]
  pi volume create VOLUME_NAME --affinity-policy anti-affinity (--anti-affinity-volumes "VOLUME1,[VOLUMEn]" | --anti-affinity-instances "INSTANCE1,[INSTANCEn]") --size SIZE [--count COUNT] [--replication-enabled] [--shareable] [--storage-tier STORAGE_TIER]

  VOLUME_NAME: The name of the volume.
```
**Available Flags**:
```
  -i, --affinity-instance string          PVM instance identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-volume is not provided.
  -a, --affinity-policy string            Affinity policy for data volume being created. Valid values are "affinity" and "anti-affinity". If --storage-pool is provided then this cannot be specified.
  -v, --affinity-volume string            Volume identifier or name to base volume affinity policy against; required if "--affinity-policy affinity" is specified and --affinity-instance is not provided.
  -j, --anti-affinity-instances strings   Comma separated list of instance identifiers or names to base volume anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified and --anti-affinity-volumes is not provided.
  -w, --anti-affinity-volumes strings     Comma separated list of volume identifiers or names to base volume anti-affinity policy against; required if "--affinity-policy anti-affinity" is specified  and --anti-affinity-instances is not provided.
  -c, --count int                         Number of volumes to create. 1 by default. (default 1)
  -r, --replication-enabled               Enables storage replication on the volume. False by default.
  -e, --shareable                         Whether the volumes can be attached to multiple VMs. False by default.
  -s, --size int                          Size of the volume (in GB). Size cannot exceed 200GB for storage tier "Tier5k".
  -p, --storage-pool string               Volume pool where the volume will be created. If --storage-pool is provided then --affinity-policy values cannot be specified.
  -t, --storage-tier string               Tier of the volume (use "ibmcloud pi storage-tiers" to see available storage tiers in the targeted region). Default to tier3 if not provided.
```

---

#### `ibmcloud pi volume delete`
{: #ibmcloud-pi-volume-delete}
**Alias**: `delete, del`
**Description**: Delete a volume.
**Usage**: 
```
delete VOLUME_ID

  VOLUME_ID: The unique identifier or name of the volume.
```

---

#### `ibmcloud pi volume flash-copy-mapping`
{: #ibmcloud-pi-volume-flash-copy-mapping}
**Alias**: `flash-copy-mapping, fcm`
**Description**: Get a list of flash copy mappings of a volume directly from primary storage host.
**Usage**: 
```
flash-copy-mapping VOLUME_ID

  VOLUME_ID: The unique identifier or name of the volume.
```

---

#### `ibmcloud pi volume get`
{: #ibmcloud-pi-volume-get}
**Alias**: `get`
**Description**: View details of a volume.
**Usage**: 
```
get VOLUME_ID

  VOLUME_ID: The unique identifier or name of the volume.
```

---

#### `ibmcloud pi volume list`
{: #ibmcloud-pi-volume-list}
**Alias**: `list, ls`
**Description**: List all storage volumes in a workspace.
**Usage**: `list [--auxiliary=True|False] [--long] [--replication-enabled=True|False]`
**Available Flags**:
```
  -a, --auxiliary             Filter auxiliary volumes if set to True or non-auxiliary volumes if False. True by default. (default true)
  -l, --long                  Retrieve all volume details.
  -r, --replication-enabled   Filter replication-enabled volumes if set to True or non-replication-enabled volumes if False. True by default. (default true)
```

---

#### `ibmcloud pi volume onboarding`
{: #ibmcloud-pi-volume-onboarding}
**Alias**: `onboarding, on`
**Description**: IBM Cloud Power Virtual Server Volume Onboarding.
**Usage**: `onboarding`
**Available Commands**:
- `create`:    Create a volume onboarding operation.
- `get`:    Get the information of volume onboarding operation.
- `list`:    List all volume onboarding operations.

---

##### `ibmcloud pi volume onboarding create`
{: #ibmcloud-pi-volume-onboarding-create}
**Alias**: `create, cr`
**Description**: Create a volume onboarding operation.
**Usage**: `create <--auxiliary-volumes "AUXVOLUMENAME1 [NAME1]"> --source-crn SOURCE_CRN [--description DESCRIPTION]`
**Available Flags**:
```
  -a, --auxiliary-volumes strings   Comma separated list of identifiers of the volume(s) at storage host level. Repeat this option to add more auxiliary volumes.
  -d, --description string          Volume onboarding description.
  -s, --source-crn string           CRN of source ServiceBroker instance from where auxiliary volumes need to be onboarded.
```

---

##### `ibmcloud pi volume onboarding get`
{: #ibmcloud-pi-volume-onboarding-get}
**Alias**: `get`
**Description**: Get the information of volume onboarding operation.
**Usage**: 
```
get VOLUME_ONBOARDING_ID

  VOLUME_ONBOARDING_ID: The unique identifier of the onboarding operation.
```

---

##### `ibmcloud pi volume onboarding list`
{: #ibmcloud-pi-volume-onboarding-list}
**Alias**: `list, ls`
**Description**: List all volume onboarding operations.
**Usage**: `list`

---

#### `ibmcloud pi volume remote-copy-relationship`
{: #ibmcloud-pi-volume-remote-copy-relationship}
**Alias**: `remote-copy-relationship, rcr`
**Description**: Get the remote copy relationship information of a volume.
**Usage**: 
```
remote-copy-relationship VOLUME_ID

  VOLUME_ID: The unique identifier or name of the volume.
```

---

#### `ibmcloud pi volume update`
{: #ibmcloud-pi-volume-update}
**Alias**: `update, upd`
**Description**: Update a volume.
**Usage**: 
```
update VOLUME_ID [--bootable=True|False] [--name NEW_NAME] [--size NEW_SIZE] [--shareable=True|False]

  VOLUME_ID: The unique identifier or name of the volume.
```
**Available Flags**:
```
  -b, --bootable      New value for whether the volume can be booted.
  -n, --name string   New name of the volume.
  -t, --shareable     New value for whether the volume can be attached to multiple VMs.
  -s, --size int      New size of the volume. Size cannot exceed 200GB for storage tier "Tier5k".
```

---

### `ibmcloud pi volume-group`
{: #ibmcloud-pi-volume-group}
**Alias**: `volume-group, vg`
**Description**: IBM Cloud Power Virtual Server Volume Groups.
**Usage**: `volume-group`
**Available Commands**:
- `action`:    Perform an action on a volume group.
- `create`:    Create a volume group.
- `delete`:    Delete a volume group.
- `get`:    View details of a volume group.
- `list`:    List all storage volume groups in a workspace.
- `remote-copy-relationships`:    Get the remote copy relationship information of a volume group.
- `storage-details`:    Get storage details for a volume group.
- `update`:    Update a volume group.

---

#### `ibmcloud pi volume-group action`
{: #ibmcloud-pi-volume-group-action}
**Alias**: `action, act`
**Description**: Perform an action on a volume group.
**Usage**: 
```
action VOLUME_GROUP_ID --operation reset [--status STATUS]
  pi volume-group action VOLUME_GROUP_ID --operation start [--source SOURCE]
  pi volume-group action VOLUME_GROUP_ID --operation stop [--allow-read-access=True|False]

```
**Available Flags**:
```
  -a, --allow-read-access   Allow the auxiliary volume to be accessible after stopping the volume group. Default is false.
  -o, --operation string    Operation to be done in a volume group. Valid values are "start", "stop", and "reset".
      --source string       The copying volume source. Allowed values are master or auxiliary. Default is "master". (default "master")
      --status string       New status to be set for a volume group. Default is "available". (default "available")
```

---

#### `ibmcloud pi volume-group create`
{: #ibmcloud-pi-volume-group-create}
**Alias**: `create, cr`
**Description**: Create a volume group.
**Usage**: `create (--volume-group-name VOLUME_GROUP_NAME | --consistency-group-name CONSISTENCY_GROUP_NAME) --member-volume-ids "VOLUME_ID_1,[VOLUME_ID_N]"`
**Available Flags**:
```
  -c, --consistency-group-name string   Storage volume group name. This is required to onboard existing volume group on the target site for DR set up.
  -m, --member-volume-ids strings       Comma separated member volume identifiers.
  -v, --volume-group-name string        Storage volume group name. This is required for the creation of new volume group.
```

---

#### `ibmcloud pi volume-group delete`
{: #ibmcloud-pi-volume-group-delete}
**Alias**: `delete, del`
**Description**: Delete a volume group.
**Usage**: 
```
delete VOLUME_GROUP_ID

  VOLUME_GROUP_ID: The unique identifier or name of the volume group.
```

---

#### `ibmcloud pi volume-group get`
{: #ibmcloud-pi-volume-group-get}
**Alias**: `get`
**Description**: View details of a volume group.
**Usage**: 
```
get VOLUME_GROUP_ID [--long] 

  VOLUME_GROUP_ID: The unique identifier or name of the volume group.
```
**Available Flags**:
```
  -l, --long   Retrieve additional details for the volume group.
```

---

#### `ibmcloud pi volume-group list`
{: #ibmcloud-pi-volume-group-list}
**Alias**: `list, ls`
**Description**: List all storage volume groups in a workspace.
**Usage**: `list [--long]`
**Available Flags**:
```
  -l, --long   Retrieve additional details for the volume group.
```

---

#### `ibmcloud pi volume-group remote-copy-relationships`
{: #ibmcloud-pi-volume-group-remote-copy-relationships}
**Alias**: `remote-copy-relationships, rcr`
**Description**: Get the remote copy relationship information of a volume group.
**Usage**: 
```
remote-copy-relationships VOLUME_GROUP_ID

  VOLUME_GROUP_ID: The unique identifier or name of the volume group.
```

---

#### `ibmcloud pi volume-group storage-details`
{: #ibmcloud-pi-volume-group-storage-details}
**Alias**: `storage-details, sd`
**Description**: Get storage details for a volume group.
**Usage**: 
```
storage-details VOLUME_GROUP_ID

  VOLUME_GROUP_ID: The unique identifier or name of the volume group.
```

---

#### `ibmcloud pi volume-group update`
{: #ibmcloud-pi-volume-group-update}
**Alias**: `update, upd`
**Description**: Update a volume group.
**Usage**: 
```
update VOLUME_GROUP_ID [--add-member-volume-ids "VOLUME_ID_1,[VOLUME_ID_N]"] [--remove-member-volume-ids "VOLUME_ID_1,[VOLUME_ID_N]"]

  VOLUME_GROUP_ID: The unique identifier or name of the volume group.
```
**Available Flags**:
```
  -a, --add-member-volume-ids strings      Comma separated volume identifiers to add as members of the volume group.
  -r, --remove-member-volume-ids strings   Comma separated volume identifiers to remove as members of the volume group.
```

---

### `ibmcloud pi vpn`
{: #ibmcloud-pi-vpn}
**Alias**: `vpn`
**Description**: IBM Cloud Power Virtual Server Virtual Private Networking.
**Usage**: `vpn`
**Available Commands**:
- `create`:    Create a VPN connection.
- `delete`:    Delete a VPN connection.
- `get`:    View details of a VPN connection.
- `list`:    List all VPN connections.
- `peer-subnet`:    IBM Cloud Power Virtual Server Virtual Private Networking Peer-Subnets.
- `subnet`:    IBM Cloud Power Virtual Server Virtual Private Networking Subnets.
- `update`:    Update a VPN connection.

---

#### `ibmcloud pi vpn create`
{: #ibmcloud-pi-vpn-create}
**Alias**: `create, cr`
**Description**: Create a VPN connection.
**Usage**: 
```
create VPN_CONNECTION_NAME --ike-policy-id IKE_POLICY_ID --ipsec-policy-id IPSEC_POLICY_ID --mode MODE --peer-gateway-address PEER_GATEWAY --peer-subnet-cidrs "CIDR1 [CIDRn]" --subnets "ID1 [IDn]"

  VPN_CONNECTION_NAME: A unique name of the VPN connection.
```
**Available Flags**:
```
  -k, --ike-policy-id string          Unique ID of IKE policy selected for this VPN connection.
  -p, --ipsec-policy-id string        Unique ID of IPSec policy selected for this VPN connection.
  -m, --mode string                   Mode to be used by the VPN connection and cannot be updated later. Valid values are 'route' and 'policy'.
  -g, --peer-gateway-address string   IP address of the peer gateway attached to this VPN connection.
  -c, --peer-subnet-cidrs strings     Comma separated list of peer subnet CIDRs.
  -s, --subnets strings               Comma separated list of subnet IDs attached to this VPN connection.
```

---

#### `ibmcloud pi vpn delete`
{: #ibmcloud-pi-vpn-delete}
**Alias**: `delete, del`
**Description**: Delete a VPN connection.
**Usage**: 
```
delete VPN_CONNECTION_ID

  VPN_CONNECTION_ID: The unique identifier of the VPN connection.
```

---

#### `ibmcloud pi vpn get`
{: #ibmcloud-pi-vpn-get}
**Alias**: `get`
**Description**: View details of a VPN connection.
**Usage**: 
```
get VPN_CONNECTION_ID

  VPN_CONNECTION_ID: The unique identifier of the VPN connection.
```

---

#### `ibmcloud pi vpn list`
{: #ibmcloud-pi-vpn-list}
**Alias**: `list, ls`
**Description**: List all VPN connections.
**Usage**: `list`

---

#### `ibmcloud pi vpn peer-subnet`
{: #ibmcloud-pi-vpn-peer-subnet}
**Alias**: `peer-subnet, pnet`
**Description**: IBM Cloud Power Virtual Server Virtual Private Networking Peer-Subnets.
**Usage**: `peer-subnet`
**Available Commands**:
- `attach`:    Attach a peer subnet to a specific VPN connection.
- `detach`:    Detach a peer subnet from a specific VPN connection.
- `list`:    Get a list of peer subnets attached to a specific VPN connection.

---

##### `ibmcloud pi vpn peer-subnet attach`
{: #ibmcloud-pi-vpn-peer-subnet-attach}
**Alias**: `attach, att`
**Description**: Attach a peer subnet to a specific VPN connection.
**Usage**: 
```
attach VPN_CONNECTION_ID --peer-subnet-cidr CIDR

  VPN_CONNECTION_ID: The unique identifier of the VPN connection.
```
**Available Flags**:
```
  -p, --peer-subnet-cidr string   Peer subnet CIDR to attach to the VPN connection.
```

---

##### `ibmcloud pi vpn peer-subnet detach`
{: #ibmcloud-pi-vpn-peer-subnet-detach}
**Alias**: `detach, det`
**Description**: Detach a peer subnet from a specific VPN connection.
**Usage**: 
```
detach VPN_CONNECTION_ID --peer-subnet-cidr CIDR

  VPN_CONNECTION_ID: The unique identifier of the VPN connection.
```
**Available Flags**:
```
  -p, --peer-subnet-cidr string   Peer subnet CIDR to detach from this VPN connection.
```

---

##### `ibmcloud pi vpn peer-subnet list`
{: #ibmcloud-pi-vpn-peer-subnet-list}
**Alias**: `list, ls`
**Description**: Get a list of peer subnets attached to a specific VPN connection.
**Usage**: `list VPN_CONNECTION_ID`

---

#### `ibmcloud pi vpn subnet`
{: #ibmcloud-pi-vpn-subnet}
**Alias**: `subnet, snet`
**Description**: IBM Cloud Power Virtual Server Virtual Private Networking Subnets.
**Usage**: `subnet`
**Available Commands**:
- `attach`:    Attach a subnet to a specific VPN connection.
- `detach`:    Detach a subnet to a specific VPN connection.
- `list`:    Get a list of subnets attached to a specific VPN connection.

---

##### `ibmcloud pi vpn subnet attach`
{: #ibmcloud-pi-vpn-subnet-attach}
**Alias**: `attach, att`
**Description**: Attach a subnet to a specific VPN connection.
**Usage**: 
```
attach VPN_CONNECTION_ID --subnet ID

  VPN_CONNECTION_ID: The unique identifier of the VPN connection.
```
**Available Flags**:
```
  -s, --subnet string   Subnet ID to attach to the VPN connection.
```

---

##### `ibmcloud pi vpn subnet detach`
{: #ibmcloud-pi-vpn-subnet-detach}
**Alias**: `detach, det`
**Description**: Detach a subnet to a specific VPN connection.
**Usage**: 
```
detach VPN_CONNECTION_ID --subnet ID

  VPN_CONNECTION_ID: The unique identifier of the VPN connection.
```
**Available Flags**:
```
  -s, --subnet string   Subnet ID to detach from the VPN connection.
```

---

##### `ibmcloud pi vpn subnet list`
{: #ibmcloud-pi-vpn-subnet-list}
**Alias**: `list, ls`
**Description**: Get a list of subnets attached to a specific VPN connection.
**Usage**: `list VPN_CONNECTION_ID`

---

#### `ibmcloud pi vpn update`
{: #ibmcloud-pi-vpn-update}
**Alias**: `update, upd`
**Description**: Update a VPN connection.
**Usage**: 
```
update VPN_CONNECTION_ID [--name VPN_CONNECTION_NAME] [--peer-gateway-address PEER_GATEWAY] [--ike-policy-id IKE_POLICY_ID] [--ipsec-policy-id IPSEC_POLICY_ID]

  VPN_CONNECTION_ID: The unique identifier of the VPN connection.
```
**Available Flags**:
```
  -k, --ike-policy-id string          New ID of IKE policy selected for this VPN connection.
  -p, --ipsec-policy-id string        New ID of IPSec policy selected for this VPN connection.
  -n, --name string                   New unique name of this VPN connection.
  -g, --peer-gateway-address string   New IP address of the peer gateway attached to this VPN connection.
```

---

### `ibmcloud pi workspace`
{: #ibmcloud-pi-workspace}
**Alias**: `workspace, ws`
**Description**: IBM Cloud Power Virtual Server Workspaces.
**Usage**: `workspace`
**Available Commands**:
- `create`:    Create a workspace.
- `delete`:    Delete a workspace.
- `get`:    View details of a workspace.
- `list`:    List all workspaces for this account.
- `target`:    Target a workspace.

---

#### `ibmcloud pi workspace create`
{: #ibmcloud-pi-workspace-create}
**Alias**: `create`
**Description**: Create a workspace.
**Usage**: 
```
create WORKSPACE_NAME --datacenter DATACENTER --group RESOURCE_GROUP --plan PLAN

  WORKSPACE_NAME: The desired name of the workspace
```
**Available Flags**:
```
  -d, --datacenter string   The datacenter location where the instance should be hosted. Use the "datacenter list" command to see possible values.
  -g, --group string        The ID of the resource group. Use the "ibmcloud resource groups" command to see possible values.
  -p, --plan string         Plan associated with the offering. Valid values are "public" or "private".
```

---

#### `ibmcloud pi workspace delete`
{: #ibmcloud-pi-workspace-delete}
**Alias**: `delete`
**Description**: Delete a workspace.
**Usage**: 
```
delete WORKSPACE_ID

  WORKSPACE_ID: The unique identifier of the workspace
```

---

#### `ibmcloud pi workspace get`
{: #ibmcloud-pi-workspace-get}
**Alias**: `get`
**Description**: View details of a workspace.
**Usage**: 
```
get WORKSPACE_ID

  WORKSPACE_ID: The unique identifier of the workspace
```

---

#### `ibmcloud pi workspace list`
{: #ibmcloud-pi-workspace-list}
**Alias**: `list, ls`
**Description**: List all workspaces for this account.
**Usage**: `list ([--long | --private])`
**Available Flags**:
```
  -l, --long      Retrieve all workspace details.
  -p, --private   List private workspaces.
```

---

#### `ibmcloud pi workspace target`
{: #ibmcloud-pi-workspace-target}
**Alias**: `target, tg`
**Description**: Target a workspace.
**Usage**: 
```
target WORKSPACE_CRN

  WORKSPACE_CRN: The unique identifier of the workspace.
```
**Available Flags**:
```
```

---