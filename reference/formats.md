# Statement and billing formats

Relevant because the monthly fee check is far easier against structured data than against a
PDF, and because enrollment has a lag that catches people out.

## The two to ask for

**camt.086** — the ISO 20022 bank services billing statement. Your fee invoice as structured
XML rather than a PDF. This is what makes "charged against agreed" something you can run
rather than read. Known in older documentation as BSB, the TWIST standard it came from.

**camt.053** — the ISO 20022 end-of-day account statement. Ask for it if the bank is still
sending MT940 or PDF. `camt.052` is the intraday equivalent.

## The part that catches people

Banks produce these from the date you enroll. They will not go back and reissue history, so
everything before enrollment stays in whatever format you had at the time.

Enrollment is what starts the clock. It costs an email and nothing is lost if automation never
happens.

## What this means for the record

The format each bank sends is worth noting once in the record's sources table rather than
taking a row of its own. It becomes a row only if the bank agreed in writing to provide
something they are not yet providing, which makes it an open promise.
