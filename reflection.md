# Project Reflection

## GitHub Contribution Evidence

Throughout the project, GitHub was used to store documentation, screenshots, diagrams, packet captures, and supporting files. The commit history provides evidence of project development and individual participation.

![GitHub commit evidence](./images/github-commits.png)

## Team Contribution Summary

| Student | Student ID | Key Responsibilities |
|----------|------------|----------------------|
| Syed Omair | 12321346 | OpenWRT deployment, website hosting, firewall testing, network configuration, screenshots, network documentation |
| Sania Fatima | 12319430 | System hardening, SSH configuration, traffic capture, Wireshark investigation, security recommendations |
| Ahmed Uddin Syed | 12325506 | Risk assessment, network diagrams, documentation review, project validation |

### Activity Breakdown

| Activity | Primary Contributor | Supporting Evidence |
|-----------|-------------------|--------------------|
| Project planning | Entire team | `plan.md` |
| Business scenario development | Entire team | `network.md` |
| Interface verification | Syed Omair | `openwrt-ip-addr.png` |
| VirtualBox configuration review | Syed Omair | `virtualbox-adapter-1.png`, `virtualbox-adapter-2.png` |
| Website deployment | Syed Omair | `website-browser-success.png` |
| Firewall implementation | Syed Omair | HTTP, ICMP, SSH and management screenshots |
| Lab topology design | Ahmed Uddin Syed | `lab-network-diagram.png` |
| Production network design | Ahmed Uddin Syed | `production-network-diagram.png` |
| Password and account security review | Sania Fatima | `root-password-change.png`, `etc-shadow-hash.png` |
| SSH authentication setup | Sania Fatima | `ssh-key-generation.png`, `ssh-key-login-success.png` |
| Service reduction and hardening | Sania Fatima | `enabled-services-before.png`, `service-disabled-after.png` |
| HTTP packet investigation | Sania Fatima | HTTP capture files and screenshots |
| SSH packet investigation | Sania Fatima | SSH capture files and screenshots |
| Risk evaluation | Entire team | `risk-assessment.xlsx` |
| Security recommendations | Entire team | `security.md` |
| Reflection report | Entire team | `reflection.md` |

## Evaluation of Contributions

GitHub commits provide a useful record of repository activity; however, they do not always reflect the full amount of effort invested in a task. Several practical activities required extensive troubleshooting, testing, and verification before any files could be uploaded. As a result, some important technical work produced relatively few commits despite requiring significant effort.

Examples include firewall testing, SSH authentication configuration, packet analysis, and troubleshooting network connectivity. These tasks involved multiple attempts, verification checks, and configuration adjustments before final evidence could be collected.

The repository contains a combination of Markdown reports, screenshots, packet captures, diagrams, and risk assessment documents. Together, these files provide a complete record of the work completed by the team.

The project benefited from regular collaboration during planning, deployment, testing, hardening, analysis, and documentation stages. Future projects would benefit from more frequent individual commits so that contribution records better represent ongoing progress.

## Reflection on Teamwork

The project was completed by dividing responsibilities between technical implementation and documentation tasks. Practical activities were completed first so that the report could be supported by genuine screenshots, real configuration data, tested firewall rules, packet captures, and verified results. This approach improved consistency between the technical work and written documentation.

One challenge encountered involved locating the correct web directory used by the OpenWRT server. Initially, changes were made in the wrong location, which caused outdated webpage content to continue appearing. The issue was resolved after identifying the correct directory and updating the active website files.

Another difficulty involved SSH administration. Modifying the SSH port and enabling key-based authentication occasionally caused connection failures due to incorrect settings. The issue was resolved by reviewing Dropbear configuration files, restarting services, and retesting connections until successful access was restored.

Traffic analysis also presented challenges. During HTTP packet inspection, cached responses such as "304 Not Modified" appeared in several captures. While these packets still provided useful information, they highlighted the influence of browser caching on network analysis activities.

For future projects, maintaining a shared checklist and documenting technical issues immediately would improve efficiency. Recording file locations, commands, IP addresses, and configuration changes during implementation would reduce troubleshooting time and simplify report preparation.

Overall, this project strengthened understanding of OpenWRT administration, VirtualBox networking, firewall rule management, SSH security, packet capture techniques, Wireshark analysis, and the importance of aligning technical evidence with professional documentation.
```
