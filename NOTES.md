# Resume & Job Hunting — Session Notes
*Reference file for future Claude sessions. Last updated: May 27, 2026.*

---

## Quick Start for Claude

Tell Claude: "Read NOTES.md in my Resume-JobHunting folder before we start."

Key facts to know before making any edits:
- **Master archive is the source of truth.** All tailored resumes derive from it.
- **Always regenerate PDFs after editing .md files** (see PDF Generation section below).
- **Do not remove content from Boot.Dev.md** — it's Allen's personal notes combining Full Stack + DevOps tracks.
- **Teleperformance and Convergys** are shown with total umbrella tenure + individual contracts underneath.

---

## File Structure

### resumes/ — Master Archive
Each 2026-05-26 resume has three files: `.md` (source), `.tex` (LaTeX), `.pdf` (compiled output).

| File | Purpose |
|---|---|
| `2026-05-26 - Allen Schultz - Resume Archive (Master).md/.tex/.pdf` | Complete employment history — all jobs, all skills. Source for all tailored resumes. |
| `2026-05-26 - Allen Schultz - Resume Archive (Master) - Georgia.tex/.pdf` | Georgia font variant (XeLaTeX) — same content as Master, no separate .md |

### resumes/ — Tailored Resumes (current)
| File | Target Role |
|---|---|
| `2026-05-26 - Allen Schultz - IT Tech Support Resume.md/.tex/.pdf` | Help Desk, Tier 1–3 IT Support, Desktop Support |
| `2026-05-26 - Allen Schultz - Data Entry Resume.md/.tex/.pdf` | Data Entry, Order Processing, Administrative Support |
| `2026-05-26 - Allen Schultz - DevOps Engineer Resume.md/.tex/.pdf` | Linux Admin, DevOps Engineer, Infrastructure Automation |
| `2026-05-26 - Allen Schultz - General Admin Office Resume.md/.tex/.pdf` | Office Admin, Clerical, Customer Service, Virtual Assistant |
| `2026-05-26 - Allen Schultz - NOC Technician Resume.md/.tex/.pdf` | NOC Technician, Network Admin, Network Operations |

### resumes/ — Archived (do not update)
- `2025-12-29 - Allen Schultz - Resume Long.md/.pdf` — superseded by Master Archive
- `2025-12-29 - Allen Schultz - Linux Systems Administrator Resume.md` (full and shortened)
- `2025-12-29 - Allen Schultz - Data Entry Resume Structure 1pg.md`
- `2025-12-30 - Allen Schultz - Data Entry Resume.md/.pdf`
- `2025-12-30 - Allen Schultz - Resume.pdf`

### cover-letters/ — Generic Templates (undated — living documents)
| File | Target Role |
|---|---|
| `Allen Schultz - Cover Letter - Generic (IT Linux Admin).md` | General IT / Linux roles |
| `Allen Schultz - Cover Letter - Linux Admin.md` | Linux Administrator |
| `Allen Schultz - Cover Letter - DevOps.md` | DevOps Engineer / SRE |
| `Allen Schultz - Cover Letter - Network Admin.md` | Network roles |
| `Allen Schultz - Cover Letter - Data Entry Generic.md` | Data Entry |

### cover-letters/ — Specific Applications (dated)
| File | Job Applied For |
|---|---|
| `2025-12-31 - Allen Schultz - Cover Letter - NOC - RedHelm.md` | NOC Technician I — RedHelm |
| `2026-01-12 - Allen Schultz - Cover Letter - DevOps - Digia.md` | DevOps — Digia |
| `2026-04-23 - Allen Schultz - Cover Letter - Network Admin - ODOT.md` | Network Admin — ODOT |
| `2026-04-26 - Allen Schultz - Cover Letter - REAL ID Specialist - ODOT.md` | REAL ID Specialist — ODOT |
| `2026-04-26 - Allen Schultz - Cover Letter - Roseburg Litter Patrol - ODOT.md` | Litter Patrol — ODOT (physical; hold until post-surgery) |
| `2026-04-26 - Allen Schultz - Cover Letter - Kroger.txt` | General role — Fred Meyer/Kroger |
| `2026-06-15 - Allen Schultz - Cover Letter - Dispatch Coordinator - ODOT.md` | Dispatch Coordinator — ODOT (REQ-201132, **submitted Jun 15, under review**) |

