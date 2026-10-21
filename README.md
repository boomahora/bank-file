# Bank file

A bank relationship context layer for corporate treasury. One short record per bank holding
what was agreed, the words it was agreed in, when it takes effect and who looks at it next.

Built because the answer to "what did they agree to charge us" usually exists in writing and
cannot be retrieved. That is a structure problem, not a knowledge problem, and structure is
free.

## What it does

- Turns fee schedules, facility agreements, emails and meeting notes into a sourced record
- Finds the deadline that matters: renewal or maturity minus the notice period, which appears
  in no document and no system
- Builds the pack for a bank review, with every line quoted so it can go across the table
- Checks a record for gaps, and runs a handover test on it

## Install

**Claude Code or the Claude desktop app:** clone it into your skills directory, or into a
project folder. Claude picks it up from `SKILL.md`.

```
git clone https://github.com/boomahora/bank-file.git ~/.claude/skills/bank-file
```

Or use the green Code button above, then Download ZIP, and unzip it as a folder called
`bank-file`.

**A Claude Project:** upload the files and paste `SKILL.md` into the project instructions.

**Anywhere else:** the workflows in `workflows/` are written to be read by a person as well as
a model. They work as a checklist with no tooling at all.

## Use it

```
banks/
  northbank/
    record.md
    sources/
      2024-06-12-facility-agreement.pdf
      2025-03-04-rm-email-wire-waiver.msg
      2025-04-01-fee-schedule-v3.pdf
      2026-07-11-review-meeting-note.md
```

Start with your largest bank. Put ten to fifteen files in `sources/`, then ask for the record.

**Saving emails matters.** In Outlook use File then Save As to write a `.msg`, or drag the
message into the folder. Forwarding it to yourself rewrites the header block, and the sender
and date are what make a row provable six months later.

Searches that surface the right messages: `from:@bank-domain hasattachments:yes` and
`subject:(waiver OR pricing OR "fee schedule" OR concession)`.

## What is in here

| Path | What it is |
|---|---|
| `SKILL.md` | The rules, the six rows and how the workflows route |
| `workflows/build-record.md` | Documents to a record |
| `workflows/derived-dates.md` | The deadline behind the deadline, ending in calendar entries |
| `workflows/review-pack.md` | What to take into the review |
| `workflows/check.md` | Gaps, contradictions and the handover test |
| `reference/fields.md` | The six rows, and the twenty fields left out on purpose |
| `reference/formats.md` | camt.086 and camt.053, and why enrollment has a lag |
| `templates/record.md` | Empty record |
| `templates/meeting-note.md` | The note shape that stays extractable later |
| `example/northbank/` | One bank, filled in from four fictional documents |

Read the example first. It takes two minutes and it shows the point better than this file
does: a waiver with a 12 month term, agreed in an email, which expired without anybody
deciding to let it expire.

## What it does not do

It does not remember anything between sessions. The files remember.

It cannot read your mailbox. Somebody has to put the files in the folder.

Nothing runs unless you ask, so it will not notice a date passing. That is what the calendar
entries in `derived-dates.md` are for.

It cannot enforce the quote check. It can produce a row with a quote and tell you which file
to open. Whether you open it is on you.

## Safety

It will refuse to produce or confirm account numbers, payment instructions or signatory
changes, and it masks account numbers to the last four digits. An authoritative-looking
internal record is exactly what a business email compromise attack needs, so those changes
stay on the phone with a contact you already know.

It asks for no credentials: no mailbox access, no portal login, no API keys.

When you ask an assistant about a record, the text of what you ask about goes to whoever runs
that assistant. Use what your company has already approved for business data.

---

Built by Alex Cannon. https://alexcan.xyz

The method, with the reasoning behind the six rows:
https://alexcan.xyz/blog/bank-relationship-context-layer

MIT licensed. If you build a record and it needs two rows I left out, open an issue and tell
me which two.
