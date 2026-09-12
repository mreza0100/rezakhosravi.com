# rezakhosravi.com

Plain HTML personal site and essays, hosted on GitHub Pages. No build step on the server, no JavaScript, and nothing loads from third parties.

- Essays are generated: edit the markdown sources, then run `python3 ~/work/host-ops/blog/infra/migrate.py` from this directory. It writes `essays/<slug>/index.html` and `index.md`, `img/essays/`, the essays index, the homepage list, `feed.xml`, `sitemap.xml`, `llms.txt` and `llms-full.txt`. The sources are the single source of truth and live in `~/work/host-ops/blog/sources/` (tracked): `merged/`, `mamzi/`, `drafts/`, the reading order in `SERIES`, alt text in `ALT.tsv`. Everything under `essays/`, plus `llms*.txt`, the feed and the sitemap, is generated from them.
- Share cards: `python3 ~/work/host-ops/blog/infra/og-cards.py` (needs the dev server up) renders `img/og/<slug>.png` and `img/og/default.png`; rerun `migrate.py` afterwards so the post heads reference them.
- The other pages (home, about, work, contact, disclosures, privacy, 404) are edited by hand. The pre-publish gate checklist lives in `tmp/unpublished/_templates/post.html` (not published); run it over any new essay.
- `.nojekyll` is present on purpose: the site ships raw `.md` editions and `llms*.txt`, which Jekyll would otherwise rewrite or drop. Unpublished material (design canvas, lab page, templates) lives under the gitignored `tmp/unpublished/`.
- Images: `img/reza.jpg` (square headshot), `img/og/` (1200×630 share cards), `img/essays/<slug>/` (generated), icons at the root (`favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`, `icon-512.png`).
