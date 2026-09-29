# ONTAP Primary Setup

This blueprint runs the non-Fibre-Channel tasks from the FlexPod `ontap_primary_setup` role, in the same order. Each task runs. There is no per-task enable switch.

Fill every field the way the role's variable files are filled before `Setup_ONTAP.yml`. The only conditions copied from the role are:

- Cluster HA is changed only when `ha_pair_count` is 1.
- Licenses use legacy keys or NLF contents, based on `license_key_format`.
- FIPS mode is set from `is_fips_enabled`. Community and traphost SNMP are skipped when FIPS is enabled.
- The other SNMP tasks run only when `enable_snmp` is true.

## Before launch

1. Select an agent that can reach the ONTAP cluster management address over HTTPS.
2. The agent needs the `netapp.ontap` and `torque.collections` collections listed in `assets/ansible/netapp-ontap/requirements.yml`.
3. Enter the cluster address, credentials, and the values for each task.

## Result

`disk_class` is the class read from cluster disks. `aggregate_status` reports how many aggregates were created and verified.
