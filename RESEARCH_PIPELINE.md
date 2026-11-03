# Daily research pipeline

Existing site/schema are preserved. Schedule: 00:00 UTC / 08:00 Asia/Shanghai; GitHub schedules may be delayed. At most five papers per Shanghai calendar day, with a seven-day arXiv discovery window and a 40-candidate cost cap. This is not exhaustive coverage.

## Required setup
Choose DeepSeek official API with a funded API account. In this repository open Settings → Secrets and variables → Actions → Secrets → New repository secret. Name: DEEPSEEK_API_KEY. Paste your API key into Secret and click Add secret. Never paste the key into a chat, source file, issue, or workflow.
Optional: Variables → New repository variable → DEEPSEEK_MODEL (default deepseek-flash). No other secret is required; GitHub supplies GITHUB_TOKEN.
Actions must allow repository writes and workflow dispatch.

## Verify before relying on publication
Actions → Daily research pipeline → Run workflow → leave dry_run checked. Confirm green completion and inspect research-run artifact latest.json.
After adding the key, repeat with dry_run unchecked. Verify content changes, review a published analysis against its paper, then confirm Publish MultiModal Research Daily succeeds.
Local syntax and canonical-ID/title/HTML extraction checks passed during installation. Live AI publication has NOT been tested with user credentials.

## Behavior and limitations
arXiv metadata is authoritative for identity and submission date. Canonical arXiv IDs remove version suffixes; title and DOI matches against published archive prevent duplicates. Alternate titles/IDs can still evade matching; OpenAlex/Crossref enrichment is not yet implemented.
Only accessible arXiv HTML containing a substantial body and references is accepted. PDF-only papers are skipped. Full text exceeding the input budget is skipped rather than truncated.
AI selection, technical analysis and fact review are separate API calls; review uses a fresh context but the same provider/model, not a human or independently trained reviewer. Exact quote checks fail closed. Model review cannot guarantee factual correctness.
No qualifying papers produces an empty issue and preserves prior papers. Source/API failure does not overwrite content. Per-paper failures skip that paper; sanitized artifacts record IDs/error types without credentials or source bodies.
Dry run collects and deduplicates only, incurs no AI cost and never writes content. A successful dry run does not validate the paid AI path.
Logs are retained as Actions artifacts for 30 days. The website itself stays static.
Bot commits do not automatically trigger another Actions workflow, so the pipeline explicitly dispatches the existing pages.yml after pushing.
