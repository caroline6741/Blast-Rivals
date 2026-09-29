# Blast-Rivals

A 3D browser deathmatch shooter inspired by Roblox RIVALS. Built with Three.js in a single `index.html` — no build step, no dependencies to install.

## Play

Open `index.html` in a browser (or serve the folder with any static server). First to 10 eliminations wins the round.

- **Bombs 💣** are the currency: earn 30 per elimination, 45 per headshot, +150 for winning a round.
- **Armory**: 7 weapons from the free Blaster to the 2,000💣 Mega Launcher — higher damage costs more bombs.
- **Cosmetics**: per-gun skins and universal wraps (Gold Plate, Galaxy, Neon Circuit…).
- **Practice range**: every weapon has a Test Fire button; practice sessions do not spend currency or award XP.
- **Monthly Golden Case Day**: a deterministic random day occurs once per month. The lobby warns players the day before, shows all case contents and exact odds, and tracks 25 hard tasks. Every five completed tasks awards one case, up to five cases per account per event.
- **Catalog expansion**: 20 additional weapons, 20 additional skins, and 20 additional wraps are included.
- **Maps**: Arena, Docks, Splash, Construction.
- **Modes**: Solo vs Bots anywhere; live Multiplayer PvP uses the room provider when the published Claude artifact environment exposes it, syncing players in the same room.
- **Unlimited levels**: eliminations and round wins award XP; the level has no maximum and increases enemy difficulty over time.

Controls: WASD move, Space jump, Shift sprint, mouse aim/fire, R reload, 1–7 swap owned weapons, Esc pause.

Progress is saved in your browser via localStorage. When the room/cloud provider is unavailable, players can create a local username/password account; the password is stored as a SHA-256 hash and the profile remains on that device. The lobby shows level, XP, wins, and kills before deployment and provides Download JSON / Load JSON controls for manual backup and inspection.

The local account system is not a server-backed identity system: clearing browser storage removes local accounts, and local accounts do not sync between devices. Real cross-device multiplayer also requires the published room provider; a standalone `index.html` cannot host a multiplayer server by itself.
