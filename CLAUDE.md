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

- electrical questions: read electrical/wiring.md and electrical/verify.md first. wiring diagrams are in electrical/diagrams.md. parts are in electrical/parts.md and cable lengths in electrical/measurements.md.
- power budget and load checks: the load budget section of README.md
- manuals and datasheets: reference/, shared across subsystems. read them to settle verify items and cite the file name.

## conventions

- each subsystem folder has parts.md, a plan file (wiring.md for electrical), and verify.md. manuals live in the shared root reference/ folder, not per subsystem.
- one fact lives in one file. link to it instead of copying it.
- mark unconfirmed specs with the word verify and list them in the subsystem's verify.md.
- when a decision changes, edit the file and add a dated line to that subsystem's change log in verify.md.
- keep this file under 200 lines. put long tables and details in the subsystem files, not here.
