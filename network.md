# Network Setup

## Assumptions

This lab is based on a small Sydney accounting business named Harbour Accounting & Tax Solutions. The business provides accounting, taxation, bookkeeping, and compliance support for individuals and small business clients.

| Assumption | Description |
|---|---|
| Business name | Harbour Accounting & Tax Solutions |
| Location | Sydney, Australia |
| Business type | Accounting and tax consultancy |
| Number of staff | 8 staff members |
| Staff roles | 1 manager, 4 accounting consultants, 2 administrative staff, and 1 part-time IT support officer |
| Website information | Business profile, service details, student project details, hosting information, and contact purpose |

## OpenWRT and VirtualBox Setup

The lab network was built in VirtualBox using OpenWRT as the router, firewall, and web server. The Windows host was used to access OpenWRT, test connectivity, open the website, and record evidence.

The OpenWRT interface details were checked with the `ip addr` command.

![OpenWRT interface configuration](./images/openwrt-ip-addr.png)

| Interface | IP Address | Purpose |
|---|---|---|
| `lo` | `127.0.0.1/8` | Local loopback interface |
| `eth0` | No direct IP address | Connected to `br-mng` |
| `eth1` | `10.0.3.15/24` | NAT-side connectivity |
| `br-mng` | `192.168.56.2/24` | Management and website access |

VirtualBox adapters were checked to confirm the host-only and NAT network setup.

![VirtualBox Adapter 1](./images/virtualbox-adapter-1.png)

![VirtualBox Adapter 2](./images/virtualbox-adapter-2.png)

Connectivity was verified by pinging OpenWRT from the Windows host.

![Successful ping from Windows host to OpenWRT](./images/ping-openwrt-success.png)

### Test Website Setup

A simple business website was hosted on OpenWRT using `/srv/www/index.html`. The webpage includes business details, services, student names, student IDs, group number, campus, tutor, project date, and hosting purpose.

![Website index file evidence](./images/website-index-file.png)

![Website index file evidence continued](./images/website-index-file2.png)

The web server status was checked after creating the page.

![uHTTPd web server status](./images/uhttpd-status.png)

The site was opened from Windows using:

`http://192.168.56.2`

![Business website accessed from Windows host](./images/website-browser-success.png)

This confirms the OpenWRT-hosted website was reachable from the Windows host.

### Lab Network Diagram

The diagram shows the Windows host, OpenWRT VM, interfaces, IP addresses, adapters, and hosted website.

![Lab network diagram](./images/lab-network-diagram.png)

Draw.io source file: [lab-network.drawio](./lab-network.drawio)

## Firewall Configuration

Firewall rules were tested with before-and-after screenshots to prove changes in network access.

### HTTP Block and Allow

HTTP access worked before applying the block rule.

![HTTP access before blocking](./images/http-before-allowed.png)

A rule was added to block port 80.

![HTTP firewall block rule](./images/http-firewall-block-rule.png)

After blocking, the website could not be opened.

![HTTP access after blocking](./images/http-after-blocked.png)

The rule was removed to allow HTTP again.

![HTTP firewall allow rule](./images/http-firewall-allow-rule.png)

The page loaded again after HTTP was allowed.

![HTTP access after allowing](./images/http-after-allowed.png)

### ICMP Block and Allow

Ping worked before ICMP filtering.

![ICMP ping before blocking](./images/icmp-before-success.png)

ICMP traffic was then blocked.

![ICMP firewall block rule](./images/icmp-block-rule.png)

![ICMP firewall block rule continued](./images/icmp-block-rule2.png)

After blocking, ping failed.

![ICMP ping after blocking](./images/icmp-after-failed.png)

ICMP was allowed again, and ping succeeded.

![ICMP ping after allowing](./images/icmp-after-allowed.png)

### SSH Access and Port Change

SSH first worked on the default port 22.

![SSH access on port 22](./images/ssh-port22-success.png)

The SSH port was changed from 22 to 2222.

![SSH port change configuration](./images/ssh-port-change-config.png)

![SSH port change configuration continued](./images/ssh-port-change-config2.png)

Port 22 stopped working after the change.

![SSH port 22 failed after change](./images/ssh-port22-failed.png)

SSH then worked correctly on port 2222.

![SSH access on port 2222](./images/ssh-port2222-success.png)

Changing the SSH port reduces basic automated scanning, but strong authentication is still required.

### Management Interface Restriction

The management interface was reachable before restriction.

![Management interface before restriction](./images/management-port81-before.png)

A firewall rule was applied to restrict access to port 81.

![Management port 81 restriction rule](./images/management-port81-restricted.png)

![Management port 81 restriction rule continued](./images/management-port81-restricted2.png)

After the rule was applied, access from the Windows host was blocked.

![Management interface after restriction](./images/management-port81-after-blocked.png)

## Production Network Design

The production design separates staff devices from the public web server.

- Staff LAN
- Web Server DMZ

The staff LAN contains workstations, switch management, and printer. The DMZ contains the website server. This separation improves security because the public server is not placed directly inside the staff network.

| Student | Student ID | Last two digits | Used for |
|---|---:|---:|---|
| Syed Omair | `12321346` | `46` | Staff LAN |
| Sania Fatima | `12319430` | `30` | Web Server DMZ |
| Ahmed Uddin Syed | `12325506` | `06` | Project member |

The production subnets are:

- Staff LAN: `46.10.10.0/24`
- Web Server DMZ: `30.10.20.0/24`

![Production network diagram](./images/production-network-diagram.png)

Draw.io source file: [production-network.drawio](./production-network.drawio)

| Device | IP Address | Purpose |
|---|---|---|
| Router/firewall LAN interface | `46.10.10.1/24` | Staff LAN gateway |
| Internal switch management | `46.10.10.2/24` | Switch management |
| Manager workstation | `46.10.10.20/24` | Manager system |
| Administration workstation 1 | `46.10.10.21/24` | Admin work |
| Administration workstation 2 | `46.10.10.22/24` | Admin work |
| Accounting workstation 1 | `46.10.10.23/24` | Client service |
| Accounting workstation 2 | `46.10.10.24/24` | Client service |
| Accounting workstation 3 | `46.10.10.25/24` | Client service |
| Accounting workstation 4 | `46.10.10.26/24` | Client service |
| IT support workstation | `46.10.10.30/24` | IT support |
| Network printer | `46.10.10.40/24` | Printing |
| Router/firewall DMZ interface | `30.10.20.1/24` | DMZ gateway |
| Web server | `30.10.20.10/24` | Hosts the business website |
```
