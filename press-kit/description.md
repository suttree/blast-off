# Blast Off — CrazyGames Submission Kit

Specs below are pulled directly from the CrazyGames developer docs
(docs.crazygames.com/requirements/game-covers/, /requirements/technical/,
/requirements/quality/) as of this kit's creation. All required assets are
generated to those exact dimensions.

## Store listing copy

**Title:** Blast Off

**Tagline (short, ~60 chars):**
A pixel-art quick-draw duel against the fleet. React first or die.

**Short description (~150–200 chars):**
Wait for READY… AIM… FIRE! then blast your opponent before they blast you.
Fire too early and you're defenseless — freeze up and you're outgunned.
Every round the enemy gets faster.

**Long description:**

**Blast Off** is a one-button pixel-art quick-draw duel, reimagined as a
spaceship showdown. You face off against a lone enemy ship down a starlit
corridor — you at the bottom looking up, they at the top looking down.
A referee call runs through three beats: **READY… AIM… FIRE!** The instant
FIRE! appears, whoever fires first wins the round. Everyone else gets shot.

It sounds simple. It is not forgiving:

- **Fire too early** (before FIRE! appears) and you're disqualified —
  worse, you're left defenseless, and the enemy gets a free shot.
- **Freeze up or react too slowly** and the enemy outguns you before
  you can pull the trigger.
- **React first** and your laser streaks across the screen for a clean hit.

You've got three lives. The enemy fleet gets faster and more varied every
round: small saucer scouts give way to wide-winged raiders, sleek stealth
cruisers, and finally hulking dreadnoughts — each with its own silhouette,
size, and color. How many rounds can you survive?

Built entirely from hand-placed pixel-art sprites and procedurally
generated sound (ambient space drone, snappy laser blasts) — no external
art or audio assets. Runs great on mobile and desktop; tap, click, or hit
SPACE to fire.

**Controls:** Tap / click anywhere, or press SPACE, the instant FIRE! appears.

**Genre / tags:** Arcade, Reflex, Reaction, Skill, Space, Sci-Fi, One-Button,
Pixel Art, Shooter, Endless, High Score

**Suggested age rating:** PEGI 3 / all ages — stylized pixel-art lasers only,
no blood, no text to localize.

## Asset checklist vs. CrazyGames requirements

| Requirement (per docs.crazygames.com) | File | Status |
|---|---|---|
| Cover, landscape 1920×1080 (16:9) | `covers/cover-landscape-1920x1080.png` | ✅ exact size |
| Cover, portrait 800×1200 (2:3) | `covers/cover-portrait-800x1200.png` | ✅ exact size |
| Cover, square 800×800 (1:1) | `covers/cover-square-800.png` | ✅ exact size |
| Preview video, landscape 1080p (16:9), ≤20s, no audio | `video/preview-landscape-1920x1080.mp4` | ✅ 1920×1080, 19.7s, no audio track |
| Preview video, portrait 1080p (2:3), ≤20s, no audio | `video/preview-portrait-1080x1620.mp4` | ✅ 1080×1620, 19.7s, no audio track |
| Game description + controls text | this file | ✅ |

Covers follow CrazyGames' design guidelines: game title rendered directly
on the cover, no borders/store logos/extra icons/text beyond the title,
consistent visual identity across all three sizes, no raw screenshots (used
the hero ship + logo instead). Both preview videos open on their matching
static cover frame (per their "use your static cover as the opening frame"
rule), contain no audio track, no black bars, and no visible cursor.

**One spec I couldn't fully pin down:** CrazyGames' docs describe covers
in general layout terms (title + hero art, no clutter) but don't give a
minimum/maximum file size in KB, so I didn't constrain for that — all three
PNGs are a few hundred KB, which should be well within any reasonable limit.

## Bonus / reference assets (not part of the CrazyGames spec, extra material)

- `screenshots/01-title.png` → `09-title-wide.png` — actual gameplay
  screenshots (title screen, READY/AIM/FIRE sequence, a laser mid-flight,
  a landed hit, mid-round streak, game over) — useful for a press page,
  social posts, or other portals that do want raw screenshots
- `video/gameplay-demo.mp4` — ~44s uncut gameplay session (multiple rounds,
  a loss, a retry) — longer than CrazyGames' 20s cap, good for a YouTube/
  press-page embed instead
- `video/gameplay-highlight.gif` — ~6.5s looping clip, handy for anywhere
  a static preview video is easier than mp4 (README, forum post, etc.)

## How everything was captured

All assets are real captures, not mockups: Playwright drove an actual
headless Chrome instance against the live game (served locally), scripting
correctly-timed input to win rounds, progress through enemy tiers, and
reach the game-over screen — then screenshotted and video-recorded the
actual DOM/canvas output. Videos were assembled with ffmpeg (cover-frame
prepend, trim to spec, strip audio, encode to h264 mp4).
