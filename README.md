# Bank file

A bank relationship context layer for corporate treasury. One short record per bank holding
what was agreed, the words it was agreed in, when it takes effect and who looks at it next.

Built because the answer to "what did they agree to charge us" usually exists in writing and
cannot be retrieved. That is a structure problem rather than a knowledge problem. Structure is
free.

## What it does

- Files and names whatever you drop in a bank folder, from the date inside each document
- Turns fee schedules, facility agreements, emails and meeting notes into a record where every
  row carries the words it came from
- Finds the deadline that matters: renewal or maturity minus the notice period, which appears
  in no document and no system
- Builds the pack for a bank review, with every line quoted so it can go across the table
- Checks a record for gaps, then tries to answer what the bank agreed using nothing but the
  folder, so you find what is missing before a handover does

## The two rules

**A row with no quote is not a fact.** Not a paraphrase and not a summary. The words somebody
wrote, with the file they wrote them in. Where the documents do not state something, the
record says so rather than inferring it.

**A new value supersedes rather than overwrites.** The old row stays, with its date. The
history is the negotiating position, because "when did this change" is usually the question
that matters.

## Install

**Claude Code or the Claude desktop app:** clone it into your skills directory or into a
project folder. Claude picks it up from `SKILL.md`.

```
git clone https://github.com/boomahora/bank-file.git ~/.claude/skills/bank-file
```

Or use the green Code button above, then Download ZIP, unzipping it as a folder called
`bank-file`.

**A Claude Project:** upload the files and paste `SKILL.md` into the project instructions.

**Anywhere else:** the workflows in `workflows/` are written to be read by a person as well as
a model. They work as a checklist with no tooling at all.

## Use it

Make a folder for one bank and drop the documents in. They can be named anything.

```
banks/
  northbank/
    Scan_0012.pdf
    fee schedule FINAL (3).pdf
    RE_ RE_ FW_ pricing.eml
    notes from thursday.docx
```

Then ask it to take the folder in. It reads each file, names it from the contents with the
document's own date, moves it into `sources/` and writes the record:

```
banks/
  northbank/
    record.md                                  written for you
    sources/
      2024-06-12-facility-agreement.pdf
      2025-03-04-rm-email-wire-waiver.eml
      2025-04-01-fee-schedule-v3.pdf
      2026-07-11-review-meeting-note.md
```

The **Sources** table keeps the name each file arrived under, so a row can still be traced
back to what is on the shared drive.

After that, drop new documents into the folder whenever they turn up and ask it to update.
It reads only what it has not seen, supersedes the rows that changed and tells you what moved.

Start with your largest bank. Ten to fifteen files is plenty.

**Saving emails matters.** In Outlook use File then Save As. Dragging the message into the
folder does the same. Forwarding it to yourself rewrites the header block, which loses the
sender and the date, the two things that make a row provable six months later. Choose `.eml`
if the dialog offers it, since a `.msg` is a container that may not open. Intake names the
files it could not read rather than filing them blind.

Searches that surface the right messages: `from:@bank-domain hasattachments:yes` and
`subject:(waiver OR pricing OR "fee schedule" OR concession)`.

## What is in here

| Path | What it is |
|---|---|
| `SKILL.md` | The rules, the six rows and how the workflows route |
| `workflows/intake.md` | Names and files whatever you dropped in, by the date inside each document |
| `workflows/build-record.md` | Documents to a record, then updates when new ones land |
| `workflows/derived-dates.md` | The deadline behind the deadline, ending in calendar entries |
| `workflows/review-pack.md` | What to take into the review |
| `workflows/check.md` | Gaps, contradictions and the handover test |
| `reference/fields.md` | The six rows plus the twenty fields left out on purpose |
| `reference/formats.md` | camt.086 and camt.053, plus why enrollment has a lag |
| `templates/record.md` | The empty record, with the superseded and not-stated sections most people would not think to add |
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
changes. It masks account numbers to the last four digits. An authoritative-looking
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
