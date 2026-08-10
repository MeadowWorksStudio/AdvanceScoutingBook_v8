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