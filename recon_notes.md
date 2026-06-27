# Reconnaissance Notes — Metasploitable2 VAPT Assessment

**Assessor:** Manikanth Pattar  
**Date:** 20/06/2026
**Target IP:** 172.19.137.4  
**Target OS:** Kali Linux  
**Assessment Type:** Black Box Penetration Test  
**Environment:** Isolated VirtualBox Lab  

---

## 1. Scope

| Item | Details |
|------|---------|
| Target | Metasploitable2 VM |
| IP Address | 172.19.137.4 |
| In Scope | All ports, services, web applications |
| Testing Window | 20/06/2026 |

---

## 2. Tools Used

| Tool | Purpose |
|------|---------|
| Nmap | Port scanning, service detection |
| Nikto | Web server vulnerability scanning |
| Gobuster | Directory brute-forcing |
| Burp Suite | Web application testing |
| Metasploit | Exploitation framework |
| SQLMap | SQL injection automation |

---

## 3. Open Ports & Services

## Open Ports and Services

## Open Ports and Services

| Port | Service | Version | Risk |
|------|----------|----------|------|
| 21 | FTP | vsftpd 2.3.4 | Critical |
| 22 | SSH | OpenSSH 4.7p1 | Medium |
| 23 | Telnet | Linux telnetd | High |
| 25 | SMTP | Postfix smtpd | Medium |
| 53 | DNS | ISC BIND 9.4.2 | Medium |
| 80 | HTTP | Apache 2.2.8 | High |
| 111 | RPCBind | RPC #100000 | Medium |
| 139 | NetBIOS | Samba smbd | High |
| 445 | SMB | Samba 3.0.20-Debian | Critical |
| 512 | rexec | netkit-rsh rexecd | High |
| 513 | rlogin | Login Service | High |
| 2049 | NFS | NFS v2-v4 | High |
| 2121 | FTP | ProFTPD 1.3.1 | High |
| 3306 | MySQL | MySQL 5.0.51a | High |
| 5432 | PostgreSQL | PostgreSQL 8.3.x | High |
| 5900 | VNC | VNC Protocol 3.3 | High |
| 6667 | IRC | UnrealIRCd 3.2.8.1 | Critical |
| 8009 | AJP13 | Apache JServ Protocol | Medium |
| 8180 | HTTP | Apache Tomcat 5.5 | High |

---

## 4. Web Directories Found

## Web Directories Discovered (Gobuster)

### Configuration Files
- `/.hta`
- `/.htaccess`
- `/.htpasswd`

### Web Applications
- `/phpMyAdmin`
- `/phpMyAdmin/`
- `/twiki`
- `/twiki/`

### Server Information Pages
- `/phpinfo`
- `/phpinfo.php`
- `/server-status`

### Application Entry Points
- `/index`
- `/index.php`

### Potentially Sensitive Directories
- `/cgi-bin/`
- `/dav`
- `/dav/`
- `/test`
- `/test/`

---

## 5. High Priority Targets

| Priority | Target                                                | Reason                                                          |
| -------- | ----------------------------------------------------- | --------------------------------------------------------------- |
| CRITICAL | FTP (21) vsftpd 2.3.4                                 | Known backdoored version (CVE-2011-2523), possible remote shell |
| CRITICAL | SMB (445) Samba 3.0.20                                | Vulnerable to usermap_script RCE → potential root access        |
| CRITICAL | IRC (6667) UnrealIRCd 3.2.8.1                         | Backdoored service allowing remote command execution            |
| CRITICAL | Shell service (1524 if present in Metasploitable lab) | Pre-installed root bind shell (direct access)                   |
| HIGH     | HTTP (80) Apache 2.2.8                                | Outdated web server with multiple known vulnerabilities         |
| HIGH     | phpMyAdmin (/phpMyAdmin)                              | Exposed DB admin panel → brute force / misconfig risk           |
| HIGH     | /phpinfo.php                                          | Sensitive information disclosure (system + config leak)         |
| HIGH     | WebDAV (/dav/)                                        | Possible file upload / overwrite → web shell risk               |
| HIGH     | Tomcat (8180)                                         | Apache Tomcat 5.5 → outdated with known exploits                |
| HIGH     | MySQL (3306)                                          | Old version, weak credentials common in lab setups              |
| MEDIUM   | PostgreSQL (5432)                                     | Legacy DB service, potential weak authentication                |
| MEDIUM   | SSH (22) OpenSSH 4.7p1                                | Old crypto + possible brute force                               |
| MEDIUM   | NFS (2049)                                            | Possible unauthorized mount/exfiltration                        |
| MEDIUM   | Telnet (23)                                           | Cleartext credentials exposure                                  |
| MEDIUM   | FTP (2121) ProFTPD 1.3.1                              | Older FTP service, potential misconfig issues                   |
