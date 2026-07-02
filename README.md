# transLation — Cakap Omputih 🇲🇾→🇺🇸

A Malay → **native English** learning app. Type a phrase in Bahasa Melayu and get back how a real American would say it — not textbook English.

## MVP (current)

For every Malay phrase, the app returns:

- **FORMAL** — for professional / official situations
- **CASUAL (native)** — how Americans actually say it day-to-day
- **💡 Context note** — one line (in Malay) on when to use which

Everything lives in a single `index.html` — no build step. Translations come from Gemini via a serverless proxy so the API key stays secret.

## How it works

```
index.html (GitHub Pages)
    └── POST { prompt } → Vercel proxy /api/gemini
                              └── Gemini 2.5 Flash (GEMINI_API_KEY env var)
```

Currently `PROXY_URL` in `index.html` points at the existing shared proxy (`muhasabah-app.vercel.app/api/gemini`), which already allows `rezkysaid.github.io` — so the app works as soon as GitHub Pages is enabled.

### To give this app its own proxy (optional)

1. Deploy the `proxy/` folder as a new Vercel project.
2. Set the `GEMINI_API_KEY` environment variable in Vercel.
3. Update `PROXY_URL` at the top of the `<script>` in `index.html`.

## Roadmap

- **Phase 2:** slang/idiom breakdowns, common Malaysian mistakes, extra example sentences, pronunciation hints
- **Phase 3:** business English mode, saved phrases/history, reverse mode (English → explained in Malay)

See `SPEC.md` for the full spec.
