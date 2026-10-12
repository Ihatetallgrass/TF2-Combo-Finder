Can’t make up your mind? Picking an Unusual is hard when there are hundreds of hats, effects and sellers to compare. Combo Finder puts everything that’s for sale on backpack.tf in one place. Pick a class, a quality and the effects you like, and see every matching hat, misc and taunt side by side, with pictures and prices, cheapest first.

Sharing without the hassle. Instead of sending friends hat links one at a time, copy the whole list in one click. You get a short, Discord-friendly message with every item, its price and a link to that exact listing.

See it before you buy it. Not sure how an effect looks on a hat? Every listing has a “Try in loadout” button that opens loadout.tf with that exact hat and effect equipped on the right class, so you can see it in-game before you trade.

Everything runs on your own PC, and your backpack.tf token never leaves it except to talk to backpack.tf.
Combo Finder
See what's for sale on backpack.tf for Team Fortress 2, by class, quality and Unusual effect: hats, misc and taunts side by side, cheapest first, with item pictures. Spot hat + misc combos and try any listing on in loadout.tf with one click.
Runs entirely on your own PC. Nothing to sign up for except your own backpack.tf token.
Features
Browse by class: any class, all-class, multi-class or one of the nine classes. Leave the lists empty to scan every hat / misc for that class, or pick specific items.
Hats, misc and taunts, each with its own quality (Unusual, Unique, Strange, ...).
Unusual effects from a list: hat effects and taunt effects, no typing.
Only items that can really be Unusual are offered when a side is set to Unusual (promos, achievement rewards and other non-Unusual items are hidden).
Combo view: sellers listing a hat and a misc at the same time, cheapest pair first.
Item pictures, built from your own TF2 files.
Try in loadout: opens loadout.tf with the item and its effect equipped.
Copy the listed hats / misc / taunts as a short, Discord-friendly text list with a link to each exact item.
Fast repeat scans: results are cached, items with no sellers are skipped for a while, and rate limits are waited out automatically.
Privacy
Your tokens and your data stay with you:
Local only. Combo Finder is a small server that listens on `127.0.0.1` (your own PC). Nobody else on your network or the internet can reach it.
Other websites can't use it. Requests that don't come from Combo Finder's own page are refused, so a site open in another tab can't make it use your token or read your results.
Your token only goes to backpack.tf. The token and API key are sent only to `https://backpack.tf` over HTTPS (redirects to anywhere else are refused). They are never printed, logged, cached, shown in the page, or sent anywhere else.
Encrypted on disk. On Windows, the token and API key in `config.json` are encrypted with your Windows account the first time Combo Finder starts. A copied `config.json` is useless on another PC or account.
No tracking. No analytics, no ads, no third-party scripts. The page loads nothing from the internet; links to backpack.tf, Steam and loadout.tf only open when you click them.
Nothing private in this repo. `config.json`, the cache and files built from TF2 are in `.gitignore`.
Install
Install Python 3 (on Windows, tick "Add python.exe to PATH").
Download this repository (green Code button → Download ZIP) and unzip it anywhere.
Have Team Fortress 2 installed through Steam. Combo Finder builds its item list and pictures from your TF2 files on the first start (takes about half a minute).
Get your backpack.tf access token
backpack.tf only shows other people's listings to signed-in users, so Combo Finder needs your own access token (free):
Sign in to backpack.tf with Steam and open your Third Party Connections / API access page (`https://backpack.tf/connections`).
Copy your Access Token (not the API key).
Start Combo Finder once so it creates `config.json`, then open `config.json` and paste the token:
```json
   "token": "paste-your-token-here",
   ```
Save and start Combo Finder again. It encrypts the token right away (Windows).
Optional: a backpack.tf API key (`https://backpack.tf/developer`) in `"api\_key"` makes the "can be Unusual" lists use backpack.tf's own price list.
Never share your token or `config.json` with anyone.
Use
Double-click `Start Combo Finder.bat` (or run `python combo\_finder.py`). Your browser opens `http://127.0.0.1:8765`.
Pick a class and qualities. For Unusual, pick one or more effects: backpack.tf lists Unusual items per effect.
Press Scan. Keep the console window open while you use it; close it to stop.
Settings (`config.json`)
Setting	What it does	Default
`token`	your backpack.tf access token (encrypted automatically on Windows)	–
`api\_key`	optional backpack.tf API key	–
`port`	local port	8765
`seconds\_between\_requests`	spacing between requests to backpack.tf	1.1
`cache\_minutes`	how long results are reused	120
`empty\_hours`	how long items with no sellers are skipped	6
How it works
`combo\_finder.py`: the local server (Python standard library only). Talks to backpack.tf's classifieds snapshot API with your token.
`index.html`: the page.
`tools/build\_data.py`: builds `cosmetics.json`, `effects.json` and `icons/` from your TF2 install (item schema, English names, backpack pictures). Run it again after a TF2 update to pick up new items: `python tools/build\_data.py`.
Pillow (`pip install pillow`) is only needed to make the item pictures; the launcher installs it if it's missing.
Notes
backpack.tf limits how fast one token can make requests. Large first scans take a few minutes; repeat scans are much faster.
The listings snapshot endpoint is used by trading bots but isn't in backpack.tf's public docs, so it could change.
Not affiliated with Valve, backpack.tf or loadout.tf. Team Fortress 2 and its item names and images belong to Valve; nothing from the game is included in this repository.
