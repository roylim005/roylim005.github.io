# TPB Interview Copilot — PSY265 GBA01

Live-interview aid for the HSG screening-uptake interviews: the human interviewer reads each
question aloud and types the interviewee's answer in; the tool suggests the next question,
grounded in whichever Theory of Planned Behaviour construct (attitude, subjective norms,
perceived behavioural control, intention, barriers/motivators) still needs coverage — so
nothing sounds scripted or repeats what was just said.

## Files

- `index.html` — the tool itself.
- `interview-guide.md` — the underlying semi-structured question guide (fallback questions,
  probing technique, demographic intake template, findings log).

## Important: this only runs as a published Claude Artifact right now

`index.html` calls two Claude-specific runtime APIs that only exist when the page is opened as
a **published Claude artifact** (`claude.ai/artifact/...`):

- `claude.use("sample")` — asks Claude for the next question, live, on the viewer's own Claude
  usage.
- `claude.use("db")` — saves interview progress across sessions/devices.

Cloning this repo and opening `index.html` directly in a browser (or hosting it on GitHub Pages)
will load the page and its fixed backup question bank, but `window.claude` won't exist there —
so the AI-suggested questions, autosave, and export-to-file features will be unavailable; only
the static fallback flow works.

**To keep using the live/AI version:** open it via the Claude artifact link, not this repo.

**To make it run outside Claude, against any model (OpenAI, Gemini, a local model, etc.):** the
`buildPrompt()` and `sample.json(...)` call in the `nextQuestion()` function (and the matching
call in `summarize()`) would need to be replaced with a fetch to whichever provider's API. That
requires a small backend to hold the API key safely (an API key can't live in client-side HTML
without being exposed to every visitor) — a genuinely different, bigger project than this
student-assignment tool needs. Worth doing only if this becomes something used beyond the GBA01
assignment.

## GenAI disclosure note (per the GBA01 brief)

This tool actively shapes what gets asked during real interview data collection, not just
question brainstorming beforehand — disclose its use per your assignment's GenAI disclosure
format, alongside the question-guide brainstorming.
