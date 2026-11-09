# Day 4 — Client-Side Attacks

**Client-Side Attacks Report — Malware Classification, Payload Telemetry & Career Statement**

| | |
|---|---|
| **Target environment** | Isolated VMware lab, host-only / internal segment |
| **Target workstation** | Windows 10 (author-owned VM, snapshotted before the exercise) |
| **Author** | Sallar Ali Ahmad Khan |
| **Module** | DFCS Day 4 — Client-Side Attacks |

> ⚠️ All payload work below was performed inside a self-contained lab on machines owned by
> the author, with no route to the internet and nothing delivered to any outside system.

## 📄 The report

- **[Client-Side-Attacks-Report.pdf](report/Client-Side-Attacks-Report.pdf)** — renders inline on GitHub
- **[Client-Side-Attacks-Report.docx](report/Client-Side-Attacks-Report.docx)** — authoritative source

## Task 1 — Malware classification (9/9 families)

All nine standard malware families mapped to a real-world example, its spread mechanism,
and the primary defence:

| Family | Example | Primary defence |
|--------|---------|-----------------|
| Virus | Melissa (1999) | Disable macros on externally-sourced documents |
| Worm | Conficker (2008) | Patch MS08-067; disable removable-media autorun |
| Trojan | Zeus (2007) | Staff training + application allowlisting |
| Ransomware | WannaCry (2017) | Patch MS17-010; disable SMBv1 |
| Spyware | FinFisher (2011) | Vet software sources; tuned endpoint detection |
| Adware | Fireball (2017) | Restrict installs to vetted sources |
| Rootkit | TDL-4 / TDSS (2011) | Patch the drive-by entry point |
| Botnet agent | Mirai (2016) | Change default IoT creds; block inbound telnet |
| Fileless | Astaroth (2019) | Behavioural detection (e.g. Sysmon → SIEM) |

## Task 2 — Payload engineering & execution telemetry

A Windows payload generated, delivered, and caught end-to-end inside the lab, documented
figure by figure in the [`evidence/`](evidence/) folder:

| Figure | Evidence | Shows |
|--------|----------|-------|
| 3.1 | `fig-3.1-msfvenom.png` | Payload generation |
| 3.2 | `fig-3.2-handler-full.png`, `fig-3.2-handler-zoom.png` | Handler setup, including the port correction |
| 3.3 | `fig-3.3-http-log.png` | Delivery via local HTTP server — access log confirms download |
| 3.4 | `fig-3.4-taskmgr.png` | Target process confirmation via Task Manager |
| 3.5 | `fig-3.5-session-getsystem.png` | Session established, identity confirmed, privilege escalation |

**Remediation** emphasises UAC set to *Always notify*, SmartScreen / application control to
block unsigned executables outright, behavioural monitoring (Sysmon → SIEM) for anomalous
process parentage, prompt patching, and removing unnecessary local-admin membership.

## Task 3 — Career statement

Specialism: **offensive security / penetration testing**. Certification roadmap: **eJPT**
near-term, **OSCP** to follow. Three-month portfolio goal: the eJPT earned, five–six fully
written-up HackTheBox / TryHackMe boxes, and a self-built Active Directory lab attacked and
documented end-to-end.
