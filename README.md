# Combo Finder

Find, compare, share and try on TF2 Unusuals, all in one place.

Combo Finder is a small app for Team Fortress 2 traders. It shows you everything that's for sale on [backpack.tf](https://backpack.tf) for the class, quality and Unusual effects you pick - hats, misc and taunts side by side, with pictures and prices, cheapest first. When you've found something you like, send the whole list to a friend in one click, or open it in [loadout.tf](https://loadout.tf) to see exactly how it looks in-game.

It runs entirely on your own PC. Your backpack.tf token never leaves it, except to talk to backpack.tf.

---

## Why Combo Finder?

### Can't make up your mind?

Picking an Unusual is hard. There are hundreds of hats, hundreds of effects, and thousands of listings spread across backpack.tf, and clicking through them one item at a time takes forever. You end up with twenty tabs open and still no idea what you actually want.

Combo Finder does the digging for you. Pick a class - say Soldier - choose the effects you're interested in, and press Scan. You get one page with every matching hat for sale, each with its picture, effect, price and seller, sorted so the best deals are at the top. Change the sort, set a price limit, narrow the effects, and compare everything without opening a single extra tab.

Looking for a full look rather than a single hat? Turn on combo view to see sellers who are listing a hat *and* a misc at the same time, cheapest pair first - perfect for buying a matching set from one trader.

### A faster way to share hats

Asking friends "which one should I get?" usually means pasting link after link into Discord. With Combo Finder you copy the whole list in one click: a short, tidy message with every item, its price and a link straight to that exact listing on backpack.tf. Links are formatted so Discord doesn't flood the chat with previews.

> Unusual hats for sale (6)
> • Green Energy Team Captain - 1,100 keys - &lt;backpack.tf/item/…&gt;
> • Green Energy Team Captain - 1,250 keys - &lt;backpack.tf/item/…&gt;
> • Sunbeams Team Captain - 4,000 keys - &lt;backpack.tf/item/…&gt;

### See it in-game before you trade

A screenshot never quite shows how an effect really looks on a hat. Every listing in Combo Finder has a Try in loadout button that opens loadout.tf with that exact item and effect already equipped on the right class - spin the character around, compare it with what you're wearing, and decide before you spend a single key. In combo view, one button puts the hat and the misc on together.

---

## Features

- Browse by class: Any class, All-class, Multi-class (items a few classes share, like the Team Captain) or any of the nine classes.
- Hats, misc and taunts, each with its own quality: Unusual, Unique, Strange, Genuine, Vintage, Haunted or Collector's.
- Effects from a list: pick Unusual hat effects and Unusual taunt effects from a searchable list, no typing names and hoping they match.
- Only real Unusuals: when a side is set to Unusual, items that can't come as Unusual (promos, achievement rewards, event prizes) are hidden, so scans stay short.
- Proper hat / misc split: "hats" are items that use the hat slot; everything you can wear alongside a hat counts as misc, the way traders think about it.
- Combo view: sellers listing a hat and a misc together, cheapest pair first.
- Item pictures: every hat, misc and taunt shows its in-game backpack picture.
- Try in loadout: opens loadout.tf with the item and its effect equipped.
- One-click copy: copy hats, misc, taunts or everything as a short, Discord-friendly list with a link to each exact item.
- Price filters: a maximum price in keys, with your own key-to-ref rate for accurate totals.
- Fast repeat scans: results are reused for a while, items with nobody selling are skipped, the most likely items are checked first, and backpack.tf rate limits are waited out automatically.
- Clean item list: no tournament medals, badges, Halloween-only or untradable items cluttering the lists.

---

## Privacy

If you're going to give an app your backpack.tf token, you should know exactly what it does with it. Combo Finder is built so your token and your data stay yours:

- Local only. Combo Finder is a small server that runs on your own PC and only listens on `127.0.0.1`. Nobody else on your network or the internet can reach it.
- Other websites can't use it. Any request that doesn't come from Combo Finder's own page is refused - so a website open in another browser tab can't make it use your token or read your results.
- Your token only goes to backpack.tf. The token (and optional API key) are only ever sent to `https://backpack.tf` over HTTPS, and redirects to anywhere else are refused. They are never printed, logged, saved in the cache, shown in the page, or sent anywhere else.
- Encrypted on disk. On Windows, the token and API key in `config.json` are encrypted with your Windows account the first time Combo Finder starts. If someone copies your `config.json`, it's useless on another PC or account.
- No tracking. No analytics, no ads, no accounts, no third-party scripts. The page loads nothing from the internet; links to backpack.tf, Steam and loadout.tf only open when you click them.
- Nothing private in this repository. Your `config.json`, cache and the files built from your TF2 install are excluded by `.gitignore`.

The whole app is a few readable files - you're welcome to check `combo_finder.py` yourself.

---

## Getting started

### What you need

- Windows (the launcher is a `.bat` file; the app itself is plain Python and also runs elsewhere with `python combo_finder.py`)
- [Python 3](https://www.python.org/downloads/) - when installing, tick "Add python.exe to PATH"
- Team Fortress 2 installed through Steam
- A free backpack.tf account (sign in with Steam)

### Install

1. Download the latest ComboFinder.zip from the [Releases](../../releases) page (or click Code → Download ZIP).
2. Unzip it anywhere, for example your Desktop.
3. Double-click `Start Combo Finder.bat`.

The first start takes about half a minute: Combo Finder builds its list of every tradable hat, misc and taunt - plus their pictures - straight from your own TF2 files. Nothing is downloaded for this, and it only happens once.

### Add your backpack.tf access token

backpack.tf only shows other people's listings to signed-in users, so Combo Finder needs your own access token. It's free:

1. Sign in to [backpack.tf](https://backpack.tf) with Steam.
2. Open your Third Party Connections / API access page (`https://backpack.tf/connections`).
3. Copy your Access Token (not the API key).
4. Open `config.json` in the Combo Finder folder (it's created on the first start) and paste the token between the quotes:
   ```json
   "token": "paste-your-token-here",
   ```
5. Save the file and start Combo Finder again. On Windows the token is encrypted straight away.

Optional: paste a backpack.tf API key (from `https://backpack.tf/developer`) into `"api_key"` to let Combo Finder use backpack.tf's own list of which items exist as Unusual.

Never share your token or your `config.json` with anyone.

---

## How to use it

1. Start Combo Finder - your browser opens `http://127.0.0.1:8765`. Keep the console window open while you use it; close it to stop.
2. Pick a class and the quality for hats and misc.
3. For Unusuals, pick one or more effects. backpack.tf files Unusual listings per effect, so Combo Finder checks each item with each effect you pick.
4. Leave the hat or misc list empty to scan everything for that class, or add specific items to scan just those.
5. Want taunts too? Tick Scan taunts (or pick taunts) and choose taunt effects.
6. Press Scan. Results appear as they come in, the most likely items first.
7. Sort, filter by price, switch on combo view, copy the list, or hit Try in loadout on anything that catches your eye.

### Tips

- The line under the Scan button tells you how many items are answered instantly from earlier scans and how many still need checking.
- A first scan of a whole class takes a few minutes, because backpack.tf limits how fast one account can ask for listings. Repeat scans within a couple of hours are much faster.
- Tick Ignore cache when you want completely fresh results.

---

## Settings

All settings live in `config.json`:

| Setting | What it does | Default |
|---|---|---|
| `token` | your backpack.tf access token (encrypted automatically on Windows) | – |
| `api_key` | optional backpack.tf API key | – |
| `port` | the local port the app uses | 8765 |
| `seconds_between_requests` | spacing between requests to backpack.tf | 1.1 |
| `cache_minutes` | how long scan results are reused | 120 |
| `empty_hours` | how long items with nobody selling are skipped | 6 |

---

## FAQ

Is this safe to use with my token?  
Yes - see [Privacy](#privacy). The token is only sent to backpack.tf, stored encrypted, and the app can't be reached from other computers or other websites.

Why do I have to pick effects for Unusuals?  
backpack.tf lists each Unusual under its effect (for example "Sunbeams Team Captain"), so there's no single "all Unusual Team Captains" list to ask for. Picking the effects you care about also keeps scans short.

Why does the first scan take a while?  
backpack.tf only allows a certain number of requests per minute per account. Combo Finder stays under that limit so your account never gets blocked, remembers what it found, and skips items with nobody selling on the next scan.

New items came out in a TF2 update - how do I get them?  
Run `python tools/build_data.py` in the Combo Finder folder (or delete `cosmetics.json` and start the app). It rebuilds the item list and pictures from your updated game files.

Does it work on servers / the game itself?  
No - Combo Finder doesn't touch TF2 at all. It only reads your installed game files once to build its item list and pictures, and it never modifies anything.

Something isn't working.
Open an issue on this repository and describe what you did and what you saw. Please never include your token or `config.json`.

---

## How it works

- `combo_finder.py` - the local server (Python standard library only). It asks backpack.tf's classifieds listings API for each item you scan, using your token.
- `index.html` - the page you use in your browser.
- `tools/build_data.py` - builds `cosmetics.json`, `effects.json` and the `icons/` pictures from your TF2 install (item schema, English item names and backpack images).
- `tools/vpk_reader.py` - reads files out of TF2's game archives.
- Pillow (`pip install pillow`) is only used to make the item pictures; the launcher installs it automatically if it's missing.

---

## Disclaimer

Combo Finder is a fan-made tool and is not affiliated with or endorsed by Valve, backpack.tf or loadout.tf. Team Fortress 2, its item names and images belong to Valve Corporation. No game files are included in this repository - everything is built from your own installed copy of TF2.
