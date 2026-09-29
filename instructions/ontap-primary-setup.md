# ONTAP Primary Setup

This is one blueprint. Each task has its own `run` or `skip` choice, and every choice defaults to `skip`.

The cluster management address, username, and password are required. Select an agent as well, because that is where the tasks run. Leave every action on `skip` to move through Next and Finish without configuring anything else.

Set an action to `run` to show and apply that task. For DNS and NTP only, set `dns_action` and `ntp_action` to `run`, fill those fields, and leave the other actions on `skip`.

| Action | Task |
| --- | --- |
| `cluster_location_action` | Cluster name and location |
| `cluster_mgmt_action` | Cluster management interface |
| `broadcast_domains_action` | Delete default broadcast domains |
| `sp_network_action` | Service-processor addresses |
| `aggregates_action` | Disk class discovery and aggregate creation |
| `zero_spares` | Zero spare disks |
| `cluster_ha_action` | Cluster HA when `ha_pair_count` is 1 |
| `flow_control_action` | Disable flow control on listed data ports |
| `cdp` / `lldp` | Enable CDP or LLDP |
| `dns_action` / `ntp_action` | DNS or NTP |
| `storage_failover` | Enable takeover |
| `timezone_action` | Cluster timezone |
| `autosupport_action` | AutoSupport |
| `license_key_format` | `skip`, `legacy`, or `NLF` |
| `is_fips_enabled` | `skip`, `true`, or `false` |
| `snmp_action` | SNMP |
| `login_banner_action` | Login banner |
