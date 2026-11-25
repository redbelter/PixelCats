# PixelCats — pixel ghost-cat overlays for OBS

Tiny transparent-background HTML widgets: a pixel ghost cat that hovers over your scene and drifts around on its own. Drop any file into an OBS **Browser Source** and it just works.

## Files

| File | What it is |
|---|---|
| `ghostcat-finalists-live.html` | ⭐ Top-5 finalists with full animation repertoires (arc wander, hop chains with squash-and-stretch, upside-down hovering, pendulum swings, mid-dash spins). Best starting point. |
| `ghostcat-finalists.html` | The same 5 finalists with simpler per-cat motion (tail flicks, ring float, fringe sway). |
| `ghostcat-variations.html` | 10 variations — rounded silhouettes, wisp-fringe feet. |
| `ghostcat-variations-b.html` | 20 more variations — headgear, body-shape and tail-treatment axes. |
| `ghostcat-overlay.html` | First prototype (16×11 ghost cat, steps-style bob + blink). |
| `ghostcat-overlay-2.html` | Second prototype (round blob, tail flick, hover bob). |

## Using in OBS

1. Add a **Browser Source**.
2. URL: `file:///C:/Users/<you>/ghostcat/ghostcat-finalists-live.html` (adjust to where you keep the files).
3. Tick **Transparent Background**, set size to your canvas (e.g. 1920×1080).

The cat repositions itself on resize and respects `prefers-reduced-motion` (parked still, no drift).

## Behaviour design notes

- **Edge-biased spot picking** — corners and side margins most likely, lower-center avoided so captions/chat stay unobstructed.
- **Long idle gaps** — drifts take 4–9s with 2.5–11s rests between them: rare enough to feel alive, not twitchy.
- **Accent layers** — each sprite defines its own accent colour channel (tail tip, halo ring, fringe, glasses) that moves out of phase with the body, which is what makes the loops read as "alive" rather than a bouncing box.
- Sprites are plain row-string arrays + a palette map at the top of each file; edit them directly to reskin without touching logic.
