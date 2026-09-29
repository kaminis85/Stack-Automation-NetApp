# Stack-Automation-NetApp

ONTAP primary setup packaged for Stack Automation from the FlexPod Base IMM role `roles/ONTAP/ontap_primary_setup`.

```
assets/ansible/netapp-ontap/   one playbook per task group
blueprints/ontap-primary-setup.yaml
graphics/netapp.svg
instructions/ontap-primary-setup.md
```

One blueprint chains the grains. A new task is a new playbook plus a grain in that blueprint, not a new blueprint.
