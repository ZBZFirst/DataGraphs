# DataGraphs

Static public data for [ZeBeZo Job Review](https://www.zebezo.org/web-experiments/job-review/).

This bundle contains the exact JSON from the approved `20260929-job-review-v2`
release: 42 observed dates through September 28, 2026; 42 graph snapshots;
42 pay summaries; and 12,811 individual public job-detail cards.
The JSON data is approximately 289 MB (276 MiB).

## Files

- `data/manifest.json`: timeline index, filter metadata and data delivery paths.
- `data/timeline/`: canonical graph snapshots with geometry, organization colors,
  sectors and keyword-match sets.
- `data/pay/`: annualized pay summaries, loaded for visible dates.
- `data/jobs/`: public job details, loaded only when a job is clicked. Filenames
  are the SHA-256 digest of the canonical job ID.
- `SHA256SUMS`: checksums for every data file.
- `bundle-info.json`: counts and release identity.
- `.nojekyll`: publishes these static files without Jekyll processing.
- `index.html`: a small landing page linking to the manifest and ZeBeZo viewer.

The SQLite database, raw saved pages, application records, interview notes,
resumes and private server configuration are not included. These are public
listing/enrichment exports, not a full database upload. Historical listings use
stored enrichment captured at publication, not reconstructed historical enrichment.

## Upload and host

Upload the **contents** of this folder to the root of your public repository,
keeping the `data/` subdirectories intact and including `.nojekyll`.
Use Git to push this bundle, since it contains more than 12,000 files.
Do not use Git LFS for the published JSON files.

In repository **Settings → Pages**, choose **Deploy from a branch**, select the
branch containing these files (usually `main`) and choose **/ (root)**.
GitHub's instructions:
https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

Once Pages is published, the URLs will normally look like:

```text
https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/
https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/data/manifest.json
```

Send the published Pages URL back so the ZeBeZo viewer can be connected to it.
A public repository alone does not enable Pages hosting. Hosting does not change
node positions, pay calculations or filter membership, and updates still require
publishing a refreshed dataset.

## Connection boundary

The website stays on ZeBeZo. Only the static JSON requests will move to the new
hosting origin. The existing manifest contains relative paths such as
`./data/timeline/web_graph_2026-09-28.json` and `./data/jobs/`.
When connecting this bundle, the viewer must resolve them against the GitHub
Pages repository root, rather than the ZeBeZo page URL. Its current URL resolver
will need that small configuration change after the hosting URL is known.
Cross-origin JSON fetching will be verified then. The live ZeBeZo page has not
been switched to any placeholder URL.

## Verify the local upload folder

```bash
cd /home/paulwasthere/DataGraphs
sha256sum -c SHA256SUMS
```
