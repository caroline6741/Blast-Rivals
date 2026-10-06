# Blast-Rivals

A 3D browser deathmatch shooter inspired by Roblox RIVALS. Built with Three.js in a single `index.html` — no build step.

## Play

Open `index.html` in a browser (or serve the folder with any static server). First to 10 eliminations wins the round.

- **Bombs 💣** are the currency: earn 30 per elimination, 45 per headshot, +150 for winning a round.
- **Armory**: 7 weapons from the free Blaster to the 2,000💣 Mega Launcher — higher damage costs more bombs. Hold to fire.
- **Cosmetics**: per-gun skins and universal wraps (Gold Plate, Galaxy, Neon Circuit…).
- **Maps**: Arena, Docks, Splash (ride the slides!), Construction, Neon District, Glacier, Temple.
- **Modes**: Solo vs Bots (they get harder over time and across rounds) or live Multiplayer on the published Claude artifact.

Controls: WASD / arrow keys move, Space jump, Shift sprint, mouse aim/fire, R reload, 1–7 swap weapons, Esc pause.

## Accounts — save progress and log in from any computer

The game has three save modes and picks one automatically:

| Where the game runs | How progress is saved |
|---|---|
| Any site with Firebase configured (recommended) | **Username + password login**, progress in a Firestore database, live-synced across devices |
| The published Claude artifact | Account code (`BR-XXXX-XXXX`) in the artifact's built-in database |
| Plain `index.html` with no Firebase config | This device only (localStorage) |

### Set up Firebase (about 5 minutes, free)

1. Go to <https://console.firebase.google.com>, **Add project**, name it (e.g. `blast-rivals-game`). Google Analytics can be off.
2. **Build → Authentication → Get started → Sign-in method → Email/Password → Enable → Save.**
   (Players type a username; the game turns it into `username@players.blastrivals.app` behind the scenes.)
3. **Build → Firestore Database → Create database → Start in production mode** → pick a region → Enable.
4. In Firestore open the **Rules** tab, replace everything with the contents of [`firestore.rules`](firestore.rules), and **Publish**. This makes every player's save private to them.
5. **Project settings (gear) → Your apps → Web (`</>`) → register the app** (no hosting needed) → copy the `firebaseConfig` object.
6. Paste it into [`firebase-config.js`](firebase-config.js) as `window.BLAST_FIREBASE_CONFIG = { ... };` and commit.
7. **Authentication → Settings → Authorized domains → Add domain**: add where the game is hosted, e.g. `caroline6741.github.io`. (`localhost` is already allowed for testing.)

Reload the game — the panel under the wallet now shows **Log in / Sign up**. Sign up once, then log in from any laptop and your bombs, guns, skins and rounds-won carry over. Changes sync live between open devices.

### Optional: host on Firebase instead of GitHub Pages

With the Firebase CLI installed (`npm i -g firebase-tools`):

```bash
firebase login
firebase use --add        # pick your project
firebase deploy           # publishes the site and the Firestore rules
```

Your game will be live at `https://<project-id>.web.app`, and that domain is authorized for login automatically.
