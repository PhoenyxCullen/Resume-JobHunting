# Resume & Job Hunting — Session Notes
*Reference file for future Claude sessions. Last updated: May 26, 2026 (evening).*

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
| `2026-05-26 - Allen Schultz - NOC Analyst Resume.md/.tex/.pdf` | NOC Technician, Network Admin, Network Operations |

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
Recompile a single file:
```bash
cd "/home/allen/Projects/Resume-JobHunting/resumes"
pdflatex -interaction=nonstopmode "FILENAME.tex" && rm -f *.aux *.log *.out
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
  "2026-05-26 - Allen Schultz - NOC Analyst Resume"; do
  pdflatex -interaction=nonstopmode "${f}.tex" && echo "OK: ${f}.pdf"
done && rm -f *.aux *.log *.out
```

### Georgia variant (xelatex) — 1 file
```bash
cd "/home/allen/Projects/Resume-JobHunting/resumes"
xelatex -interaction=nonstopmode "2026-05-26 - Allen Schultz - Resume Archive (Master) - Georgia.tex"
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
- **Harry and David** — Seasonal Data Entry Associate, Sep 2023–Dec 2025. Three deployments: Sep–Dec 2023; Sep 2024–Feb 2025; Sep–Dec 2025. Keyboard typing into order management system.
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
- Curriculum order: Python → Linux → Bookbot → Learn Git (Webflyx) → OOP → ... (see Boot.Dev.md)

### Physical / Availability
- Surgery May 18, 2026 (cecectomy — appendix + large intestine section removed). No heavy lifting ~4–6 weeks (through late June/early July 2026).
- Available immediately for desk and remote work.
- Seeking income sufficient for apartment. Current situation: not enough income.

### Preferences
- Strong preference for remote work.
- Open to temp, contract, or permanent.
- Salary: $46,500+/yr ($22.36/hr minimum).

---

## Suggested Job Roles to Apply For

All are desk/remote-friendly and suitable during surgery recovery:

| Role | Best Resume to Use |
|---|---|
| IT Help Desk / Desktop Support Tier 1–2 | IT Tech Support |
| NOC Analyst / Network Operations Technician | NOC Analyst |
| Linux System Administrator | DevOps Engineer |
| DevOps Engineer / SRE | DevOps Engineer |
| VoIP / Telephony Administrator | DevOps or Master Archive |
| Data Entry / Order Processing | Data Entry |
| Administrative Assistant / Virtual Assistant | General Admin Office |
| Remote Customer Service (Technical) | IT Tech Support or General Admin |
| Technical Writer / Documentation | General Admin or DevOps |
| Logistics / Dispatch Coordinator | General Admin Office |
