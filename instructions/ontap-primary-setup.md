# ONTAP Primary Setup

The launch form does not show run or skip switches. Leave a section blank and that task stays skipped. Enter values and that task runs.

Required fields are the agent, cluster management address, username, and password. You can click Next and Finish with only those filled in.

Service-processor, aggregate, and data-port values are plain text. Leave them blank. A table widget inserts an empty row, and that empty row keeps Finish disabled.

| Filled in | Task that runs |
| --- | --- |
| Cluster name and location | Update cluster location |
| Cluster management interface | Set auto-revert on that interface |
| Node port counts | Delete default broadcast domains |
| Service-processor rows | Configure the service processor |
| Aggregate rows | Discover the disk class and create aggregates |
| `ha_pair_count` set to 1 | Enable cluster HA |
| Data-port rows | Disable flow control |
| DNS domain and DNS servers | Configure DNS |
| NTP servers | Configure NTP |
| Node names | Enable storage failover |
| Cluster name and timezone | Set the timezone |
| Node names plus AutoSupport mail settings | Configure AutoSupport |
| Legacy license keys or NLF contents | Add licenses |
| `true` or `false` in FIPS | Set SSL FIPS mode |
| Any SNMP contact, location, user, community, or traphost | Configure SNMP |
| Login banner text | Set the login banner |

CDP, LLDP, and spare-disk zeroing have no values to enter, so those grains stay skipped.
