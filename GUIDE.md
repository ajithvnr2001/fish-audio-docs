# GUIDE — docs.fish.audio docs: full redo + incremental updates (end to end)

Written from the run that produced the full corpus. Redo from scratch via §2; daily updates via §3 (GitHub Actions, already wired).

## 0. Scope + architecture

Crawls **https://docs.fish.audio/** — 175 sitemap pages (api-reference 73, developer-guide 53, agents 35, features, overview, contributing, archive). `llms.txt` (curated AI-agent index) + `llms-full.txt` (full raw markdown) snapshotted to `docs/_llms/`.

Pipeline (`crawl_fish.py::fetch_one`): `Scrapling` → main-content → **ScrapeGraphAI** → **Crawl4AI** fallback → **httpx**. Raw `.txt` mirrors fetched as text.

State: `crawl_state.json`, `docs/_index.jsonl`, `docs/_meta/*`, `docs/_manifest.json`, `docs/_last_verified.json`, `crawl.log`.

## 1. Setup (fresh machine)

```bash
git clone https://github.com/ajithvnr2001/fish-audio-docs
pip install -r requirements.txt
python -m playwright install chromium
```

## 2. Full crawl redo

```bash
python3 crawl_fish.py --max-pages 800 --concurrency 10
python3 update_incremental.py --check-only            # expect new=0
find docs -name '*.md' | wc -l
```

Resumable; failed pages recorded in the state file.

## 3. Daily incremental updates (GitHub Actions)

`.github/workflows/update-docs.yml` runs daily **07:30 UTC** (staggered docs family). Same mechanics as siblings: live sitemap + `lastmod` diff → crawl new → refresh stale newest-first (cap 100) → daily stamp + README "Last verified:" → commit + push with rebase-retry (`--ours` on stamp files).

Manual: Actions → daily-docs-update → Run workflow, or locally `python3 update_incremental.py --concurrency 10`.

## 4. Verifying

```bash
python3 update_incremental.py --check-only
python3 -c "import json;print(json.load(open('docs/_last_verified.json')))"
```

## 5. VM eviction recovery

`fish-crawl.service` (`Restart=on-failure`) + `boot.sh` + `cloud-init.yaml`; `/data` durable, git secondary.

## 6. Gotchas (real ones we hit)

| Symptom | Fix |
|---|---|
| llms-full.txt is a single 1MB blob | saved as `_llms/` snapshot, not parsed as docs — sitemap is the seed of truth. |
| `.md` links inside llms.txt point to raw content | intentionally NOT fetched as separate docs (they duplicate sitemap pages); use them via the coder scripts if you want. |
| Mintlify client-side nav | main-content extraction handles it; check `method` in frontmatter when debugging. |
| Stamp-file rebase conflicts in Actions | `--ours` checkout (already in workflow). |
