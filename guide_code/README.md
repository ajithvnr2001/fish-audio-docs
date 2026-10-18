# Guide: scrape + update Fish Audio docs (coder end-to-end)


Last verified: 2026-10-18 (rewritten daily by GitHub Actions).
Base: `/data/opencode/fishaudio/` · Target: `https://docs.fish.audio/` (6,854 sitemap URLs → ~653 canonical after `?hl=` locale dedupe + linked reference domains)

Last verified: 2026-10-18 (stamp rewritten daily by the GitHub Action).

## 1. Scrape one page (all 3 libs)

```bash
python3 guide_code/coder_scrape.py https://docs.fish.audio/gemini-api/docs /tmp/g.md
```

Flow (`coder_scrape.py`): `Fetcher.get(stealthy_headers=True)` → keep `<main>/<article>` → `scrapegraph-ai/utils/convert_to_md.py::convert_to_md` → fallback `AsyncWebCrawler(CacheMode.BYPASS)`. Raw-text mirrors (`*.md.txt` in sitemap) are fetched as-is.

## 2. Full crawl

```bash
python3 crawl_ai.py --max-pages 8000 --concurrency 15
```

Seeds = `sitemap_0_of_1.xml` (deduped) ; `normalize_url()` allows `docs.fish.audio` + `aistudio/saif/discuss/developer.android/developer.chrome`, skips binary/`.json`/backtick/console; saves `docs/<path>.md` + `_meta/*.json`, appends `_index.jsonl`. Reference domains land in `docs/_subdomains/<host>/` (depth ≤ 1, login-walled hosts recorded as failed).

## 3. Update without recrawling

```bash
python3 update_incremental.py --check-only
python3 update_incremental.py
python3 guide_code/coder_update.py --check-only
python3 guide_code/coder_update.py --run --concurrency 10
```

## 4. Verify

```bash
python3 update_incremental.py --check-only   # expect new=0
find docs -name '*.md' | wc -l
cat docs/_manifest.json
```

## 5. Surviving VM restarts

- `fish-crawl.service` (systemd, `Restart=on-failure`) + `boot.sh` + `cloud-init.yaml`: power returns → service starts → crawl resumes from `crawl_state.json`.
- One-time: attach `cloud-init.yaml` as custom-data if the VM is ever deleted/recreated.

## Tools

- D4Vinci/Scrapling, unclecode/crawl4AI, ScrapeGraphAI/Scrapegraph-ai (`tools/`, symlinked shared clones; pip fallback in resolver).