### education/ — Transcripts & Academic Records
| File | Purpose |
|---|---|
| `~/Documents/EMCC Unofficial Transcript.txt` | Copied to PhoenyxCullen/education/ on GitHub. Confirms: Certificate of Completion, Networking Administration: Cisco (Dec 1999); CNT 140/150/160/170 Cisco sequence; BPC 170 A+ Prep; CIS 162 C Programming. Cumulative GPA 3.468. |
| `~/Documents/Allen_Estrella_Mountain_Transcript.pdf` | Official Parchment PDF — same data as above. |
| `~/Documents/SLCC Transcript.txt` | Official transcript (emailed), copied to PhoenyxCullen/education/ on GitHub. Key credentials: AS Computer Science (Aug 2004); Certificate of Proficiency, Linux System Administration (Aug 2017). Key courses: Unix Internals, Linux System Admin I & II, Certified Ethical Hacker, Data Communications/Networking, Software Engineering, Fundamentals of Database Management, Technical Writing. WGU (2010–2011, not completed) — earned CIW Web Foundations Associate there, then dropped due to finances. |

### Root — Utility Files
| File | Purpose |
|---|---|
| `Boot.Dev.md` | Personal notes on Boot.dev Full Stack + DevOps curriculum |
| `staffing_agencies_quick_reference.md` | Local/regional staffing agency contacts |
| `job_hunting_log.csv` | Application tracking spreadsheet |
| `NOTES.md` | This file |

---

## PDF Generation

PDFs are generated directly from LaTeX source (`.tex` files). Two compile workflows:

### Latin Modern (pdflatex) — 6 files
Recompile a single file (two passes required for correct "Page X of Y" footer):
```bash
cd "/home/allen/Projects/Resume-JobHunting/resumes"
pdflatex -interaction=nonstopmode "FILENAME.tex" > /dev/null && \
pdflatex -interaction=nonstopmode "FILENAME.tex" > /dev/null && \
rm -f *.aux *.log *.out
```
Recompile all 6 LM files at once:
```bash
cd "/home/allen/Projects/Resume-JobHunting/resumes" && \
for f in \
  "2026-05-26 - Allen Schultz - Resume Archive (Master)" \
  "2026-05-26 - Allen Schultz - IT Tech Support Resume" \
  "2026-05-26 - Allen Schultz - Data Entry Resume" \
  "2026-05-26 - Allen Schultz - DevOps Engineer Resume" \
  "2026-05-26 - Allen Schultz - General Admin Office Resume" \
  "2026-05-26 - Allen Schultz - NOC Technician Resume"; do
  pdflatex -interaction=nonstopmode "${f}.tex" > /dev/null && \
  pdflatex -interaction=nonstopmode "${f}.tex" > /dev/null && \
  echo "OK: ${f}.pdf"
done && rm -f *.aux *.log *.out
```

### Georgia variant (xelatex) — 1 file
```bash
cd "/home/allen/Projects/Resume-JobHunting/resumes"
xelatex -interaction=nonstopmode "2026-05-26 - Allen Schultz - Resume Archive (Master) - Georgia.tex" > /dev/null && \
xelatex -interaction=nonstopmode "2026-05-26 - Allen Schultz - Resume Archive (Master) - Georgia.tex" > /dev/null && \
rm -f *.aux *.log *.out
```

### Font specs (all 2026-05-26 .tex files)
- **LM files (6):** `extarticle` 9pt body / `\fontsize{11}{13.2}` section headers / `\footnotesize` (8pt) tagline+contact
- **Georgia file (1):** same `extarticle` 9pt + `fontspec` `\setmainfont[Ligatures=NoCommon]{Georgia}` — xelatex only

### Font specs (all 2026-05-26 .tex files)
- **All resumes:** all-black (`\definecolor{accent}{RGB}{0,0,0}`) — no colored text anywhere
- **LM files (6):** `extarticle` 9pt body / `\fontsize{11}{13.2}` section headers / `\footnotesize` (8pt) tagline+contact
- **Georgia file (1):** `extarticle` 9pt body / `\fontsize{9.5}{11.4}` section headers (`\singlespacing`) / `\small` tagline+contact — xelatex only

### Georgia Master section design
```
0.8pt black rule → (−2pt) → HEADER TEXT → (−8pt) → 0.3pt gray rule → 4pt → content
titlespacing: {0pt}{−5pt}{4pt}
```

### ATS compliance baked into all .tex files
- No ligature glyphs: `\DisableLigatures{encoding=*,family=*}` (LM) / `Ligatures=NoCommon` (Georgia)
- No math-mode glyphs: `\textasciitilde{}` not `$\sim$`; literal `->` not `$\rightarrow$`
- `\widowpenalty=9999` / `\clubpenalty=9999` — prevents orphaned single lines at page breaks
- `beginpenalty=9999, midpenalty=9000` in `\setlist[itemize]` — bullet blocks stay with their job/project headers
- Page footer on all files: "Allen Schultz | Page X of Y" (fancyhdr + lastpage; requires 2 compile passes)

