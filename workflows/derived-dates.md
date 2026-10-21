# Find the real deadlines

The date in the agreement is not the date that matters.

A facility maturing on 12 June 2027 with 90 days' notice in clause 4.3 has a real deadline of
14 March 2027. Miss that and the term rolls on terms nobody chose. The second date appears in
no document, which is why it is in no system either.

## What to do

Read every agreement in `sources/`. For each one produce a row:

| Agreement | Renewal or maturity | Notice period | Clause | Notice due by |
|---|---|---|---|---|

Rules:

- **Quote the notice clause.** Notice provisions are written in ways that look similar and
  behave differently. "Not less than 90 days prior to" and "90 days from the date of notice"
  are not the same thing
- **Show the arithmetic.** State the maturity date, the period and the result, so the user can
  check it without redoing it
- **Count calendar days unless the clause says business days.** If the clause says business
  days, say which calendar you have assumed and that the user needs to confirm it
- **Flag anything conditional.** Automatic renewal unless notice is served behaves differently
  from a fixed maturity. Say which one each agreement is
- **Say `not stated`** where no notice period is given, rather than assuming a market standard

Cover service agreements and cash management terms too, not only facilities. Notice periods
hide in those as well.

## Then get them out of the file

A date that only exists in a file is a date nobody is chasing. Finish by producing calendar
entries the user can paste or import, one per deadline, with a reminder 30 days before and the
clause reference in the body.

Offer the list as `.ics` if the user wants to import it directly.
