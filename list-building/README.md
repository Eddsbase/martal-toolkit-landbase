# List-Building — SDR-Hiring Sales Decision-Makers

Build a list of **sales decision-makers** (CRO, VP/Head/Director of Sales, VP Sales Development, VP RevOps) at companies with **≥50 employees AND ≥$50M revenue** that are **actively hiring SDRs/BDRs** and/or **publicly voicing pipeline / booked-meeting pain**.

## Files

- **`intent-signal-search-kit.csv`** — the LinkedIn Sales Navigator, LinkedIn/ATS jobs, and Reddit searches to source candidates, with signal strength.
- **`sdr-hiring-decision-makers-list.csv`** — the list template (Landbase-mappable columns). Rows are placeholders, not real people.

## Workflow

1. **Source** — run the searches in `intent-signal-search-kit.csv`. Strongest signal = a company hiring SDRs *while* a sales leader posts about the meeting gap.
2. **Qualify** — keep only accounts meeting the ICP (≥50 employees AND ≥$50M revenue). Record the company + the proof-of-pain `signal_source_url`.
3. **Enrich** — import qualified rows into the **Landbase platform** to populate `work_email` / `direct_phone` and verify them. This is the only compliant way to get contact data — Reddit is pseudonymous and LinkedIn can't be scraped, so contacts are never hand-keyed from social.
4. **Activate** — push the verified, signal-backed list into outreach with the `personalization_hook` (their actual pain) as the opener.