---

## Key Facts About Allen's Background

### Employment (reverse chronological)
- **Uber Eats** — Independent contractor, 2023–2026 approx. (dates TBD — verify). DWS classifies as accessory income.
- **Harry and David (1800Flowers Team Services Inc)** — Seasonal Data Entry Associate. Official employer of record: **1800FLOWERS TEAM SERVICES INC**, PO BOX 712, Medford OR 97501. Three deployments (exact dates for unemployment/official use):
  - Season 1: **Sept 27, 2023 – Jan 5, 2024**
  - Season 2: **Oct 9, 2024 – Feb 7, 2025**
  - Season 3: **Sept 3, 2025 – Jan 2, 2026**
  - First day ever: Sept 27, 2023. Last day ever: Jan 2, 2026.
  - Separation reason: Laid off due to lack of work (seasonal end).
  - Keyboard typing into order management system. HR line: 541-864-2082.
- **Superior Service Transport** — Driver Check-in Clerk/Scheduling, Apr–Jul 2023. Verified/scanned transport orders; weekly load/route optimization ("tetris" truck space). Specialized transport management system.
- **Caregiving gap** — 2014–2023. Maintained skills through personal lab projects and self-study.
- **RidgeCrest Herbals** — Linux Sysadmin & VoIP Admin, May 2012–Feb 2014. SSH/in-person support mostly. FreeSWITCH migration, PXE/TFTP automation.
- **ITT Systems (DoD, Afghanistan)** — Network Admin, Sep 2009–May 2010. Primary: Cisco (VLANs, ACLs, routing). Secondary: Windows workstation provisioning (OS/Office/DoD settings), AD computer/user account management, SATCOM/crypto maintenance.
- **Teleperformance USA** — Total tenure May 2005–Oct 2008, three contracts:
  - Dell Tier 2 (Jul 2007–Oct 2008): TeamViewer remote support (user goes to site, enters one-time code)
  - Clearwire (Apr 2006–Jul 2007): VoIP SME, Email Specialist
  - Cox TV (May 2005–Mar 2006): AS/400 database access when Java app down
