# Check a record

Two passes. Run the first after building a record, and the second before a review or a
handover.

## Pass 1: mechanical

Report every instance of:

- A row with no quote, or with a paraphrase where a quote should be
- A quote whose filename does not exist in `sources/`
- A row with no effective date and no `not stated`
- A next-look date that has already passed
- Two rows stating different values for the same thing with no date separating them, and no
  entry in the **Superseded** table
- A full account number anywhere in the record. These must be masked to the last four digits
- More than six active rows, which means the record is growing into a template

Report what you found and where. Do not fix anything silently.

## Pass 2: the handover test

Answer these three questions using nothing but the record and `sources/`:

1. What did this bank agree that is not in the published fee schedule?
2. What did they promise that has not been delivered?
3. When must notice be served to exit or renegotiate?

Then report, for each one, either the answer with its source or **cannot be answered from
this folder**, plus which document would settle it.

This is the same test a team should run on a colleague who sat in none of the meetings. What
cannot be answered is the gap, and finding it now is much cheaper than finding it during an
actual handover.

Do not soften the result. A record that passes this test is worth keeping, and one that does
not is a list of notes.
