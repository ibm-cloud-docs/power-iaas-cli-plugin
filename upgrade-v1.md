---

copyright:
  years: 2024
lastupdated: "2024-01-23"

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
{{site.data.keyword.attribute-definition-list}}

#  What’s new in IBM {{site.data.keyword.powerSys_notm}} CLI V 1.0 
{: #whats-new-v1}

In this Upgrade Guide, you will find a concise overview of the changes and improvements made in the {{site.data.keyword.powerSysFull}} command-line interface (CLI) as we transition from version 0.7.1 to 1.0.0. This topic highlight any modifications that may affect your usage and is tailored to facilitate a smooth transition to the latest release, enabling you to seamlessly leverage the enhanced capabilities of our CLI.

The following tables in the section below shows what’s changed in the new V 1.0.0 comparing with the V 0.7 version.

## ibmcloud pi cloud-connection
{: connection}

<!-- Insert table here -->

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi connection-create      | ibmcloud pi cloud-connection create     |
| ibmcloud pi connection-delete      | ibmcloud pi cloud-connection delete     |
| ibmcloud pi cloud-connection       | ibmcloud pi cloud-connection get        |
| ibmcloud pi connection-update      | ibmcloud pi cloud-connection update     |
| ibmcloud pi connections            | ibmcloud pi cloud-connection list       |
| ibmcloud pi connection-vpcs        | ibmcloud pi connection-vpcs             |

## ibmcloud pi cloud-connection subnet
{: connect-subnet}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi connection-attach-network      | ibmcloud pi cloud-connection subnet attach      |
| ibmcloud pi connection-detach-network      | ibmcloud pi cloud-connection subnet detach      |

## ibmcloud pi disaster-recovery
{: dr}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi disaster-recovery-locations     | ibmcloud pi disaster-recovery      |

## ibmcloud pi ike-policy
{: ike}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi vpn-ike-policy-add     | ibmcloud pi ike-policy create      |
| ibmcloud pi vpn-ike-policy-delete  | ibmcloud pi ike-policy delete      |
| ibmcloud pi vpn-ike-policy         | ibmcloud pi ike-policy get         |
| ibmcloud pi vpn-ike-policies       | ibmcloud pi ike-policy list        |
| ibmcloud pi vpn-ike-policy-update  | ibmcloud pi ike-policy update      |

## ibmcloud pi image
{: image}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi image-create          | ibmcloud pi image create          |
| ibmcloud pi image-delete          | ibmcloud pi image delete          |
| ibmcloud pi image                 | ibmcloud pi image get             |
| ibmcloud pi image-export          | ibmcloud pi image export          |
| ibmcloud pi image-export-show     | ibmcloud pi image export-show <br/> Note: The 'image export-show' now displays information about the latest image export job without requiring a 'job_id' parameter. |
| ibmcloud pi image-import          | ibmcloud pi image import          |
| ibmcloud pi image-import-show     | ibmcloud pi image import-show     |
| ibmcloud pi image-list-catalog    | ibmcloud pi image list-catalog    |
| ibmcloud pi images                | ibmcloud pi image list            |

## ibmcloud pi instance
{: instance}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
|ibmcloud pi instance-create    | ibmcloud pi instance create   |
|ibmcloud pi instance-delete    | ibmcloud pi instance delete   |
|ibmcloud pi instance           | ibmcloud pi instance get      |
|ibmcloud pi instances          | ibmcloud pi instance list     |
|ibmcloud pi instance-operation | ibmcloud pi instance operation|
|ibmcloud pi instance-update    | ibmcloud pi instance update   |

## ibmcloud pi instance sap
{: inst-sap}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
|ibmcloud pi sap-create-instance    | ibmcloud pi instance sap create |
|ibmcloud pi sap-profile            | ibmcloud pi instance sap profile|
|ibmcloud pi sap-list               | ibmcloud pi instance sap list   |

## ibmcloud pi instance action
{: inst-action}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
|ibmcloud pi instance-hard-reboot <br/> ibmcloud pi instance-reset-state <br/> ibmcloud pi instance-soft-reboot <br/> ibmcloud pi instance-start <br/> ibmcloud pi instance-stop <br/> ibmcloud pi instance-immediate-shutdown | ibmcloud pi instance action |

## ibmcloud pi instance capture
{: inst-capture}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
|ibmcloud pi instance-capture       | ibmcloud pi instance capture create   |
|ibmcloud pi instance-capture-show  | ibmcloud pi instance capture show     |

## ibmcloud pi instance console
{: inst-console}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi instance-get-console              | ibmcloud pi instance console get     |
| ibmcloud pi instance-list-console-languages   | ibmcloud pi instance console list    |
| ibmcloud pi instance-update-console-language  | ibmcloud pi instance console update  |

## ibmcloud pi instance snapshot
{: inst-snap}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi instance-list-snapshots   | ibmcloud pi instance snapshot list    |

## ibmcloud pi instance subnet
{: inst-subnet}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi instance-attach-network       | ibmcloud pi instance subnet attach  |
| ibmcloud pi instance-detach-network       | ibmcloud pi instance subnet detach  |
| ibmcloud pi instance-networks             | ibmcloud pi instance subnet list    |

## ibmcloud pi instance volume
{: inst-vol}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi volume-attach | ibmcloud pi instance volume attach    |
| ibmcloud pi volume-detach | ibmcloud pi instance volume detach    |

## ibmcloud pi ipsec-policy
{: ipsec}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi vpn-ipsec-policy-add      | ibmcloud pi ipsec-policy create   |
| ibmcloud pi vpn-ipsec-policy-delete   | ibmcloud pi ipsec-policy delete   |
| ibmcloud pi vpn-ipsec-policy          | ibmcloud pi ipsec-policy get      |
| ibmcloud pi vpn-ipsec-policies        | ibmcloud pi ipsec-policy list     |
| ibmcloud pi vpn-ipsec-policy-update   | ibmcloud pi ipsec-policy update   |

## ibmcloud pi job
{: job}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi job-delete    | ibmcloud pi job delete  |
| ibmcloud pi job           | ibmcloud pi job get     |
| ibmcloud pi jobs          | ibmcloud pi job list    |

## ibmcloud pi placement-group
{: pg}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi placement-group-create        | ibmcloud pi placement-group create        |
| ibmcloud pi placement-group-delete        | ibmcloud pi placement-group delete        |
| ibmcloud pi placement-group               | ibmcloud pi placement-group get           |
| ibmcloud pi placement-groups              | ibmcloud pi placement-group list          |
| ibmcloud pi placement-group-server-add    | ibmcloud pi placement-group server-add    |
| ibmcloud pi placement-group-server-remove | ibmcloud pi placement-group server-remove |

## ibmcloud pi shared-processor-pool
{: spp}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi shared-processor-pool-create |ibmcloud pi shared-processor-pool create  |
| ibmcloud pi shared-processor-pool-delete |ibmcloud pi shared-processor-pool delete  |
| ibmcloud pi shared-processor-pool        |ibmcloud pi shared-processor-pool get     |
| ibmcloud pi shared-processor-pools       |ibmcloud pi shared-processor-pool list    |
| ibmcloud pi shared-processor-pool-update |ibmcloud pi shared-processor-pool update  |


## ibmcloud pi shared-processor-pool placement-group
{: spp-pg}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi spp-placement-group-create        | ibmcloud pi shared-processor-pool placement-group create        |
| ibmcloud pi spp-placement-group-delete        | ibmcloud pi shared-processor-pool placement-group delete        |
| ibmcloud pi spp-placement-group               | ibmcloud pi shared-processor-pool placement-group get           |
| ibmcloud pi spp-placement-groups              | ibmcloud pi shared-processor-pool placement-group list          |
| ibmcloud pi spp-placement-group-member-add    | ibmcloud pi shared-processor-pool placement-group member-add    |
| ibmcloud pi spp-placement-group-member-remove | ibmcloud pi shared-processor-pool placement-group member-remove |

## ibmcloud pi snapshot
{: snap}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi snapshot-create       | ibmcloud pi snapshot create   |
| ibmcloud pi snapshot-delete       | ibmcloud pi snapshot delete   |
| ibmcloud pi snapshot              | ibmcloud pi snapshot get      |
| ibmcloud pi snapshots             | ibmcloud pi snapshot list     |
| ibmcloud pi snapshot-restore      | ibmcloud pi snapshot restore  |

## ibmcloud pi ssh-key
{: ssh-key}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi key           | ibmcloud pi ssh-key get       |
| ibmcloud pi key-create    | ibmcloud pi ssh-key create    |
| ibmcloud pi key-delete    | ibmcloud pi ssh-key delete    |
| ibmcloud pi key-update    | ibmcloud pi ssh-key update    |
| ibmcloud pi keys          | ibmcloud pi ssh-key list      |

## ibmcloud pi storage-pools
{: storage-pool}

| V 0.7  | V 1.0 |
| ------------- |:-------------:
|ibmcloud pi storage-pools  | ibmcloud pi storage-pools <br/> (Unchanged) |

## ibmcloud pi subnet
{: subnet}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi network-create-private <br/> ibmcloud pi network-create-public <br/> Note: The commands that have changed in ppc-aas.    | ibmcloud pi subnet create |
| ibmcloud pi network-delete    | ibmcloud pi subnet delete   |
| ibmcloud pi network           | ibmcloud pi subnet get      |
| ibmcloud pi networks          | ibmcloud pi subnet list     |
| ibmcloud pi network-update    | ibmcloud pi subnet update   |

## ibmcloud pi system-pools
{: sys-pool}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi system-pool   | ibmcloud pi system-pools  |

## ibmcloud pi volume
{: vol}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi volume-action                     | ibmcloud pi volume action                     |
| ibmcloud pi volume-create                     | ibmcloud pi volume create                     |
| ibmcloud pi volume-delete                     | ibmcloud pi volume delete                     |
| ibmcloud pi volume-flash-copy-mapping         | ibmcloud pi volume flash-copy-mapping         |
| ibmcloud pi volume                            | ibmcloud pi volume get                        |
| ibmcloud pi volumes                           | ibmcloud pi volume list                       |
| ibmcloud pi volume-remote-copy-relationship   | ibmcloud pi volume remote-copy-relationship   |
| ibmcloud pi volume-update                     | ibmcloud pi volume update                     |

## ibmcloud pi volume-clone
{: vol-cone}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi volume-clone          | ibmcloud pi volume clone get      |
| ibmcloud pi volume-create-clone   | ibmcloud pi volume clone create   |

## ibmcloud pi volume-group
{: vol-group}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi volume-group-create                       | ibmcloud pi volume-group create                     |
| ibmcloud pi volume-group-delete                       | ibmcloud pi volume-group delete                     |
| ibmcloud pi volume-group                              | ibmcloud pi volume-group get                        |
| ibmcloud pi volume-groups                             | ibmcloud pi volume-group list                       |
| ibmcloud pi volume-group-remote-copy-relationships    | ibmcloud pi volume-group remote-copy-relationships  |
| ibmcloud pi volume-group-storage-details              | ibmcloud pi volume-group storage-details            |
| ibmcloud pi volume-group-update                       | ibmcloud pi volume-group update                     |

## ibmcloud pi volume-group action
{: vol-group-action}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi volume-group-reset        | ibmcloud pi volume-group action reset |
| ibmcloud pi volume-group-start        | ibmcloud pi volume-group action start |
| ibmcloud pi volume-group-stop         | ibmcloud pi volume-group action stop  |

## ibmcloud pi volume-onboarding
{: vol-onboard}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi volume-onboarding-create      | ibmcloud pi volume onboarding create  |
| ibmcloud pi volume-onboarding             | ibmcloud pi volume onboarding get     |
| ibmcloud pi volume-onboardings            | ibmcloud pi volume onboarding list    |

## ibmcloud pi vpn
{: vpn}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
|       | ibmcloud pi vpn create    |
| ibmcloud pi vpn-connection-delete      | ibmcloud pi vpn delete    |
| ibmcloud pi vpn-connection             | ibmcloud pi vpn get       |
| ibmcloud pi vpn-connections            | ibmcloud pi vpn list      |
| ibmcloud pi vpn-connection-update      | ibmcloud pi vpn update    |

## ibmcloud pi vpn peer-subnet
{: vpn-peer-subnet}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi vpn-connection-peer-subnet-attach     | ibmcloud pi vpn peer-subnet attach  |
| ibmcloud pi vpn-connection-peer-subnet-detach     | ibmcloud pi vpn peer-subnet detach  |
| ibmcloud pi vpn-connection-peer-subnets           | ibmcloud pi vpn peer-subnet list    |

## ibmcloud pi vpn subnet
{:vpn-subnet}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi vpn-connection-network-attach | ibmcloud pi vpn subnet attach |
| ibmcloud pi vpn-connection-network-detach | ibmcloud pi vpn subnet detach |
| ibmcloud pi vpn-connection-networks       | ibmcloud pi vpn subnet list   |

## ibmcloud pi workspace
{: workspace}

| V 0.7  | V 1.0 |
| ------------- |:-------------:|
| ibmcloud pi service-list      | ibmcloud pi workspace list    |
| ibmcloud pi service-target    | ibmcloud pi workspace target  |


## Removed Commands
{: removedcmd}

ibmcloud pi task <br/>
ibmcloud pi task-delete

## New Commands
{: newcmd}

ibmcloud pi instance volume-list