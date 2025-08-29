# API Key Usage Checker (Meme)

Single-file joke page that “checks” whether someone else is using your API key. Everything runs 100% in the browser: there is no backend and nothing is sent anywhere (besides loading Tailwind from a CDN and avatars from Unavatar).

> Obviously a joke — don’t paste real API keys anywhere.

## Run locally

- Open `index.html` in your browser. No build or server is needed.
- An internet connection loads Tailwind (CDN) and avatars (Unavatar). Offline, the page still works but will look unstyled and without avatars.

## Features

- API key format validation (not real verification): OpenAI and Anthropic.
- Simulated scan with progress bar and final result.
- Random result: sometimes it “finds” someone else with an X/Twitter handle and avatar.
- Fixed list of possible users: `levelsio`, `theo`, `plbiojout`, `rauchg`, `leerob`, `shadcn`, `gnukeith`, `nicolasoulianov`.
- Tiny floating disclaimer that appears in a random position on each page reload.

## How it works

- 100% client-side. The key you paste never leaves the browser.
- Only the pattern (format) is validated, not real authenticity. If the format isn’t OpenAI/Anthropic-like, the scan won’t start and inline feedback appears.
- If “someone else” is detected (configurable probability), one user is picked from your list and displayed with an avatar (`unavatar.io`) and link to `twitter.com/<handle>`.

## Quick customization

- Suspects list: edit `SUSPECT_USERS` at `index.html:61`.
- Probability for “someone else”: edit `PROB_USED_BY_SOMEONE` at `index.html:63`.
- Recognized key patterns: extend `KEY_PATTERNS` at `index.html:65`.
- Floating disclaimer (text/position): element `#floatingNote` at `index.html:223` and the positioning script just below it.

## Key validation (approximate)

- OpenAI: patterns like `sk-live-…`, `sk-test-…`, `sk-proj-…`, and long `sk-…` alphanumerics.
- Anthropic: patterns `sk-ant-…`.
- To add another provider, add an object to `KEY_PATTERNS` with a `vendor` label and `match(key)` predicate using your RegExp.

## Dependencies & network

- CSS: Tailwind via CDN (`https://cdn.tailwindcss.com`).
- Avatars: Unavatar (`https://unavatar.io/x/<handle>` with a fallback to `https://unavatar.io/<handle>`).
- Offline: the page opens, but without CDN styles and avatar images.

## Safety & privacy

- Don’t paste real API keys. This is for laughs only.
- The input is never sent anywhere; it lives only in browser memory.
- For extra peace of mind, disconnect from the internet and open the file; it still runs (just unstyled and no avatars).

## Credits

- Tailwind CSS (CDN)
- Unavatar for profile images

---

Made for fun. Use responsibly. 😄
