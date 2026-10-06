---
name: bem-brand
description: Apply the Black Executive Men (BEM) brand to the motion graphics of any video. Covers navy and gold palette, EB Garamond / Cinzel / Lato type, executive and polished motion, the BEM monogram, intro and outro bumpers, lower thirds, and caption style. Use whenever a video, reel, Short, ad, promo, Fireside Chat, event recap, or any motion graphic is for Black Executive Men, BEM, blackexecutivemen.com, the Elite Membership Network, Executive Fireside Chats, or the Sponsorship Summit, or when asked to "brand this video", "add our intro/outro", "add lower thirds", or "use our brand".
---

# BEM brand for motion graphics

This skill makes any HyperFrames video look and move like Black Executive Men. It
works as a layer on top of the other skills. `edit-video`, `short-form-edit`,
`make-a-video`, `video-storytelling`, and `hyperframes-video-beats` still own the
edit. This skill owns how it looks and moves.

The spec lives in `style-library/03-bem-executive/`:

- `DESIGN.md` covers palette, type, logo, ornament, motion, formats, and what not to do. Read it first.
- `tokens.css` holds every color, font, and ease as CSS variables. Never hardcode them.
- `references/` holds the brand images the spec was derived from.
- `cards/` holds ready-made, format-adaptive components (below).

## Step 1: ask what the video is (always)

Before designing anything, ask the user in **one** message, and skip anything they have
already said:

1. **What kind of video is this?** Examples: Fireside Chat or interview, a member or
   speaker spotlight, an event promo (Sponsorship Summit), an event recap, a short-form
   social clip, a paid ad, a sponsor or partner video, or something else.
2. **Where will it run, and in what format?** YouTube or a webinar (16:9, 1920×1080);
   Reels, Shorts, TikTok, or Stories (9:16, 1080×1920); LinkedIn or Instagram feed
   (1:1, 1080×1080).
3. **Who is on screen?** For each speaker, get the name exactly as it should appear,
   the title, and the organization. These go into the lower thirds.
4. **Call to action for the end card.** Defaults: kicker "Elite Membership Network",
   CTA "Join the Network", sub-line "For C-Suite Executives and Vice Presidents",
   URL `blackexecutivemen.com`. Event videos usually swap in the date, city, and a
   registration line.
5. **Which brand elements to include.** The intro bumper, lower thirds, captions, and
   outro are all on by default. Short-form usually drops the intro or trims it to about
   2 seconds.

If the user can't say, recommend from the table below and confirm before building.

| Video type | Format | Brand package |
|---|---|---|
| Fireside Chat or interview (long-form) | 16:9 | Intro (5s), lower third per speaker at first appearance, captions optional, outro (8s) |
| Speaker or member spotlight | 16:9 or 1:1 | Intro, lower third, quote or stat cards in brand style, outro |
| Event promo (Sponsorship Summit) | 9:16 and 16:9 | Intro with event tagline, CTA outro with date, city, and registration |
| Event recap | 16:9 | Intro, lower thirds for featured voices, captions, outro |
| Short-form social clip | 9:16 | Captions (plate on), lower third once, a short outro with the URL; no full intro |
| Paid ad | 9:16 or 1:1 | Captions, a brand monogram in the first 2s, CTA outro |

## Step 2: set up the project

1. Create the project as usual (`npm run new-video -- <slug>`).
2. Copy `style-library/03-bem-executive/DESIGN.md` into the project root as `DESIGN.md`.
   Every other skill reads the project's DESIGN.md, so this is what makes the BEM brand
   apply everywhere, including cards from other styles that you restyle.
3. Copy `tokens.css` into the project (for example `compositions/bem/tokens.css`) and
   copy the cards you need next to it, keeping the relative `../../tokens.css` link
   valid or updating it.
4. Localize GSAP the way the project already does. The cards load GSAP from the CDN for
   standalone preview. When mounted, the parent provides GSAP (see
   `style-library/GUIDE.md`, "Standalone vs mounted form").

## Step 3: use the components

All four components read `data-width` and `data-height` from their root and adapt to
16:9, 9:16, or 1:1. Set those values to the project's format, along with `data-duration`.

| Component | File | Slots | Notes |
|---|---|---|---|
| Intro bumper | `cards/custom/bem-intro.html` | `tagline`, `kicker` | Opaque, 5s. Arcs and monogram draw, the wordmark tracks in, the gold rule draws, then the tagline appears. Defaults to the brand tagline and mission kicker. For a series or event, put the series name in `tagline` (for example "Executive Fireside Chats"). |
| Outro end card | `cards/custom/bem-outro.html` | `kicker`, `cta`, `sub`, `url` | Opaque, 8s, the final scene. A gold frame draws around the CTA, the lockup settles, then it fades to navy. |
| Lower third | `cards/tier2/t2-lt-executive.html` | `name`, `role`, `org` | Transparent overlay, 6s by default. Includes its own exit. Show it once per speaker, 1 to 3s after they start speaking. |
| Captions | `cards/custom/bem-captions.html` | transcript JSON, emphasis list | Put the word-level transcript of the **edited** footage in the script's `WORDS` array and names or brand terms in `EMPH`; numbers turn gold automatically. Set `data-plate="true"` for busy footage and for most 9:16 social video. |

Filling slots: replace the text of each `data-slot` element and respect the max
characters in `style.json`. Names must match exactly what the user gave.
Never invent titles or credentials.

## Step 4: style everything else on brand

For any graphic without a ready-made card (title cards, stat callouts, quote cards,
section dividers, data), start from a card in another style or from scratch, then
apply this checklist:

- Use a navy canvas for takeovers. Overlays use a navy panel at about 90% with a gold hairline border. Corners stay square.
- Headlines go in EB Garamond, or Cinzel for event-style titles, in white or gold. Supporting text goes in Lato in ivory. Kickers use spaced Cinzel caps in gold.
- Use one gold accent per line: a name, a number, or a key word. Gold rules sit under headlines.
- Ornament comes only from the brand set: gold arcs, the faint globe, square gold frames, short rules.
- For motion, use the entrance eases from DESIGN.md, give text 0.7 to 1.0s, give line draws 1.0 to 1.6s, and hold for at least 2s. Never use bounce, elastic, glow, glitch, or neon.
- Numbers use `font-variant-numeric: tabular-nums` and count up with a `power2.out` ease.
- Scene transitions are crossfades or a dip to navy.

## Step 5: verify

Follow the repo's verification rules (`CLAUDE.md`): lint, preflight, Studio review,
draft render, and hero-frame inspection. In addition, check these BEM-specific items:

- Colors match the palette, and no off-brand hues come from other styles' cards.
- No graphic covers a face, and 9:16 text stays inside y=200 to 1600, clear of the right-edge UI.
- Lower-third names and titles are spelled exactly as provided.
- Gold never appears on more than one word per caption line, apart from listed phrases.
- The intro and outro read cleanly at the actual project resolution.
