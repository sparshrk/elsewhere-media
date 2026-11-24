# rule-ep1-visa-refusals — "UK student visa refusals: the rule nobody tells you"

Series: **The Rule Nobody Tells You** (TRA-161), pillar "The Decision Nobody Explains to You" (TRA-158 rev. 2).
Episode 1 of 2. Vertical 1080×1920, 30 fps, 29.0 s, English only. Instagram/Facebook Reel for @elsewhereedu.
Audience: UK/Ireland PG working professionals, 24-32 (master's/MBA applicants — not 18-year-old undergrads).
Facts: FACTS.md (gov.uk only, checked 24 Nov 2026).

## Shared series template (built for TRA-161, reused verbatim by Ep 2)
- **Base style**: Data Storytelling ("dataviz" in `styles/`), reused via its existing engine
  (`films/_shared/engine.js`, copied unchanged from `films/cost-compare/engine.js`, itself an elsewhereedu
  dataviz film already in this repository): cream paper, ink, pencil-red/blue accent, handwriting + mono-type
  primitives, pencil-stroke underlines/rings. Chosen because "reveal a rule/number/date" content maps directly
  onto this engine's big-number and annotation primitives, and because it is already the brand's proven look
  for elsewhereedu Reels, which satisfies "same look every episode" without inventing a new visual language
  from scratch under a same-day deadline.
- **Adaptation**: rather than reuse `cost-compare`'s bar-race `film.js`, each episode uses a simpler sequence
  of full-bleed "reveal cards" (title → big number → annotation) built on the same engine primitives.
- **Shared cold open** (`films/_shared/shared.js`, `coldOpen()`): 0.0-1.6 s, near-black card, title slams in,
  red accent rule draws in, then the episode's one-line hook appears by t≈0.35-0.65 s — inside the ticket's
  1-2 s hook window.
- **Shared end card** (`films/_shared/shared.js`, `endCard()`): "SAVE THIS" / "Follow @elsewhereedu" / the
  gov.uk source + check-date line / "AI-generated video" disclosure line. Same design, different source string.

## Candidate structures
1. **A single number that turns into a trap.** Chosen: the hook is already a number, and "day 19 breaks the
   run" is one clean visual turn.
2. Before/after comparison of the two fee amounts only — no turn, rejected.
3. Checklist-first — buries the hook, rejected.

Logline: a UK student visa can be refused not for lacking money, but for one broken day inside a 28-day window.
Setup (28 days, no dips) → money + date line (30 Nov 2026) → the turn (day 19 breaks the streak) → the fix
(check your statement date, count back 28 days) → who this matters to → end card.

## Shot list / beat sheet
| t (s) | Card | Content |
|---|---|---|
| 0.0-1.6 | Cold open | Hook: "Your UK student visa can be refused over ONE day." |
| 1.6-5.9 | A | "UK STUDENT VISA — the maintenance-funds rule"; big "28"; "days in a row" |
| 5.9-14.8 | B | "FROM 30 NOV 2026" stamp; £1,570/mo London (was £1,529); £1,203/mo outside (was £1,171) |
| 14.8-18.5 | C | "MISS THE STREAK BY ONE DAY"; 28-dot calendar strip; day 19 breaks (red ✕) |
| 18.5-23.5 | D | checklist (statement date; count back 28 days; no dips); who it's for |
| 23.5-29.0 | End card | SAVE THIS / Follow @elsewhereedu / gov.uk source + 24 Nov 2026 / AI-generated disclosure |

## Sound design
 Calm chord bed (A minor → C major → F major → A minor), numpy-synthesised "plonk" sonification on each reveal,
light graphite/paper/wood foley, narration ~11 dB above the music bed while speaking. 100% original synthesis
(no sampled libraries). Mastered to -14 LUFS / true peak -1.6 dBFS via core/render/mux.sh (confirmed in build log).

## Known shortcut (declared, not hidden)
`readcheck.mjs` (automated reading-time check) could not be wired up in the time budget: `texts()` returns `[]`.
On-screen hold times were designed by hand well above the ≥1.8 s / (words÷15+1.5) s rule (each card holds 3.5-9 s).
