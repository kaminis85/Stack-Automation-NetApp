# NetApp ONTAP Data Aggregates

This deployment calls the reusable ONTAP aggregate blueprint. Its first block
discovers and prints the cluster disk class. Its second block creates the data
aggregates you list and verifies each aggregate on its assigned node.

## Before launch

1. Select an agent that can reach the ONTAP cluster management address over
   HTTPS. The agent needs the `netapp.ontap` and `torque.collections` Ansible
   collections, as listed in
   `netapp-sa/assets/ansible/netapp-ontap/requirements.yml`.
2. Enter the cluster management address and ONTAP administrator credentials.
3. Fill in the aggregates table, one row per aggregate:

   | Node Name | Aggregate Name | Disk Count |
   | --- | --- | --- |
   | `AA02-C800-01` | `AA02_C800_01_SSD_CAP_1` | 15 |
   | `AA02-C800-02` | `AA02_C800_02_SSD_CAP_1` | 15 |

   Add one row per node for an HA pair, or keep a single row for a single-node
   cluster.

## Result

The `aggregate_status` output reports how many aggregates were created and
verified. The deployment log labels each step as
`<aggregate_name> on <node_name>` so you can confirm the placement.
