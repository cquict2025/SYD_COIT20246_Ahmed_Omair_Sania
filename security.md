# Risk Assessment and Security Controls

## Risk Assessment

[View risk assessment spreadsheet](./risk-assessment.xlsx)

# Security Controls

A short cyber security risk review was completed using the TVAMatrix for **Harbour Accounting & Tax Solutions**. The assessment focused on a small OpenWRT-based business network that included the router/firewall, hosted website, staff devices, administration access, and sensitive business information.

The key project members used for this updated version are:

- **Syed Omair** — `12321346`
- **Sania Fatima** — `12319430`
- **Ahmed Uddin Syed** — `12325506`

The main assets reviewed were:

| Asset | Asset Type | Reason for Including |
|---|---|---|
| Client tax records | Data | Holds private client, tax, and financial details |
| Staff login details | Data | Used for system and service access |
| Website files | Data | Contains public business website content |
| Firewall settings | Configuration | Controls network access rules |
| OpenWRT router/firewall | Hardware/software | Main security and routing device |
| Web server service | Service | Hosts the business website |
| Staff computers | Hardware | Used for normal business work |
| IT support computer | Hardware | Used for admin and troubleshooting tasks |

Important risks included:

- Unauthorised access
- Weak passwords
- Data interception
- Malware infection
- Phishing
- Firewall misconfiguration
- Denial of service
- Exposed services
- Insider misuse
- Loss of availability

The highest-risk asset was **client tax records** because the business handles tax, identity, and financial information. If this data is leaked, changed, or lost, the business may face privacy issues, financial loss, legal concerns, reputation damage, and loss of client trust.

The practical project work supported this assessment. Firewall testing showed how HTTP, SSH, ICMP, and management access can be controlled. Hardening tasks showed why password security, SSH keys, and service reduction matter. Traffic analysis also proved that HTTP exposes readable details, while SSH protects session data through encryption.

## Security Controls

**Client tax records** were selected as the main asset for protection. The following controls reduce the most serious risks.

### Control 1: Strong Access Control and SSH Key-Based Administration

Access should be limited to authorised users only. OpenWRT administration should be handled by trusted IT support users. SSH key-based login should be used instead of password-only access.

This control helps by:

- Reducing brute-force login risk
- Protecting router administration
- Limiting unauthorised configuration changes
- Improving access control for sensitive systems

The weakness is that SSH keys must be managed carefully. Lost or stolen private keys can create access problems or security risks.

### Control 2: Firewall Filtering and Network Segmentation

Firewall rules should restrict unnecessary traffic. The production network should separate staff devices from the public web server.

- Staff LAN: `46.10.10.0/24`
- Web Server DMZ: `30.10.20.0/24`

This setup reduces direct exposure of internal staff systems. HTTP, SSH, ICMP, and management access should only be allowed where required.

### Control 3: Encrypted Communication and Regular Backup

Sensitive administration and data transfer should use encrypted communication. SSH should be used for administration, and HTTPS should replace plain HTTP for website traffic.

Backups should also be created for:

- Client records
- Website files
- Firewall settings
- Important business documents

Backups must be stored safely and tested regularly.

### Summary of Recommended Controls

| Control | Risk Reduced | Implementation in Scenario |
|---|---|---|
| Strong access control and SSH keys | Unauthorised admin access | Restrict admin access and use SSH keys |
| Firewall filtering and segmentation | Unwanted access and lateral movement | Separate Staff LAN and DMZ |
| Encryption and backups | Data exposure and data loss | Use SSH/HTTPS and maintain secure backups |

Together, these controls protect client tax records from unauthorised access, network exposure, interception, and loss.