# Sparky Calc — offline electrical calculator (PWA)

> [!CAUTION]
> This app is ALPHA! It is not suitable for use in live systems at this time.

## Deploy

Serve this folder over HTTPS (service workers require it; `localhost` also works).
Any static host works: GitHub Pages, Netlify, Cloudflare Pages, S3, nginx.
Local test: `python3 -m http.server 8000` → http://localhost:8000

Install: Android/Chrome shows an install prompt. iOS: Safari → Share → Add to Home Screen.
After the first load, everything runs offline. Bump `CACHE` in `sw.js` when you change any file.
Use **Refresh** in the app to check for and load the latest version. If you are offline or the update
cannot be reached, the currently cached app remains available.

## How it works

Type a number, then a function key to **store** it. Press a function key with no entry to **solve** it.
`2nd` gives the function printed above a key. `Rcl` + key shows a stored value. Tap the display to see all stored values.

Examples

- `85 Wire size` → smallest conductor for 85 A (uses chips: phase, Cu/Al, 60/75/90°C)
- `230 Volts 5 HP 2nd HP` → motor FLC from Table 430.248/430.250; then `Breaker` → 250% next-standard size
- `120 Volts 20 Amps 100 Length 12 Size VD %` → voltage drop
- With Volts and Length stored, `Wire size` also upsizes to meet the VD limit (default 3%)
- `3 Size` (3 AWG), `4 2nd Conduit` (4 wires), then `Conduit` → smallest raceway per Chapter 9

## Sources (NEC 2023)

310.16, 310.15(B) ambient (formula method), 310.15(C)(1) adjustment, 240.4(D), 240.6(A), 250.122,
430.22, 430.32(A)(1), 430.52(C)(1), 430.248, 430.250, Chapter 9 Tables 1, 4, 5, 8.
Table values were transcribed by hand; verify against your code book and local amendments.
