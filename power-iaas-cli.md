---

copyright:
  years: 2019, 2021
lastupdated: "2021-05-20"

---

{:new_window: target="_blank"}
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

Use these release notes to learn about the latest changes to the {{site.data.keyword.powerSysShort}} service.
{: shortdesc}

### September 2021
{: #sep-2021}

- You can now use [Import Image](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-image-import) to Import an image from IBM Cloud Object Storage by using CLI.
- You can now use [Jobs](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#ibmcloud-pi-job) to View details of a job by using CLI.

### May 2021
{: #mar-2021}

- You can now use [Cloud connection](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#create-connection) to automate the way you connect your Power Systems Virtual Server instances to the IBM Cloud resources by using CLI.

### March 2021

- You can now manage [snapshots](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#snapshot-id) of a cloud instance by using the CLI.
- You can create and list [SAP profiles](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#sapprofile-info) by using CLI.
- You can [list of available system pools](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#system-pools-support) within a particular data center by using CLI.
- You can [attach](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#attach-network), [detach](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#detach-network), or [list all the attached networks](/docs/power-iaas-cli-plugin?topic=power-iaas-cli-plugin-power-iaas-cli-reference#list-networks) to an instance.
- Added image-import progress (task) monitoring.


## Commands
{: #power-iaas-cli-commands}

### `ibmcloud pi image`
{: #ibmcloud-pi-image}

#### View details of an image

`ibmcloud pi image IMAGE_ID [--json]`

- `IMAGE_ID`: The unique identifier or name of the image.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-create`
{: #ibmcloud-pi-image-create}

#### Create a copy of an image from the image catalog in this account

`ibmcloud pi image-create IMAGE_ID [--json]`

- `IMAGE_ID`: The unique identifier or name of the image.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-delete`
{: #ibmcloud-pi-image-delete}

#### Delete an image from this account

`ibmcloud pi image-delete IMAGE_ID`

- `IMAGE_ID`: The unique identifier or name of the image.

---

### `ibmcloud pi image-export`
{: #ibmcloud-pi-image-export}

#### Export an image from IBM Cloud Object Storage

`ibmcloud pi image-export IMAGE_ID --bucket BUCKET_NAME --region REGION_NAME --access-key KEY --secret-key KEY [(--job | --task)] [--json]`

- `IMAGE_ID`: The unique identifier or name of the image.

**Options**

- `--bucket`: Cloud Object Storage bucket name.
- `--region`: Cloud Object Storage region (us-east, us-south, eu-de).
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

- `IMAGE_ID`: The unique identifier or name of the image.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-import`
{: #ibmcloud-pi-image-import}

#### Import an image from IBM Cloud Object Storage

`ibmcloud pi image-import IMAGE_NAME [--os-type OSTYPE] --disk-type DISKTYPE [--bucket-access private] --access-key KEY --secret-key KEY --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME --job [--json]`
`ibmcloud pi image-import IMAGE_NAME [--os-type OSTYPE] --disk-type DISKTYPE --bucket-access public --image-file-name IMAGE_FILE_NAME --bucket BUCKET_NAME --region REGION_NAME  --job [--json]`
`DEPRECATED: ibmcloud pi image-import IMAGE_NAME --image-path PATH [--os-type OSTYPE] [--disk-type DISKTYPE] --access-key KEY --secret-key KEY [--task] [--json]`

- `IMAGE_NAME`: The desired name of the image

**Options**

- `--image-path`: [DEPRECATED] Replaced by image-file-name, region and bucket. Path to image starting with service endpoint and ending with image file name.
- `--os-type`: Operating system contained in the image (`rhel`, `sles`, `aix`, `ibmi`). Required when importing a raw image.
- `--disk-type`: Type of disk storage (i.e. tier1, tier3).
- `--access-key`: Cloud Object Storage HMAC access key.
- `--secret-key`: Cloud Object Storage HMAC secret key.
- `--image-file-name`: The image file name.
- `--bucket-access value`: Indicates the bucket access type (private or public). Private access requires access and secret keys. Default is private.
- `--bucket value`: Cloud Object Storage bucket name
- `--region value`: Cloud Object Storage region (us-east, us-south, eu-de)
- `--job`: The operation will be processed as a job. image-file-name, region, and bucket is required.
- `--task`: [DEPRECATED] The operation will be processed as a task. Task processing is deprecated in favor of job processing. Default.
- `--json`: Format output in JSON.

---

### `ibmcloud pi image-import-show`
{: #ibmcloud-pi-image-import-show}

#### View details of an image import job

`ibmcloud pi image-import-show [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi images`
{: #ibmcloud-pi-images}

#### List all of the images for this account

`ibmcloud pi images [--long] [--json]`

**Options**

- `--long`: Retrieve all image details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance`
{: #ibmcloud-pi-instance}

#### View details of a server instance

`ibmcloud pi instance INSTANCE_ID [--json]`

- `INSTANCE_ID`: The unique identifier or name of the instance.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-capture`
{: #ibmcloud-pi-instance-capture}

#### Capture a server instance

`ibmcloud pi instance-capture INSTANCE_ID --destination DEST --name NAME [--volumes "VOLUME-ID1 .. VOLUME-IDn"] [--access-key KEY] [--secret-key KEY] [--region REGION] [--image-path PATH] [(--job | --task)]`

- `INSTANCE_ID`: The unique identifier or name of the instance.

**Options**

- `--destination`: Destination for the deployable image (image-catalog, cloud-storage, both).
- `--name`: Name of the deployable image that is created for the captured instance.
- `--volumes`: Space separated list of identifiers or names of the volumes to capture with the instance.
- `--access-key`: Cloud Object Storage HMAC access key. Required if destination is cloud-storage.
- `--secret-key`: Cloud Object Storage HMAC secret key. Required if destination is cloud-storage.
- `--region`: Cloud Object Storage region (us-east, us-south, eu-de). Required if destination is cloud-storage.
- `--image-path`: Cloud Object Storage image path. Required if destination is cloud-storage.
- `--job`: The operation will be processed as a job.
- `--task `: [DEPRECATED] The operation will be processed as a task. Task processing is deprecated in favor of job processing. Default.

---

### `ibmcloud pi instance-capture-show`
{: #ibmcloud-pi-instance-capture-show}

#### View the job details of the last server instance capture

`ibmcloud pi instance-capture-show INSTANCE_ID [--json]`

- `INSTANCE_ID`: The unique identifier or name of the instance.

**Options**

- `--json`: Format output in JSON

---

### `ibmcloud pi instance-create`
{: ibmcloud-pi-instance-create}

#### Create a server instance

`ibmcloud pi instance-create INSTANCE_NAME --image IMAGE [--memory MEMORY] <--network \"NETWORK1 [IP1]\"> ... [--processors PROCESSORS] [--processor-type PROC_TYPE] [--volumes \"VOLUME1 VOLUMEN\"] [--key-name NAME] [--sys-type TYPE] [--storage-type STORAGE_TYPE] [--replicants NUMBER] [--replicant-scheme SCHEME] [--replicant-affinity-policy AFFINITY_POLICY] [--pin-policy POLICY] [--IBMiCSS-license] [--IBMiDBQ-license] [--IBMiPHA-license] [--IBMiRDS-users NUMBER-USERS] [--json]`

- `INSTANCE_NAME`: The name of the instance.

**Example**

`ibmcloud pi instance-create instance-name1 --network "private-network1 192.168.0.120" --network "private-network2" --image AIX-7100-05-05**`

**Options**

- `--image`: Operating system image identifier or name.
- `--memory`: Amount of memory (GB) to allocate to the instance. Default value is 2GB.
- `networks`: (deprecated - replaced by network) Space-separated list of identifiers or names of the networks to associate with the instance.
- `--network`: Space separated list of identifier or name and optional IP address to associate with the instance.
- `--processors`: Number of processors to allocate to the instance. Default is 1 core.
- `--processor-type`: Type of processors: 'shared' or 'dedicated' or 'capped'.
- `--volumes`: Space separated list of identifiers or names of the volume(s) to associate with the instance.
- `--key-name`: Name of SSH key.
- `--sys-type`: Name of System Type ("s922", "e880", "e980"). Default is "s922".
- `--storage-type`: Storage type for server deployment when deploying a stock image.
- `--replicants`: Number of duplicate instances to create in this request.
- `--replicant-scheme`: Naming scheme to use for duplicate VMs (suffix, prefix).
- `--replicant-affinity-policy`: Affinity policy to use when multicreate is used (affinity, anti-affinity).
- `--pin-policy`: Pin policy ("none", "soft", "hard"). Default  is "none".
- `--IBMicss-license`: IBMi CSS software license associated with the instance.
- `--IBMiDBQ-license`: IBMi DBQ software license associated with the instance.
- `--IBMiPHA-license`: IBMi PHA software license associated with the instance.
- `--IBMiRDS-users`: Number of IBMi RDS users software license associated with the instance, default IBMiRDSUsers=0 (no license).
- `--json`: Format output in JSON.

---

### `ibmcloud pi inc --help`
{: ibmcloud-pi-inc-help}

#### Create a server instance

`ibmcloud pi instance-create INSTANCE_NAME --image IMAGE --memory MEMORY --networks "NETWORK1 NETWORK2" --processors PROCESSORS --processor-type PROC_TYPE [--volumes "VOLUME1 VOLUME2"] [--key-name NAME] [--sys-type TYPE] [--replicants NUMBER] [--replicant-scheme SCHEME] [--replicant-affinity-policy AFFINITY_POLICY][--IBMiCSS-license] [--IBMiDBQ-license] [--IBMiPHA-license] [--IBMiRDS-users NUMBER-USERS] [--json]`

- `INSTANCE_NAME`: The name of the instance.

**Options**

- `--image`: Operating system image identifier or name.
- `--memory`: Amount of memory (GB) to allocate to the instance.
- `--networks`: Space separated list of identifiers or names of the networks to associate with the instance.
- `--processors`: Number of processors to allocate to the instance.
- `--processor-type`: Type of processors shared or dedicated.
- `--volumes`: Space separated list of identifiers or names of the volumes to associate with the instance.
- `--key-name`: Name of SSH key.
- `--sys-type`: Name of System Type (s922, e880, e980).
- `--storage-type`: Storage type for server deployment when deploying a stock image.
- `--replicants`: Number of replicants (default 1). You must set the value to 2 to create two instances.
- `--replicant-scheme`: Naming scheme to use for duplicate VMs (suffix, prefix).
- `--replicant-affinity-policy`: Affinity policy to use when multicreate is used (affinity, anti-affinity).
- `--IBMiCSS-license`: IBMi CSS software license associated with the instance.
- `--IBMiDBQ-license`: IBMi DBQ software license associated with the instance.
- `--IBMiPHA-license`: IBMi PHA software license associated with the instance.
- `--IBMiRDS-users`: Number of IBM i RDS users software license associated with the instance, default IBMiRDSUsers=0 (no license).
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-delete`
{: #ibmcloud-pi-instance-delete}

#### Delete a server instance

`ibmcloud pi instance-delete INSTANCE_ID`

- `INSTANCE_ID`: The unique identifier or name of the instance.

---

### `ibmcloud pi instance-get-console`
{: #ibmcloud-pi-instance-get-console}

#### Get the console of an instance

`ibmcloud pi instance-get-console INSTANCE_ID [--json]`

- `INSTANCE_ID`: The unique identifier or name of the instance.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-hard-reboot`
{: #ibmcloud-pi-instance-hard-reboot}

#### Hard restart the operating system of an instance

`ibmcloud pi instance-hard-reboot INSTANCE_ID`

- `INSTANCE_ID`: The unique identifier or name of the instance.

---

### `ibmcloud pi instance-list-volumes`
{: #ibmcloud-pi-instance-list-volumes}

#### Get a list of volumes attached to an instance

`ibmcloud pi volume INSTANCE_ID [--long] [--json]`

**Options**

- `--long`: Retrieve all volume details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volc`
{: #ibmcloud-pi-volc}

#### Create a volume

`ibmcloud pi volume-create VOLUME_NAME [--type TYPE] --size SIZE [--shareable] [--affinity-policy POLICY] [--affinity-volume VOLUME] [--json]`

- `VOLUME_NAME`: The name of the volume.

**Options**

- `--type value`: Type of the volume (use 'ibmcloud pi storage-types' to see available storage types in the targeted region); required if affinity-policy is not provided otherwise it is ignored
- `--size value`: Size of the volume (in GB)
- `--shareable`: Whether volume can be attached to multiple VMs
- `--affinity-policy value`: Affinity policy for data volume being created; requires affinity-volume to be specified. Allowable values: [affinity,anti-affinity]
- `--affinity-volume value`: Format output in JSON.Volume (ID or Name)to base volume affinity policy against; required if affinity-policy provided
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-soft-reboot`
{: #ibmcloud-pi-instance-soft-reboot}

#### Soft restart the operating system of an instance

`ibmcloud pi instance-soft-reboot INSTANCE_ID`

- `INSTANCE_ID`: The unique identifier or name of the instance.

---

### `ibmcloud pi instance-immediate-shutdown`
{: #ibmcloud-pi-instance-shutdown}

#### Immediately shut down a server instance

`ibmcloud pi instance-immediate-shutdown INSTANCE_ID`

- `INSTANCE_ID`: The unique identifier or name of the instance

---

### `ibmcloud pi instance-reset-state`
{: #ibmcloud-pi-instance-reset}

#### Reset a server instance in error state - use with caution

`ibmcloud pi instance-reset-state INSTANCE_ID`

- `INSTANCE_ID`: The unique identifier or name of the instance

---

### `ibmcloud pi instance-start`
{: #ibmcloud-pi-instance-start}

#### Start a server instance

`ibmcloud pi instance-start INSTANCE_ID`

- `INSTANCE_ID`: The unique identifier or name of the instance.

---

### `ibmcloud pi instance-stop`
{: #ibmcloud-pi-instance-stop}

#### Stop a server instance

`ibmcloud pi instance-stop INSTANCE_ID`

- `INSTANCE_ID`: The unique identifier or name of the instance.

---

### `ibmcloud pi instance-update`
{: #ibmcloud-pi-instance-update}

#### Update a server instance

`ibmcloud pi instance-update INSTANCE_ID [--memory AMOUNT] [--name NEW_NAME] [--pin-policy POLICY] [--processors NUMBER] [--processor-type TYPE] [--profile-id SAP_PROFILE_ID] [--json]`

- `INSTANCE_ID`: The unique identifier or name of the instance.

**Options**

- `--memory`: New amount of memory for the server instance.
- `--name`: New name of the server instance.
- `--pin-policy`: New pin policy for the server instance ("none", "soft", "hard").
- `--processors`: New number of processors for the server instance.
- `--processor-type`: New processor type for the server instance.
- `--profile-id`: SAP profile ID.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instances`
{: #ibmcloud-pi-instances}

#### List all server instances

`ibmcloud pi instances [--long] [--json]`

**Options**

- `--json`: Format output in JSON.
- `--long`: Retrieve all instance details.

---

### `ibmcloud pi instance-operation`
{: #ibmcloud-pi-instances-operation}

#### Perform an operation on an IBMi server instance

`ibmcloud pi instance-operation INSTANCE_ID --operation-type TYPE [--boot-mode MODE] [] [--boot-operating-mode MODE] [--job-task TASK]`

- `INSTANCE_ID`: The unique identifier or name of instance.

**Examples**

`ibmcloud pi instance-operation IBMi-TEST_VM --operation-type job --job-task dston`

or

`ibmcloud pi instance-operation IBMi-TEST_VM --operation-type boot --boot-mode a --boot-operating-mode normal`

**Options**

- `--operation`: Operating system image identifier or name.

- `--boot-mode`: Name of the server boot mode. Allowed values are **a**, **b**, **c**, and **d**.

- `--boot-operating-mode`: Name of the server operating mode. Allowed values are **normal** and **manual**.

- `--job-task`: Name of the job task to execute. Allowed values are **dston**, **retrydump**, **consoleservic**, **iopreset**, **remotedstof**, **remotedston**, **iopdump**, and **dumprestart**.

---

### `ibmcloud pi instance-list-console-languages`
{: #ibmcloud-pi-instance-list-console-languages}

#### List the avaialble console languages of an instance

`ibmcloud pi instance-list-console-languages INSTANCE_ID [--json]`

- `INSTANCE_ID`: The unique identifier or name of instance.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-update-console-language`
{: #ibmcloud-pi-instance-update-console-language}

#### Update the console language of an instance. This update may take some time to take affect.

`ibmcloud pi instance-update-console-language INSTANCE_ID --code CODE`

- `INSTANCE_ID`: The unique identifier or name of instance.

**Options**

- `--code value`: Language code to set.

---

### `ibmcloud pi job`
{: #ibmcloud-pi-job}

#### View details of a job

`ibmcloud pi job JOB_ID [--json]`

- `JOB_ID`: The unique identifier of the job.

**Options**

- `--json`: Format output in JSON.

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

### `ibmcloud pi job-delete`
{: #ibmcloud-pi-job-delete}

#### Delete a job

`ibmcloud pi job-delete JOB_ID`

**Options**

- `--JOB_ID`: The unique identifier of the job.

---

### `ibmcloud pi key`
{: #ibmcloud-pi-key}

#### View details of a key

`ibmcloud pi key KEY_NAME [--json]`

- `KEY_NAME`: The name of the key

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi key-create`
{: #ibmcloud-pi-key-create}

#### Import an RSA public key

`ibmcloud pi key-create KEY_NAME --key KEY [--json]`

- `KEY_NAME`: The name of the SSH key.

**Options**

- `--key`: SSH RSA key string.
- `--json`: Format output in JSON.

---

### `ibmcloud pi key-delete`
{: #ibmcloud-pi-key-delete}

#### Delete a key

`ibmcloud pi key-delete KEY_NAME`

- `KEY_NAME`: The name of the SSH key.

---

### `ibmcloud pi key-update`
{: #ibmcloud-pi-key-update}

#### Update the name of a key

`ibmcloud pi key-update KEY_NAME --new-name NEW_NAME --new-key NEW_KEY [--json]`

- `KEY_NAME`: The name of the SSH key.

**Options**

- `--new-name`: New SSH key name.
- `--new-key`: New SSH RSA key string.
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

- `NETWORK_ID`: The unique identifier or name of the network.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi network-create-private`
{: #ibmcloud-pi-network-create-private}

#### Create a private network

`ibmcloud pi network-create-private NETWORK_NAME --cidr-block CIDR --ip-range "startIP-endIP[,startIP-endIP]" [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--json]`

- `NETWORK_NAME`: The name of the network.

**Options**

- `--cidr-block`: Network in CIDR notation (192.168.0.0/24).
- `--dns-servers`: Space separated list of DNS Servers to use for this network.
- `--gateway`: Gateway to use for this network.
- `--ip-range`: IP addresses range or ranges for this network.
- `--json`: Format output in JSON.

---

### `ibmcloud pi network-create-public`
{: #ibmcloud-pi-network-create-public}

#### Create a public network

`ibmcloud pi network-create-public NETWORK_NAME [--dns-servers "DNS1 DNS2"] [--json]`

- `NETWORK_NAME`: The name of the network.

**Options**

- `--dns-servers`: Space separated list of DNS Servers to use for this network.
- `--json`: Format output in JSON.

---

### `ibmcloud pi network-delete`
{: #ibmcloud-pi-network-delete}

#### Delete a network

`ibmcloud pi network-delete NETWORK_ID`

- `NETWORK_ID`: The unique identifier or name of the network.

---

### `ibmcloud pi network-update`
{: #ibmcloud-pi-network-update}

#### Update a network

`ibmcloud pi network-update NETWORK_ID [--name NETWORK_NAME] [--starting-ip IP] [--ending-ip IP] [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--json]`

- `NETWORK_ID`: The unique identifier or name of the network.

**Options**

- `--name`: New name of the network.
- `--dns-servers`: Space separated list of new DNS Servers to use for this network.
- `--gateway`: New gateway to use for this network.
- `--ip-range`: New IP addresses range or ranges for this network.
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

### `ibmcloud pi service-list`
{: #ibmcloud-pi-service-list}

#### List all services for this account and region

`ibmcloud pi service-list [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi service-target`
{: #ibmcloud-pi-service-target}

#### Target a service

`ibmcloud pi service-target [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi storage-types`
{: #ibmcloud-pi-storage-types}

#### List all storage types

`ibmcloud pi storage-types [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume`
{: #ibmcloud-pi-volume}

#### View details of a volume

`ibmcloud pi volume VOLUME_ID [--json]`

- `VOLUME_ID`: The unique identifier or name of the volume.

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-attach`
{: #ibmcloud-pi-volume-attach}

#### Attach a volume to an instance

`ibmcloud pi volume-attach VOLUME_ID --instance INSTANCE [--json]`

- `VOLUME_ID`: The unique identifier or name of volume.

**Options**

- `--instance`: Instance to attach the volume to.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-create`
{: #ibmcloud-pi-volume-create}

#### Create a volume

`ibmcloud pi volume-create VOLUME_NAME --type TYPE --size SIZE [--shareable] [--json]`

- `VOLUME_NAME`: The name of the volume.

**Options**

- `--type`: Type of the volume (`ssd`, `standard`, `tier1`, or `tier3`).
- `--size`: Size of the volume (GB).
- `--shareable`: Whether volume can be attached to multiple VMs.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-delete`
{: #ibmcloud-pi-volume-delete}

#### Delete a volume

`ibmcloud pi volume-delete VOLUME_ID`

- `VOLUME_ID`: The unique identifier or name of the volume

---

### `ibmcloud pi volume-detach`
{: #ibmcloud-pi-volume-detach}

#### Detach a volume from an instance

`ibmcloud pi volume VOLUME_ID --instance INSTANCE [--json]`

- `VOLUME_ID`: The unique identifier or name of the volume.

**Options**

- `--instance`: Instance to detach the volume from.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-update`
{: #ibmcloud-pi-volume-update}

#### Update a volume

`ibmcloud pi volume-update VOLUME_ID [--bootable] [--name NEW_NAME] [--size NEW_SIZE] [--shareable] [--json]`

- `VOLUME_ID`: The unique identifier or name of the volume.

**Options**

- `--bootable`: New volume bootable.
- `--name`: New name of the volume.
- `--size`: New size of the volume.
- `--shareable`: New for whether volume can be attached to multiple VMs.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volumes`
{: #ibmcloud-pi-volumes}

#### List all volumes

`ibmcloud pi volumes [--long] [--json]`

**Options**

- `--long`: Retrieve all volume details.
- `--json`: Format output in JSON.

---

### ibmcloud pi instance-attach-network
{: #attach-network}

#### Attach a network to the server instance

`ibmcloud pi instance-attach-network INSTANCE_NAME --network "NETWORK_ID" --ip-address "IP_ADDRESS" [--json]`

- `INSTANCE_NAME`: The name of the instance.

**Options**

- `--network`: The network ID.
- `--ip-address`: The requested IP address of this network interface.
- `--json`: Format output in JSON.

---

### ibmcloud pi instance-attach-volumes --help
{: #attach-instance-attach-volumes}

#### Attach volumes to an instance.

`ibmcloud pi instance-attach-volumes INSTANCE_ID --volume-ids "VOLUME_ID1 [VOLUME_IDn]"`

- `INSTANCE_ID`: TThe unique identifier or name of the instance.

**Options**

- `--volume-ids value`: Space separated list of volume IDs to the volumes to attach to the instance.
  
---

### ibmcloud pi instance-detach-network
{: #detach-network}

#### Detach all or a specific network from the server instance

`ibmcloud pi instance-detach-network INSTANCE_NAME -network "NETWORK_ID" [--mac-address "MAC_ADDRESS"]`

- `INSTANCE_NAME`: The name of the cloud connection.

**Options**

- `--network`: The network ID.
- `--mac-address`: The mac address of the network interface to be removed. The defualt value is all mac addresses.

---

### ibmcloud pi instance-networks
{: #list-networks}

#### List all the attached networks

`ibmcloud pi instance-detach-network INSTANCE_NAME [--json]`

- `INSTANCE_NAME`: The name of the cloud connection.

**Options**

- `--json`: Format output in JSON.

---

### ibmcloud pi instance-system-pool
{: #system-pools-support}

#### List of available system pools within a particular data center
{: #list-system-pools}

`ibmcloud pi system-pool [--json]`

**Options**

- `--json`: Format output in JSON.

---

### ibmcloud pi instance-sap-create-instance
{: #create-sap-instance}

#### Create an SAP instance
{: #create-new-sappvm}

`ibmcloud pi sap-create-instance SAP_INSTANCE_NAME --image IMAGE --profile-id PROFILE_ID networks "NETWORK1 [IP1]" [--pin-policy POLICY] [--volumes "VOLUME1 VOLUME2"] [--key-name KEY-NAME] [--json]`

- `SAP_INSTANCE_NAME`: The name of the SAP instance

**Options**

- `--image`: Operating system image identifier or name.
- `--profile-id`: The unique identifier of the SAP profile.
- `--networks`: Space separated identifier or name of the network and optional IP address to associate with the instance.
- `--pin-policy`: Pin policy state **none**, **soft**, or **hard**. Default Pin policy is **none**.
- `--volumes value Space`: Separated list of identifiers or names of the volumes that are associated with the instance.
- `--key-name`: Name of SSH key.
- `--json`: Format output in JSON.

---

### ibmcloud pi instance-sap-list
{: #instance-list}

#### List all SAP profiles
{: #sapprofile-list}

`ibmcloud pi sap-list [--json]`

**Options**

- `--json`: Format output in JSON.

---

### ibmcloud pi instance-sap-profile
{: #sapprofile-info}

#### Get information on an SAP profile
{: #get-sapprofile-info}

`ibmcloud pi sap-profile SAP_PROFILE_ID [--json]`

- `SAP_INSTANCE_ID`: The unique identifier of the SAP profile.

**Options**

- `--json`: Format output in JSON.

---

### ibmcloud pi instance-snapshot
{: #snapshot-id}

### Get the detail of a snapshot
{: #snapshot-details}

`ibmcloud pi snapshot SNAPSHOT_ID`

- `SNAPSHOT_ID`: The unique identifier of the snapshot.

**Options**

- `--json`: Format output in JSON.

---

### ibmcloud pi instance-snapshot-create
{: #create-snapshot}

#### Create a snapshot
{: #create-snapshot}

`ibmcloud pi snapshot-create INSTANCE_ID [--volumes] [--name] [--description] [--json]`

- `INSTANCE_ID`: The unique identifier or name of the instance.

**Options**

- `--volumes`: Space separated list of volumes to include in the PVM instance snapshot. This parameter is optional. If you do not specify this parameter or if the volumes list is empty, all the volumes that are attached to the PVM instance are included in the snapshot.
- `--name`: Name of the snapshot.
- `--description`: Snapshot description.
- `--json`: Format output in JSON.

---

### ibmcloud pi instance-snapshot-delete
{: #delete-snapshot}

#### Delete a snapshot
{: #delete-snapshot}

`ibmcloud pi snapshot-delete SNAPSHOT_ID`

- `SNAPSHOT_ID`: The unique identifier of the snapshot.

**Options**

- `--json`: Format output in JSON.

---

### ibmcloud pi instance-snapshot-restore
{: #restore-snapshot}

#### Restore a PVM instance snapshot
{: #restore-pvminstance-snapshot}

`ibmcloud pi snapshot-restore INSTANCE_ID --snapshot [--force] [--restore]`

- `INSTANCE_ID`: The unique identifier or name of the instance.

**Options**

- `--snapshot`: The unique identifier of the snapshot.
- `--force`: By default the VM must be shut off during a snapshot restore, if force set to true, relaxes the VM shutoff pre-condition.
- `--restore`: Action to take on a failed snapshot restore. Allowed values are **retry** or **rollback**.

---

### ibmcloud pi instance-snapshot
{: #snapshot-list}

#### List all snapshots
{: #snapshot-list}

`ibmcloud pi snapshots [--long] [--json]`

**Option**

- `--json`: Format output in JSON.

---

### ibmcloud pi volume-clone
{: #volume-clone}

#### Get the status of a clone request for the specified clone task ID
{: #volume-clone-status}

`ibmcloud pi volume-clone CLONE_TASK_ID [--json]`

- `CLONE_TASK_ID`: The unique identifier of a clone task.

**Options**

- `--json`: Format output in JSON.

---

### ibmcloud pi volume-create-clone
{: #create-volume-clone}
#### Create a volume clone for specific volumes

`ibmcloud pi volume-create-clone CLONE_NAME --volumes "VOLUME1 ..VOLUMEn" [--json]`

- `CLONE_NAME`: The name of a clone.

**Options**

- `--volumes value Space`: separated list of the volume(s) to be cloned.
- `--json`: Format output in JSON.

---
### `ibmcloud pi connections`
{: #connections}

#### List all cloud Connections

`ibmcloud pi connections [--long] [--json]`

**Options**

- `--long`: Retrieve all cloud connections in detail
- `--json`: Format output in JSON

---

### ibmcloud pi connection-attach-network
{: #attach-network}

#### Attach a network to the cloud connection

`ibmcloud pi connection-attach-network CONNECTION_ID --network NETWORK_ID[--json]`

- `CONNECTION_ID`: The unique identifier of the cloud connection

**Options**

- `--network`: The unique identifier (network ID) of the network

---

### ibmcloud pi connection-create
{: #create-connection}

#### Create a cloud connection

`ibmcloud pi connection-create CONNECTION_NAME --speed SPEED [--vpc --vpcID "VPC-ID"] ([--classic [--networks "NETWORK_ID1..NETWORK_IDn" [--gre-tunnel "CIDR DEST-IP"]]] | [--networks "NETWORK_ID1..NETWORK_IDn"]) [--global-routing] [--metered] [--json]`

- `CONNECTION_NAME`: The unique name of the cloud connection

**Options**

- `--speed value`: Speed of the cloud connection (speed in megabits per second). Allowed values are 50, 100, 200, 500, 1000, 2000, 5000
- `--networks value`: Space separated network identifiers
- `--vpc`: Enable VPC cloud connection endpoint
- `--vpcID value`: VPC ID (i.e. crn:v1:..) to add to cloud connection. Use with "--vpc" option
- `--classic`: Enable Classic cloud connection endpoint
- `--gre-tunnel value`: Space separated "cidr" and "destinationIPAddress". Use with "--classic" option
- `--metered`: Metered cloud connection flag
- `--global-routing`: Global routing flag
- `--json`: Format output in JSON

---

### ibmcloud pi connection-delete
{: delete-connection}

#### Delete a Cloud Connection

`ibmcloud pi connection-delete CONNECTION_ID`

- `CONNECTION_ID`: The unique identifier of the cloud connection

---

### ibmcloud pi connection-detach-network
{: #connection-detach-network}

#### Detach a network from the cloud connection

`ibmcloud pi connection-detach-network CONNECTION_ID --network NETWORK_ID [--json]`

- `CONNECTION_ID`: The unique identifier of the cloud connection

**Options**

- `--network`: The unique identifier (network ID) of the network
- `--json`: Format output in JSON

---

### ibmcloud pi connection-update
{: #connection-update}

#### Update a cloud connection

`ibmcloud pi connection-update CONNECTION_ID [--speed SPEED] [--vpc=True|False [<--vpcID "VPC-ID">]] [--classic=True|False [--gre-tunnel "CIDR DEST-IP"]] ...[--global-routing=True|False] [--metered=True|False] [--name NAME] [--json]`

- `CONNECTION_ID`: The unique identifier of the cloud connection

**Options**

- `--speed`: New speed value for the cloud connection
- `--vpc`: Enable or disable VPC cloud connection endpoint
- `--vpcID`: VPC ID to add to cloud connection for use with "--vpc" option
- `classic`: Enable or disable classic cloud connection endpoint
- `--gre-tunnel`: Space separated **cidr**, **destination IPaddress** for use with "--classic" option
- `--global-routing`: Enable or disable global routing
- `--metered`: Enable or disable metering
- `--name`: Name of cloud connection
- `--json`: Format output in JSON

---

### ibmcloud pi connection-vpcs
{: #connection-vpcs}

#### List all virtual private clouds

`ibmcloud pi connection-vpcs [--json]`

**Options**

- `--json`: Format output in JSON

---

<!--### ibmcloud pi connection-network
{: #network-connection}

#### Get information about a cloud connection's attached network

`ibmcloud pi connection-network CONNECTION_ID --network NETWORK_ID [--json]`

- `CONNECTION_ID`: The unique identifier or name of the cloud connection.

**Options**

- `network`: The unique identifier (network ID) of the network.
- `json`: Format output in JSON.-->

---

### ibmcloud pi vpn-connections
{: #vpn-connections}

#### List all VPN connections

`ibmcloud pi vpn-connections [--json]`


**Options**

- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection
{: #vpn-connection}

#### View details of a VPN connection

`ibmcloud pi vpn-connection VPN_CONNECTION_ID [--json]`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection-create
{: #vpn-connection-create}

#### Create a VPN connection

`ibmcloud pi vpn-connection-create VPN_CONNECTION_NAME --mode (policy|route) --peer-gateway-address PEER_GATEWAY  --peer-subnet-cidrs "CIDR1 [CIDRn]" --connection-state=(True|False) --ike-policy-id IKE_POLICY_ID --ipsec-policy-id IPSEC_POLICY_ID --network-ids "ID1 [IDn]" [--json]`

- `VPN_CONNECTION_NAME`: A unique name of the VPN connection.
  
**Options**

- `--mode value`: Policy-based or route-based mode to be used by the connection and cannot be updated later
- `--peer-gateway-address value`: IP address of the peer gateway attached to this VPN connection
- `--peer-subnet-cidrs value`: Space separated list of peer subnet CIDRs
- `--connection-state`: Desired connection state for the VPN connection on creation. The default is False.
- `--ike-policy-id value`: Unique ID of IKE policy selected for this VPN connection
- `--ipsec-policy-id value`: Unique ID of IPSec policy selected for this VPN connection
- `--network-ids value`: Space separated list of network IDs attached to this VPN connection
- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection-update
{: #vpn-connection-update}

#### Update a VPN connection

`ibmcloud pi vpn-connection-update VPN_CONNECTION_ID [--name VPN_CONNECTION_NAME] [--peer-gateway-address PEER_GATEWAY] [--connection-state=True|False] [--ike-policy-id IKE_POLICY_ID] [--ipsec-policy-id IPSEC_POLICY_ID] [--json]`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--name value`: New name of this VPN connection
- `--peer-gateway-address value`: New IP address of the peer gateway attached to this VPN connection
- `--connection-state`: Desired connection state for the VPN connection on creation
- `--ike-policy-id value`: New ID of IKE policy selected for this VPN connection
- `--ipsec-policy-id value`: New ID of IPSec policy selected for this VPN connection
- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection-delete
{: #vpn-connection-delete}

#### Delete a VPN connection

`ibmcloud pi vpn-connection-delete VPN_CONNECTION_ID`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection

---

### ibmcloud pi vpn-connection-networks
{: #vpn-connection-netowkrs}

#### Get a list of networks attached to a specific VPN connection

` ibmcloud pi vpn-connection-networks VPN_CONNECTION_ID [--json]`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection-network-attach
{: #vpn-connection-network-attach}

#### Attach a network to a specific VPN connection

`ibmcloud pi vpn-connection-network-attach VPN_CONNECTION_ID --network-id ID [--json]`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--network-id value`: Network ID to attach to the VPN connection
- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection-network-detach
{: #vpn-connection-network-detach}

#### Detach a network from a specific VPN connection

`ibmcloud pi vpn-connection-network-detach VPN_CONNECTION_ID --network-id ID`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--network-id value`: Network ID to detach from the VPN connection
  
---

### ibmcloud pi vpn-connection-peer-subnets
{: #vpn-connection-peer-subnets}

#### Get a list of peer subnets attached to a specific VPN connection

`ibmcloud pi vpn-connection-peer-subnets VPN_CONNECTION_ID [--json]`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection-peer-subnet-attach
{: #vpn-connection-peer-subnet-attach}

#### Attach a peer subnet to a specific VPN connection

`ibmcloud pi vpn-connection-peer-subnet-attach VPN_CONNECTION_ID --peer-subnet-cidr CIDR [--json]`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--peer-subnet-cidr value`: Peer subnet CIDR to attach to the VPN connection
- `--json`: Format output in JSON
  
---

### ibmcloud pi vpn-connection-peer-subnet-detach
{: #vpn-connection-peer-subnet-detach}

#### Detach a peer subnet from a specific VPN connection

`ibmcloud pi vpn-connection-peer-subnet-detach VPN_CONNECTION_ID --peer-subnet-cidr CIDR`

- `VPN_CONNECTION_ID`: The unique identifier of the VPN connection
  
**Options**

- `--peer-subnet-cidr value`: Peer subnet CIDR to attach to the VPN connection
 
---

### ibmcloud pi vpn-ike-policies
{: #vpn-ike-policies}

#### List all VPN IKE policies

`ibmcloud pi vpn-ike-policies [--json]`
  
**Options**

- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ike-policy
{: #vpn-ike-policy}

#### View details of a VPN IKE policy

`ibmcloud pi vpn-ike-policy IKE_POLICY_ID [--json]`

- `IKE_POLICY_ID`: The unique identifier of the VPN IKE policy
  
**Options**

- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ike-policy-add
{: #vpn-ike-policy-add}

#### Add a VPN IKE policy

`ibmcloud pi vpn-ike-policy-add IKE_POLICY_NAME --version VERSION --authentication AUTHENTICATION --encryption ENCRYPTION --dh-group DH_GROUP --preshared-key KEY --key-lifetime SECONDS [--json]`

- `IKE_POLICY_NAME`: The name of the VPN IKE policy. The maximum name length is 47 characters.

**Options**

- `--version value`: Version number of the IKE Policy. Valid values are 1, 2
- `--authentication value`: Authentication algorithm of the IKE Policy. Valid values are none, sha1, md5, sha-256, sha-384
- `--encryption value`: Encryption algorithm of the IKE policy. Valid values are 3des-cbc, aes-128-cbc, aes-128-gcm, aes-192-cbc, aes-256-cbc, aes-256-gcm, des-cbc. When using aes-128-gcm or aes-256-gcm authentication should be set to 'none'
- `--dhgroup value`: DH group number of the IKE Policy. Valid values are 1, 2, 5, 14, 19, 20, 24
- `--presharedkey value`: Preshared key used in this VPN connection. The key length must be even.
- `--key-lifetime value`: Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ike-policy-update
{: #vpn-ike-policy-update}

#### Update a VPN IKE policy

`ibmcloud pi vpn-ike-policy-update IKE_POLICY_ID  [--name NEW_NAME] [--version VERSION] [--authentication AUTHENTICATION] [--encryption ENCRYPTION] [--dh-group DH_GROUP] [--preshared-key KEY] [--key-lifetime SECONDS] [--json]`

- `IKE_POLICY_ID`: The unique identifier of the VPN IKE policy
  
**Options**

- `--name value`: New name of the IKE Policy. The maximum name length is 47 characters
- `--version value`: Version number of the IKE Policy. Valid values are 1, 2.
- `--authentication value`: Authentication algorithm of the IKE Policy. Valid values are none, sha1, md5, sha-256, sha-384.
- `--encryption value`: Encryption algorithm of the IKE Policy. Valid values are 3des-cbc, aes-128-cbc, aes-128-gcm, aes-192-cbc, aes-256-cbc, aes-256-gcm, des-cbc. When using aes-128-gcm or aes-256-gcm authentication should be set to 'none'.
- `--dhgroup value`: DH group number of the IKE Policy. Valid values are 1, 2, 5, 14, 19, 20, 24.
- `--presharedkey value`: Preshared key used in this VPN connection. The key length must be even.
- `--key-lifetime value`: Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ike-policy-delete
{: #vpn-ike-policy-delete}

#### Delete a VPN IKE policy

`ibmcloud pi vpn-ike-policy-delete IKE_POLICY_ID`

- `IKE_POLICY_ID`: The unique identifier of the VPN IKE policy
 
---

### ibmcloud pi vpn-ipsec-policies
{: #vpn-ipsec-policies}

#### List all IPSec policies

`ibmcloud pi vpn-ipsec-policies [--json]`
  
**Options**

- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ipsec-policy
{: #vpn-ipsec-policy}

#### View details of a VPN IPSec policy

`ibmcloud pi vpn-ipsec-policy IPSEC_POLICY_ID [--json]`

- `IPSEC_POLICY_ID`: The unique identifier of the VPN IPSEC policy
  
**Options**

- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ipsec-policy-add
{: #vpn-ipsec-policy-add}

#### Add a VPN IPSec policy

`ibmcloud pi vpn-ipsec-policy-add IPSEC_POLICY_NAME --authentication AUTHENTICATION --encryption ENCRYPTION --dh-group DH_GROUP --key-lifetime SECONDS [--pfs] [--json]`

- `IPSEC_POLICY_NAME`: The name of the VPN IPSEC policy. The maximum name length is 47 characters
  
**Options**

- `--authentication value`: Authentication encryption type of the IPSec Policy. Valid values are none, hmac-md5-96, hmac-sha-256-128, hmac-sha1-96
- `--encryption value`: Connection encryption policy of the IPSec Policy. Valid values are 3des-cbc, aes-128-cbc, aes-128-gcm, aes-192-cbc, aes-192-gcm, aes-256-cbc, aes-256-gcm, des-cbc. When using aes-128-gcm, aes-192-gcm or aes-256-gcm authentication should be set to 'none'
- `--dhgroup value`: DH group number of the IPSec Policy. Valid values are 1, 2, 5, 14, 19, 20, 24
- `--pfs`: Enable perfect forward secrecy
- `--key-lifetime value`: Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ipsec-policy-update
{: #vpn-ipsec-policy-update}

#### Update a VPN IPSec policy

`ibmcloud pi vpn-ipsec-policy-update IPSEC_POLICY_ID  [--name NEW_NAME] [--authentication AUTHENTICATION] [--encryption ENCRYPTION] [--dh-group DH_GROUP] [--key-lifetime SECONDS] [--pfs=True|False] [--json]`

- `IPSEC_POLICY_ID`: The unique identifier of the VPN IPSec policy
  
**Options**

- `--name value`: New name of the IKE Policy. The maximum name length is 47 characters
- `--authentication value`: Authentication algorithm of the IKE Policy. Valid values are none, hmac-md5-96, hmac-sha-256-128, hmac-sha1-96
- `--dhgroup value`: DH group number of the IKE Policy. Valid values are 1, 2, 5, 14, 19, 20, 24
- `--key-lifetime value`: Key lifetime of the IKE policy in seconds. Valid range is 180 to 86400 seconds.
- `--pfs`: Enable or disable perfect forward secrecy
- `--json`: Format output in JSON

---

### ibmcloud pi vpn-ipsec-policy-delete
{: #vpn-ipsec-policy-delete}

#### Delete a VPN IPSec policy

`ibmcloud pi vpn-ipsec-policy-delete IPSEC_POLICY_ID`

- `IPSEC_POLICY_ID`: The unique identifier of the VPN IPSec policy
  
---