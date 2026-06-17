# Guide to U.S. Map Resources Update Workflow

## Project Purpose

This project updates and verifies the map collection information represented in the
2006 published edition of the _Guide to U.S. Map Resources_. The update process
must preserve the historical 2006 data while creating current, evidence-backed
records for present-day map collections, contacts, locations, and access points.

## Historical Baseline

- Treat `US-Maps-2006.csv` as a historical baseline source.
- Do not edit `US-Maps-2006.csv` directly unless the user explicitly requests it.
- Treat the 2006 data as credible but known to be dated.
- Current research should be recorded in separate tables and linked back to the
  original 2006 record by its ID or another stable foreign key.
- If no current value can be verified, preserve the historical 2006 value in the
  current research table only when clearly marked as historical or stale.

## Suggested Data Tables

Use separate linked tables rather than overwriting the baseline data.

- `current_collections.csv`: current collection- or institution-level records.
- `collection_evidence.csv`: fact-level citations and evidence notes.
- `contacts.csv`: optional later table if contact records become complex enough
  to separate from collection records.

Every current record that corresponds to a 2006 entry should carry the original
2006 ID as a foreign key.

## Scope and Priorities

- Include all map collections that can be reasonably verified, including special
  collections with weak or minimal web presence.
- There is no strict lower limit for number of maps held.
- Prioritize larger collections, especially those with roughly 10,000 or more map
  sheets.
- Do not spend excessive time seeking fine-grained details for very small
  collections unless they are regionally important, unusually well documented, or
  the user requests deeper research.
- Focus first on current contact and access information:
  - institution name
  - library, department, unit, or collection name
  - physical location and mailing address
  - public phone number
  - public email address
  - collection or department URL
  - named contact, when current and well supported
  - current status and successor organization, if renamed, merged, or reorganized
- Update detailed holdings information only when there is strong, current
  evidence.

## Evidence and Citation Requirements

- Every factual value added or changed must have a citation.
- Record citations at the fact level whenever possible, not merely at the
  institution or row level.
- For each cited fact, capture:
  - field name
  - field value
  - source title or page label
  - source URL
  - access date
  - source type
  - source freshness or staleness assessment
  - evidence note explaining what the source supports
- Do not treat an old official webpage as sufficient evidence of current status by
  itself.
- Rank sources by both authority and apparent freshness.

## Preferred Source Hierarchy

Prefer sources in roughly this order, while using judgment for each case:

1. Current official institutional pages, especially library, archives, special
   collections, government, or map library pages.
2. Current official staff directories, contact pages, Ask a Librarian pages,
   department pages, or public service desk pages.
3. Current catalog, finding aid, LibGuide, repository, or collection management
   records hosted by the institution.
4. Trusted third-party collection directories or bibliographic sources, including
   WorldCat/OCLC, ArchiveGrid, state library directories, professional
   association pages, university catalogs, and relevant annual reports.
5. Web archives, old official pages, PDFs, newsletters, and other stale sources,
   used mainly to establish history, continuity, or clues for further research.

## Contact Information Rules

- Prefer departmental, unit, service desk, reference, map library, archives, or
  special collections contact information over personal contact information.
- Try to identify a named contact when there is current, strong evidence, but do
  not force one.
- Role-based contacts are often safer and more durable than named individuals.
- Email addresses and phone numbers require strong evidence.
- Prefer `.edu`, `.gov`, and institutional `.org` email addresses.
- Treat personal email domains such as Gmail, Hotmail, Yahoo, or similar services
  as questionable unless clearly supported by current institutional context.
- If no map-specific contact exists, use a main reference desk, special
  collections desk, archives desk, or Ask a Librarian contact as a fallback.
- Avoid relying on personal emails or phone numbers scraped from stale PDFs,
  newsletters, or archived pages unless the user explicitly asks for deeper
  investigation and the uncertainty is clearly marked.

## Status and Uncertainty

Use explicit uncertainty statuses rather than hiding ambiguity in notes.

Recommended statuses:

- `confirmed_current`: current status is supported by strong recent evidence.
- `likely_current`: probably current, but evidence is incomplete or indirect.
- `partial_evidence`: some current facts are verified, but major questions remain.
- `historical_only`: only historical or stale evidence is available.
- `merged_or_renamed`: the 2006 collection appears to have a current successor.
- `unable_to_verify`: reasonable searching did not verify current status.
- `probably_inactive`: evidence suggests the collection or public service point is
  no longer active, but this is not fully confirmed.
- `needs_human_review`: the case requires judgment, outreach, or user review.

## Renames, Mergers, and Reorganizations

- Preserve the 2006 identity and link it to any current successor record.
- Do not silently replace an old institution, department, or collection name with
  a new one.
- Record evidence for the relationship between the 2006 entity and the current
  successor.
- Use research notes to explain changes such as renamed libraries, merged map
  collections, reorganized special collections departments, campus closures, or
  transferred holdings.

## Batching Workflow

- Default to state-by-state batches.
- Keep batches small enough that each record can be reviewed and audited.
- For each batch, produce or update current records and evidence records together.
- Do not run broad, expensive, or unfocused research across many states unless the
  user explicitly asks for it.

## Per-Collection Checklist

For each 2006 entry under review:

1. Confirm whether the institution still exists.
2. Confirm whether the map collection, map library, archive, or successor unit
   still exists.
3. Identify any current successor name if renamed, merged, or reorganized.
4. Verify current physical location or mailing address.
5. Verify departmental, unit-level, or map-specific public contact page.
6. Verify public email address.
7. Verify public phone number.
8. Look for a named contact when available and current.
9. Record source evidence for every fact.
10. Assign an uncertainty status.
11. Write a short human-readable research note.

## Public-Ready vs. Research-Only Data

- It is acceptable to collect fields that are useful for research but may not
  appear in a final public guide.
- Mark uncertain, stale, private-looking, or otherwise questionable values as
  research-only or requiring review.
- Public-facing final data should favor durable institutional contacts and
  clearly verified facts.
