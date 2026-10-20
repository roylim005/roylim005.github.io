# PSY353 well-being study instruments

Static pages for administering the ECA interview and three well-being scales. No server and no tracking: answers stay in the browser (localStorage) until exported as JSON.

| File | Instrument | Items | Export file |
| --- | --- | --- | --- |
| `index.html` | Landing page linking all instruments | – | – |
| `interview.html` | Semi-structured interview notes (16 questions, probes, quotes) | 16 | `interview_<pseudonym>_<date>.json` |
| `swls.html` | Satisfaction With Life Scale (Diener et al., 1985) | 5 | `swls_<pseudonym>_<date>.json` |
| `flourishing.html` | Flourishing Scale (Diener et al., 2010) | 8 | `flourishing_<pseudonym>_<date>.json` |
| `perma.html` | PERMA-Profiler (Butler & Kern, 2016) | 23 | `perma-profiler_<pseudonym>_<date>.json` |

## Publish with GitHub Pages
1. Create a repository and upload all files to its root.
2. Settings > Pages > Build and deployment: deploy from the `main` branch, `/ (root)`.
3. Open `https://<username>.github.io/<repo>/`.

Consider a private repository or an unlisted name. The pages hold no data, but the URL is public on a free account.

## JSON structure (surveys)
- `instrument`: id, name, citation, response range and labels
- `participant.pseudonym`
- `session`: started_at, exported_at, duration_seconds
- `complete`, `missing_items`
- `responses[]`: item, code, text, value, label or anchors, answered_at
- `scores`: totals or domain means, plus comparison norms

The interview export holds session details, each question with probes covered, notes and key quotes, and the interviewer reflections. It also includes a `raw` block so the file can be reloaded into `interview.html` with **Load JSON**.

## Notes
- Use pseudonyms only. On a shared device, download each JSON and then clear the answers.
- PERMA-Profiler: register with the developers before use (see the PERMA-Profiler PDF). Free for noncommercial use with credit.
