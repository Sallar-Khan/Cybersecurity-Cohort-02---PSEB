# Day 3 — Vulnerability Assessment to Reporting

**VA/PT Report — Metasploitable2 Lab Assessment**

| | |
|---|---|
| **Target** | `192.168.40.130` (Metasploitable2) |
| **Attacker host** | `192.168.40.133` (Kali Linux) |
| **Network** | `192.168.40.0/24` — isolated VMware lab segment, no internet / production route |
| **Engagement** | Grey-box (target IP only, no credentials supplied) |
| **Author** | Sallar Ali Ahmad Khan |
| **Classification** | Confidential — internal lab use only |

## 📄 The report

- **[VAPT-Report-Metasploitable2.pdf](report/VAPT-Report-Metasploitable2.pdf)** — renders inline on GitHub
- **[VAPT-Report-Metasploitable2.docx](report/VAPT-Report-Metasploitable2.docx)** — authoritative source

## Summary

A single-host internal assessment focused on demonstrating real exploitation paths rather
than just listing scanner output. Services were enumerated with an Nmap service/version
scan, interrogated manually (`mysql` client, `showmount`, `rlogin`), and exploited with the
Metasploit Framework where a module existed.

### Findings

| # | Finding | Severity | CVSS |
|---|---------|----------|------|
| 1 | Apache Tomcat Manager default credentials → remote code execution | **Critical** | 9.8 |
| 2 | MySQL `root` account with no password set | **Critical** | 9.1 |
| 3 | Insecure NFS export allowing unauthenticated filesystem access | **High** | 7.4 |
| 4 | Rlogin trust relationship allowing passwordless root login | **Critical** | 9.8 |

**Totals:** 3 Critical · 1 High. An attacker with only network reachability to this host
can obtain a root shell via two independent paths and gain unrestricted access to every
database on the box — without deploying any custom exploit code.

> Apache on port 80 (DVWA / Mutillidae / phpMyAdmin) was scanned during reconnaissance but
> deliberately left out of scope for this report as a candidate for a dedicated follow-up.

### Remediation priorities

1. Remove `/etc/hosts.equiv` / `.rhosts` trust entries and disable rlogin/rsh *(Finding 4)*
2. Set a strong MySQL root password and unbind from public interfaces *(Finding 2)*
3. Rotate Tomcat manager credentials and restrict `/manager` to a management VLAN *(Finding 1)*
4. Re-scope the NFS export and enable `root_squash` *(Finding 3)*
5. Patch/upgrade all four services off their end-of-life versions *(all)*

## 📸 Evidence

The [`evidence/`](evidence/) folder holds the 16 screenshots captured during the
assessment (Nmap enumeration, manual service interrogation, exploitation sessions, and
OpenVAS scanning), numbered `evidence-01` … `evidence-16`. Full context for each is given
in the report.
