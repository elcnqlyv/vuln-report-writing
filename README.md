# Vulnerability Report Writing Skill

A Claude skill that writes, rewrites and reviews penetration test findings, bug bounty submissions and coordinated-disclosure reports. The goal is a report a triager can verify quickly and trust, written in a plain, human style.

## What it does

- Reads the target program's policy first: contact, severity scale, reward table, required format, scope and ignore list.
- Maps each finding to that policy. It reframes or demotes findings the program would ignore, such as "weak password", "theoretical without PoC" or "SSL/TLS hardening".
- Verifies hashes, offsets and strings against the target binary when it is available, without running it.
- Rewrites each finding as title, summary, affected version, evidence, reproduction steps, impact, severity, fix, and what could not be confirmed.
- Recomputes every CVSS 3.1 score from its vector and checks that the label matches.
- Reviews proof-of-concept scripts for weak success checks, toy demonstrations, unsafe defaults and unmarked guesses.
- Produces Markdown, PDF or Word output on request, plus a separate review-notes file that lists every change and its reason.

## Writing style

- No em dashes and no semicolons.
- Short sentences in active voice, first person for what the researcher did.
- No stock AI words, sales language or vague hedging.
- Every impact claim points to evidence. Untested links are written as conditions.
- No invented addresses, hashes, versions or results.

## Repository structure

```
vuln-report-writing/
├── SKILL.md
├── vuln-report-writing.skill
├── README.md
└── LICENSE
```

- `SKILL.md` holds the style rules, finding structure, honesty rules, PoC checklist, rewrite workflow and a CVSS 3.1 formula for self-checks.
- `vuln-report-writing.skill` is the same skill packaged for upload.

## Installation

1. Download `vuln-report-writing.skill` from this repository.
2. In Claude, open the skill settings and upload the file.

To build the package yourself, put `SKILL.md` in a folder named `vuln-report-writing`, zip the folder, and rename the file to `vuln-report-writing.skill`.

## Usage

Give Claude your draft report, the program's policy link, and any PoC scripts. Examples:

- "Rewrite this report for the vendor's bug bounty program. Here is the policy page."
- "Review my pentest findings and check the CVSS scores."
- "Make this disclosure report sound human and professional."
- "Review these PoC scripts before I submit them."

## License

MIT. See `LICENSE`.
