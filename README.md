# Fish Audio Docs — End-to-End Crawler

> Last verified: 2026-10-23 — see `docs/_last_verified.json` (rewritten daily by GitHub Actions).

Crawls **https://docs.fish.audio/** completely (175 sitemap pages: api-reference, developer-guide, agents, features, overview) and saves clean markdown. Three stacks: **Scrapling** → **Crawl4AI** → **ScrapeGraphAI** (local, no LLM key). `llms.txt` (curated agent index) + `llms-full.txt` (full raw markdown) snapshotted under `docs/_llms/`.

## Install

```bash
pip install -r requirements.txt
python -m playwright install chromium
```

## Run (resume-safe — re-run to resume)

```bash
python3 crawl_fish.py --max-pages 800 --concurrency 10
python3 update_incremental.py --check-only   # new URLs + lastmod-stale only, never recrawls
python3 update_incremental.py
```

## Layout

```
crawl_fish.py  update_incremental.py  requirements.txt
guide_code/      # coder guide + coder_scrape.py / coder_update.py
fish-crawl.service  boot.sh  cloud-init.yaml   # spot-VM boot resilience
docs/            # output: <section>/<path>.md + _meta/ + _index.jsonl + _manifest.json
```

## Notes

- `lastmod` on every sitemap URL → incremental refresh is precise.
- The curated agent-facing `llms.txt` changes independently — snapshotted each run.
