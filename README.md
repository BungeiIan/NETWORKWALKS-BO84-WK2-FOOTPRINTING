# NETWORKWALKS-BO84-WK2-FOOTPRINTING

Week 2 practical work from the **Networkwalks Cybersecurity & Ethical Hacking Program** (Batch B084): reconnaissance and footprinting of a lab target, followed by host discovery on a local network.

**Author:** Ian Bungei Imbayi, Cybersecurity & Ethical Hacking student, Networkwalks

---

## Overview

This repository holds the report and evidence for two Week 2 modules:

| Module | Topic | Environment |
|---|---|---|
| **W2-PM1** | Footprinting with multiple Kali tools | Kali Linux |
| **W2-PM5** | Network scanning with Zenmap | Windows |

Together they follow the first two phases of a penetration test:

1. **Reconnaissance & Footprinting**: gather what the outside world can see about a target.
2. **Scanning & Network Discovery**: work out which machines are alive on a network.

Phases 3 to 5 will be covered in later modules.

## Targets

- **networkwalks.com**: the course's designated lab target (footprinting).
- **My own Windows network (192.168.5.0/24)**: a Mobile Hotspot I control (scanning).

> **Scope note:** my Wi-Fi network is shared and I have no permission to test it, so I did not scan it. All scanning was done on the hotspot network I own.

## Tools Used

| Tool | Purpose |
|---|---|
| `whois` | Domain registration data: registrar, key dates, name servers |
| `whatweb` | Website fingerprinting: web server, CMS, plugins, scripts |
| `nslookup` | Resolves the domain name to an IP address |
| `curl -I` | Fetches only the HTTP response headers |
| `wafw00f` | Detects a Web Application Firewall |
| `dnsrecon` | Enumerates DNS records: NS, MX, SPF/TXT, SRV |
| Zenmap (Nmap GUI) | Discovers live hosts, IP and MAC addresses, topology |
| Windows CMD (`ipconfig`) | Local IP address, subnet mask, gateway and MAC address |

## Commands Run

**Footprinting (Kali Linux)**

```bash
whois networkwalks.com
whatweb networkwalks.com | tee whatweb_output.text
nslookup networkwalks.com | tee nslookup_output.txt
curl -I https://networkwalks.com
wafw00f networkwalks.com | tee wafw00f_output.txt
dnsrecon -d networkwalks.com | tee dnsrecon_output.txt
```

**Scanning (Windows)**

```cmd
ipconfig /all
```

Zenmap target `192.168.5.0/24` with the Ping scan profile (`nmap -sn 192.168.5.0/24`), then the Topology tab.

## Report Contents

The full write-up is in the Word report in this repository. It contains:

1. Liability disclaimer
2. Introduction
3. Tools used
4. Activities performed (footprinting and Zenmap scanning)
5. Risk analysis / impact
6. Recommendations
7. Conclusion
8. Evidences collected (Figures 1 to 9)

## Repository Contents

```
.
├── PM1_footprinting_reconnaisance/     # Footprinting evidence and tool output (whois, whatweb, nslookup, curl, wafw00f, dnsrecon)
├── PM1_zenmap_scanning/        # Zenmap scan and topology evidence, ipconfig output
├── W2-PM-FINAL_Footprinting_and_Network_Scanning_Report_B084.docx
└── README.md
```

## Key Takeaway

A lot can be learned about an environment before any exploitation takes place. Careful reading of public data and network replies already builds a detailed picture, and defenders can get the same picture by running these tools against their own systems.

## Disclaimer

Everything in this repository was carried out only on systems I own or was authorised to test, as part of an assigned educational lab. It is provided for education and research. Accessing a system without permission is a criminal offence in most countries, even when nothing is damaged. Networkwalks, its instructors and the author accept no responsibility for how this material is used.

The findings are observations from reconnaissance and host discovery, not confirmed vulnerabilities. Nothing was exploited.
