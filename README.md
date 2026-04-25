# monitoring-tumbleweed-config

> Umbrella repository — Full monitoring stack for openSUSE Tumbleweed

This repository is the central reference for the complete monitoring stack running on openSUSE Tumbleweed.
It links to each dedicated theme repository. Clone only the theme(s) you need.

---

## Stack

| Component    | Role                                 | Port  |
|--------------|--------------------------------------|-------|
| Prometheus   | Metrics collection and storage       | 9091  |
| Grafana      | Dashboards and alerting              | 3000  |
| Loki         | Log aggregation                      | 3100  |
| Alloy        | Log pipeline agent                   | 12345 |
| Alertmanager | Alert routing                        | 9093  |

---

## Theme repositories

| Repository | Monitoring theme | Status |
|---|---|---|
| [tumbleweed-prometheus-monitoring](https://github.com/crisis1er/tumbleweed-prometheus-monitoring) | Base stack — Prometheus, Grafana, Loki, Alloy | 🔧 In progress |
| [tumbleweed-unbound-monitoring](https://github.com/crisis1er/tumbleweed-unbound-monitoring) | Unbound DNS resolver | 🔧 In progress |
| [tumbleweed-squid-monitoring](https://github.com/crisis1er/tumbleweed-squid-monitoring) | Squid proxy | 🔧 In progress |
| [tumbleweed-caddy-monitoring](https://github.com/crisis1er/tumbleweed-caddy-monitoring) | Caddy web server | 🔧 In progress |
| [tumbleweed-node-monitoring](https://github.com/crisis1er/tumbleweed-node-monitoring) | System — CPU, RAM, disk, network, SMART | 🔧 In progress |
| [tumbleweed-network-monitoring](https://github.com/crisis1er/tumbleweed-network-monitoring) | Network probing — blackbox + ping | 🔧 In progress |
| [tumbleweed-libvirt-monitoring](https://github.com/crisis1er/tumbleweed-libvirt-monitoring) | KVM/libvirt virtual machines | 🔧 In progress |
| [tumbleweed-snmp-monitoring](https://github.com/crisis1er/tumbleweed-snmp-monitoring) | SNMP network equipment | 🔧 In progress |
| [tumbleweed-security-monitoring](https://github.com/crisis1er/tumbleweed-security-monitoring) | Security — AIDE file integrity + auditd | 🔧 In progress |

---

## Architecture

```
Prometheus (:9091)   ←  Exporters (scrape every 15s)
     ↓
Grafana (:3000)      ←  Loki (:3100)  ←  Alloy (:12345)  ←  Log files
     ↑
Alertmanager (:9093)
```

---

## Exporters

| Exporter          | Port  | Theme repo                        |
|-------------------|-------|-----------------------------------|
| node_exporter     | 9100  | tumbleweed-node-monitoring        |
| smartctl_exporter | 9633  | tumbleweed-node-monitoring        |
| blackbox_exporter | 9115  | tumbleweed-network-monitoring     |
| ping_exporter     | 9427  | tumbleweed-network-monitoring     |
| squid_exporter    | 9116  | tumbleweed-squid-monitoring       |
| unbound_exporter  | 9167  | tumbleweed-unbound-monitoring     |
| libvirt_exporter  | 9177  | tumbleweed-libvirt-monitoring     |
| snmp_exporter     | 9117  | tumbleweed-snmp-monitoring        |

---

## Platform

- openSUSE Tumbleweed (rolling release)
- SELinux enforcing
- Firewalld active

## License

GNU General Public License v3.0 — see [LICENSE](./LICENSE)
