# Risk Assessment and Security Controls

## Risk Assessment

The Harbour Accounting & Tax Solutions network has been evaluated in terms of its possible cyber security vulnerabilities with the help of the TVAMatrix tool. The audit involved the key elements of the OpenWRT environment, which comprise network security devices, Web hosting, staff computing devices, administrative access mechanisms and vital organisational information.

### Project Information

| Item | Details |
|---|---|
| Business Name | Harbour Accounting & Tax Solutions |
| Location | Sydney, Australia |
| Business Type | Accounting and Tax Consultancy |
| Group Number | 24 |
| Campus | SYD |
| Tutor | Ahmad Saeed |
| Student 1 | Syed Omair (12321346) |
| Student 2 | Sania Fatima (12319430) |
| Student 3 | Ahmed Uddin Syed (12325506) |

### Repository Files

- `README.md`
- `plan.md`
- `network.md`
- `harden.md`
- `security.md`
- `reflection.md`
- `images/`
- `captures/`
- `risk-assessment.xlsx`

### Key Assets Considered

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

### Main Risk Factors

The assessment considered several important cyber security risks, including:

- Unauthorised access to systems or client records
- Weak or reused passwords
- Interception of data during communication
- Malware infection on staff devices
- Phishing attacks against employees
- Incorrect firewall rules or poor configuration
- Denial-of-service attacks
- Exposure of unnecessary services
- Insider misuse or accidental mistakes
- Loss of system or data availability

## Highest-Risk Asset

There are different technical, administrative and operations controls that can considerably enhance the security posture of Harbour Accounting & Tax Solutions. Strong authentication (e.g., SSH key authentication) can be used to restrict access to critical systems and through firewalling and network segmentation to limit unauthorised access and lateral movement over the network. It should be secured with sensitive information being transmitted such as SSH and HTTPS transmission. This system configurations and all these client records should be periodically backed up so that in case of cyber attacks or system crashes, the records can be recovered. Moreover, continuous incident-response, ongoing security testing, personnel cyber security education, and routine software updates can be introduced in order to improve the overall security preparedness and resilience of the organisation in regard to emerging cyber threats.

# Security Controls

The client tax records were the main assets thought to be reinforced. These details might feature your client's identity, monetary information, tax records and business files. These are suggested controls to reduce the risks to this asset.

## Control 1: Strong Access Control and SSH Key-Based Administration

To minimise risk of unauthorised activities, access to systems holding or handling the client's tax data should be restricted to authorised users. Only one employee should be granted the login privilege for administrative purposes inside OpenWRT, and several means of authorized authentication should be used instead of one password: effective implementation of SSH key authentication, custom SSH port configuration as part of the project to improve the security of remote administration and minimise the risk of automated attacks. These controls help to maintain security and integrity of the network, security and integrity of network devices/services, help reduce risk of unauthorised access by a third party, and to offer an additional layer of security to the valuable business information. The effectiveness of this measure will depend on handling authentication keys: if lost or compromised, it can cause issues for operations and security if not resolved as soon as possible.

### Key Points:

- Only authorised users need to use the system.
- Limit OpenWRT administration privileges to IT support staff.
- Authenticate with SSH keys, rather than with passwords only.
- Adjust a non-default port of SSH to minimize automated attacks.
- Secure routers, firewalls and network services.
- Minimize the risks of data exposure and compromising the system.
- Ensure the safe storage and routine cleaning of SSH keys.
- At once revoke and replace lost keys.

## Control 2: Firewall Filtering and Network Segmentation

The network traffic should be managed carefully by the use of firewall policies in order to ensure that it does not open unnecessary or even harmful connections to a crucial system. Firewall policies must be used to handle the network traffic in such a way that it does not expose it to unnecessary or even damaging connections to a vital system. A segmentated network architecture can also lead to greater security, through isolation of infrastructure in hypervisor, who owns devices and services with other infrastructure, where services are publicly available.

The internal staff network is running on **46.10.10.0/24** in this configuration whereas the web server environment is on **30.10.20.0/24**. This setup minimizes the chances of sensitive business and client data being exposed to the internet-facing systems and minimizes the potential damage of a compromise of a web server. The firewall settings were set during testing to imply how HTTP, SSH, ICMP and administrative access are to be controlled and how service availability, network visibility and privileged access can be controlled to reduce the security risks and minimise attack surface.

### Additional firewall controls should include:

- Allowing only required services
- Blocking unused ports
- Restricting admin access to trusted devices
- Reviewing firewall rules regularly
- Keeping separate rules for staff LAN and DMZ traffic

## Control 3: Encrypted Communication and Regular Backup

Whenever sensitive business information is accessed or passed across the network, then secure modes of communication should be used. Traffic analysis performed at the time of the project indicated that unencrypted protocols may disclose the information in human-readable form, but encrypted protocols ensure that the information at the session cannot be viewed by unauthorised entity. That is why the administrative operations are to be carried out with the help of SSH, as well as the organisation should be designed to work with HTTPS in order to offer secure data transmission.

Moreover, there should be routine backups of valuable assets such as client records, webpage content, and network settings which should be stored in a secured place. The backup files must be periodically tested to make sure that the copy files can be recovered successfully after the system failures, inadvertent loss, cyber attacks or loss through data corruptions. Encryption and backup, when used together, enhance the protection of data as well as business continuity by ensuring the safety of the data throughout the transmission and ensuring its recovery in case of an incident. Nonetheless, such measures need constant care, such as certificate management, monitoring of backup, recovery testing, and compliance of the staff to the predefined backup guidelines to be efficient.

## Summary of Recommended Controls

The transmission of information is secured by encrypted communications protocols and frequent backups of information ensure that valuable information may be retrieved should the information be lost, the system crash or a cyber attack. Besides that, routine maintenance of systems, and awareness of their security by personnel can be implemented to make an operating environment more resilient and secure.

### Recommended Security Measures

- Strong access controls to admin systems.
- Use SSH key authentication for secure remote management.
- Protect from uncontrolled network traffic by using firewall filtering.
- Strip away internal business systems that aren't part of public facing services.
- Ensure that communication is secure using encryption protocols (for example, SSH and HTTPS).
- Regular backups of client records and configurations of system.
- Perform regular Firewall reviews and audits.
- Reduce the risks of phishing and social engineering, through staff training.
- Security Patches—Keep operating systems and applications updated.
- Design incident response/recovery procedure for cyber security incidents.

## Conclusion

The suggested precautions are coordinated in minimizing the key dangers to client tax records. The increased access control of administrative services, firewall filtering and segmentation reduce the exposure to risk, and the data is encrypted and is backed up during transmission and recovery. Such controls enable Harbour Accounting & Tax Solutions to improve the confidentiality, integrity and availability of its precious business and client data.
