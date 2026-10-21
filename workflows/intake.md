# Take in a folder of documents

The user drops files into a bank folder. This files them, names them and records what
arrived. Run it before `build-record.md` on a new folder, or on its own whenever new
documents land.

Everything happens inside that bank's folder. Never move a file out of it, never delete one
and never overwrite one.

## What arrived

Two sets of files are the work:

- Anything in the bank folder that is not already inside `sources/`
- Anything in `sources/` that the record's **Sources** table does not mention

Read each file before naming it. The name comes from the contents. The name it arrived under
is usually a scanner default, a download counter or a mail client's version of a subject line.

## Naming

`YYYY-MM-DD-what-it-is.ext`, date first so the folder sorts itself.

| Kind | Example |
|---|---|
| Facility or loan agreement | `2024-06-12-facility-agreement.pdf` |
| Mandate or account opening | `2024-05-02-mandate-letter.pdf` |
| Fee schedule | `2025-04-01-fee-schedule-v3.pdf` |
| Relationship manager email | `2025-03-04-rm-email-wire-waiver.eml` |
| Meeting note | `2026-07-11-review-meeting-note.md` |
| Fee invoice or billing statement | `2026-03-31-fee-invoice-march.pdf` |
| Selection or RFP material | `2024-03-18-rfp-scoring-sheet.xlsx` |

The date is the date **in** the document: the date the agreement was signed, the date a
schedule takes effect, the date an email was sent. Not today. Not the file's modified time,
which is the date somebody last opened it.

**Say where each date came from**, quoting the words or naming the page. A date in a filename
is inherited by every row sourced from that file, so it cannot be a guess.

**A document with no date in it gets an `undated-` prefix** and goes on the list of things
needing one. Never infer a date from the files around it or from how banks usually work.

## Filing

Move each file into `sources/`. If that name is already taken and the contents differ, add
`-b`, then `-c`, rather than replacing anything. Say when you did.

Then produce the log:

| As delivered | Filed as | What it is | Date from |
|---|---|---|---|

Update the record's **Sources** table from it, keeping the delivered name. Somebody
cross-checking a row against the shared drive is looking for the name the bank sent, not the
one you chose.

Where a record already exists and cites a file you have just renamed, update those citations
to the new name and say which rows you touched. A quote pointing at a filename that no longer
exists reads as a broken record, and `workflows/check.md` will flag it as one.

## Where to stop and ask

File the obvious ones in one pass and report. Stop and ask on:

- A file whose contents do not identify it
- A document with no date in it
- Two files that look like the same document with different contents
- Something that is not a bank document and probably landed there by accident
- A file you cannot read. `.msg` is a container and may not open, while `.eml` or a PDF export
  will. Name the files you could not open rather than filing them blind

## What this does not touch

Values. Filing and naming are mechanics, and this does them without asking.

A row in the record is a different thing. Rows change only through `build-record.md`, with a
quote, and a value that replaces another goes through the **Superseded** table. Nothing here
edits a row.
