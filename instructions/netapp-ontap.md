# ONTAP Create Data Aggregates

This blueprint runs two ordered automation stages:

1. `discover_disk_class` gets and prints the cluster disk class.
2. `create_data_aggregates` creates each requested aggregate, then verifies
   that it exists on the assigned node.

## Before launch

1. Select an agent that can reach the ONTAP cluster management address over
   HTTPS.
2. Ensure the agent has the `netapp.ontap` and `torque.collections` Ansible
   collections installed. The required collections are listed in
   `assets/ansible/netapp-ontap/requirements.yml`.
3. Enter the cluster management address and ONTAP administrator credentials.
4. Fill in the aggregates table. Each row creates one aggregate:

   | Node Name | Aggregate Name | Disk Count |
   | --- | --- | --- |
   | `AA02-C800-01` | `AA02_C800_01_SSD_CAP_1` | 15 |
   | `AA02-C800-02` | `AA02_C800_02_SSD_CAP_1` | 15 |

   For an HA pair, add one row per node. For a single-node cluster, keep one
   row. To create several aggregates on the same node, repeat the node name on
   another row with a different aggregate name.

If the table renders as a text field instead of a grid, enter the same data as
JSON:

```json
[
  {"node_name": "AA02-C800-01", "aggregate_name": "AA02_C800_01_SSD_CAP_1", "disk_count": 15},
  {"node_name": "AA02-C800-02", "aggregate_name": "AA02_C800_02_SSD_CAP_1", "disk_count": 15}
]
```

Rows missing a node name, aggregate name, or a disk count above zero fail
validation before any aggregate is created, as do duplicate aggregate names.

## Result

The `aggregate_status` output reports how many aggregates were created and
verified. The deployment log labels each step as
`<aggregate_name> on <node_name>` so you can confirm the placement. The ONTAP
aggregate module is idempotent, so relaunching with the same table does not
create duplicates.
