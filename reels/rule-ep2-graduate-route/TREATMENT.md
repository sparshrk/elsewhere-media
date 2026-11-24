# rule-ep2-graduate-route — "The UK Graduate Route change"

Series: **The Rule Nobody Tells You** (TRA-161), pillar "The Decision Nobody Explains to You". Episode 2 of 2.
Vertical 1080×1920, 30 fps, 27.8 s, English only. Instagram/Facebook Reel for @elsewhereedu.
Audience: UK/Ireland PG working professionals, 24-32. Facts: FACTS.md (gov.uk only, checked 24 Nov 2026).

## Shared series template (identical to Ep 1)
Same engine (`engine.js`, copied from `films/cost-compare`), same cold open and end card (`shared.js`,
identical to Ep 1's copy, only the per-episode `hook` and `source` strings differ), same palette, type, and
"reveal card" grammar. This episode re-skins the already-researched `films/graduate-route` facts (2 years → 18
months, HC 1333, PhD exemption) into that shared template, dropping its old bespoke "3D Map Explainer" visuals
entirely, per TRA-161.

## Candidate structures
1. **Today's number, then the date-line split, then the exception.** Chosen: mirrors Ep 1's grammar exactly,
   hook is number-based from frame one.
2. Start from the PhD exception and work backward — buries the hook, rejected.
3. The retired `graduate-route`'s runway/timeline metaphor — not reusable in this template without inventing
   new geometry under a same-day budget, rejected per the ticket.

Logline: the Graduate Route is being cut from 2 years to 18 months for anyone applying from 1 January 2027,
with PhD graduates unaffected. Setup (today: 2 years) → the turn (the 1 Jan 2027 date line) → the exception
(PhD: still 3 years) → the fix (plan your 18-month runway; start early) → end card.

## Shot list / beat sheet
| t (s) | Card | Content |
|---|---|---|
| 0.0-1.6 | Cold open | Hook: "Your UK work visa just got 6 months shorter." |
| 1.6-6.5 | A | "GRADUATE ROUTE — stay and work after your UK degree"; big "2" / "YEARS, TODAY" |
| 6.5-15.3 | B | "FROM 1 JAN 2027" stamp; "Apply by 31 Dec 2026 → 2 YEARS"; "Apply from 1 Jan 2027 → 18 MONTHS" (red) |
| 15.3-17.3 | C | "ONE EXCEPTION"; big "3" / "YEARS, UNCHANGED" — PhD graduates |
| 17.3-23.8 | D | checklist: plan for 18 months; start the job hunt in term one |
| 23.8-27.8 | End card | SAVE THIS / Follow @elsewhereedu / gov.uk source (HC 1333) + 24 Nov 2026 / AI-generated disclosure |

## Sound design
Identical palette to Ep 1 (numpy-synthesis plonks + chord pad + light foley, no sampled libraries), re-timed to
this episode's VO durations. Mastered to -14 LUFS (confirmed in build log: I -14.0 LUFS, peak -1.6 dBFS).

## Known shortcut (declared, same as Ep 1)
`readcheck.mjs`'s automated reading-time check is not wired up (`texts()` returns `[]`); on-screen hold times
were designed by hand well above the DIRECTOR.md §7 minimums.
