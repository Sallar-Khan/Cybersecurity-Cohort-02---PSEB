# Day 6 — Recon Workflow & File Upload Exploitation

**Three-part assignment · DFCS Day 6 — Recon & Upload**

| | |
|---|---|
| **Author** | Sallar Ali Ahmad Khan |
| **Lab** | DVWA 1.0.7 on Metasploitable 2 (`192.168.40.130`) |

> 🔒 **Lab-only.** Every tool and technique here was run against author-controlled lab
> targets or a neutral `example.com` placeholder. Running recon, fuzzing, or upload exploits
> against any system without written authorisation is an offence under Pakistan's
> **Prevention of Electronic Crimes Act 2016 (PECA)**.

## 📄 The report

- **[Recon-and-Upload-Exploitation-Report.pdf](report/Recon-and-Upload-Exploitation-Report.pdf)** — renders inline on GitHub
- **[Recon-and-Upload-Exploitation-Report.docx](report/Recon-and-Upload-Exploitation-Report.docx)** — authoritative source

## Tasks

| # | Task | Weight | What it covers |
|---|------|:---:|----------------|
| 1 | **My recon workflow** | 35% | A repeatable 10-step recon process, each step with an explicit stopping condition, plus a justification for adding `rustscan` ahead of `nmap` (full 65,535-port sweep in seconds, then `nmap -sV -sC` depth on the open ports). |
| 2 | **DVWA file-upload walkthrough** | 40% | The upload vulnerability carried through all four DVWA security levels — Low, Medium, High, Impossible — with 13 embedded screenshots. |
| 3 | **Remediation brief** | 25% | A one-page, non-technical brief for a manager on why unrestricted upload is critical and what must change — written without jargon like "payload" or "shell". |

## File-upload walkthrough — the four levels

| Level | Outcome |
|-------|---------|
| **Low** | No validation — a `.php` file uploads and executes as `www-data`; `id` / `hostname` / `pwd` confirm remote command execution. |
| **Medium** | Client-declared type is checked; bypassed by intercepting in Burp and falsifying `Content-Type: image/jpeg`. |
| **High** | Extension/content checks force a **polyglot** — a valid 50×50 JPEG with code appended; the file is served as an image and **not executed** (bypass does not reach RCE). |
| **Impossible** | Analysed from DVWA source — content re-encoding and renaming defeat every bypass above. |

## 📸 Evidence

The [`evidence/`](evidence/) folder holds all 13 screenshots, named by figure and content
(e.g. `fig-04-cmd-id-www-data.png`, `fig-12-kali-polyglot-jpeg.png`), matching the figure
numbers in the report.

## Remediation (summary)

Re-encode every uploaded image before storing (discards appended code — defeats the
polyglot); store uploads outside the web root or where no handler executes them; validate
real file content and rename to a random safe name; and cap size / rate with alerting on
type mismatches.
