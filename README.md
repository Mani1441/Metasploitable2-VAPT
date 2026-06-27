# Metasploitable2 — Full-Scope VAPT Assessment

End-to-end black box penetration test on Metasploitable2 in an isolated 
VirtualBox lab. 10 vulnerabilities documented with professional PDF report.

## Summary

| Item | Details |
|------|---------|
| Target | Metasploitable2 |
| Type | Black Box Penetration Test |
| Environment | Isolated VirtualBox Lab |
| Total Findings | 10 |
| Critical | 6 |
| High | 2 |
| Medium | 2 |

## Findings

| # | Finding | Severity | CVSS | OWASP |
|---|---------|----------|------|-------|
| 1 | SQL Injection | Critical | 9.8 | A03:2021 |
| 2 | Reflected XSS | Medium | 6.1 | A03:2021 |
| 3 | Unrestricted File Upload | Critical | 9.8 | A04:2021 |
| 4 | Command Injection | Critical | 9.8 | A03:2021 |
| 5 | vsftpd 2.3.4 Backdoor | Critical | 10.0 | A06:2021 |
| 6 | Samba usermap_script RCE | Critical | 10.0 | A06:2021 |
| 7 | UnrealIRCd Backdoor | Critical | 10.0 | A06:2021 |
| 8 | Credential Exposure | Critical | 9.0 | A02:2021 |
| 9 | No Brute Force Protection | Medium | 5.3 | A07:2021 |
| 10 | Cleartext Telnet Service | High | 7.5 | A02:2021 |

## Tools Used
Nmap · Nikto · Gobuster · Burp Suite · Metasploit · SQLMap · Netcat

## Full Report
[Download PDF Report](report/Metasploitable2_VAPT_Report.pdf)

## Disclaimer
This assessment was performed on an intentionally vulnerable VM in a 
completely isolated lab for educational and portfolio purposes only.

**Assessor:** Manikanth Pattar  
**LinkedIn:** linkedin.com/in/manikanthpattar1441  
**GitHub:** github.com/Mani1441# Metasploitable2-VAPT
Full-scope Vulnerability Assessment and Penetration Testing on Metasploitable2 — 10 findings documented with professional VAPT report
