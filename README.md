# Puzzle Arena — Multiplayer Kids Challenge (V0.2)

Mobile-first room-based educational quiz for ages 3–12, supporting 2–10 players.

## V0.2 updates
- English / Bahasa Melayu interface selector.
- Malay picture-answer vocabulary and Malay word-completion questions.
- Room host's language selection determines the question language for everyone in that room.
- Fixed round progression: the host now checks the live Realtime Database snapshot whenever room data changes. When every current player has submitted an answer, the host automatically changes the round to the reveal phase and the **Next Round** button appears. The 20-second timer remains the fallback.

## Files
- `index.html` — game frontend and multiplayer logic
- `firebase-config.js` — Firebase web configuration
- `database.rules.json` — prototype Realtime Database rules

## Publish update
Upload/replace these files in the root of the existing GitHub repository and commit the changes. GitHub Pages will redeploy automatically. Keep the repository's existing Pages settings (`main` / root).

## Important security note
The current database rules are only suitable for controlled prototype testing. Any signed-in anonymous user can read and write room records. Before public use, implement server-enforced host permissions, answer ownership, score validation, rate limits and room expiry (e.g. trusted backend/Cloud Functions). Do not collect children's personal information; use nicknames only.
