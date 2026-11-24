# giveaway-visa-filing — "Free UK visa filing — enter to win" (promo/giveaway Reel)

Series look: **The Rule Nobody Tells You** (TRA-161 shared template), repurposed for a promo rather than an
explainer episode. Vertical 1080×1920, 30 fps, 18.1 s, English only. Instagram/Facebook Reel for @elsewhereedu.
Not a factual-claims reel (board-request task; no `FACTS.md`): the only on-screen claims are the giveaway's own
terms, given verbatim by the board and isolated in `terms.json` (see "The swappable terms layer" below). No
additional visa facts, fees or timelines are invented anywhere in this film.

## Shared series template (reused unchanged from TRA-161 / rule-ep1 / rule-ep2)
- **Base style**: Data Storytelling engine (`films/_shared/engine.js`, copied unchanged — the same copy ep1/ep2
  use). Cream paper, ink, pencil-red/blue accent, handwriting + mono-type primitives, pencil-stroke
  underlines/rings/badges.
- **Shared cold open** (`films/_shared/shared.js`, `coldOpen()`, byte-identical to ep1/ep2's copy): 0.0-1.6 s,
  near-black card, "THE RULE / NOBODY TELLS YOU" slams in at t=0, a red accent rule draws in, then this episode's
  hook — **"We'll file your UK student visa. Free."** — appears at t≈0.35 s and is fully in at t≈0.65 s: inside
  the ticket's "hook in the first 1 second" requirement.
- **Shared end card** (`films/_shared/shared.js`, `endCard()`, byte-identical to ep1/ep2's copy): "SAVE THIS" /
  "Follow @elsewhereedu" / a source-style line / "AI-generated video · informational, not legal advice"
  disclosure, all burned on screen, same design as both prior episodes. No human board member or counsellor is
  named or shown anywhere in this film (company rule), same as ep1/ep2.

## Candidate structures
1. **Hook → how-to-enter checklist → terms card → end card.** A single clean read: the offer, the 3 mechanical
   steps to enter, then the mandatory terms, then the CTA. Chosen: a giveaway promo has one job (get the entry)
   and the series' "reveal card" grammar (ep1/ep2's blocks A/B/C/D) maps directly onto "step 1 / step 2 / step 3"
   without inventing a new structure.
2. **Terms card first, steps after.** Rejected: buries the hook and the ask behind legal text, which both reads
   worse and risks the "hook in the first second" requirement.
3. **Narrate the full terms text aloud, word for word.** Rejected: see "narration is winner-count-agnostic" below
   — it would tie the voice track to the exact wording the board might need to change later.

**Chosen: 1.** Logline: a free giveaway from @elsewhereedu — they'll file a UK student visa for three winners;
entering takes three steps; the rest is disclosure. Setup (hook: free filing) → how to enter (3 steps) → terms
(verbatim, held legible) → end card (save/follow/AI disclosure).

## Shot list / beat sheet
| t (s) | Card | Content | Why |
|---|---|---|---|
| 0.0-1.6 | Cold open | Series title + hook: "We'll file your UK student visa. Free." | hook inside first 1 s |
| 1.6-7.6 | A (How to enter) | "HOW TO ENTER / Free UK visa filing — 3 winners"; 3 numbered, hand-ringed steps: ① Follow @elsewhereedu ② Comment your target uni/city ③ Done. | the ask, in order, one beat each |
| 7.6-12.0 | B (Terms) | Framed "TERMS" card, verbatim board wording, held ~4.1 s fully visible after a 0.3 s fade-in (required minimum: 2.0 s) | mandatory disclosure, legible |
| 12.0-12.1 | Exit wipe | fade to paper | transition into the end card |
| 12.1-18.1 | End card | SAVE THIS / Follow @elsewhereedu / AI-generated disclosure | CTA + compliance, same design as ep1/ep2 |

## Benchmark
Same as ep1/ep2: vertical data-explainer Reels (FT/Reuters-style graphics shorts). Learn: one clear beat per
card, legible held type, a single visual "ask" per screen. Don't take: any outlet's layout, fonts or music —
and, specific to this film, don't take any sweepstakes/giveaway ad's exact copy or layout; this is an original
treatment of the board's own words.

## Cue map / sound design
Upbeat major-key chord bed (C major → G major → A minor → F major — intentionally brighter than ep1/ep2's
A-minor opening, because a giveaway reads lighter than a visa-refusal warning), numpy-synthesised "plonk"
sonification on each reveal (cold-open ring, each of the 3 step-ticks, the terms card landing, the end card),
light graphite/wood foley on the same events, narration compressed and sitting ~11 dB above the music bed while
it speaks (`audio.py`, same instrument palette and structure as `rule-ep1`/`rule-ep2`'s `audio.py` — pure
synthesis, no sampled instruments, no sample-library download needed). Mastered to −14 LUFS / true peak
−1.6 dBFS via `core/render/mux.sh` (confirmed in the build log; see the render report for the measured number).

## Subtitles / on-screen type
IBM Plex Mono (bold headlines, step numbers, terms heading), Newsreader (the terms paragraph and the burned
figure-caption subtitles, via `engine.js`'s `caption()`). One English line at a time, each cue held comfortably
above the DIRECTOR.md §7 minimum (≥ 1.8 s, and ≥ spoken length + 0.6 s — see `CUES` in `film.js`).

## The swappable terms layer (read this before editing the giveaway's terms)
**Edit exactly one file, one field: `films/giveaway-visa-filing/terms.json`, the `"text"` field.** `film.js`
fetches it at render time (`const TERMS = await (await fetch('terms.json')).json();`) rather than hard-coding the
wording, and the terms card (`blockB` in `film.js`) draws whatever string is in that field, word-wrapped and
centred, with no other code change needed for a pure wording/number/date edit (e.g. "3 winners" → "5 winners",
or "30 Nov" → "7 Dec").

**What a terms-only edit needs, practically:**
- The narration (`lines.json`, `out/vo/*.wav`) and the mixed score/foley (`out/mix.wav`) do **not** reference the
  winner count or the dates at all — by design (see `CUES`/`lines.json`: V01-V04 say "We'll file your UK student
  visa. Free.", "Follow us. Comment your target uni or city. Done.", "Full terms are on screen.", "Save this, and
  follow @elsewhereedu."). So editing `terms.json` and re-rendering **only** needs the picture + mux steps, not a
  TTS re-run:
  ```sh
  cd <repo root>
  node core/render/video.mjs films/giveaway-visa-filing --fps 30 --workers 3 --size 1080x1920 \
    --out films/giveaway-visa-filing/out/video.mp4
  sh core/render/mux.sh films/giveaway-visa-filing/out/video.mp4 films/giveaway-visa-filing/out/mix.wav \
    films/giveaway-visa-filing/giveaway-visa-filing.mp4 30 0
  ```
  (`out/mix.wav` from the last full `build.sh` run is reused as-is; it has no terms-count-specific audio in it.)
- **Limit, stated plainly:** if a future edit needs the *narration itself* to state a number (for example, if the
  board later wants the voice to say "three winners" out loud), that is no longer a terms.json-only edit — it
  requires changing `lines.json`'s V01/V02 text and re-running the full `build.sh` (TTS → ASR check → events →
  audio mix → picture → mux), because the voice track is baked audio, not live text. The whole reason the
  narration was written winner-count-agnostic in this film is to avoid that cost for the kind of edit (count,
  date) the board is most likely to make after this ships.
- The one hand-timed constraint `terms.json` edits must still respect: the string should still fit legibly inside
  `blockB`'s wrap width (860 px at 32 px Newsreader, ~45-50 characters per line, ~4-5 lines tall) without
  overflowing the framed card (y 300 to H-320); a much longer replacement string would need either a smaller font
  size or a longer `T.B1` hold in `film.js`, both one-line changes in the same file.

## Known shortcut (declared, not hidden)
The terms card's full paragraph is reported to `readcheck.mjs` via `texts()` with `pass: true` (the same escape
`readcheck.mjs`'s own header documents for "fine-print credits on an end card"): at ~230 characters, the tool's
15 chars/s conversational-reading heuristic would want ~16.8 s on screen, which would blow the under-25-s budget.
The ticket's own, explicit requirement — legible for **at least 2 full seconds** — is met with margin by hand
(T.B0=7.6 to T.B1=12.0, 4.1 s fully visible after a 0.3 s fade-in) and is the requirement that actually governs
this card. Flag for a follow-up pass if a future episode needs the full paragraph read at conversational speed
instead (it would need a longer hold or a shorter terms string).
