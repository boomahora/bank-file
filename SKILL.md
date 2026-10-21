---
name: bank-file
description: Build and maintain a bank relationship context layer for corporate treasury. Use when reading bank fee schedules, facility agreements, mandate letters, relationship manager emails or bank meeting notes. Also use when asked what a bank agreed, what a bank promised, when notice must be served, whether charged fees match agreed fees, or to prepare for a bank review or a handover.
---

# Bank file

A bank relationship context layer. One short record per bank holding what was agreed, the
words it was agreed in, when it takes effect and who looks at it next.

Most of what people put in a bank relationship template is already somewhere authoritative.
This skill captures only the six things that exist nowhere retrievable.

## The two rules

These are not style preferences. Breaking either one produces a record that cannot be used in
a conversation with a bank.

**1. A row with no quote is not a fact.**

Every row carries the exact words from the source, not a paraphrase or a summary, plus the
filename they came from. If the source does not state something, write `not stated`. Never
infer a value, a date or an amount that is not written down. Never fill a gap with how banks
usually work.

When a row is produced from a document, present it as a candidate and tell the user which
file and which page or clause to open. You cannot verify your own extraction. Say so rather
than implying the row is confirmed.

**2. A new value supersedes rather than overwrites.**

When a value changes, keep the old row with its effective date and add the new one. The
history is the negotiating position, because "when did this change" is usually the question
that matters.

## The six rows

| Row | What it captures |
|---|---|
| Waivers and concessions | Anything agreed outside the published fee schedule, with its expiry |
| Pricing agreed outside the schedule | A rate that contradicts the document on file |
| Service commitments | What they said they would provide, in a meeting or an email |
| Open promises | A commitment with no evidence of delivery, dated |
| Derived deadlines | Renewal or maturity minus the notice period. Computed, never quoted |
| Why this bank | The reason it was selected, and what was considered against it |

Everything else belongs where it already lives. `reference/fields.md` lists what is
deliberately left out and why.

## Workflows

| Ask | Read |
|---|---|
| Documents dropped in a bank folder, unsorted | `workflows/intake.md` |
| Build or update a record from documents | `workflows/build-record.md` |
| Find the real deadlines in agreements | `workflows/derived-dates.md` |
| Prepare for a bank review | `workflows/review-pack.md` |
| Check a record for gaps, or run the handover test | `workflows/check.md` |

Templates are in `templates/`. A filled example is in `example/northbank/`.

The usual path is one bank folder with documents dumped in it: file and name them, build the
record, find the dates. After that, each time new documents land, intake files them and
`build-record.md` updates only what they changed.

## What maintaining it means

File names, filing, the **Sources** table and spotting what arrived are mechanics. Do them
without asking.

A value in a row is not mechanics. It changes only with a quote behind it, and a value that
replaces another goes through the **Superseded** table with its date. Never tidy, merge or
correct a row silently, because the record is only worth having if every row can be traced to
words somebody wrote.

## Safety

**Never produce or confirm payment detail.** Not account numbers, not payment instructions,
not signatory or beneficiary changes. If asked, decline and say the change has to be verified
by phone with a known contact. This record is exactly the kind of authoritative-looking
source a business email compromise attack needs.

**Mask account numbers to the last four digits**, even when the source document shows the
whole number. Write `····4417`. The last four identify an account well enough for this
purpose, and it caps what the folder is worth to anyone who should not have it.

**Ask for no credentials.** No mailbox access, no bank portal login, no API keys. This skill
reads files it is handed.

**Record facts, not opinions.** Anything in the file may be read in a dispute or an audit, so
keep opinions about a bank's staff out of it.
