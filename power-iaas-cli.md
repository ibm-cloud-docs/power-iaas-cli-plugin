---

copyright:
  years: 2019
lastupdated: "2019-10-06"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# IBM Power Systems Virtual Servers CLI Reference
{: #power-iaas-cli-reference}

This document provides a reference of the command-line interface (CLI) that are available for the {{site.data.keyword.powerSysFull}}. There are also application programming interfaces (APIs) that are available for the {{site.data.keyword.powerSys_notm}}. For more information, see [API references](https://console.{DomainName}/apidocs/power-cloud){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
{: shortdesc}

## Before you begin
{: #power-iaas-cli-before}

1. Install the [{{site.data.keyword.cloud}} CLI](https://cloud.ibm.com/docs/cli?topic=cloud-cli-getting-started){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

1. Install or update the `power-iaas` plug-in.

  To install:
  ```shell
  ibmcloud plugin install power-iaas
  ```
  {: codeblock}

  To update:
  ```shell
  ibmcloud plugin update
  ```
  {: codeblock}

  To view installed plug-ins and versions:
  ```shell
  ibmcloud plugin list
  ```
  {: codeblock}

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

To determine what {{site.data.keyword.powerSys_notm}} endpoint can be used, the power-iaas command-line plug-in uses the region that `ibmcloud login` targets. For example, to use the {{site.data.keyword.powerSys_notm}} endpoint `https://cloud.ibm.com` you must use the `ibmcloud login -a https://cloud.ibm.com` command to target the `us-east` region.

  If you have a federated account, use the following command:
  ```shell
  ibmcloud login -a https://cloud.ibm.com -sso
  ```
  {: codeblock}

---

## Commands
{: #power-iaas-cli-commands}

### `ibmcloud pi image`
{: #ibmcloud-pi-image}

#### View details of an image

`ibmcloud pi image IMAGE_ID [--json]`

- `IMAGE_ID`:  The unique identifier or name of the image

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-create`
{: #ibmcloud-pi-image-create}

#### Create a copy of an image from the image catalog in this account

`ibmcloud pi image-create IMAGE_ID [--json]`

- `IMAGE_ID`:  The unique identifier or name of the image

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-delete`
{: #ibmcloud-pi-image-delete}

#### Delete an image from this account

`ibmcloud pi image-delete IMAGE_ID`

- `IMAGE_ID`:  The unique identifier or name of the image

---

### `ibmcloud pi image-export`
{: #ibmcloud-pi-image-export}

#### Export an image from IBM Cloud Object Storage

`ibmcloud pi image-export IMAGE_NAME --bucket BUCKET_NAME --region REGION_NAME --access-key KEY --secret-key KEY [--json]`

- `IMAGE_ID`:  The unique identifier or name of the image

**Options**

- `--bucket`: Cloud Object Storage bucket name.
- `--region`: Cloud Object Storage region (us-east, us-south).
- `--access-key`: Cloud Object Storage HMAC access key.
- `--secret-key`: Cloud Object Storage HMAC secret key.
- `--json`: Format output in JSON.

---

### `ibmcloud pi image-import`
{: #ibmcloud-pi-image-import}

#### Import an image from IBM Cloud Object Storage

`ibmcloud pi image-import IMAGE_NAME --image-path PATH --os-type OSTYPE --access-key KEY --secret-key KEY [--json]`

- `IMAGE_NAME`:  The wanted name of the image

**Options**

- `--image-path`: Path to image that starts with the service endpoint and ends with the image file name.
- `--os-type`: Operating system contained in the image (aix, ibmi).
- `--access-key`: Cloud Object Storage HMAC access key.
- `--secret-key`: Cloud Object Storage HMAC secret key.
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

- `INSTANCE_ID`:  The unique identifier or name of the instance

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-capture`
{: #ibmcloud-pi-instance-capture}

#### Capture a server instance

`ibmcloud pi instance-capture INSTANCE_ID --destination DEST --name NAME [--volume-ids "VOLUME1 VOLUME2"] [--access-key KEY] [--secret-key KEY] [--region REGION] [--image-path TYPE]`

- `INSTANCE_ID`:  The unique identifier or name of the instance

**Options**

- `--destination`: Destination for the deployable image (image-catalog, cloud-storage, both).
- `--name`: Name of the deployable image that is created for the captured instance.
- `--volumes`: Space separated list of identifiers or names of the volumes to capture with the instance.
- `--access-key`: Cloud Object Storage HMAC access key. Required if destination is cloud-storage.
- `--secret-key`: Cloud Object Storage HMAC secret key. Required if destination is cloud-storage.
- `--region`: Cloud Object Storage region (us-east, us-south). Required if destination is cloud-storage.
- `--image-path`: Cloud Object Storage image path. Required if destination is cloud-storage.

---

### `ibmcloud pi instance-create`
{: #ibmcloud-pi-instance-create}

#### Create a server instance

`ibmcloud pi instance-create INSTANCE_NAME --image IMAGE --memory MEMORY --networks "NETWORK1 NETWORK2" --processors PROCESSORS --processor-type PROC_TYPE [--volumes "VOLUME1 VOLUME2"] [--key-name NAME] [--sys-type TYPE]  [--replicants NUMBER] [--replicant-scheme SCHEME] [--json]`

- `INSTANCE_NAME`:  The name of the instance

**Options**

- `--image`: Operating system image identifier or name.
- `--memory`: Amount of memory (in GB) to allocate to the instance.
- `--networks`: Space separated list of identifiers or names of the networks to associate with the instance.
- `--processors`: Number of processors to allocate to the instance.
- `--processor-type`: Type of processors: 'shared' or 'dedicated'.
- `--volumes`: Space separated list of identifiers or names of the volumes to associate with the instance.
- `--key-name`: Name of SSH key.
- `--sys-type`: Name of System Type ("s922", "e880", "any").
- `--replicants`: Number of replicants (default 1). You must set the value to "2" to create two instances.
- `--replicant-scheme`: Naming scheme to use for duplicate VMs ("suffix", "prefix").
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-delete`
{: #ibmcloud-pi-instance-delete}

#### Delete a server instance

`ibmcloud pi instance-delete INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier or name of the instance

---

### `ibmcloud pi instance-get-console`
{: #ibmcloud-pi-instance-get-console}

#### Get the console of an instance

`ibmcloud pi instance-get-console INSTANCE_ID [--json]`

- `INSTANCE_ID`:  The unique identifier or name of the instance

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-hard-reboot`
{: #ibmcloud-pi-instance-hard-reboot}

#### Hard restart the operating system of an instance

`ibmcloud pi instance-hard-reboot INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier or name of the instance

---

### `ibmcloud pi instance-list-volumes`
{: #ibmcloud-pi-instance-list-volumes}

#### Get a list of volumes attached to an instance

`ibmcloud pi volume INSTANCE [--long] [--json]`

**Options**

- `--long`: Retrieve all volume details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-soft-reboot`
{: #ibmcloud-pi-instance-soft-reboot}

#### Soft restart the operating system of an instance

`ibmcloud pi instance-soft-reboot INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier or name of the instance

---

### `ibmcloud pi instance-start`
{: #ibmcloud-pi-instance-start}

#### Start a server instance

`ibmcloud pi instance-start INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier or name of the instance

---

### `ibmcloud pi instance-stop`
{: #ibmcloud-pi-instance-stop}

#### Stop a server instance

`ibmcloud pi instance-stop INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier or name of the instance

---

### `ibmcloud pi instance-update`
{: #ibmcloud-pi-instance-update}

#### Update a server instance

`ibmcloud pi instance-update INSTANCE_ID [--memory AMOUNT] [--name NEW_NAME] [--processors NUMBER] [--processor-type TYPE] [--json]`

- `INSTANCE_ID`:  The unique identifier or name of the instance

**Options**

- `--memory`: New amount of memory for the server instance.
- `--name`: New name of the server instance.
- `--processors`: New number of processors for the server instance.
- `--processor-type`: New processor type for the server instance.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instances`
{: #ibmcloud-pi-instances}

#### List all server instances

`ibmcloud pi instances [--long] [--json]`

**Options**

- `--long`: Retrieve all instance details.
- `--json`: Format output in JSON.

---

### `ibmcloud pi key`
{: #ibmcloud-pi-key}

#### View details of a key

`ibmcloud pi key KEY_NAME [--json]`

- `KEY_NAMEThe name of the key

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

### `ibmcloud pi key-delete`
{: #ibmcloud-pi-key-delete}

#### Delete a key

`ibmcloud pi key-delete KEY_NAME`

- `KEY_NAME`: The name of the SSH key

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

- `NETWORK_ID`:  The unique identifier or name of the network

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi network-create-private`
{: #ibmcloud-pi-network-create-private}

#### Create a private network

`ibmcloud pi network-create-private NETWORK_NAME --cidr-block CIDR --ip-range "startIP-endIP[,startIP-endIP]" [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--json]`

- `NETWORK_NAME`:  The name of the network

**Options**

- `--cidr-block`: Network in CIDR notation (192.168.0.0/24).
- `--dns-servers`: Space separated list of DNS Servers to use for this network.
- `--gateway`: Gateway to use for this network.
- `--ip-range`: IP addresses range or ranges for this network, format: startIP-endIP[,startIP-endIP].
- `--json`: Format output in JSON.

---

### `ibmcloud pi network-create-public`
{: #ibmcloud-pi-network-create-public}

#### Create a public network

`ibmcloud pi network-create-public NETWORK_NAME [--dns-servers "DNS1 DNS2"] [--json]`

- `NETWORK_NAME`:  The name of the network

**Options**

- `--dns-servers`: Space separated list of DNS Servers to use for this network.
- `--json`: Format output in JSON.

---

### `ibmcloud pi network-delete`
{: #ibmcloud-pi-network-delete}

#### Delete a network

`ibmcloud pi network-delete NETWORK_ID`

- `NETWORK_ID`:  The unique identifier or name of the network

---

### `ibmcloud pi network-update`
{: #ibmcloud-pi-network-update}

#### Update a network

`ibmcloud pi network-update NETWORK_ID [--name NETWORK_NAME] [--starting-ip IP] [--ending-ip IP] [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--json]`

- `NETWORK_ID`:  The unique identifier or name of the network

**Options**

- `--name`: New name of the network.
- `--dns-servers`: Space separated list of new DNS Servers to use for this network.
- `--gateway`: New gateway to use for this network.
- `--ip-range`: New IP addresses range or ranges for this network, format: startIP-endIP[,startIP-endIP].
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

`ibmcloud pi volume VOLUME_ID --instance INSTANCE [--json]`

- `VOLUME_ID`: The unique identifier or name of the volume.

**Options**

- `--instance`: Instance to attach the volume to.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-create`
{: #ibmcloud-pi-volume-create}

#### Create a volume

`ibmcloud pi volume-create VOLUME_NAME --type TYPE --size SIZE [--shareable] [--json]`

- `VOLUME_NAME`:  The name of the volume

**Options**

- `--type`: Type of the volume (ssd, standard).
- `--size`: Size of the volume (in GB).
- `--shareable`: Whether volume can be attached to multiple VMs.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-delete`
{: #ibmcloud-pi-volume-delete}

#### Delete a volume

`ibmcloud pi volume-delete VOLUME_ID`

- `VOLUME_ID`:  The unique identifier or name of the volume


---

### `ibmcloud pi volume-detach`
{: #ibmcloud-pi-volume-detach}

#### Detach a volume from an instance

`ibmcloud pi volume VOLUME_ID --instance INSTANCE [--json]`

- `VOLUME_ID`:  The unique identifier or name of the volume, INSTANCE

**Options**

- `--instance`: Instance to detach the volume from.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-update`
{: #ibmcloud-pi-volume-update}

#### Update a volume

`ibmcloud pi volume-update VOLUME_ID [--bootable] [--name NEW_NAME] [--size NEW_SIZE] [--shareable] [--json]`

- `VOLUME_ID`:  The unique identifier or name of the volume

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
