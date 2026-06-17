# Claude Code — Project Init

This is Allen Schultz's resume and job-hunting workspace.

## Session start — run this first

```bash
date
```

This gives current date and time for context — helps track how much time has passed since last session, whether pending items (SLCC transcript, CIW email, doctor followup, etc.) have had time to resolve, and whether any dated notes in NOTES.md or memory are stale.

## Start here

Read **NOTES.md** for the full project reference (file structure, compile commands, employment history, preferences).

Memory files in `/home/allen/.claude/projects/-home-allen-Projects-Resume-JobHunting/memory/` add cross-session context:
- `user_background.md` — skills, employment quirks, important distinctions
- `project_job_hunt_context.md` — recovery status, income situation, preferences
- `project_resume_latex_state.md` — LaTeX design decisions, what's done, compile rules

## Critical rules (must follow every session)

**Compile:** Always run pdflatex/xelatex **twice** per file — `lastpage` needs two passes for correct "Page X of Y" footer. Single-pass produces "Page X of ??".

**Font/compile pairing:**
- Latin Modern (5 specialized + 1 master): `pdflatex`
- Georgia master: `xelatex`

**Colors:** All resumes are **all-black** (`\definecolor{accent}{RGB}{0,0,0}`). The gray thin rule under section headers (`{\color{black!35}\rule{\linewidth}{0.3pt}}`) is an intentional design element, not a color violation.

**Page breaks:** Use `\usepackage{needspace}` + `\needspace{5\baselineskip}` before each job/contract title header. Do NOT use `\nopagebreak` before `\begin{itemize}` — too aggressive. Rule: title + minimum 2 content lines before/after a page break.

**Experience order:** Reverse chronological in all resumes (most recent first).

**Header spacing:** All tailored resumes need `\vspace{-10pt}` immediately after `\end{center}` (before the first `\section*`) to eliminate excess gap from `center` environment trailing glue.

**After editing .tex:** Always recompile to PDF. Two passes, then `rm -f *.aux *.log *.out`.

**Keep in sync:** Update NOTES.md and memory after significant changes.

## File naming

All current resumes use date prefix `2026-05-26` (matches master LM last-modified date). Do not change unless explicitly asked.

## Batch compile command (all 6 LM files)

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
