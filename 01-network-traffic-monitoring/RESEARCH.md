## Research Methods
As a SOC analyst, investigation is 70% documentation and research, 30% tools. This section documents my repeatable workflow for finding, validating, and documenting threat intelligence during incident investigation.

### 1. Information Evaluation Framework
Before acting on any finding, I validate credibility using four criteria:
- **Source**: Is the author or organization reputable and authoritative?
- **Evidence**: Are claims backed by hard facts and logical reasoning?
- **Objectivity**: Is the information impartial or pushing a product/agenda?
- **Corroboration**: Do multiple independent reliable sources agree on the central claims?

### 2. Advanced Search Operators
I use Google dorks to locate technical documentation and threat reports quickly instead of relying on the first 5 results:
- `"exact phrase"` - Find specific terminology
- `site:[domain]` - Limit searches to trusted domains like `site:mitre.org` or `site:tryhackme.com`
- `-` (minus) - Exclude irrelevant results like `-tourism` when researching "pyramids"
- `filetype:[pdf|docx|xls]` - Locate reports and presentations, e.g. `filetype:pdf "cyber warfare report"`
- **Resource**: [Advanced Search Operators List](https://github.com/cipher387/Advanced-search-operators-list) for platform-specific controls

### 3. Threat Intelligence Platforms
| Tool | Purpose | URL |
| :--- | :--- | :--- |
| **Shodan** | Discover internet-connected devices, servers, and IoT equipment | [shodan.io](https://www.shodan.io) |
| **Censys** | Audit certificates and internet assets for rogue infrastructure | [censys.com](https://censys.com) |
| **VirusTotal** | Scan files and URLs against multiple antivirus engines | [virustotal.com](https://www.virustotal.com) |
| **Have I Been Pwned** | Check if credentials appeared in data breaches | [haveibeenpwned.com](https://haveibeenpwned.com) |
| **GitHub** | Search for Proof-of-Concept (PoC) and exploit code related to CVEs | [github.com](https://github.com) |

### 4. Vulnerability & Exploit Research
- **CVE (Common Vulnerabilities and Exposures)**: Use unique identifiers like `CVE-2014-0160` (Heartbleed) to ensure consistent reference across the industry
    - Resources: [MITRE CVE](https://cve.mitre.org), [NVD](https://nvd.nist.gov)
- **Exploit Database**: [exploit-db.com](https://www.exploit-db.com) for verified exploit codes and context

### 5. Technical Documentation
Official documentation is my primary source for accurate, up-to-date technical details:
- **Linux Man Pages**: `man [command]` e.g. `man ip` for networking utilities and configuration files
- **Microsoft Technical Documentation**: Official portal for Windows commands like `ipconfig`
- **Product Docs**: [Snort](https://snort.org/documents), [Apache HTTP Server](https://httpd.apache.org/docs/), [PHP](https://www.php.net/docs.php), [Node.js](https://nodejs.org/en/docs/)

### 6. Social Media & OSINT Awareness
- **LinkedIn**: Research professional and technical background of employees during security evaluations
- **Personal Privacy**: Be aware of oversharing that could reveal answers to security questions like "Which school did you go to?"
- **Staying Updated**: Follow SOC and threat intelligence channels to track new trends and TTPs

### 7. Practical Application Example
**Scenario**: Investigating suspicious Apache server traffic
1. Search Shodan for `apache 2.4.1` to identify exposed servers and their geographic distribution
2. Cross-reference CVE identifiers with NVD for vulnerability context  
3. Check official Apache documentation for expected configuration behavior
4. Document all findings with timestamps and source links for SOC handover
