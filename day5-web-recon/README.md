# Day 5 — Web Application Reconnaissance & Scanning

**Four-part assignment (25% each) · DFCS Day 5 — Web Pentest & Recon**

| | |
|---|---|
| **Author** | Sallar Ali Ahmad Khan (firm: Devsecplus) |
| **Scope of exercises** | Task 1 hypothetical; Tasks 2–3 a private bug-bounty program (invite-held); Task 4 a local, deliberately-vulnerable lab |

> 🔒 **Redaction note.** Tasks 2 and 3 were performed on a private bug-bounty program with a
> non-disclosure rule. The company, its domain, and third-party names are replaced with
> placeholders such as `target.example`. Screenshots for those tasks are held privately by
> the author, not embedded.

## 📄 The report

- **[Web-Recon-and-Scanning-Report.pdf](report/Web-Recon-and-Scanning-Report.pdf)** — renders inline on GitHub
- **[Web-Recon-and-Scanning-Report.docx](report/Web-Recon-and-Scanning-Report.docx)** — authoritative source

## Tasks

| # | Task | What it covers |
|---|------|----------------|
| 1 | **Scope & Rules of Engagement** | A full RoE for a hypothetical `*.intel.com` web assessment — objective & methodology, in-scope / exclusions, data handling, a break-glass clause, and a step-by-step emergency procedure. |
| 2 | **Dork Report** | Six real exposures on an authorised target, each with the exact dork used (Google operators, Wayback CDX, GitHub code search), the result, and the fix. |
| 3 | **Subdomain Reconciliation** | Three tools (subfinder, amass, crt.sh) merged into one deduplicated list — what each tool found alone, and why. |
| 4 | **Scanner Comparison — ZAP vs Burp** | OWASP ZAP and Burp Suite Professional run against the same target (Mutillidae), what each caught that the other missed, false positives, and what neither found. |

## 📸 Evidence

The [`evidence/`](evidence/) folder holds the raw scanner output backing Task 4:

- **[ZAP-Report.html](evidence/ZAP-Report.html)** — OWASP ZAP scan report
- **[burp-mutillidae.html](evidence/burp-mutillidae.html)** — Burp Suite scan report

> GitHub shows these as source rather than rendering them; download and open in a browser to
> view the formatted reports.

## Key takeaway (Task 4)

Burp was more thorough per page (more input points, out-of-band confirmation, client-side
analysis); ZAP covered more of the server surface and gave more configuration feedback. The
practical conclusion: run **ZAP for broad, free, repeatable coverage** (e.g. in CI) and
**Burp for deep testing** of important pages — then confirm both manually, since neither
tool's raw output should reach a client unverified.
