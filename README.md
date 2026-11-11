# Live Hand Log

A fast, phone-friendly recorder for live No-Limit Hold'em hands. It exports PokerStars-format hand histories that PokerTracker 4, Holdem Manager 3 and Hand2Note can import.

Everything runs in your browser. There is no account and no server, and your hands never leave your device unless you share them.

## Features

- **Set up once per session.** Enter blinds, currency, table size and stacks one time. Every hand after that starts with one question: your position.
- **Only legal actions.** Each player's turn shows only the moves they can make: Fold / Call / Raise when facing a bet, Check / Bet when not.
- **Real cash amounts.** Type what was actually bet. It's converted to big blinds as you type, and calls fill in automatically.
- **"Folds to" shortcut.** Tap a player and everyone before them folds (or checks). Most preflop hands take one tap.
- **Straddles.** Pick None, UTG, double, triple or button straddle from a dropdown at the start of any hand and set each amount. The preflop action order is shown on screen and the minimum raise adjusts. On a button straddle the SB acts first and the button acts last. The choice stays on for later hands until you set it back to None.
- **Stacks.** Your stack is editable at the start of every hand (it also carries over automatically). Tap any player's seat during a hand to enter their stack, for example a short stack about to shove, so all-ins and uncalled bets come out right.
- **Board and showdown.** You're asked for the flop, turn and river as each betting round closes. At the end you enter your cards and, optionally, your opponents' cards. The winner is worked out for you, side pots included.
- **Undo** any step. A half-entered hand survives closing the page.
- **Export** a session (or everything) as a `.txt` hand history file.
- **Share a hand for review.** Send a plain-text summary in big blinds or cash, plus a link that opens a step-by-step replay. The person you send it to can save the hand into their own log. The whole hand is encoded inside the link, so nothing is uploaded.
- **Works offline** after the first visit. Install it to your home screen like an app.
- **Backup and restore** all your data as a `.json` file.

## Use it

### On your phone (recommended)

Open the GitHub Pages address for this repository, for example `https://<your-username>.github.io/live-hand-log/`, then add it to your home screen:

- **iPhone (Safari):** Share → **Add to Home Screen**
- **Android (Chrome):** ⋮ menu → **Add to Home screen** (or **Install app**)

### On a computer

Download or clone this repository and open `index.html` in your browser. Share links and offline mode need the app to be served from a web address. Run a tiny local server for that:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Import into your tracker

1. In a session, tap **Export .txt**.
2. Import the file:
   - **PokerTracker 4:** File → Import Hands From Files
   - **Holdem Manager 3:** Import → Import Files
   - **Hand2Note:** Import → Import hand history files
3. Your player name in the file is the one you set when starting the session (default `Hero`). Opponents are named by position (`UTG`, `CO`, `BTN` and so on), so their stats aren't meaningful across hands, but yours are.

## Where your data lives

Hands are stored in your browser's local storage on the device you use. They are not synced between devices. Clearing your browser's site data deletes them, so use **Save backup** on the home screen regularly. **Restore backup** merges a backup file into what's already there.

## Host your own copy on GitHub Pages

1. Fork or upload this repository to your GitHub account.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
4. After a minute, the site is live at `https://<your-username>.github.io/<repo-name>/`.

## Not supported yet

- Antes and rake (rake is exported as 0)
- Straddles are exported as `posts straddle`. If your tracker rejects those hands, please open an issue.
- Games other than No-Limit Hold'em
- If you fold with several opponents still in, the pot is given to the last player who bet or raised. Your own result is still correct.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: interface, hand engine, hand evaluator, export and sharing |
| `sw.js` | Service worker that caches the app for offline use |
| `manifest.webmanifest`, `icon*.png`, `icon.svg` | Home-screen install details and icons |

## License

MIT. See [LICENSE](LICENSE).
