# Puzzle Arena — V0.3 Smart Multiplayer Edition

Mobile-first multiplayer educational quiz game for ages 3–12.

## V0.3 changes
- Room QR code in the host lobby. Scanning opens the game with the room PIN prefilled; the player enters a nickname and taps Join.
- Expanded age-calibrated question bank for pictures, maths, spelling and logic.
- Question IDs are remembered per room across sessions until the pool needs to recycle.
- Leave controls moved away from Next Round and protected by a confirmation prompt.
- Existing English/Bahasa Melayu interface and Firebase Realtime Database support retained.

## Firebase
Keep `firebase-config.js` alongside `index.html`. It contains the Firebase web-app configuration for this project. Firebase web config is public client configuration; secure access with Realtime Database Security Rules. Do not add service-account credentials or Admin SDK secrets.

## GitHub Pages
Upload all files in this folder to the repository root, replacing the previous version, then commit. GitHub Pages should publish from `main` and `/(root)`.

## Notes
The room QR image is generated using the QR Server image endpoint at runtime. A network connection is required to display it. QR scanning uses the URL query parameter `?room=PIN`.
