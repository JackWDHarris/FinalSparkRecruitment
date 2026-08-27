# Final Spark — Recruitment Deck

Open `index.html` in a browser. Fullscreen with **F**.

| Key | Action |
| --- | --- |
| `→` `↓` `Space` / click right half | Next step or slide |
| `←` `↑` / click left half | Back |
| `Home` / `End` | First / last slide |
| `F` | Fullscreen |

Click-through reveals: **2** (2), **6** (2, slide enters empty), **8** (1), **14** (1), **15** (3), **20** (4, slide enters empty).

23 slides. Slide 22 lists the roles, carried over from the pitch deck's recruiting grid with the headcounts, filled markers and duplicate seats stripped out.

---

## How assets work

Every image slot names a path **without an extension**. On load the deck probes
for that basename and uses the first file it finds:

```
mp4 → webm → mov → gif → png → jpg → webp
```

So `assets/fav-tunic.gif` and `assets/fav-tunic.mp4` both just work, and an
animated source stays animated. **A clip or GIF wins over a still of the same
name** — if you want the static version, delete or rename the moving one.

Anything unresolved renders as a dashed gold box naming the asset and its path,
so the deck stays presentable and fails visibly rather than silently.

---

## Assets still needed

Only one slot is empty:

### Slide 4 — gods
Three portrait plates (3:4) under "MYTHOLOGY and Gods and MONSTERS".

- `assets/god-1`
- `assets/god-2`
- `assets/god-3`

### Slide 18 — art direction
The eight tiles are still the ones carried over from the pitch deck. Replace them
in place, matching the shape so the grid stays balanced: `art-01` portrait,
`art-02` landscape, `art-03` portrait, `art-04` landscape, `art-05` landscape,
`art-06` portrait, `art-07` portrait, `art-08` landscape.

## Already in place

From `~/Documents/fall recruitment images/`. Anything animated was converted to
mp4 — a 19MB gif decodes frame-by-frame on the CPU and stalls the deck, an mp4 of
the same clip is hardware-decoded and a twentieth of the size.

| Asset | Source | Slide |
| --- | --- | --- |
| `guildrun.mp4` + `.jpg` | `guildrun.gif` (5.4MB → 635KB) | 8 |
| `prototype-3d.mp4` | `new demo.mov`, 3024px → 1600px (23MB → 1.3MB) | 11 |
| `blue-prince.mp4`, `fav-blueprince.mp4` + `.jpg` | `blue prince gif.gif` (6.5MB → 480KB) | 14, 15, 17 |
| `elden-ring.mp4` | `elden ring.gif` (19MB → 933KB) | 17 |
| `fav-tunic.mp4` | `tunic.gif` (2.1MB → 114KB) | 14, 15 |
| `fav-silksong.webp` | copied as-is | 14 |
| `fav-animalwell.jpeg` | copied as-is | 14, 15 |
| `fav-hierophant.png` | copied as-is | 14, 15 |
| `story-1.png` | `thread of fate image.png` | 20, beat 1 |
| `story-2.webp` | `cracked cosmos.webp` | 20, beat 2 |
| `story-3.jpg` | `black water.jpg` | 20, beat 3 |
| `story-4a.jpg`, `story-4b.jpeg` | `primordial 1`, `primordial 2` | 20, beat 4 |

Guildrun's hour count (**142.5**) was read off `guildrun hours.png` and set on
`data-hours` in slide 8; the deck animates a count-up to it.

Extracted from `FinalSpark_PitchDeckWebsite/index.html`:

- `hours-sts`, `hours-sts2`, `hours-hades`, `hours-tft` — slide 2 playtime shots (550.5 + 93.3 + 117.7 + 4,458 = 5,219 hrs)
- `demo-1`, `demo-2` — slide 5. Frames from the old 2D demo capture. `olddemo-1..4.jpg` are the other candidates if you want to swap.
- `fav-tft`, `fav-hades`, `fav-sts` — as **mp4 clips** (slides 14, 15) with `.jpg` stills alongside as fallbacks
- `tft-clip`, `hades-clip` — slide 16 comparison clips
- `art-01..08` — slide 18, pending replacement

Fonts (Cinzel, Inter, Raleway) are embedded, so the deck works offline.

---

## Scaling

The deck is authored on a fixed **1600 × 900** canvas and scaled as a single unit
to fit the window, so every slide holds the proportions it was laid out with on
any display, projector, or aspect ratio. Nothing reflows; off-16:9 screens get
letterboxed against the deck's own background. If you edit sizes, work in plain
pixels against that canvas — viewport units (`vw`/`vh`) would measure the real
window rather than the canvas and break the scaling.

## Hosting

Copy this folder into `FinalSpark_PitchDeckWebsite/` as a subdirectory and it
publishes at `/<foldername>/` alongside the pitch deck, using the same `push.sh`.
