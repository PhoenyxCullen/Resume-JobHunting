# Resume & Job Hunting — Session Notes
*Reference file for future Claude sessions. Last updated: Jul 5, 2026.*

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
| `2026-04-26 - Allen Schultz - Cover Letter - Roseburg Litter Patrol - ODOT.md` | Litter Patrol — ODOT REQ-198659 (**REJECTED Jun 24** — position filled) — was physical role, couldn't take during recovery anyway |
| `2026-04-26 - Allen Schultz - Cover Letter - Kroger.txt` | General role — Fred Meyer/Kroger |
| `2026-06-15 - Allen Schultz - Cover Letter - Dispatch Coordinator - ODOT.md` | Dispatch Coordinator — ODOT (REQ-201132, **REJECTED Jun 24** — missing emergency dispatch/roadway/leadwork experience) |

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
| `YYYY-MM-DD - Checklist.md` | Daily checklists (e.g. `2026-06-27 - Checklist.md`) |

### File Naming Convention
All dated files use `YYYY-MM-DD - Subject.md` format. Inside the file, the header matches: `# YYYY-MM-DD - Subject (Day of Week)`. Day of week goes in the header only, not the filename. Never use relative date references ("tomorrow", "today") in filenames or headers — always use the actual date.

### Medical Information — Strict Separation
- **NOTES.md / checklists:** scheduling info only — appointment dates, provider names, phone numbers, locations. Nothing clinical.
- **medical/ (GPG encrypted):** all PMI/PII — diagnoses, test results, medication decisions, lab values, symptoms, anything clinical.
- Never log clinical medical details in NOTES.md, memory, or any unencrypted file.

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
- **Appointment: Friday Jun 26, 1:00 PM — Treadmill Stress Test — Shannon at Providence** — arrive 12:45 PM — wear walking/running shoes — NO EATING 3–4 hours before (stop eating by ~9–10 AM) — NO CAFFEINE day of test until after
  - Location: **Providence McAndrews** — same building as general surgery — check in at outpatient counter, 2nd floor
  - Shannon callback: (541) 732-5082 — **CALL SHANNON when BP medicine is assigned** to confirm it doesn't interfere with stress test before Friday
- **Appointment: Monday Aug 3, 10:00 AM — Wellness visit, Daniel P. Wood, DO** — arrive 9:45 AM
- **BP medication decision — SENT Jun 27 via MyChart** — agreed to start both amlodipine (CCB) and losartan (ARB) at low doses in liquid formulation. Awaiting prescriptions from Sage Sherer PA-C. Providence closed weekends — prescriptions expected Monday.
- **Stress test Jun 26 — completed** — results in MyChart (details in encrypted medical log)
- **Sleep Medicine referral — APPROVED** — call PMG Medford Pulmonary to schedule: 1698 E McAndrews Rd Ste 300B, 541-732-7600 — **PREREQ: BP medication must be stable/at good baseline first — do not schedule until then**
- **Chiropractor:** McFarland Chiropractic — (541) 772-5000 — 308 Howard St, Medford OR — $48/visit — **Appointment: Wed Jul 1, ~10:30 AM (unconfirmed) — be ready by 9:30 AM**
- **Lab orders (from Dr. Sage Jun 22):** Hepatitis C antibody + HIV AG/AB 4th gen reflex — ON HOLD until BP medication is stable — do not schedule yet
- **Community Resource Desk referral — APPROVED (Jun 22)** — schedule via (503) 893-6353 (Portland office) or Sylvia locally (541) 601-6793 — details in medical/
- **Dtap vaccine overdue** — tetanus/pertussis booster — ask Providence to schedule
- **Oncology appointment: July 1, 2026** — arrive 1:50 PM, appt 2:20 PM (1 hour) — NP Consult with Radhika Gali, MD
  - Asante Heimann Cancer Center Hematology Oncology, 3011 E Barnett Rd, Medford OR 97504 — 541-789-4673
  - Cannot cancel online — must call to cancel
  - Questionnaires: DONE on paper Jun 23, 2026
  - Bring: Personal Health Summary (print from encrypted medical/ before Jul 1)
- **Laundry:** Free access runs through end of July 2026 — tied to stay at Ed's RV (extended to end of July)

---

## Oregon Unemployment (OED) — Status
- **Weekly claim Jun 28–Jul 4:** NOT yet filed — 5 activities completed (AllCare Health + Ko-Kwel + Viasat applications, Kalsoom Fatima + Izhan Yousaf LinkedIn connections) — 3 direct employer contacts — file next claim day
- **Weekly claim Jun 21–27: FILED Jul 1** — confirmation # 0-014-354-047 — reported $59.16 Uber Eats earnings, 6 hrs — 2 direct contacts (Tech People 247/Sharp Brains Jun 25; A First Choice Staffing Jun 22) + 3 work-seek activities
- **Weekly claim Jun 14–20: FILED** — confirmation # 0-014-235-471 — reported $85.05 Uber Eats earnings, 7 hrs
- **First OED payment $204 RECEIVED Jun 23, 2026** — confirmed in bank account
- **ACCESS called Allen back Jun 24 (morning)** — missed the call — return call ASAP: (541) 414-0317 or (541) 779-6691 — hours Mon–Thu 7:30am–6pm, Fri 8am–4:30pm

