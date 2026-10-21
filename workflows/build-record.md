# Build or update a record

## Before starting

Check that a `sources/` folder exists with files in it. If it is empty, stop and give the
user the capture list below rather than producing a record from nothing.

**What to put in `sources/`:**

- The facility agreement, the mandate letter, the current fee schedule and the one before it
- Emails from the relationship manager, saved as `.msg` or `.eml`. Saving the message or
  dragging it into the folder keeps the sender and the date. Forwarding it to yourself
  rewrites the header block and loses both, which is what makes a row provable later
- Meeting notes, however rough
- The RFP scoring sheet or selection note, if one exists

Outlook searches that surface them: `from:@bank-domain hasattachments:yes`, and
`subject:(waiver OR pricing OR "fee schedule" OR concession)`.

Name files date first so the folder sorts itself: `2025-03-04-rm-email-wire-waiver.msg`.

Ten to fifteen files is plenty for a first pass.

## Extraction

Read every file in `sources/`. For each of the six rows, look for what the documents actually
state.

Produce at most six rows. If a document contains something interesting that does not fit one
of the six, note it under **Not stated** rather than adding a seventh row. The record stays
short or it does not get maintained.

For every row produce:

- **Value.** What was agreed. Where it contradicts another document on file, say so in the
  value: `€28, not the €35 in schedule v3`
- **Source.** The exact quote, in quotation marks, plus the filename and the page or clause.
  A paraphrase is not a source
- **Effective.** The date the thing starts, as written in the document. If no date is stated,
  write `not stated`, never today's date and never the document's date
- **Next look.** An expiry, a review date or a derived deadline. For a waiver with a term,
  this is the day it lapses. Mark a promise with no delivery `Overdue`
- **Owner.** Leave blank for the user to fill in. Do not assign owners

## Confidence and abstention

Say `not stated` rather than producing a plausible value. A missing row is information: it
tells the user what to ask the bank for. A wrong row that looks right is the failure mode
this whole method exists to prevent.

Where two documents disagree and no date separates them, produce both rows and flag the
conflict. Do not pick one.

## Where the record goes

Write it to `record.md` beside `sources/`, in the shape of `templates/record.md`, creating the
file if it is not there. Fill the **Sources** table with every file in `sources/` and one line
on what each covers.

The user builds `sources/` by hand, because nothing here can read a mailbox or decide which
twelve documents matter. Everything from there on is output: the record, the superseded rows
and the Not stated list.

Where there is no file access, such as a Claude Project, output the whole record as one block
for the user to paste into `record.md` instead. Never hand back loose rows with no file to put
them in.

## Handing back

Present the rows as candidates, then say plainly:

> These are candidates. I cannot verify my own reading. Open each source, find the quoted
> sentence and then the row is yours.

List the file and the page or clause per row so checking takes ten minutes rather than an
hour.

## Updating an existing record

Never edit a value in place. Move the old row into the **Superseded** table with the date it
stopped applying and what replaced it, then add the new row. If the old row's effective date
is unknown, say so rather than guessing one.
