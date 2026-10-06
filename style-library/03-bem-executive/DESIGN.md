# BEM Executive: Black Executive Men visual identity

> Source of truth: the brand references in `references/`. They are the website banner,
> the BEM monogram, the Sponsorship Summit poster, the executive office scene, and the
> *Executive Fireside Chats* series overview. Every BEM composition traces its palette,
> type, and motion back to this file.

## Style prompt

Black Executive Men is the network for C-suite executives and vice presidents, built to
advance Black male enterprise leadership. The brand feels like a boardroom at dusk:
deep navy, warm gold hairlines, white classical serif, and generous negative space.
It is prestigious, composed, and invitation-only. It is never loud. Motion feels
**executive and polished**. Elements arrive with quiet confidence, gold lines draw
themselves like a pen stroke on a letterhead, and nothing bounces, flashes, or glows
neon. When a speaker is on screen, graphics serve them. They are framed, restrained,
and out of the way of the face.

## Colors

| Token | Hex | Role |
|---|---|---|
| `--navy` | `#011B42` | Primary canvas (banner and monogram navy) |
| `--navy-deep` | `#000F29` | Vignette edges, depth |
| `--navy-royal` | `#0B3470` | Lifted panels, the textured blue of the PDF |
| `--gold` | `#E0B264` | Primary accent: wordmark, rules, names, highlighted words |
| `--gold-bright` | `#E3A91A` | Monogram frame only |
| `--gold-muted` | `#8E774D` | Hairline arcs, globe lines, faint ornament |
| `--white` | `#FFFFFF` | Headlines and monogram letters on navy |
| `--ivory` | `#F4EFE4` | Body copy, roles, captions |
| `--onyx` | `#141210` | Optional black "executive office" canvas, used for variety |

Navy, gold, and white make up the brand. Gold is an accent. Keep it to roughly 10% of
any frame. It belongs on lines, one key word, and the wordmark, never on large fills.

## Typography

- **EB Garamond** (500 to 700) is the wordmark voice: the *BEM* monogram,
  `BLACK EXECUTIVE MEN` in caps with `0.10em` tracking, speaker names, and headlines.
- **Cinzel** (400 to 600) supplies Trajan-style inscriptional caps for event titles
  (*Executive Fireside Chats*, *Sponsorship Summit*), small kickers, dates, and URLs.
  Kickers use `0.28em` tracking (`TO ADVANCE BLACK MALE ENTERPRISE LEADERSHIP`).
- **Lato** (300 to 700) is the humanist sans. It stands in for the Gill Sans used in
  the PDF and handles roles, captions, and body copy.

House pattern: Garamond or Cinzel statement, a gold rule, then a supporting line in Lato
or in spaced Cinzel caps. Names are gold. Roles are ivory.

## Logo and lockups

- **Monogram:** white serif `BEM` centered in a square gold frame (`--gold-bright`,
  1.5 to 2% of the box width) on navy. Built in HTML and CSS in every card, so it stays
  vector-crisp at any size. The reference is `references/bem-monogram.webp`.
- **Wordmark:** `BLACK EXECUTIVE MEN` in gold EB Garamond caps over a full-width gold rule.
- **Sub-brand line:** `ELITE MEMBERSHIP NETWORK` in small gold caps under a white
  wordmark (the Fireside Chat lockup).
- **Tagline:** "The Network for C-Suite Executives and Vice Presidents".
- **Mission kicker:** "To Advance Black Male Enterprise Leadership".
- **URL:** `blackexecutivemen.com`.
- Clearspace is half the monogram's height. Never stretch, recolor, or add a glow.

## Ornament

- **Gold arcs:** two thin concentric arcs sweeping in from a corner, taken from the banner.
- **Globe lines:** a faint latitude and longitude wireframe in `--gold-muted` at
  about 15% opacity, taken from the banner.
- **Frames:** square gold hairline boxes around key text (the summit poster's callout box).
- **Rules:** short centered gold rules under headlines and long rules under the wordmark.
- **Diagonal gold lines:** used only at the corners of full-frame event or promo cards.

## Motion

Executive and polished. Confident, unhurried, and precise.

- **Entrance eases:** `power3.out` (default), `expo.out` (big type and tracking-in),
  `power2.inOut` (anything that *draws*: rules, frames, arcs), `sine.inOut` (ambient
  push-ins). **Never** `back`, `elastic`, `bounce`, or `steps`.
- **Durations:** text 0.7 to 1.0s, draws 1.0 to 1.6s, holds of at least 2s on anything
  the viewer must read. Stagger supporting lines 0.25 to 0.4s apart.
- **Signature moves:**
  1. **Gold line draw:** rules and frames draw with `scaleX` or a stroke-dash offset.
  2. **Tracking-in:** wordmark letter-spacing eases from `0.45em` to `0.10em` with opacity.
  3. **Rise and settle:** text rises 12 to 20px with opacity. No blur slams.
  4. **Slow push-in:** background or ornament scales from 1.00 to 1.04 over the shot.
- **Exits:** lower thirds and captions exit with a gentle fade or a mask in 0.5 to 0.6s
  (`power2.in`). Scene changes use soft crossfades or a navy dip, never whip pans.
- Deterministic only. No `Math.random()` and no `Date.now()`.

## Format rules

Every card adapts through its root `data-width` and `data-height`. A small init script
sets `--u` (1px at 1080 on the short side) and a format class.

| Format | Size | Use | Notes |
|---|---|---|---|
| Landscape 16:9 | 1920×1080 | YouTube, webinars, Fireside Chats, event recaps | Lower thirds bottom-left, captions bottom center |
| Portrait 9:16 | 1080×1920 | Reels, Shorts, TikTok, Stories | Keep text inside y=200 to 1600 and away from the right edge (platform UI) |
| Square 1:1 | 1080×1080 | LinkedIn and Instagram feed | Center-weighted, larger type |

## Card kinds in this style

- `custom` **intro bumper:** a monogram draw, then wordmark tracking-in, gold rule, and tagline (5s).
- `custom` **outro end card:** monogram and wordmark, CTA, URL (8s).
- `tier2` **lower third:** a navy panel with a gold edge, gold name, ivory role, and spaced organization caps (6s).
- `custom` **captions:** an executive caption style where Lato words rise into place and key words turn gold.

## What NOT to do

1. No neon, glows, lens flares, chrome, or glitch effects. This is a boardroom, not a nightclub.
2. No playful motion such as bounce, elastic, overshoot, wiggle, or emoji.
3. No colors outside the palette. No bright blues, reds, greens, or purples. Data needs
   use navy tints plus gold.
4. No rounded pills or bubbly cards. Corners are square, like the monogram box.
5. No full-screen linear gradients (they band in H.264). Use solid navy, localized radial pools, and grain.
6. Avoid the `transparent` keyword in gradients. Use `rgba(1,27,66,0)`.
7. No covering faces. Overlays stay in the lower third or the safe side of frame.
8. No all-gold paragraphs. Gold marks one name, one number, or one key word per line.
9. Never stretch, recolor, or add effects to the monogram.
