# DataGraphs

Static public data for [ZeBeZo Job Review](https://www.zebezo.org/web-experiments/job-review/).

This bundle contains 43 observed dates through September 29, 2026, with one
graph snapshot and pay summary per date and 13,111 individual public job-detail
cards. The September 29 listing population is complete, while its enrichment is
marked partial in the manifest and graph snapshot.

## Files

- `data/manifest.json`: timeline index, filter metadata and data delivery paths.
- `data/timeline/`: canonical graph snapshots with geometry, organization colors,
  sectors and keyword-match sets.
- `data/pay/`: annualized pay summaries, loaded for visible dates.
- `data/jobs/`: public job details, loaded only when a job is clicked. Filenames
  are the SHA-256 digest of the canonical job ID.
- `data/search/`: compact term-to-job indexes by organization, loaded only for
  a word search. These contain no raw descriptions or parsed item text.
- `SHA256SUMS`: checksums for every data file.
- `bundle-info.json`: counts and release identity.
- `.nojekyll`: publishes these static files without Jekyll processing.
- `index.html`: a small landing page linking to the manifest and ZeBeZo viewer.

The SQLite database, raw saved pages, application records, interview notes,
resumes and private server configuration are not included. These are public
listing/enrichment exports, not a full database upload. Historical listings use
stored enrichment captured at publication, not reconstructed historical enrichment.
