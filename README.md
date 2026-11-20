# Puzzle Arena — Multiplayer Kids Challenge

Mobile-first multiplayer quiz game for ages 3–12, with room PINs and Firebase Realtime Database.

## This update
- Word Guessing is text-only: no picture hint.
- Word questions show an incomplete word and four spelling choices. Each question has one correct answer and three deliberately incorrect distractors.
- English and Bahasa Melayu word clues and choices are authored as separate language versions; the answer key remains stable across languages.
- Each player selects their own language before joining.
- Retains room PIN, QR join, age groups, four puzzle categories, leaderboard, auto-advance and Play Again reset.

## Deploy to GitHub Pages
1. Download and extract this ZIP.
2. Open the existing GitHub repository `puzzle-arena`.
3. Replace `index.html`, `firebase-config.js`, `database.rules.json`, and `README.md` with the files in this package, then commit.
4. Wait for GitHub Pages to publish and refresh the site.
5. Test with two separate devices/browser sessions, including a Malay player and an English player in the same room.

## Firebase security note
The included database rules are prototype-only and allow any authenticated user to read/write room data. Do not use these rules for a public launch, especially with children. Before public release, implement trusted server-side validation for scores, room membership, answer submission, capacity and room expiry. Never publish Firebase Admin SDK credentials or service-account keys.
