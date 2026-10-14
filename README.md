# Chronos — a countdown studio

Build a live countdown for anything — a product launch, an exam, a wedding, a
festival morning — and share it with a single link. Any date, any timezone. It
counts down, or up.

One HTML file. No framework, no build step, no server, no tracking.

## Under the hood

- **Pure-JS QR encoder** — byte mode, versions 1–15, Reed–Solomon over GF(256), all eight masks scored by the spec's penalty rules. No library.
- **WebGL 2 fragment shader** background, tinted live to your accent colour.
- **Web Worker + OffscreenCanvas** — confetti physics and the clock tick run off the main thread.
- **CompressionStream** — every share link is deflate-raw compressed, then base64url packed into the URL itself.
- **Astronomical sun times** — the countdown computes the real sunrise and sunset at the event's location.
- **BroadcastChannel** — open tabs stay in sync.
- **Web Audio** sonification, speech synthesis, haptics, notifications, wake lock.
- **PWA** — service worker, offline shell, installable, own icon.
- **`<chronos-countdown>`** — a real custom element backed by a shadow root.
- Plus: time-warp scrubber, PNG poster export, natural-language dates ("next friday 6pm"), native `<dialog>`, CSS `@property`, container queries, scroll-driven CSS, View Transitions, Speculation Rules.

Open the **Lab** page in the app to watch all ~42 APIs probed live on your own device.

## Deploy your own

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy

## Files

- `index.html` — the whole app (markup, styles, engine)
- `sw.js` — service worker: offline shell, stale-while-revalidate
- `manifest.webmanifest`, `icon.svg` — PWA install
- `_redirects` — SPA fallback
- `netlify.toml` — publish configuration

## Use the component

```html
<chronos-countdown
  title="Product launch"
  date="2027-01-15"
  time="10:00"
  accent="#FF7A45"></chronos-countdown>
```

## Public API

`window.Chronos` exposes the engine: `qr()`, `drawQR()`, `makeLink()`,
`unpack()`, `parseWhen()`, `sunTimes()`, `skyPhase()`, `capabilities()`.

## Run it locally

Open `index.html` in any browser. Serve over HTTP to get the service worker.
