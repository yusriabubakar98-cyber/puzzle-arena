# Puzzle Arena — Multiplayer Kids Challenge (Update)

Mobile-first multiplayer educational quiz for ages 3–12, with 2–10 players per room. Hosted as a static site (e.g. GitHub Pages) and synchronized through Firebase Realtime Database.

## Update contents
- **Play Again reset:** host returns the same room to the lobby; player scores and round state reset; host can start a fresh match.
- **Automatic progression:** when every connected player has submitted, the answer reveal appears and the host automatically advances after 3.5 seconds. If someone does not answer, the 20-second timer triggers the reveal and auto-advance.
- **Per-player language:** English or Bahasa Melayu is saved separately for each player before creating/joining. The same canonical question and answer are used for all players; supported question/answer text is rendered in each player's language.
- **QR room join:** lobby QR opens the same site with the room PIN prefilled; PIN entry remains available.
- Retains age groups, four puzzle modes, room PIN, 2–10 player rooms and leaderboard.

## Deploy to the existing GitHub Pages site
1. Download and extract this ZIP.
2. Open your existing GitHub repository `puzzle-arena`.
3. Replace the existing `index.html`, `firebase-config.js`, `database.rules.json`, and `README.md` with these files (upload/commit all four).
4. Wait for GitHub Pages to finish publishing, then refresh the game URL.
5. Test with two separate devices or browser sessions: create room, join by PIN, join by QR, answer, auto-advance, finish, Play Again, and start a second match.

## Firebase configuration and safety
The Firebase web config is a public client configuration, not an Admin credential. Never publish service-account JSON or Admin SDK private keys.

**Important:** `database.rules.json` is retained as a prototype-only ruleset, not secure for public use with children. It permits any authenticated anonymous user to read and write room data. Before a public launch, implement server-enforced room membership, host-only state changes, answer ownership, score validation, rate limiting and room expiry (e.g. Cloud Functions). Do not collect children's real names or other personal data.

## Technical notes / current limitations
- QR generation uses the QRCode.js CDN; the first load needs internet access.
- The question bank remains a small prototype bank. Language translation covers the included starter questions and answer choices; some English puzzle content (especially letter-pattern questions) remains unchanged where direct translation would change the puzzle.
- Auto-advance is coordinated by the host browser. If the host disconnects during a round, automatic progression pauses until the host reconnects.
- This ZIP has been statically checked; live Firebase multiplayer behavior must still be tested on the deployed site with at least two clients.
