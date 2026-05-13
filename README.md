What's in the ZIP
01-enterprise-network-design/

ACC-SW-1.cfg — Full access switch config (VLANs, portfast, bpduguard, SSH, port-security, syslog)
DIST-SW-1.cfg — Distribution switch with HSRP (active/standby), OSPF, STP root, inter-VLAN routing, ACLs
WAN-EDGE-RTR.cfg — BGP to ISP, OSPF redistribution, NAT/PAT, WAN ACL
docs/validation-checklist.md — How to verify every protocol after deployment

02-datacenter-rack-installation/

README.md — 8-step DC installation guide: site survey, rack elevation, PDU sizing, structured cabling (TIA-942), hot/cold aisle, cable testing, handover docs
rack-layout/R01-network-rack.md — Full 42U rack elevation with device positions, management IPs, cable schedule

03-network-automation/

bgp_policy_push.py — Python/Netmiko script: renders Jinja2 templates, backs up before pushing, auto-rollback if BGP drops
bgp_policy.j2 — Jinja2 template for prefix-lists and route-maps
vlan_provision.yml — Ansible playbook: add/remove VLANs across all switches with pre/post verification
compliance_checker.py — Nornir+NAPALM parallel compliance scan with Slack alerting
compliance_rules.yaml — 14 security/hardening rules (SSH v2, no telnet, BPDU guard, NTP, etc.)

04-troubleshooting-runbooks/

L3-03-bgp-session-down.md — BGP state machine explanation + systematic isolation to root cause
DC-02-thermal-alert.md — Thermal incident response: single device → rack → room-wide HVAC failure

05-monitoring-and-alerting/

telegraf.conf — SNMPv3 polling (CPU, memory, interface counters, BGP state) + gNMI streaming + ping probes
docker-compose.yml — One-command docker-compose up -d spins up Telegraf + InfluxDB + Grafana

.github/workflows/ci.yml — CI pipeline: black formatter, flake8, ansible-lint, Jinja2 render test, YAML schema validation, Gitleaks secret scan
