# My translation results (GAIC workshop)

**Setup:** macOS (Apple Silicon), Node v22.21.1 (via fnm), @qvac/sdk 0.22.0, model BERGAMOT_EN_FR.

**Commands run**

1. `npm install --fetch-timeout=600000 --fetch-retries=8 --fetch-retry-mintimeout=20000`
   The default `npm install` failed with `ETIMEDOUT`; longer timeouts and retries fixed it (5 minutes).
2. `npm run translate` (first run downloads the model)
3. `npm run translate -- "The meeting starts at 6 pm."`

**Results**

| Input (English) | Output (French) | Time |
|---|---|---|
| The meeting starts at 5 pm. | La rencontre commence à 17 heures. | 203 ms |
| The meeting starts at 6 pm. | La rencontre débute à 18h. | 198 ms |

**Spanish (extra feature):** `npm run translate:es` uses BERGAMOT_EN_ES with from `en` to `es`.

| Input (English) | Output (Spanish) | Time |
|---|---|---|
| The meeting starts at 5 pm. | La reunión comienza a las 5 p.m. | 209 ms |
| The meeting starts at 6 pm. | La reunión comienza a las 6 p.m. | 214 ms |

**Checks**

- Numbers: 5 pm became 17 heures and 6 pm became 18h. Both are correct 24-hour times.
- Names and dates: none in these sentences.
- Main message (the meeting starts at a given time): kept.
- Wording: "rencontre" is understandable, but "réunion" is the more usual word for a business meeting. Quality not yet checked by a fluent French speaker.

**Offline test:** not yet tested. A connected run is not proof of offline operation.

**Blockers:** none now. Earlier network timeouts only affected the install.