- **USPS** — Data Conversion Operator, Dec 2001–Jan 2004. Address IMAGE CODING (building#, 3-digit street code, city/state code from mail piece image) — NOT general typing. Production coding speed. Under 4% error rate.
- **Convergys** — Total tenure Apr 2000–Nov 2001, two contracts:
  - AT&T T1 installations (Aug 2000–Nov 2001): Cisco/Paradyne router config, layer 1–3 troubleshooting
  - @Home Internet Support (Apr–Aug 2000): AS/400 database access when app down
- **EMCC Computer Lab** — Student worker, Sep 1997–Dec 1999. Lab support, LAN setup project.
- **Del Webb Corporation** — Accounting Intern (high school), Oct 1996–Apr 1997. Paper filing/records, AS/400 data entry.

### Certifications — Full List
**Active:** CompTIA A+ (2007) · CompTIA Security+ (2010) · Linux Essentials — LPI (2023)
**Academic Credentials (Education section):** AS Computer Science — SLCC (Aug 2004) · Certificate of Proficiency, Linux System Administration — SLCC (Aug 2017) · Certificate of Completion, Networking Administration: Cisco — EMCC (Dec 1999)
**In Progress:** LFCS · LFCE (Linux Foundation)
**Historical (Certifications section):** Cisco CCNA · Dell Tier 2 Hardware Certification · AT&T Provisional Technical Engineer · Clearwire VoIP SME · CIW Web Foundations Associate (earned at WGU, 2010–2011) · CIW Web Languages: JavaScript Fundamentals · Networking Administration: Cisco — EMCC Certificate of Completion (1999)

### Skills — Important Distinctions
- **USPS coding speed ≠ typing speed.** USPS was numeric code lookup from address images, not typing full text.
- **Typing speed:** ~60–80 WPM (estimated, not currently certified).
- **Spreadsheets:** Basic proficiency — can use formulas and look things up, not independently advanced.
- **Remote desktop:** TeamViewer specifically at Dell Tech Support. RidgeCrest was SSH + in-person. ITT Systems was Cisco + AD, no remote desktop.
- **AS/400:** Used at Del Webb (accounting), @Home (backdoor DB access), Cox TV (backdoor DB access when Java app down).
- **Java:** Academic (Windows). Uses Java apps on Linux (MegaMek/OpenJDK) but has not programmed in Java on Linux.
- **C/C++:** Academic. EMCC = macOS 6–9 and Windows. SLCC = Windows and Linux.
- **Office suites:** MS Office 97–2010, Google Workspace, LibreOffice — "once you learn one you know them all."
- **Uber Eats:** Independent contractor, not formal employment. Dates approximate — verify before putting on applications.

### Boot.dev Projects
- Local repos: `~/Repos/bootdotdev/`
  - `bookbot/` — Python guided project. Completed Apr 25, 2026. **github.com/PhoenyxCullen/bookbot**
  - `webflyx/` — Git Ops 1 / Learn Git guided project. Completed Apr 25, 2026. **github.com/PhoenyxCullen/webflyx**
- Curriculum order: Python → Linux → Bookbot → Learn Git (Webflyx) → **Docker → CI/CD → Kubernetes** (priority track) → then OOP, Data Structures, Go, SQL (see Boot.Dev.md)
- Rationale for reorder: Docker/CI/CD/Kubernetes most directly hireable for DevOps roles; Go/OOP/DS deferred but not skipped

### Physical / Availability
- Surgery May 18, 2026 (cecectomy — appendix + large intestine section removed). No heavy lifting ~4–6 weeks (through late June/early July 2026).
- Available immediately for desk and remote work.
- Seeking income sufficient for apartment. Current situation: not enough income.

### Preferences
- Strong preference for remote work.
- Open to temp, contract, or permanent.
- Salary: $46,500+/yr ($22.36/hr minimum).

---

## Week of Jun 16 — Schedule & Goals

- **5 applications this week, minimum 1/day**
- **Heat strategy:** Sleep through afternoon heat (Afghanistan-style), Uber early + evening
- **Wed Jun 17:** Early Uber → Chick-fil-A breakfast → post free RV wanted ad → oncology form → 1 app → 6:30 PM bowling (talk to Pam re: JRV 3rd reference)
- **Thu Jun 18:** Talk to Chelle, Rich, Dennis (housing) → 1 app → Uber cool hours
- **Fri–Sun:** 3 more apps
- **Sun Jun 22:** File OED weekly claim for Jun 15–21

---

## Health — PCP & Follow-ups

- **PCP:** Daniel Wood, DO — 541-732-8000
- **Appointment: Monday Jun 22 — COMPLETED — Sage G. Sherer, PA-C** — Providence Primary Care Central Point — details in medical/ (encrypted)
  - **Community Resource Desk referral** — left VM, callback pending — (541) 601-6793 (Sylvia)
    - Locations: Stewart Meadows Medical Plaza, 70 Bower Dr Medford OR (2nd floor sports med lobby); PMG Central Point, 870 S Front St Central Point OR (main 1st floor lobby)
- **Appointment: Tuesday Jun 23, 11:00 AM — Clinical Support Regular (BP check)** — Providence Primary Care Central Point, 870 S Front St Suite 200, Central Point OR 97502 — 541-732-8000
- **Appointment: Monday Aug 3, 10:00 AM — Wellness visit, Daniel P. Wood, DO** — arrive 9:45 AM
- **Chiropractor:** McFarland Chiropractic — (541) 772-5000 — 308 Howard St, Medford OR — $48/visit — left VM Jun 22 ~5:30 PM — awaiting callback
- **Oncology appointment: July 1, 2026** — arrive 1:50 PM, appt 2:20 PM (1 hour) — NP Consult with Radhika Gali, MD
  - Asante Heimann Cancer Center Hematology Oncology, 3011 E Barnett Rd, Medford OR 97504 — 541-789-4673
  - Cannot cancel online — must call to cancel
  - Questionnaires available Jun 24, 2026 in MyChart
  - Form: filled out Jun 19, 2026

---

## Oregon Unemployment (OED) — Status
- **Weekly claim Jun 14–20: FILED** — confirmation # 0-014-235-471 — reported $85.05 Uber Eats earnings, 7 hrs

- Claim filed June 2026. Claim #: 001-2242885 | Claimant ID: 0001-1070971
- **WBA: $204/week | MBA: $3,022 total**
- Benefit begin: Jun 7, 2026 / Eligible through: Jun 5, 2027
- Wages confirmed correct: $9,067.36 / 567 hrs from 1800Flowers (base year)
- **Identity Verification: DONE — completed Jun 16, 2026 at USPS post office**
- **Weekly claim for Jun 8-14: FILED**
- Wage appeal deadline: June 22, 2026 — no action needed (wages accurate)
- **Weekly claim must be filed each week** — 3 job search activities required, at least 1 direct employer contact
- Must report all Uber Eats earnings each week (partial benefits still paid above threshold)
- **A First Choice Staffing Service** (also "The Medical Registry") — (541) 776-7505 — 1150 Crater Lake Ave Ste K, Medford OR 97504 — Mon–Thu 8am–5pm, Fri 8am–noon — has Allen's info, actively circulating to medical employers as of Jun 22, 2026 — no responses back yet — check in periodically
- **211 call: DONE** — confirmation in email
- **ACCESS** — (541) 779-6691 — 3630 Aviation Way, Medford OR — housing coordinated entry / Centralized Interest List — Mon–Thu 7:30am–6pm, Fri 8am–4:30pm — left VM Jun 22
- **ACCESS (rent assistance line per Sylvia/Providence)** — (541) 414-0317
- **Sylvia — Providence Community Resource Desk** — (541) 601-6793 — referred by Dr. Sage Jun 22 — left VM Jun 22 ~5:15 PM re: housing + rent assistance — awaiting callback
- **AllCare Health Flexible Services** — (888) 460-0185 — OHP members only — internet assistance + rent assistance (up to 6 months for established rentals) — care coordinator calls back — left VM Jun 22
- **Housing Authority of Jackson County** — (541) 779-5785 — affordable/subsidized rentals, waitlists — Mon–Thu 8am–4:30pm

---

## Health — Recipes
- BP/LDL/pre-diabetes meal: Rice + Madras Lentils + Eggs — see `~/Documents/recipes/rice-lentils-eggs.md`

---

## Bookmarks
- karl-voit.at — German researcher into personal information management systems: file naming schemes, tag directories, email organization, hard drive structure, system of systems for storing/sorting/filing data

---

## Deadlines — Financial
- **Vehicle registration expires July 20, 2026 — $166 renewal due** — required to continue Uber Eats
- **End of June 2026 — need $650–800 to move to new place** (researched on FB Marketplace)
- **Still no free RV found** — post "looking for free RV, I do NOT have one to sell/give" on Facebook

## Income — Urgent (June 2026)
- **Uber Eats** — fastest income, start evenings after Dr. Sage appointment Jun 22
- **Spark Driver** (Walmart delivery) — apply at sparkdriver.com, background check 2-5 days
- **Mom's executor** — ask about another $1,000 advance from estate
- **OED** — Jun 14-20 claim filed, payment pending — check when it hits
- **Leave 10 mins before appointments** — e.g. 3:35 PM for 3:45 PM Dr. Sage

---

## Health Log — Design Spec (Future Implementation)

### Data Source: bp_log.csv
- Keep ALL historical data in the CSV forever — never delete rows
- Log: date, time, systolic, diastolic, pulse, SpO2, HRV RMSSD, stress, resp rate, weight, notes/symptoms
- Garmin Venu 3 tracks sleep quality — must wear all night for sleep data

### Print Workflow (to implement)
1. Decrypt bp_log.csv from GPG
2. Script pulls last ~3 months of rows
3. Formats into a clean LaTeX table
4. Injects into Personal Health Summary before compiling
5. Compiles PDF (2 passes pdflatex), prints, cleans up unencrypted files

### Printed Table Format
Columns: Date | Time | Sys | Dia | Pulse | SpO2 | HRV | Notes
Footer: Monitor: Microlife BP3GY1-2N | Watch: Garmin Venu 3 | Scale: Taylor 5329324

### Why 3 months
- Clinical standard for BP trend analysis (PCP/cardiologist)
- Full history stays in CSV for specialists/insurance if needed

---

## Keyboard — Cooler Master MK770

- Model: MK-770-MCKR1-US (Kailh Box V2 Linear Red, Bluetooth/2.4GHz, hot-swap)
- Ordered Jun 10, delivered Jun 16 to KNH — **picked up Jun 16, in car**

---

## Suggested Job Roles to Apply For

All are desk/remote-friendly and suitable during surgery recovery:

| Role | Best Resume to Use |
|---|---|
| IT Help Desk / Desktop Support Tier 1–2 | IT Tech Support |
| NOC Technician / Network Operations Analyst | NOC Technician |
| Linux System Administrator | DevOps Engineer |
| DevOps Engineer / SRE | DevOps Engineer |
| VoIP / Telephony Administrator | DevOps or Master Archive |
| Data Entry / Order Processing | Data Entry |
| Administrative Assistant / Virtual Assistant | General Admin Office |
| Remote Customer Service (Technical) | IT Tech Support or General Admin |
| Technical Writer / Documentation | General Admin or DevOps |
| Logistics / Dispatch Coordinator | General Admin Office |