- Claim filed June 2026. Claim #: 001-2242885 | Claimant ID: 0001-1070971
- **WBA: $204/week | MBA: $3,022 total**
- Benefit begin: Jun 7, 2026 / Eligible through: Jun 5, 2027
- Wages confirmed correct: $9,067.36 / 567 hrs from 1800Flowers (base year)
- **Identity Verification: DONE — completed Jun 16, 2026 at USPS post office**
- **Weekly claim for Jun 8-14: FILED**
- Wage appeal deadline: June 22, 2026 — no action needed (wages accurate)
- **Weekly claim must be filed each week** — 5 job search activities required, at least 2 direct employer contacts
- **Frances Online — Direct Contact field options:**
  - Contact Method: In-person, Email, Mail, Phone, Other
  - Results: Applied for job, Interviewed, Hired, Not hired, Not hiring
- Must report all Uber Eats earnings each week (partial benefits still paid above threshold)
- **A First Choice Staffing Service** (also "The Medical Registry") — (541) 776-7505 — 1150 Crater Lake Ave Ste K, Medford OR 97504 — Mon–Thu 8am–5pm, Fri 8am–noon — has Allen's info, actively circulating to medical employers as of Jun 22, 2026 — no responses back yet — check in periodically
- **211 call: DONE** — confirmation in email
- **ACCESS** — (541) 779-6691 — 3630 Aviation Way, Medford OR — housing coordinated entry / Centralized Interest List — Mon–Thu 7:30am–6pm, Fri 8am–4:30pm — left VM Jun 22 — system says 1 VM only, do NOT leave another — keep calling back to reach someone live
- **ACCESS Affordable Housing Application — SUBMITTED Jun 23, 2026** — applied to all Medford properties (Wyatt House, Woodrow Pines, Birch Corners, Four Oaks) — if vacancy, notified within 90 days — if waitlist, added upon submission
- **ACCESS (rent assistance line per Sylvia/Providence)** — (541) 414-0317 — same 1 VM policy — keep calling live
- **Ed has given Allen one more month (until end of July 2026)** — confirmed Jun 27. Breathing room secured.
- **BackerKit — World's Largest Dungeon miniatures** — ~$1,000 pledge from 2024–2025 — fulfillment still pending — do not cancel
- **Lynette Moon Van Buege (cousin-in-law)** — asked Jun 24 if Allen has a place to put a trailer — potential housing option if a parking spot can be found (Chelle's homestead? Dennis?)
- **Sylvia A. Miranda — Providence Community Resource Desk** — sylvia.a.miranda@providence.org — CRD desk (971) 430-2411 — cell/text (541) 601-6793 — email received Jun 23
  - **Goodwill Training Center** — 11 W. Jackson Ave, Medford OR — 8-week training course (employment)
  - **RentWell Class** — starting July 2026 — Magali Ramirez will contact Allen to register — helps qualify for rental housing
  - **Search and apply** for low-income apartments in Medford OR — start now
  - **St. Vincent de Paul** — can help cover rental application fees — contact when applying
- **AllCare Health Flexible Services** — (888) 460-0185 — OHP members only — internet assistance + rent assistance (up to 6 months for established rentals) — care coordinator calls back — left VM Jun 22
- **Housing Authority of Jackson County** — (541) 779-5785 — affordable/subsidized rentals, waitlists — Mon–Thu 8am–4:30pm (closed noon–1pm for lunch effective May 1) — left VM Jun 23
  - **Section 8 application SUBMITTED Jun 25, 2026**
  - Control Number: **S800147**
  - Registration Code: **B6F52Q** (expires Aug 24, 2026 — create account at hajc.net before then)
  - **Lilac Meadow RD public housing application SUBMITTED Jun 25, 2026**
  - Control Number: **LMRD00154**
  - Registration Code: **6HC8J9** (expires Aug 24, 2026 — same account at hajc.net)
  - Account at hajc.net lets you update info, message HA, exchange documents, check status

---

## Health — Recipes
- BP/LDL/pre-diabetes meal: Rice + Madras Lentils + Eggs — see `~/Documents/recipes/rice-lentils-eggs.md`

---

## Bookmarks
- karl-voit.at — German researcher into personal information management systems: file naming schemes, tag directories, email organization, hard drive structure, system of systems for storing/sorting/filing data

---

## Bills & Payments — Urgent

| Bill | Amount | Due | Status |
|---|---|---|---|
| **Pandora** | $54.89 | PAST | **CANCELLED Jun 24** — card deleted, subscription confirmed cancelled |
| **U-Haul storage** | AA0384M: $61.93 / AA3935Q: $71.90 | 7/27 & 7/16 | $0 balance both units — enrolled in auto pay, no action needed |
| **AFLOC** | $70 minimum | Jun 30 | Pay before end of month |
| **WFCC credit card** | $56 minimum | PAID Jun 24 | Overlimit: $231.29 — do not use card |
| **WF Everyday Checking** | monthly fee | pending | Balance only $5.96 — risk of overdraft from fee |
| **Vehicle registration** | $166 | Jul 20 | Required for Uber Eats — plan ahead |

---

## Deadlines — Financial
- **Vehicle registration expires July 20, 2026 — $166 renewal due** — required to continue Uber Eats
- **End of June 2026 — need $650–800 to move to new place** (researched on FB Marketplace)
- **Still no free RV found** — post "looking for free RV, I do NOT have one to sell/give" on Facebook

## Income — Urgent (June 2026)
- **Uber Eats** — fastest income, start evenings after Dr. Sage appointment Jun 22
- **Spark Driver** (Walmart delivery) — apply at sparkdriver.com, background check 2-5 days
- **Mom's executor: Ilene Clark (cousin)** — messaged Jun 23 re: DFAS VSI estate form + requesting $1,000 advance — awaiting response
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

## Hardware — ashvolund (System76 Bonobo WS, formerly "Kirby")

Order #177521, shipped Aug 21, 2024. Serial: 8O08SC235433.

**Name origin:** Phoenyx (ash = phoenix burns to ash before rising) + Völundr (Norse smith god) = ashvolund. DevOps beast identity.

| Component | Spec |
|---|---|
| CPU | Intel i9-14900HX — 5.8 GHz, 8 P-cores + 16 E-cores, 36MB cache — **VT-d supported** |
| GPU | NVIDIA RTX 4080 12GB — 7424 CUDA cores — GPU passthrough possible but complex |
| RAM | 64GB DDR5 4800MHz (2x32GB) |
| Storage | 3x 4TB PCIe Gen 4 NVMe = **12TB total** |
| Display | 17.3" 2K QHD 240Hz matte |
| Wireless | WiFi 6E + Bluetooth 5.3 |
| OS | Qubes OS 4.3.2 (RC) |

### Pending setup (do when back on ashvolund)
1. **Apply hostname in dom0:** `sudo hostnamectl set-hostname ashvolund` + update `/etc/hosts`
2. **URGENT security patch:** IO translation to hypervisor breach vulnerability — `sudo qubes-dom0-update` then update all VMs
3. **Arch Linux template VM** — no community Arch template for Qubes 4.3 yet; custom build in progress
4. **fabric** (CLI multi-AI tool) — install in isolated AI-only AppVM using Arch template
5. **GPG vault qube** — dedicated AppVM, no NetVM assigned (fully air-gapped), master GPG key operations only (sign subkeys, update expiration, certify). Daily use stays on YubiKey subkeys in normal AppVMs.
6. **Find YubiKey(s)** — needed for subkey daily use; confirm what's loaded on card
7. **Find encrypted backup drive** (LUKS, set up previously) — contains master GPG key export; recovery layer

### Networking for ashvolund
- No switch/hub available — one ethernet cable runs desktop→router
- ashvolund has WiFi 6E but router signal is weak at RV (2.4GHz barely reaches, 5GHz doesn't)
- **cullenholme has WiFi card** (`wlp11s0`, currently down) — can broadcast hotspot for ashvolund via NetworkManager shared connection — good option to set up
- Fallback: phone tether (Samsung A71 5G) — unlimited but 5GB cap, avoid big downloads over tether
- For initial ashvolund setup session (OS updates, model downloads): move ethernet cable to ashvolund or use cullenholme hotspot

### Planned qubes
- Arch Linux work/dev qube
- AI-only isolated qube (fabric + Ollama)
- GPG vault qube (no network, master key only)
- Gaming qube (Garuda Linux + RTX 4080 passthrough)
- Windows work qube (network access)

---

## GPG Key Setup

- Master secret key: exported text file (.asc) on cullenholme + encrypted backup drive (LUKS)
- **Do NOT store master key on networked machine day-to-day** — vault qube on ashvolund is the right home
- YubiKey holds subkeys (sign/encrypt/auth) for daily use
- **Updating expiration on YubiKey-stored key:** possible — `gpg --edit-key <keyid>` → `expire` — YubiKey performs the signing operation for the new self-signature
- **Replacing keys on YubiKey:** `gpg --card-edit` → `admin` → `factory-reset` — wipes card, then reload with `keytocard`
- GPG key ID: `0xA3D95D509B06D5E3`
- Need to: find YubiKey(s), find encrypted backup drive, set up vault qube on ashvolund

---

## fabric — CLI Multi-AI Tool

- Heard about on YouTube — CLI tool, supports multiple AI providers (local + cloud) from one interface
- Install in isolated AI-only AppVM on ashvolund (Arch Linux template)
- Supports Ollama (local models), OpenAI, Claude, Gemini, and more
- ashvolund specs (64GB RAM, RTX 4080 12GB) can run large local models: Llama 3.1 70B quantized
- Big downloads needed for initial setup — do over ethernet, not phone tether
- GitHub: danielmiessler/fabric

---

## Keyboard — Cooler Master MK770

- Model: MK-770-MCKR1-US (Kailh Box V2 Linear Red, Bluetooth/2.4GHz, hot-swap)
- Ordered Jun 10, delivered Jun 16 to KNH — **picked up Jun 16, in car**

---

## Cisco 9800 WLC Job — Sharp Brains / Tech People 247 — DECLINED Jun 27

- **Recruiter:** Anaida Saleem — Tech People 247
- **Company:** Sharp Brains Global Limited, London UK — contacts: Usama Waseem, Nazam Aslam, Husnain Amjad, Suleman Qureshi (HR)
- **Pay:** $30/hr including travel — 1099 freelance, monthly invoicing 15–30 days after submission
- **Type:** Dispatch/ticket-based, no guaranteed hours
- **First task:** July 3, 2026 — 510 Airport Rd, Medford OR (PepsiCo/Coca-Cola site)
- **Interview:** Completed Jun 25 via Teams
- **Service agreement received:** Jun 27
- **DECLINED Jun 27** — reasons: UK governing law (disputes in UK courts), zero compensation on end customer termination, 30-day payment delay, no guaranteed hours, broad personal liability clause
- **Decline letter:** `2026-06-27 - Sharp Brains Decline.txt` — **SENT Jun 28, 8:04 AM** to usama.waseem@sharpbrains.co.uk
- **Reference No:** SD/555-785-122

---

## Job Applications — Jun 28, 2026

- **Oregon BOLI IT Support Specialist (ISS5)** — REQ-202370 — Portland OR — $5,779–$8,738/mo — submitted via Workday Jun 28 — status: Application Under Review — resume: IT Tech Support — cover letter: `cover-letters/2026-06-28 - Cover Letter - Oregon BOLI IT Support Specialist ISS5.txt` — deadline was Jul 2
- **Kelley Create Systems Administrator** — Medford OR — $27–$35/hr — submitted via Indeed Easy Apply Jun 28 — resume: IT Tech Support — note: mixed reviews (1.5/5 sysadmin), O365 gap noted
- **TekManagement System Support Technician III** — Medford OR — $70–90K — emailed jobs@tekmanagement.com Jun 28 — resume: IT Tech Support — cover letter: `cover-letters/2026-06-28 - Cover Letter - TekManagement System Support Technician III.txt` — NOT same as Jun 19 Tier I application

---

## Certifications to Pursue

### Master Cert Roadmap

**Phase 1 — M365/IT Support (do ASAP, fills gap on local job applications)**

| Exam | Name | Cost | Notes |
|---|---|---|---|
| MD-102 | Endpoint Administrator Associate | $165 | No formal prereq — start here. Intune, Autopilot, Entra ID, Defender, PowerShell. Updated July 24 2026. Heavy but doable. |
| MS-102 | Microsoft 365 Administrator Expert | $165 | Requires MD-102 (or MS-700 or SC-300). M365 tenant, Entra ID, Defender XDR, Purview. |

- MS-900 (old entry-level fundamentals) — **RETIRED March 31, 2026** — skip it
- MD-102 IS the entry point now — no formal prereq exam exists anymore
- Study: free Microsoft Learn paths + free 90-day M365 developer tenant for hands-on lab
- Ref: https://learn.microsoft.com/en-us/credentials/certifications/exams/md-102/
- Ref: https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/md-102
- Ref: https://learn.microsoft.com/en-us/credentials/certifications/exams/ms-102/
- Ref: https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/ms-102
- Ref: https://developer.microsoft.com/en-us/microsoft-365/dev-program (free 90-day dev tenant)

**Phase 2 — Azure/DevOps (after MD-102 + MS-102, alongside Boot.dev)**

| Exam | Name | Cost | Notes |
|---|---|---|---|
| AZ-900 | Azure Fundamentals | $165 | Optional but recommended baseline |
| AZ-104 | Azure Administrator Associate | $165 | Linux on Azure, networking, storage — no formal prereq |
| AZ-400 | DevOps Engineer Expert | $165 | Requires AZ-104 or AZ-204 — CI/CD, pipelines, infra automation |

- Ref: https://learn.microsoft.com/en-us/credentials/certifications/exams/az-900/
- Ref: https://learn.microsoft.com/en-us/credentials/certifications/exams/az-104/
- Ref: https://learn.microsoft.com/en-us/credentials/certifications/exams/az-400/

**Pearson VUE Testing Centers — Medford OR:**
- 3560 Excel Drive Suite 105, Medford OR 97504
- 4894 North Runway Drive Suite 103, Medford OR 97502 (near airport — better parking)
- 1133 S. Riverside Ave Suite 4, Medford OR 97501 (downtown — avoid)
- Schedule at: https://home.pearsonvue.com/microsoft

---

## Session — Wednesday, July 1, 2026

### Housing — RV Stay Extended Through July
- **Ed's RV stay extended through end of July 2026**
- **Rent: $500/month to Ed — due ASAP for July**
- Laundry access also runs through end of July
- Ashvolund setup must be completed while still at RV (stable power + internet)
- $500 target: $102 bowling winnings in hand; need ~$398 more from Uber Eats; July 4th weekend is high-earning opportunity

### Oncology — Completed Wednesday, July 1, 2026
- Appointment with Dr. Radhika Gali, Asante Heimann Cancer Center, 14:20
- **Result:** Not enough data to indicate need to look further
- **Plan:** Blood test every 6 months → drop to yearly → phase out altogether
- No further action required beyond following the monitoring schedule

### OED Weekly Claim
- **Jun 21–27 claim: FILED Wednesday, July 1, 2026** ✓

### Wells Fargo CC — Over Limit
- Epoch Times attempted charge $7.99 on Jul 1 — **DECLINED** (card over limit)
- Epoch Times subscription **confirmed canceled** (cancellation email received Jul 1)
- WF CC is currently over its credit limit — priority: pay it below limit ASAP, then below 30% utilization
- Auto-pay plan: set up recurring transfer via WF online after Tuesday Uber deposit clears (lands Tuesday at AFFCU, autopay Wednesday/Thursday)

### mycreditscore.com — status unknown, verify on bank statement

### World's Largest Dungeon Miniatures
- No shipping notification as of Jul 1 — still in BackerKit fulfillment
- As of Jun 9: PDFs being finalized (Book 1 Regions A-D updated on DriveThruRPG)
- Physical miniatures not yet shipped — no announced ship date

### Uber / AFFCU Deposit Timing
- Uber weekly deposits land **Tuesday** at AFFCU (not Monday)
- Schedule any autopay for liabilities (AFLOC, WF CC) on **Wednesday or Thursday** to ensure funds cleared

### Financial Snapshot — Wednesday, July 2, 2026
**AFCU:**
- Premium Checking ****9766: $4,378.56 balance / ~$3,808 available (after ~$570 pending)
- Share Savings ****9766: $23.00
- Line of Credit ****9766: $1,941.38 balance | $70 min payment due 7/30/2026

**Wells Fargo:**
- Everyday Checking ****4927: $44.96
- Platinum Card ****3986: $990.37 balance | $800 limit | **$190.37 OVER LIMIT — due NOW**
  - Last payment: $66 on 06/28
  - Late fees: $25 (May), $40 (June) — set up autopay to prevent future fees
  - Cash advance $100 from April still accruing higher interest rate
  - HumbleBundle $16.25/mo — NOT cancelled, still charging — decide to keep or cancel

**Immediate actions:**
1. Transfer $200+ from AFCU → WF checking → pay WF CC overlimit (brings card under $800)
2. Set up WF CC autopay for minimum payment
3. Pay Ed $500 cash for July rent (Thursday July 2)
4. Cancel ViewFreeScore.com — phone: 1-888-548-4324 (charge still pending 06/30, $29.95)

### Subscriptions Audit — July 2026
**AFCU card (active):**
- T-Mobile: $83/mo (phone)
- Amazon Prime: $14.99/mo (verify if $4.99 is separate Prime Video channel)
- Google One: $18.42/mo (cloud storage)
- Audible: ~$15-22/mo (keeping)
- ANTHROPIC Claude Pro: $20/mo
- Costco membership: $130/yr (renewed 07/01 — keeping)

**AFCU card (confirmed cancelled):**
- Friends & Fables (fables.gg) — cancelled ~Jul 2

**AFCU card (verify on bank statement — cancel if still charging):**
- ViewFreeScore.com — $29.95 — cancel: 1-888-548-4324
- mycreditscore.com — amount unknown — website was broken; block via bank if still charging

**WF card (active):**
- Crunchyroll: $9.99/mo (keeping)
- Netflix: $19.51/mo (keeping)
- WorkSolo: $27/mo (keeping)
- HumbleBundle: $16.25/mo — **KEEPING**

**WF card (confirmed cancelled):**
- Epoch Times — cancelled 07/01/2026
- Medium — cancelled 06/05/2026
- Disney Plus — cancelled, ended 06/10/2026
- Pocket FM — cancelled, ended 06/28/2026

**Uber income (AFCU deposits):**
- Deposits via RASIER/RAISER LLC — land Tuesday weekly
- Recent: $75.46 (06/09), $85.05 (06/23), $59.16 (06/30)

**OED unemployment (AFCU deposits):**
- $204/week — EMPLOYMT BENEFITUI BENEFIT PPD
- Recent: $204 (06/23), $204 (06/30)

### Estate / DFAS Bridge Funds — June 2026
- **Ilene Clark (cousin/executor)** deposited $6,000 total from mom's estate as bridge money while DFAS VSI backpay is pending
  - $1,000 deposited 06/13 at Cottonwood Heights AFCU branch
  - $5,000 deposited 06/24 at Cottonwood Heights AFCU branch
- This is NOT income — it's a bridge loan/advance against the estate pending VSI resolution
- Separate from the $1,000 advance request that was still open on the checklist — clarify with Ilene whether that's been satisfied or is still owed

### RV Opportunity — Sean's Church Contact (Wednesday, July 1, 2026)
- **Unit: 2019 Keystone Montana 20th Anniversary Edition** — fifth wheel (NOT self-drivable)
- Specs confirmed: washer/dryer, full bath, full kitchen — matches destination RV vision exactly
- **Asking price: $55k**
- **Tow vehicle required:** fifth wheel needs 3/4 or 1-ton pickup (F-250/350, Ram 2500/3500) — Allen does not have one
- **Workaround:** park permanently at Chelle's homestead — only needs one tow to get there; pay someone with a truck to move it once
- **Price vs VSI:** $55k vs ~$28k backpay — gap needs financing or negotiation
- **Payment plan possible** — seller is a church member, personal connection through Sean; may accept payments over time directly (no bank, potentially no interest)
- **Next step:** Have Sean float the idea — "friend is interested but waiting on a federal payment, open to discussing terms?"
- Contact: Sean Keller (Facebook conversation, July 1)

### RV Shopping — July 3, 2026
Browsing Facebook Marketplace for RV/housing options. Key finds:

- **1993 Vectra Winnebago — $2,300, Sprague River (50mi east of Klamath Falls)** — 454 big block, under 50k miles, runs/drives, title in hand. Needs airbags for shocks, radiator cap, generator maintenance. Sitting 2 years. Remote location is a risk.
- **1996 Ford Hurricane — $5,200, Cave Junction** — 460 big block, 57k miles, new fuel pump + battery, solid roof/floor, tow dolly included. **Registration not current, bill of sale only — verify clean title before pursuing.** Best near-term option if title is clear.
- **2019 Keystone Montana 20th Anniversary (Sean's contact) — $55k** — fifth wheel, payment plan possible through church connection.
- **Strategy:** Bridge RV (Hurricane/Winnebago) now → upgrade to Montana or similar when VSI lands
- **Tow dolly on Hurricane** means car can be towed behind — enables full mobile setup (RV parked, car for Uber/errands)
- Needs to learn trailer driving — backing up is the hard part, forward towing is intuitive

### JRV — 2014 Jayco Greyhawk 31FK (July 6, 2026)
- Found JRV paperwork — destination travel trailer originally wanted was sold
- **Stock #25964 — $44,900 - $100 dealer discount = $44,800**
- Class C motorhome (self-driving, no tow vehicle needed)
- 14,500 lbs | 32 feet | 52k miles
- Water: 32 gal fresh / 40 gal grey / 32 gal black
- Layout: Rear bath, front kitchen, rear bed, couch by side entry, dinette
  - Dinette can likely be repurposed as office desk/chair area
  - Over-driver cab storage
  - Undercarriage storage (bowling balls, gear)
- **Advantage over Montana:** self-driving Class C vs fifth wheel — no truck needed, move it yourself
- **Price vs VSI:** $44,800 vs ~$28k backpay — needs financing or negotiation for the gap
- JRV: johnsonrv.com — Medford OR

### Chelle Conversation — Thursday, July 3, 2026 (bowling)
- Storage on homestead: **undecided** — may require frequent moving, not ideal for U-Haul pod contents
- Montana fifth wheel parking: NOT going to Chelle's — will go to a permanent RV park instead
- Staying option: not discussed/resolved

### Housing Plan — Updated July 3, 2026
- **Ed's deadline: end of July 2026** — confirmed, full month runway
- **Tomorrow: look at private-sale motorhome at Dennis's property** — self-driving, worth ~$10k, buying for less, word of mouth from bowling. Brand/model unknown.
  - New tires confirmed
  - Engine battery needs attention — negotiate or have seller replace
  - Rear lights working
  - Clean title claimed — seller needs to locate it. **DO NOT pay until title is physically in hand.**
  - Dennis onsite at his barbershop on same property
  - Taking experienced buyers from KNH to inspect
  - Ilene (estate executor) approved — estate will cover cost, deducted from VSI before Allen gets remainder
  - **Ilene sending $5,500** — $5,200 for RV + $300 buffer for trip permit/incidentals
  - Ilene deposits directly to AFCU (Cottonwood Heights branch ACH) — same as prior $1k/$5k deposits
  - No bank holiday issue — ACH transfer, not branch transaction
  - Price negotiated down from $10k to $5,200 already — firm, seller wants it gone
  - Seller lived in it 2 years — systems were actively used, good sign
  - Year/model unknown — check VIN on dash when inspecting tomorrow
- **Bridge motorhome = immediate housing only** — NOT an Uber vehicle, too impractical
- **Current car** continues for Uber until camper van is acquired
- **Montana fifth wheel (eventual)** — permanent spot at RV park with washer/dryer, full kitchen. Not Chelle's property.
- **Two-RV end state:** cheap motorhome now → upgrade to Montana/similar when VSI lands → park permanently at RV park

### Session — Friday, July 3, 2026

- **RV viewing postponed** — Dennis has a family situation with his father, may be holiday related
- **Ilene already deposited $5,500** to AFCU — earmarked for RV purchase, do not spend
- **UPS now at full battery** — load 2/5, Ildveilbroen on its own outlet (not on UPS)
- **RV has no running water** — Ed using the only hose that reaches for pressure washing rental property in Grants Pass
- **Outlet that UPS is on has tripped before** — risk of unclean cullenholme shutdown if it trips while Allen is out; shut down cullenholme before leaving today
- **T-Mobile visit today** — check unlimited premium data plan with USB tethering for ashvolund; ask specifically about hotspot data allowance
- **YubiKey is with Allen** — somewhere in RV, search tonight when back
- **Today's plan:** lunch → T-Mobile → job applications (5 target) → back tonight

### Open Question — Property/Windfall
- Allen mentioned a potential larger windfall and a possible property stake ("winning a house") — details unclear, needs follow-up conversation

### Move-Out Plan — Post This Week Priority
- $500/month to Ed is a stopgap — goal is to move out of Ed's RV ASAP after this week
- Build move-out plan once immediate demands (bathroom, $500, ashvolund) are handled
- Key levers: VSI/DFAS backpay, Uber income, housing options (Chelle, free RV, Section 8)

### Ed's Demands — Due Thursday, July 2, 2026
- **1. Clean the bathroom in Ed's house** (not the RV) — do first thing Thursday morning
- **2. Pay $500 rent for July** — due Thursday July 2
- $500 plan: check AFFCU balance Thursday morning — Allen thinks it's doable
- Also check at same time: which card mycreditscore.com charged and cancel it

### Thursday, July 2 — Morning Plan
- Check AFFCU balance + mycreditscore charge (do together, both in banking app)
- Pay Ed $500 for July rent
- Clean Ed's bathroom (top to bottom: toilet → sink → mirror → tub → floor → trash)
- Laundry (free access through end of July)
- Ashvolund: security patch (`sudo qubes-dom0-update`) + setup tasks
- Boot.dev session

### Network — Ildveilbroen (Nighthawk Router) at RV
- IP: `10.24.78.1/24`
- Moved to its own power port (not on UPS) after breaker trip
- UPS protection pending — connect after battery recharges tonight
- ashvolund and cullenholme both at RV on this network as of Jul 1

### Session — Sunday, July 5, 2026

#### System76 Support Call — Monday July 6
- Ashvolund kernel panic during Qubes 4.3.1 initial update — one of 3 NVMe drives dropped out
- Caused /dev/mapper/qubes-dom0-root not found on reboot
- Ambient temp 73°F — not a heat issue — likely NVMe thermals or seating
- **Call System76 today** to ask about opening it up — Order #177521, Serial: 8O08SC235433
- **NVMe thermal pads on order — ETA July 10–14** (at KNH) — install after they arrive
- Hold off on reseating until after System76 call confirms it's OK

#### cullenholme Boot Message — Resolved
- Mystery "EFI boot partition file missing" message at boot was from the **SanDisk USB (sdd)** being scanned by UEFI firmware (Boot0006), not from cullenholme's own EFI partition
- cullenholme boot chain fully verified: EFI partition clean, /boot files all present, grub.cfg references all valid, resume UUID valid (sdc1 66GB swap)
- No action needed on cullenholme

#### Qubes 4.3.1 USB — DONE
- Downloaded Qubes-R4.3.1-x86_64.iso
- GPG verified: Good signature from "Qubes OS Release 4.3 Signing Key" (F3FA3F99D6281F7B3A3E5E871C3D9B627F3FADA4)
- SHA256: `6ab99dee2c7a7b2c32053d3531084aaf3af703815842b67f90a87ba324527db6`
- dd'd to SanDisk 3.2Gen1 USB (/dev/sdd, 57.3GB) — write verified (USB SHA256 matches ISO)
- USB ejected and ready to boot ashvolund for Qubes 4.3.1 install
- GPG keyring has: Qubes Master Signing Key (ultimate), Release 4.2 Key (full), Release 4.3 Key (full)

### Ashvolund Setup — Priority List (do before losing RV)
1. **Security patch (URGENT):** `sudo qubes-dom0-update` then update all VMs (hypervisor breach vulnerability)
2. **Hostname:** `sudo hostnamectl set-hostname ashvolund` + update `/etc/hosts`
3. **Find YubiKey(s)** — needed for daily GPG subkey use
4. **Find LUKS encrypted backup drive** — master GPG key recovery
5. **Finish Arch Linux template VM build**
6. **cullenholme WiFi hotspot** (`wlp11s0`) — internet for ashvolund without phone tether

### Job Leads from Email — Jul 1
- **DebtNext System Administrator at Crown Asset Management** — Medford OR — via Indeed alert — check and apply
- **DevOps Engineer at Franklin Fitch** — up to $150K/yr — via LinkedIn
- **Junior Infrastructure Cloud Engineer at Gotham Technology Group** — via LinkedIn
- **TEKsystems technical recruiter** — LinkedIn connection request — worth responding

---

## Session — Friday, July 4, 2026

### Surgery Clearance — Full Weight Restored
- Allen confirmed full weight clearance as of July 4, 2026
- Physical restrictions (no heavy lifting) from May 18 cecectomy are fully lifted
- Physical and outdoor roles no longer need to be flagged

### Flameshot — Fixed (Downgraded to 13.3.0)
- Problem: Flameshot 14.0.0 (upgraded Jun 26) broke on MATE desktop — Qt6.11 incompatibility
- Error: "Unable to capture screen" — no GUI, no screenshot possible
- Fix: Downgraded to 13.3.0-2 via Arch Linux Archive
  ```
  sudo pacman -U /tmp/flameshot-13.3.0-2-x86_64.pkg.tar.zst
  ```
- **Optional future protection:** Add `IgnorePkg = flameshot` to `/etc/pacman.conf` to prevent auto-upgrade
- Status: Working as of July 4, 2026

### OED — Week Jun 28–Jul 4 Activities (file next claim day)
5 work search activities completed this week:
1. **AllCare Health** — Service Desk Technician I — applied via ADP (direct employer contact)
2. **Ko-Kwel Casino Resort** — IT Help Desk Technician — applied via iSolved (direct employer contact)
3. **Viasat** — Data Entry Support Trade Compliance — applied via iCIMS (direct employer contact)
4. **Kalsoom Fatima (recruiter)** — LinkedIn connection — IT/network recruiter
5. **Izhan Yousaf / Fixcruit** — LinkedIn connection — IT recruiter / CEO

All 5 logged in job_hunting_log.csv.

### Job Applications — July 4, 2026
- **AllCare Health — Service Desk Technician I** — Grants Pass OR — $27.88–$32.69/hr — Req ID 1205 — submitted via ADP — resume: IT Tech Support — cover letter: `cover-letters/2026-07-04 - Cover Letter - AllCare Health Service Desk Technician I.txt` — attached LPI cert — follow up Jul 18
- **Ko-Kwel Casino Resort — IT Help Desk Technician** — Medford OR — submitted via iSolved — resume: IT Tech Support — cover letter: `cover-letters/2026-07-04 - Cover Letter - Ko-Kwel Casino Resort IT Help Desk Technician.txt` — attached LPI cert — gaming license + background check required (tribal employer: Coquille Indian Tribe) — follow up Jul 18
- **Viasat — Data Entry Support Trade Compliance** — Remote (OR) — $17.07–$27.16/hr — Job ID 6188 — submitted via iCIMS — resume: Data Entry — cover letter: `cover-letters/2026-07-04 - Cover Letter - Viasat Data Entry Support Trade Compliance.txt` — contingent/temp — US citizenship required — follow up Jul 18
- **Ashland School District — IT Support Specialist II** — Ashland OR — $24.52–$30.25/hr — Job ID 1207 / Posting 26-65 — NOT yet submitted — cover letter ready: `cover-letters/2026-07-04 - Cover Letter - Ashland School District IT Support Specialist II.txt` — apply at applitrack.com/ashland5/onlineapp/ — **DEADLINE: July 29, 2026**

### Declined — Sharp Brains / Hardy Industries
- **Sharp Brains** (Tech People 247/Anaida Saleem) — already declined Jun 27 (bad contract: UK law, no guaranteed hours, personal liability, 30-day payment delay). Came up again as job suggestion Jul 4 — still declined.
- **Hardy Industries** — 1099 dispatch-based smart hands contractor, 1.0/5 stars — same model as Sharp Brains. Skipped.

### LPI Cert — Copied to Project Folder
- `LPI Linux Essentials Certificate - Allen Schultz.pdf` — copied from `~/Documents/LE-1.pdf`
- Use as attachment on IT job applications

### DFAS — Estate Check Wrong Zip Code
- **DFAS letter received:** Check for **$28,931.49** payable to **Estate of Penny Schultz** was mailed to wrong zip code
  - Address on check: 1717 View Pl, Medford OR **95704** (wrong — should be **97504**)
  - Letter signed by: **Sharon C. Somers** — DFAS — 1-667-894-4808
- **Non-Receipt form** is on the back of the letter
- **Allen's next steps:**
  1. Check KNH mail for the physical check (despite wrong zip, may have been delivered)
  2. Check car for any letter/check that may have arrived earlier
  3. If not found: fill out Non-Receipt form (back of letter) and return to DFAS
- **Contact:** Sharon C. Somers — 1-667-894-4808
- Do NOT fill out Non-Receipt form until confirming check was not physically delivered

---

## Errands — Pending
- **Best Buy** — recycle old SK-653 keyboard (electronics recycling bin)

## Post-VSI Shopping List

- Lap desk with wrist rest for car use (~$20-30)
- N100 mini PC for car dev environment
- Raspberry Pi 5 for exit nodes at friends' networks
- **Steam Deck** — native PoE2 + portable gaming, no streaming/latency issues
- Google Pixel (6a or 7a) + GrapheneOS

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
