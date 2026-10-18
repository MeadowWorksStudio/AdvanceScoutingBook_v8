# Advance Scouting Book - Version History & Changelog

**Current:** v6 flow-test iteration

## v1 - Foundation

Initial click-through pitch-calling prototype: pitcher/opponent setup, lineup entry, pitch type selection, plate-location logging, result logging, count/outs/inning tracking, and basic per-batter scouting history.

## v2 - Ball-in-play + game setup refinement

Replaced the old OUT/HIT result grids with a spray-chart workflow: tap ball location → contact type (GB/LD/FB/PU) → OUT/SAFE. Added base-occupancy toggles, pitcher jersey numbers, current-game spray chart viewing, and custom-pitch setup fixes.

## v3 - Rule-based pitch suggestions

Added ★ SUGGESTED directly on one pitch button with a readable reason. Suggestions combine count-state logic and batter-specific matchup history, with a mild anti-repeat penalty. Moved pitch-type stats from always-inline presentation to a pop-out pattern for a cleaner call screen.

## v4 - Batter whiff heat map + scouting controls

Added batter whiff heat map using the same 3x3 zone + four chase corners. Heat map uses whiff rate with a minimum-sample guard and red=hot/fewer whiffs, blue=cold/more whiffs. Reworked STATS / HEAT MAP / SPRAY CHART into larger direct-tap buttons with explanatory disabled states.

## v5 - Base-occupancy-aware suggestions

Extended the v3 suggestion engine with game-situation modifiers: runner on 3rd favors whiffs; scoring position penalizes low strike%; bases loaded favors strike-throwers; runner on 1st with <2 outs favors ground-ball pitches. Added arsenal-wide ground-ball fallback and context-aware suggestion reasons.

## v6 - Current flow test: faster logging + game-state corrections

Renamed the product to Advance Scouting Book. Added - OUT / + OUT controls and conditional DOUBLE PLAY +2. Removed the forced execution/command step and then simplified further to location-only logging: pitch location always means where the pitch ended, MISS was removed, and CMD% was removed. Added FOUL result/count logic. Fouls count as strikes but not whiffs; repeated fouls in the current at-bat increasingly penalize the same pitch in the suggestion engine. Heat-map legend alignment was centered. THIS AT-BAT remains visible as the live sequence summary.

## Key product decisions carried forward

- Observed-event logging: record what happened; do not require execution grading on every pitch.
- Transparent rule-based pitch suggestions.
- Manual base occupancy; not a full scorekeeper.
- Prototype features ship unlocked before freemium gating.
- Backend/persistence deferred until workflow validation.
- Effective velocity/tunneling explicitly deferred.
- Preserve versioned prototype milestone files; maintain one cumulative backlog.

## Open questions after v6 testing

- Keep the Pitch → Location → Result loop permanently?
- Does foul-timing weighting improve suggestions?
- Does a wild-pitch/noncompetitive-pitch flag need to return?
- Keep pitch stats in pop-out vs inline?
- Do coaches trust/use the suggested-pitch badge?
- When should backend/persistence begin?

## v7 — Scouting and workflow refinements

Interim iteration between the v6 flow test and v8. The detailed v7 release notes remain the historical source for v7-specific changes.

## v8 — Current testing release

- Adaptive pitch-call button sizing for changing pitcher arsenals; suggested pitch explanation stays inside the pitch button.
- Opposing lineup and bench management: Add & Next Batter, Add & Close, Add to Bench, editing, substitutions, late arrivals and independent player histories.
- Compact batter game record (hits–official at-bats and walks, e.g. `2-4, 1 BB`), shown in lineup, call screen and location header.
- LINEUP control centered between ON BASE and OUT controls in game banner.
- 17-position pitch location interface, handedness-aware batter silhouette and Catcher/Pitcher Perspective switching on location and heat-map screens.
- Four fast result buttons beneath location grid, plus detailed foul direction and conditional dropped-third-strike actions.
- Pitch Stats, Heat Map and Spray Chart controls shown from the first pitch even with insufficient batter history.
- Edit Pitcher supports adding pitch types; redundant Add Pitch Type removed from Options. Edit Inning added to Options.
- Game setup and Load Test Mode navigation fixes; edit-player modal sizing and selected-handedness highlight.
- Recommendation improvements: current-pitcher history fallback for unseen batters; per-pitcher evidence separation; no exterior chase recommendations at three-ball counts.

**Status:** testing, not production certified. Verify complete flows on a phone.
