# working rules for this repo

@README.md

## working rules

- write all content in lower case, including headings and the first word of each sentence. exceptions: acronyms and initialisms (AC, DC, DJI), unit symbols and alphanumeric model or thread codes (300A, M8, RJ45), and file names or links where case matters (CLAUDE.md, README.md, urls). this applies to everything generated in this project, including edits to these files.
- give amazon links for products by default. search links are fine when no direct page is verified.
- when recommending a tool or part, state failure modes and range limits first.
- say plainly when a spec is unverified. do not present items marked verify as facts.
- keep answers short and mobile-friendly. lead with the answer.
- AC wiring is the dangerous part. remind me to have it inspected before energizing.
- if a message contradicts these files, ask which is right, then update the file.
- do not run destructive commands or delete files without asking.
- never commit passwords, API keys, or network credentials.

## where to look

- electrical questions: read electrical/PLAN.md (design, diagrams, install order, supplies, by subsystem section — open questions and settled decisions are at its end). what's actually built is in electrical/README.md.
- power budget and load checks: the load budget section of the root README.md
- manuals and datasheets: reference/, shared across subsystems. read them to settle open questions and cite the file name.
- history of how something got decided: `git log` — every change is a commit with a descriptive message. there is no separate change log file.

## conventions

- each subsystem folder has exactly two files: README.md (as-built — only grows as something is confirmed complete or a part is confirmed in hand) and PLAN.md (the design: one section per subsystem/diagram, each leading with its diagram, then an installation checklist, then a supplies checklist, both using `[x]`/`[ ]` task-list syntax; cable lengths and physical layout notes are inline on the relevant line, not a separate table). manuals live in the shared root reference/ folder, not per subsystem.
- one fact lives in one file. link to it instead of copying it.
- mark an unconfirmed spec inline as `(verify: ...)` on the line it concerns. if it doesn't anchor to one line, put it under PLAN.md's "open questions" section.
- a rejected or settled-either-way design alternative goes under PLAN.md's "decided" section, trimmed to one line, so it doesn't get re-proposed later.
- when a decision changes, just edit the file — the commit message is the record of what changed and why, not a separate change log entry.
- keep this file under 200 lines. put long tables and details in the subsystem files, not here.
