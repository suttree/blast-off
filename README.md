# Blast Off

A one-button pixel-art quick-draw duel — spaceship edition. Wait for
**READY… AIM… FIRE!**, then react before the enemy does. Fire too early and
you're defenseless. Freeze up and you're outgunned.

Play it: open `index.html` in a browser, or serve the folder with any
static file server (it's a single self-contained file — no build step, no
dependencies).

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

## How to play

- Watch the callout: **READY…** → **AIM…** → **FIRE!**
- The instant **FIRE!** appears, tap / click anywhere or hit **SPACE**.
- Fire before **FIRE!** appears and you're disqualified — the enemy gets a
  free shot.
- React too slowly and the enemy outguns you before you can pull the
  trigger. The enemy's reaction window shrinks every round, so it gets
  faster (and less forgiving) the longer you survive.
- Three lives. Your best round is saved locally.

## Features

- Vertical face-off: your ship at the bottom looking up, the enemy at the
  top looking down, connected by a laser bolt that actually travels between
  them on every shot (exactly one shot per round — a win or a loss, never
  both).
- Four enemy ship classes that escalate in difficulty and visual scale —
  Rookie Scout, Veteran Raider, Elite Cruiser, Boss Dreadnought — each with
  its own hand-placed pixel-art silhouette, color, and size. The hull shape
  in play cycles every round independent of tier, so the enemy rarely looks
  the same twice in a row.
- Ambient space drone and laser SFX, fully synthesized at runtime with the
  Web Audio API — no external audio files.
- All sprites (player ship, four enemy classes) are hand-authored pixel
  grids rendered as inline SVG — no external art files either.
- Responsive layout, playable on mobile (portrait) and desktop.
- [CrazyGames SDK](https://docs.crazygames.com/sdk/intro/) integration:
  loading and gameplay start/stop events, plus a `happytime()` call on a
  new personal best.

## Project structure

```
index.html          the entire game — markup, styles, sprites, and logic
press-kit/           marketing assets for portal submission (see below)
  covers/            CrazyGames-spec cover art (1920×1080, 800×1200, 800×800)
  screenshots/        gameplay screenshots
  video/             preview videos + gameplay clips
  description.md     store listing copy and the CrazyGames asset checklist
```

## Tech notes

- No build step, no framework, no dependencies — everything lives in
  `index.html`. Sprites are pixel grids (ASCII-art style 2D arrays) rendered
  to `<rect>` elements at runtime.
- Enemy ship "shape" and "tier" are decoupled: shape cycles every round
  from a small pool of hull silhouettes, tier (name, color, and how fast
  the enemy reacts) escalates every 3 rounds.
- Audio is entirely procedural (WebAudio oscillators + filtered noise for
  the ambient bed, pitch-swept oscillators for the blaster SFX) and only
  starts after the player's first interaction, per browser autoplay policy.
- The press kit's screenshots and videos are real captures, not mockups —
  scripted with Playwright driving actual Chrome against the live game.
