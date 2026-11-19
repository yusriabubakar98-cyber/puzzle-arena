# Puzzle Arena — Multiplayer Kids Challenge

A mobile-first, room-based educational quiz prototype for ages 3–12. Supports 2–10 players, four question categories, timed answers, speed-based scoring and a live leaderboard.

## Included
- `index.html` — responsive game frontend
- `firebase-config.js` — Firebase web configuration placeholder
- `database.rules.json` — starter Realtime Database rules for authenticated prototype users

## Run locally
Because Firebase SDKs are loaded from Google's CDN, use a local web server rather than opening the file directly:

```bash
python -m http.server 8000
```

Open `http://localhost:8000`.

Without Firebase configuration the page displays a local preview, but room creation/joining is intentionally disabled. This avoids presenting a fake multiplayer experience.

## Enable real-time multiplayer
1. Create a project at https://console.firebase.google.com/.
2. Add a **Web app** to the project and copy its Firebase config.
3. In **Build → Authentication → Sign-in method**, enable **Anonymous**.
4. In **Build → Realtime Database**, create a database in a nearby region (Asia Southeast is suitable for Malaysia).
5. Copy the web config into `firebase-config.js`. Replace every `YOUR_...` value and use the exact `databaseURL` supplied by Firebase.
6. In Realtime Database → Rules, publish the contents of `database.rules.json`.
7. Host the files on GitHub Pages (steps below).

### Security note
The supplied rules are a prototype baseline, not production-grade authorization. Any signed-in anonymous user can read/write room records. Before inviting the public, add server-enforced validation for room capacity, host-only game-state changes, answer ownership, score integrity, rate limits and room expiry. For production, move authoritative scoring and state transitions to trusted Cloud Functions or another server.

## Publish with GitHub Pages
1. Create a GitHub repository, e.g. `puzzle-arena`.
2. Upload `index.html`, `firebase-config.js`, and `README.md` (and optionally `database.rules.json`) to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**, choose `main` and `/ (root)`, then Save.
5. Wait for GitHub Pages to publish. Your game URL will be shown on that page.

Do not commit service-account JSON files or any Firebase Admin credentials. The browser Firebase config is public by design; database rules and server-side validation provide security.

## Prototype gameplay
- Host creates a 4-digit PIN room.
- Players enter the PIN and join the lobby.
- Host starts when at least two players are present.
- Each game contains up to 10 mixed questions.
- Correct answers score up to 500 points; faster answers earn more.
- Host advances after all players answer or the 20-second timer expires.

## Current limitations
- Question bank is a small hard-coded starter set, shuffled for each game.
- The selected age range adjusts the maths and logic question difficulty; picture/word questions are shared starter content.
- No moderation, parent accounts, persistent profiles, chat or anti-cheat system yet.
- Players should use nicknames; do not collect children's personal information.
