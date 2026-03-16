<img width="700" height="768" alt="image" src="https://github.com/user-attachments/assets/6d562252-a7e6-44ab-bfeb-8a753469b117" />

[![pypresence](https://img.shields.io/badge/using-pypresence-00bb88.svg?style=for-the-badge&logo=discord&logoWidth=20)](https://github.com/qwertyquerty/pypresence) ![Platform: Windows & Linux](https://img.shields.io/badge/platform-Windows%20%26%20Linux-lightgrey?cacheSeconds=100000)


Discord Rich Presence for Valve's [Deadlock](https://store.steampowered.com/app/1422450/Deadlock/). Python application that shows your current in-game status on your Discord profile (hero, game mode, match type, party size, match timer, etc). Unfinished, expect bugs!

<img width="261" height="133" alt="image" src="https://github.com/user-attachments/assets/bb411785-66f4-43ce-8c9e-d979f6ca7e96" /> <img width="281" height="130" alt="image" src="https://github.com/user-attachments/assets/1d872c8d-a10f-4807-89ea-3f5327471e4b" /> <img width="266" height="139" alt="image" src="https://github.com/user-attachments/assets/52f40fe4-fd2a-4abf-b404-280c84a50d8e" /> <img width="263" height="134" alt="image" src="https://github.com/user-attachments/assets/112f40b9-d8d4-40f2-afa1-9f950a7ab438" />



 
## Installation and Setup

### Windows
Download **DeadlockRPC.exe** from the [latest release](https://github.com/Jelloge/DeadlockRPC/releases/latest) and run it! It will show up in your taskbar.

### Linux
```bash
git clone https://github.com/Jelloge/DeadlockRPC.git
cd DeadlockRPC
pip install -r requirements.txt
cd src
python main.py
```

### Notes
- The app launches Deadlock with `-condebug` automatically via Steam. `-condebug` is required for this app to work.
- If you manage your own Steam launch options, add `-condebug` to them.
<img width="480" height="119" alt="image" src="https://github.com/user-attachments/assets/21aaf748-3f15-41de-9479-d48b3b8eba6d" />

If you need help, message me on Discord: boba

<details>
<summary>Building from source</summary>

1. **Clone the repo**
2. **Install dependencies** - Python 3.10+ and `pip install -r requirements.txt`
3. **Configure** (optional) - edit `src/config.json` if needed
4. **Run** - `cd src && python main.py`
5. **Build executable** (optional):
```
pip install pyinstaller
python build.py
```
Output: `dist/DeadlockRPC.exe` (Windows) or `dist/DeadlockRPC` (Linux)

</details>

## How It Works

DeadlockRP monitors Deadlock's `console.log` file (written when the game runs with `-condebug`). It parses log events using regex patterns to detect game state changes that I painstakingly mapped out, and pushes updates to Discord.

The game's runtime and memory are never touched. So it's VAC-safe and won't affect performance.

## Changelog & Recent Fixes
- **Dynamic Hero Data**: Integrates with `deadlock-api.com` Hero names are now fetched automatically so new heroes work instantly without manual code updates
- **Hideout Text**: When in the hideout, your presence now displays hero-specific flavour text (e.g., *"Mixing Drinks in the Hideout"* for Infernus)
- **Fixed Queue Bug**: Addressed the issue where *"Looking for Match..."* wouldn't display when queuing in a party
- **Fixed Hero Detection**: Hero now correctly updates when entering a match, the hideout hero is cleared on match entry so the actual in-match hero is shown. Also fixed hero swapping in Sandbox
- **Fixed Match Detection**: Fixed standard and Street Brawl matches being misclassified as Bot Match due to placeholder bots loading before all players connect
- **Party Tracking**: Real party size tracking using GC party events, party size now reflects actual members instead of being capped at 2
- **Steam Path Detection**: Added Registry lookup so the app finds Deadlock regardless of where Steam is installed
- **Linux Support**: Full Linux support via Proton. game detection, Steam library paths, and system tray all (should) work on Linux

## TO-DO

- Dynamic portrait changes, for critical and gloating portraits.
- Upload new unreleased hero assets to the Discord app (names work via API, but images still require manual Dev Portal uploads)
- Localization

## Known Bugs

Please share any issues!

