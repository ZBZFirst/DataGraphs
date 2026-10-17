# Drudge archive

The graphical morning launcher runs `schooljobs_scraper/drudge_morning.py` once per
local day. It executes `Downloads/FireFoxDownloads/drudge_collect.py`, saves its
working data under `~/drudge_archive`, then commits a consistent SQLite backup
here and pushes the same `ZBZFirst/DataGraphs` repository used by Job Review.

`drudge.sqlite3` contains every collection run. `links` contains the page links
and full source directory for each run, including labels, positions,
classifications, and image URLs. `source_deltas` records source directory
changes. `sources.json` is the current comparison baseline.

To retry a failed push without collecting again:

```bash
/home/paulwasthere/Downloads/.venv/bin/python /home/paulwasthere/schooljobs_scraper/drudge_morning.py --backup-only
```

To restore the collector baseline, copy `drudge.sqlite3`, `sources.json`, and
`source_deltas.jsonl` (if present) to `~/drudge_archive/`.
