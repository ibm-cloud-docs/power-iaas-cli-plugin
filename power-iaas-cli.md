
### `ibmcloud pi image`
{: #ibmcloud-pi-image}

#### View details of an image

`ibmcloud pi image IMAGE_ID [--json]`

- `IMAGE_ID`:  The unique identifier of the image

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi images`
{: #ibmcloud-pi-images}

#### List all images for this account

`ibmcloud pi images [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-create`
{: #ibmcloud-pi-image-create}

#### Create a copy of an image from the image catalog in this account

`ibmcloud pi image-create IMAGE_ID [--json]`

- `IMAGE_ID`:  The unique identifier of the image

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi image-delete`
{: #ibmcloud-pi-image-delete}

#### Delete an image from this account

`ibmcloud pi image-delete IMAGE_ID`

- `IMAGE_ID`:  The unique identifier of the image


---

### `ibmcloud pi image-list-catalog`
{: #ibmcloud-pi-image-list-catalog}

#### List images available in the regional image catalog

`ibmcloud pi image-list-catalog [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance`
{: #ibmcloud-pi-instance}

#### View details of a server instance

`ibmcloud pi instance INSTANCE_ID [--json]`

- `INSTANCE_ID`:  The unique identifier of the instance

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-create`
{: #ibmcloud-pi-instance-create}

#### Create a server instance

`ibmcloud pi instance-create INSTANCE_NAME --image-id IMAGE_ID --memory MEMORY --network-ids "NETWORK_ID1 NETWORK_ID2" --processors PROCESSORS --processor-type PROC_TYPE [--volume-ids "VOLUME_ID1 VOLUME_ID2"] [--key-name NAME] [--sys-type TYPE] [--json]`

- `INSTANCE_NAME`:  The name of the instance

**Options**

- `--image-id`: Operating system image ID.
- `--memory`: Amount of memory (in GB) to allocate to the instance.
- `--network-ids`: Space separated list of IDs of the network(s) to associate with the instance.
- `--processors`: Amount of processors to allocate to the instance.
- `--processor-type`: Type of processors: 'shared' or 'dedicated'.
- `--volume-ids`: Space separated list of IDs of the volume(s) to associate with the instance.
- `--key-name`: Name of SSH key.
- `--sys-type`: Name of System Type.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-delete`
{: #ibmcloud-pi-instance-delete}

#### Delete a server instance

`ibmcloud pi instance-delete INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier of the instance


---

### `ibmcloud pi instance-get-console`
{: #ibmcloud-pi-instance-get-console}

#### Get the console of an instance

`ibmcloud pi instance-get-console INSTANCE_ID [--json]`

- `INSTANCE_ID`:  The unique identifier of the instance

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-hard-reboot`
{: #ibmcloud-pi-instance-hard-reboot}

#### Hard Restart the operating system of an instance

`ibmcloud pi instance-hard-reboot INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier of the instance


---

### `ibmcloud pi instance-soft-reboot`
{: #ibmcloud-pi-instance-soft-reboot}

#### Soft Restart the operating system of an instance

`ibmcloud pi instance-soft-reboot INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier of the instance


---

### `ibmcloud pi instance-start`
{: #ibmcloud-pi-instance-start}

#### Start a server instance

`ibmcloud pi instance-start INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier of the instance


---

### `ibmcloud pi instance-stop`
{: #ibmcloud-pi-instance-stop}

#### Stop a server instance

`ibmcloud pi instance-stop INSTANCE_ID`

- `INSTANCE_ID`:  The unique identifier of the instance


---

### `ibmcloud pi instance-update`
{: #ibmcloud-pi-instance-update}

#### Update a server instance

`ibmcloud pi instance-update INSTANCE_ID [--memory AMOUNT] [--name NEW_NAME] [--processors NUMBER] [--processor-type TYPE] [--json]`

- `INSTANCE_ID`:  The unique identifier of the instance

**Options**

- `--memory`: New amount of memory for the server instance.
- `--name`: New name of the server instance.
- `--processors`: New amount of processors for the server instance.
- `--processor-type`: New processor type for the server instance.
- `--json`: Format output in JSON.

---

### `ibmcloud pi instance-volumes`
{: #ibmcloud-pi-instance-volumes}

#### Get a list of volumes attached to an instance

`ibmcloud pi volume INSTANCE_ID [--json]`

- `INSTANCE_ID`:  The unique ID of the instance

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi instances`
{: #ibmcloud-pi-instances}

#### List all server instances

`ibmcloud pi instances [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi key`
{: #ibmcloud-pi-key}

#### View details of a key

`ibmcloud pi key KEY_NAME [--json]`

- `KEY_NAME`:  The name of the key

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi key-create`
{: #ibmcloud-pi-key-create}

#### Import an RSA public key

`ibmcloud pi key-create KEY_NAME --key KEY [--json]`

- `KEY_NAME`:  The name of the key

**Options**

- `--key`: SSH RSA key string.
- `--json`: Format output in JSON.

---

### `ibmcloud pi key-update`
{: #ibmcloud-pi-key-update}

#### Update the name of a key

`ibmcloud pi key-update KEY_NAME --new-name NEW_NAME --new-key NEW_KEY [--json]`

- `KEY_NAME`:  The name of the key

**Options**

- `--new-name`: SSH RSA key string.
- `--new-key`: SSH RSA key string.
- `--json`: Format output in JSON.

---

### `ibmcloud pi key-delete`
{: #ibmcloud-pi-key-delete}

#### Delete a key

`ibmcloud pi key-delete KEY_NAME`

- `KEY_NAME`:  The name of the key


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

- `NETWORK_ID`:  The unique ID of the network

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi networks`
{: #ibmcloud-pi-networks}

#### List all networks

`ibmcloud pi networks [--json]`

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi network-create`
{: #ibmcloud-pi-network-create}

#### Create a network

`ibmcloud pi network-create NETWORK_NAME --cidr-block CIDR  --ip-range "startIP-endIP[,startIP-endIP]" --network-type TYPE [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--json]`

- `NETWORK_NAME`:  The name of the network

**Options**

- `--cidr-block`: Network in CIDR notation (192.168.0.0/24).
- `--dns-servers`: Space separated list of DNS Servers to use for this network.
- `--gateway`: Gateway to use for this network.
- `--ip-range`: IP Addresses range(s) for this network, format: startIP-endIP[,startIP-endIP].
- `--network-type`: Type of Network [vlan (private), vxlan (public)].
- `--json`: Format output in JSON.

---

### `ibmcloud pi network-delete`
{: #ibmcloud-pi-network-delete}

#### Delete a network

`ibmcloud pi network-delete NETWORK_ID`

- `NETWORK_ID`:  The unique ID of the network


---

### `ibmcloud pi network-update`
{: #ibmcloud-pi-network-update}

#### Update a network

`ibmcloud pi network-update NETWORK_ID [--name NETWORK_NAME] [--starting-ip IP] [--ending-ip IP] [--dns-servers "DNS1 DNS2"] [--gateway GATEWAY] [--json]`

- `NETWORK_ID`:  The unique ID of the network

**Options**

- `--name`: New name of the network.
- `--dns-servers`: Space separated list of new DNS Servers to use for this network.
- `--gateway`: New gateway to use for this network.
- `--ip-range`: New IP Addresses range(s) for this network, format: startIP-endIP[,startIP-endIP].
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume`
{: #ibmcloud-pi-volume}

#### View details of a volume

`ibmcloud pi volume VOLUME_ID [--json]`

- `VOLUME_ID`:  The unique ID of the volume

**Options**

- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-attach`
{: #ibmcloud-pi-volume-attach}

#### Attach a volume to an instance

`ibmcloud pi volume VOLUME_ID --instance INSTANCE_ID [--json]`

- `VOLUME_ID`:  The unique ID of the volume, INSTANCE_ID

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

- `VOLUME_ID`:  The unique ID of the volume


---

### `ibmcloud pi volume-detach`
{: #ibmcloud-pi-volume-detach}

#### Detach a volume from an instance

`ibmcloud pi volume VOLUME_ID --instance INSTANCE_ID [--json]`

- `VOLUME_ID`:  The unique ID of the volume, INSTANCE_ID

**Options**

- `--instance`: Instance to detach the volume from.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volume-update`
{: #ibmcloud-pi-volume-update}

#### Update a volume

`ibmcloud pi volume-update VOLUME_ID [--name NEW_NAME] [--size NEW_SIZE] [--shareable] [--json]`

- `VOLUME_ID`:  The unique ID of the volume

**Options**

- `--name`: New name of the volume.
- `--size`: New size of the volume.
- `--shareable`: New  for whether volume can be attached to multiple VMs.
- `--json`: Format output in JSON.

---

### `ibmcloud pi volumes`
{: #ibmcloud-pi-volumes}

#### List all volumes

`ibmcloud pi volumes [--json]`

**Options**

- `--json`: Format output in JSON.

---
