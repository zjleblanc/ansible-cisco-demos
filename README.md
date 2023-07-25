# ansible-cisco-demos

Demonstrating Ansible playbooks that can be used to support common network automation tasks.

## Use cases

| Name | Description |
| --- | --- |
| Compliance | go through cisco iOS devices, execute [show ip ssh] command, generate a report on all the devices are not compliant. modules => 2048.<br>[show vtp status] commands. checking if the IOS devices configured vtp v3 and the domain name is configured.<br>[show vtp password] making sure the password is configured. |
| Dynamic MS365 ACL | Pull list of MS365 ACLs and generate network config ACLs |
| Device Life-Cycle | Pull device life-cycle information from EOX API and report |
| Software and Firmware Updates | Use Ansible to copy a new ios version to a device and perform an update |
| Route Failover | Do a SQL query to a test SQL server if it's fails. remove the static route from the DR core switches and remove the BGP network command for the 2-production server. and puts back the commands when SQL query live. |
| Uplinks labeling | do [show cdp neighbors] on switches uplink. |
| Auditing | Find all interfaces on Vlan 900 with restricted ACL and create a report<br>Find all interfaces with restricted ACL and create a report<br>Run a “show authentication session” command and report on any interface that does not have a status of “Auth” |
| Zero-day Provisioning | Allowing plant operator to push template to a new switch |
| Change AP Names | Walk through playbook used to manage aireos devices, including updating the system name |

### Compliance

| | |
| --- | --- |
| Job Template | [Networking // Cisco Compliance](https://controller.autodotes.com/#/templates/job_template/50/details) |
| Playbook | [cisco_compliance.yml](./demo_compliance.yml) |

### Dynamic MS365 ACL

| | |
| --- | --- |
| Job Template | [Networking // MS O365 ACLs](https://controller.autodotes.com/#/templates/job_template/51/details) |
| Playbook | [o365_acls.yml](./demo_o365_acls.yml) |
| Artifacts | [json-in](./artifacts/o365_acls.json)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[acls-out](./artifacts/o365_acls.txt)

### Device Life-Cycle

| | |
| --- | --- |
| Job Template | [Networking // Cisco EOX Lifecycle](https://controller.autodotes.com/#/templates/job_template/52/details) |
| Playbook | [cisco_lifecycle.yml](./demo_lifecycle.yml) |
| Artifacts | [report](https://reports.autodotes.com/networking/demo/eox_lifecycle.html) |

### Software and Firmware Updates

| | |
| --- | --- |
| Job Template | [Networking // Cisco Upgrade (ios)](https://controller.autodotes.com/#/templates/job_template/42/details) |
| Playbook | [cisco_upgrade.yml](./demo_ios_upgrade.yml) |

### Route Failover

| | |
| --- | --- |
| Playbook | [cisco_sql_route_failover.yml](./demo_sql_route_failover.yml) |
| Description | Uses wait_for with block and rescue steps to perform actions based on availability |

### Uplinks Labeling

| | |
| --- | --- |
| Playbook | [label_cdp_neighbors.yml](./demo_label_cdp_neighbors.yml) |

### Auditing

| | |
| --- | --- |
| Playbook | [cisco_vlan_acls.yml](./demo_vlan_acls.yml) |

### Zero-day Provisioning

| | |
| --- | --- |
| Playbook | [network_config.yml](./demo_network_config.yml) |
| Description | Use the ansible.netcommon collection to apply resource based configs in a vendor agnostic manner |

### Change AP Names

| | |
| --- | --- |
| Playbook | [change_ap_name.yml](./demo_change_ap_name.yml) |
| Description | Use the aireos collection to manage access point configs, specifically sysname |
