# Project Reflection: Contribution Record and Group Review

## Overview

This reflection gives an overview of how the team fulfilled the OpenWRT security and networking project. The activity was documented by GitHub commit, Markdown, network diagrams, screen shots and packet captures and a risk assessment spread sheet. The commit history was also not without purpose and was beneficial, however it did not reflect all the practical actions that needed to be done as some of them included tests and troubleshooting before the final evidence may be uploaded.

## 1. Individual Contributions

| Student | Student ID | Main contribution area |
|----------|------------|----------------------|
| Syed Omair | 12321346 | OpenWRT setup, VirtualBox network docs, website setup, firewall testing, screenshots, lab and production diagrams and network.md docs. |
| Sania Fatima | 12319430 | OpenWRT hardening, SSH key authentication, service hardening, HTTP/SSH captures, Wireshark review, risk assessment, security controls, and harden.md/security.md documentation. |
| Ahmed Uddin Syed | 12325506 | Risk assessment support, network diagrams, documentation review, project validation and final verification. |

## 2. Task and Evidence Summary

| Work completed | Main contributor | Evidence used |
|---------------|------------------|--------------|
| Project planning and assumptions | Entire team | plan.md and network.md |
| OpenWRT and VirtualBox setup | Syed Omair | OpenWRT IP screenshot and VirtualBox adapter screenshots |
| Website and firewall testing | Syed Omair | Evidence of browser success screen and HTTP, ICMP, SSH and management interface |
| Lab and production network diagrams | Ahmed Uddin Syed / Entire team | draw.io files and exported network diagram images |
| Root password and hash review | Sania Fatima | Password change and /etc/shadow hash screenshots |
| SSH key authentication | Sania Fatima | Key generation and SSH login success screenshots |
| Service hardening | Sania Fatima | Enabled-services screenshot and disabled-service evidence |
| Traffic capture and analysis | Sania Fatima | HTTP/SSH pcap files and Wireshark screenshots |
| Risk assessment and controls | Entire team | risk-assessment.xlsx and security.md |
| Final reflection | Entire team | reflection.md and GitHub commit record |

## 3. Reflection on Commits

- GitHub commits were useful in following the apparent project advancement, particularly with the addition of files like Markdown reports, screenshots, diagrams, packet captures, and spreadsheets to the repository.
- Perfect individual effort was not determined by the number of commits. Certain operations, including testing of fire walls, setting up of SSH, and packet capture, needed repeating operations before the final file was committed.
- It will be better to commit every activity done rather than waiting until a number of similar steps would be done. This would enable the project history to be clearer and examinable.

## 4. Group Work Review

The team split the work into two large fields: practical configuration, and written documentation. Practical activities were done beforehand in order to be able to support the reports with actual screen shots, actual working firewall rules and active IP addresses, and actual traffic. This would increase the accuracy of the final documentation, and minimize the chances of having to write unsupported claims. Cooperation was most effective at the planning, network design, security control selection and the ultimate review phase. Another lesson learned in the project was that it's important to have the technical evidence arranged early on, as soon as screenshots and file names fall out of control with large numbers of tasks being performed side by side.

## 5. Main Technical Issues and Fixes

| Issue | Impact | How it was managed |
|--------|--------|-------------------|
| Wrong website directory | The active web path was being used: /srv/www/index.html and not /www/index.html so the old webpage kept appearing. | The proper active directory was found and the file of the website was placed in the corresponding path. |
| SSH connection errors | Modifications of the SSH port and to key-based authentication led to connection refused issues. | Dropbear configuration has been verified, the service restarted and SSH login successfully tested again. |
| Browser cache during HTTP capture | There were also some 304 Not Modified responses for some of the HTTP packets which made the capture less clear. | It was still useful for metadata of request/response and the capture problem with caching was recorded in the analysis. |
| Evidence management | Screenshots, commands, paths and ports can be confusing if not noted down immediately. | A clearer checklist and evidence log should be used in future projects. |

## 6. Added Improvement Points

- Start with a common task checklist format, including a column on task status, an evidence file name column, a column for the command(s) run, and column for comments from the Reviewer.
- Establish a common naming convention for the screenshots and packet capturing for the final report that makes auditing more straightforward.
- Write down details of trouble-shooting at once like IPs, ports, service names, exact file paths etc.
- Make smaller but more frequent commits to convey the message of technical advances and documentation advances in the GitHub history.

## 7. Final Learning Summary

Overall, the project benefitted the group in understanding their OpenWRT networking better, their VirtualBox lab design, their firewall testing processes, the hardening of SSH, their service control processes, their traffic capturing processes, their Wireshark analysing processes, and their risk-based documentation. The most critical lesson learned was that technical work and evidence management must go hand-in-hand. Once the screenshots, commands, diagram and sections of a report are lined up correctly, the final product is clearer, more trustworthy and elevates the bar to be defensible.
