# Cybersecurity Cohort 02 — PSEB

**Digital Forensics & Cyber Security (DFCS) Bootcamp**
Pakistan Software Export Board (PSEB) · Cohort 02

Author: **Sallar Ali Ahmad Khan**

---

This repository is my working portfolio for the PSEB DFCS bootcamp. Each module is
documented the way a real engagement would be — defined scope, captured evidence, a
reproducible proof of concept, and a prioritised remediation section — so every graded
assignment doubles as portfolio-grade practice rather than throwaway coursework.

> ⚠️ **Lab-only work.** Every offensive exercise in this repository was carried out
> inside a self-contained, isolated lab against virtual machines I own and control, with
> no route to the internet or any production network. Nothing here is intended for, or
> authorises, use against any system without explicit permission. See
> [`DISCLAIMER`](#-legal--ethics) below.

## 📂 Repository structure

| Path | What's inside |
|------|---------------|
| [`s07-report/`](s07-report/) | Full VA/PT report against Metasploitable2 — service enumeration through exploitation and remediation, with 16 evidence screenshots. |
| [`s08-client-side/`](s08-client-side/) | Client-side attacks module — malware family classification, a payload generated and caught end-to-end in the lab, and a career direction statement. |
| [`course-handouts/`](course-handouts/) | The official DFCS Day 3 and Day 4 reference handouts (PDF). |

Each day's folder contains a `README.md` summary, the report in both **`.docx`** (authoritative)
and **`.pdf`** (renders inline on GitHub) form, and an `evidence/` folder of screenshots.

## 🗂️ Modules at a glance

### Day 3 — Vulnerability Assessment → Reporting
A grey-box, single-host internal assessment of a **Metasploitable2** target. Services were
enumerated with Nmap, interrogated manually, and the real findings carried through to proof
of concept and remediation:

- **4 findings** documented — 3 Critical, 1 High
- Highest severity: **Critical (CVSS 9.8)**
- Written in standard VA/PT report format: executive summary, scope, per-finding PoC,
  prioritised remediation, references, and a raw-scan appendix.

➡️ [Read the Day 3 summary](s07-report/README.md)

### Day 4 — Client-Side Attacks
The client-side attacks module, covering how malware reaches and runs on an endpoint:

- **Malware classification** — all 9 standard families mapped to a real-world example,
  how it spread, and the primary defence.
- **Payload engineering telemetry** — a Windows payload generated, delivered, and caught
  end-to-end inside the lab, documented figure by figure.
- **Career statement** — specialism, certification roadmap (eJPT → OSCP), and a 3-month
  portfolio plan.

➡️ [Read the Day 4 summary](s08-client-side/README.md)

## 🎯 Focus & roadmap

My specialism is **offensive security / penetration testing**. Near-term goals:

- **eJPT** — aligned with the week-to-week work in this bootcamp.
- **OSCP** — once enough lab hours are banked.
- A self-built **Active Directory lab** (DC + joined workstations), attacked and written
  up end-to-end, as a first step beyond intentionally-vulnerable boxes.

## ⚖️ Legal & ethics

All testing and payload execution documented here were conducted on hardware and virtual
machines owned and controlled by the author, on an isolated network segment with no route
to the internet. No payload described here was built for, delivered to, or executed against
any system or person outside this lab, and none of this material authorises doing so
elsewhere. Under Pakistan's **Prevention of Electronic Crimes Act 2016 (PECA)**, building
or delivering an unrequested payload to any system is a criminal offence regardless of
intent — this work is legitimate only because it stayed inside a controlled lab, for the
explicit purpose of learning how each attack and its defence actually work.

## 📜 License

Released under the [MIT License](LICENSE) for the author's original writing and
documentation. Course handouts remain the property of PSEB / the DFCS bootcamp and are
included here for reference within this coursework portfolio.
