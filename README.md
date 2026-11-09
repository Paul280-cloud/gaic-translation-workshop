# Local English-to-French/Spanish Translator (QVAC)

A small command-line translator that runs an AI translation model **locally** on your computer using the QVAC SDK (`@qvac/sdk` 0.22.0, Bergamot models). After the one-time model download, translation needs no internet and no API key.

Built for the GAIC x Tether bootcamp, Week 1 checkpoint.

## Feature

Translate English text to French or Spanish from the terminal.

## Setup

1. Install **Node.js 22.21.x** (check with `node --version`). On macOS you can use `brew install fnm`, then `fnm install 22.21.1` and `fnm use 22.21.1`.
2. Install dependencies. If you get `ETIMEDOUT` on a slow network, use the longer timeouts:

   ```
   npm install --fetch-timeout=600000 --fetch-retries=8 --fetch-retry-mintimeout=20000
   ```

## Run

```
npm run translate                                  # English to French, default sentence
npm run translate -- "The meeting starts at 6 pm." # your own sentence (French)
npm run translate:es                               # English to Spanish
npm run translate:es -- "The meeting starts at 6 pm."
```

The first run downloads the model (needs internet). Later runs use the saved model.

## Test results

Tested on macOS (Apple Silicon), Node v22.21.1, SDK 0.22.0.

| English | Output | Time |
|---|---|---|
| The meeting starts at 5 pm. | FR: La rencontre commence à 17 heures. | 203 ms |
| The meeting starts at 6 pm. | FR: La rencontre débute à 18h. | 198 ms |
| The meeting starts at 5 pm. | ES: La reunión comienza a las 5 p.m. | 209 ms |
| The meeting starts at 6 pm. | ES: La reunión comienza a las 6 p.m. | 214 ms |

Numbers and times were checked and are correct. Wording quality is **not yet checked by a fluent speaker**. See [MY-RESULTS.md](MY-RESULTS.md).

## Offline status

Not yet tested without internet. A connected run is not proof of offline operation.

## Blockers

None. The only issue was an `npm install` network timeout (fixed with the longer timeouts above).
