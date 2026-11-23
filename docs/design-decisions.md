# Design decisions

| Area | Decision |
|---|---|
| Inputs | Notice PDFs from multiple agent banks, each in its own layout |
| Classification | Classify the notice type first, then use a schema specific to that type |
| Extraction | Fixed schema per notice type; each field keeps its source page |
| Validation | Recalculate interest from Term SOFR, margin, day count and period; check dates and our share |
| Position matching | Through MCP tools, so the agent never queries the loan system directly |
| Booking | Only when every check passes within tolerance |
| Exceptions | Analyst queue with the mismatched fields shown side by side |
| Never | Books a mismatch, edits a facility, or changes a position outside a booked event |

## Planned evaluation

A set of sample notices in several agent-bank layouts with known correct fields, plus deliberate errors: wrong
SOFR fixing, wrong day count, wrong share, a missing payment date. Measures: field accuracy per notice type,
correct match or exception decision, and zero wrong bookings.
