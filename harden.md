# Security Hardening and Traffic Analysis

This document wraps up the OpenWRT hardening work and packet-capture analysis in a concise and clear manner. The same topic is maintained and here and there sentences have been rewritten or reworked, key points have been included.

## 1. Overview of Completed Security Work

| Area | Action Completed | Security Purpose |
|--------|----------------|------------------|
| Account Protection | Root password was changed using the passwd command. | Prevents unauthorized access through default or weak credentials. |
| Password Storage | The /etc/shadow file was reviewed to verify that passwords are stored as hashes. | Protects password information by ensuring it is not stored in plain text. |
| SSH Access | An ED25519 SSH key pair was generated and the public key was added to Dropbear authorized keys. | Enhances authentication security by using key-based login instead of passwords. |
| Service Reduction | The rpcd service was identified and disabled after reviewing active services. | Minimizes the attack surface by reducing unnecessary running services. |
| Traffic Review | Network traffic was captured with tcpdump and examined in Wireshark, including HTTP and SSH sessions. | Demonstrates the security difference between unencrypted and encrypted communications. |

## 2. OpenWRT System Hardening

### 2.1 Change of Root Password

A stronger password was used instead of the default OpenWRT root password by use of passwd command. A simple but crucial hardening measure as routers and firewalls are high value targets. Unchanged credentials can enable unauthorized users to administer the system.

![Root password change](./images/root-password-change.png)

Key benefit: Is that password guessing is more difficult, and casual / automated password attacks are less likely to be successful.

### 2.2 Checking Password Storage

A password storage file /etc/shadow was checked to ensure it is stored as hash and not as plaintext. A hash will not tell you the exact password used. Even if the attacker can see the file, he still needs to do hash cracking and only then can he find the actual password.

![Password hash in /etc/shadow](./images/etc-shadow-hash.png)

Further explanation, if necessary, access to /etc/shadow should still be tightly controlled because sometimes the weak password may be cracked from hash.

### 2.3 SSH Key-Based Authentication

Here the key comment was generated with an SSH key pair on the Windows host as keylab at user. The public key was put in the authorized_keys in the Dropbear file OpenWRT. The successful results were obtained after this setup by using the corresponding private key.

![SSH key generation](./images/ssh-key-generation.png)

![SSH key login success](./images/ssh-key-login-success.png)

A key-based login method is more secure than a password-only method since the attacker must possess the key, not just a guessed password. It also minimizes chances of brute-force break-in efforts towards the router.

### 2.4 Disabling an Unnecessary Service

OpenWRT services were reviewed before making changes. Hardening evidence was rpcd service disabling since it provides management-related remote procedure call functionality. The elimination of unnecessary services will reduce the attack surface. Critical services were not turned off. Network, firewall, Dropbear, uhttpd and dnsmasq services were running as they are necessary to be connected, access SSH, test the firewall, and provide DNS/DHCP services and test web pages.

![Enabled services before hardening](./images/enabled-services-before.png)

![Service disabled after hardening](./images/service-disabled-after.png)

### 2.5 Hardening Checklist

- Use strong administrative passwords and avoid default credentials.
- Prefer SSH key-based login for administration.
- Disable services that are not needed for the lab or production role.
- Keep essential services enabled to avoid breaking connectivity.
- Record evidence with screenshots and command outputs for verification.

## 3. Network Traffic Analysis

Traffic was first logged on OpenWRT using technique of tcpdump and then analyzed in Wireshark in the windows machine. Two packet captures were done one being HTTP traffic on port 80, and the other being SSH traffic on port 22.

### 3.1 HTTP Traffic Capture

The traffic on HTTP was taken as the windows host accessed the test site of the Sydney TaxCare Services.

![tcpdump HTTP capture command](./images/tcpdump-http-command.png)

The given packets of the HTTP protocol were easily readable under Wireshark filter.

![Wireshark HTTP request](./images/wireshark-http-request.png)

The capture indicated that the Windows host 192.168.56.1 was sending a request to the OpenWRT web server at 192.168.56.2 in the form of a GET / HTTP/1.1 request.

![Wireshark HTTP response](./images/wireshark-http-response.png)

![Wireshark HTTP visible content](./images/wireshark-http-visible-content.png)

The HTTP reply of OpenWRT was also in a readable form with status and header information. This proves that the HTTP traffic is not encrypted. Request methods, URLs, IP addresses, metadata in the form of headers and other metadata can be seen by anyone who controls the traffic. When sensitive page content is sent using the HTTP, the content can also be leaked.

### 3.2 SSH Traffic Capture

The data for SSH was collected via an admin SSH session on the Windows host to the OpenWRT host.

![tcpdump SSH capture command](./images/tcpdump-ssh-command.png)

Wireshark filter ‘ssh' displayed the SSH handshake and key exchange process as well as encrypted packets sent between 192.168.56.1 and 192.168.56.2.

![Wireshark SSH packets](./images/wireshark-ssh-packets.png)

![Wireshark SSH encrypted payload](./images/wireshark-ssh-encrypted-payload.png)

The content of the SSH session was not readable as plaintext, unlike with HTTP. All commands in the session were packaged in encrypted payloads. This is why SSH makes sense as a means of remote administration for routers, firewalls and other network devices.

## 4. HTTP and SSH Comparison

| Feature | HTTP | SSH |
|----------|------|-----|
| Encryption | Standard HTTP does not provide encryption. | Communication is encrypted after the SSH handshake process. |
| Visibility in Wireshark | Request methods, URLs, headers, and response information can be viewed directly. | Only connection metadata and encrypted packets are visible. |
| Primary Risk | Network traffic may expose sensitive information to an attacker. | Session contents are protected from unauthorized viewing. |
| Recommended Use | Suitable only for non-sensitive testing unless secured with HTTPS. | Recommended for secure remote administration and command-line access. |
| Security Insight | Plaintext protocols can expose data while it travels across the network. | Encryption helps maintain confidentiality and integrity during transmission. |

## 5. Conclusion

Configuring the root password, ensuring the hashed password system is enabled and private SSH keys are used for logging on, along with disabling an unused management service are all improvements to the OpenWRT system. These actions help minimize common vulnerabilities and the access provided by the attacker. Furthermore, the traffic analysis revealed that there is a distinct pattern between the security of HTTP and SSH. Through the use of HTTP, the information in the requested and received can be read; the activity on SSH is encrypted and protected. Encrypted protocols and no running services should be considered as "must" security measures for secure network-device management.
