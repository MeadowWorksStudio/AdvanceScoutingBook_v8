[README_Advance_Scouting_Book_v8.md](https://github.com/user-attachments/files/33617606/README_Advance_Scouting_Book_v8.md)
# Advance Scouting Book

**Version:** v8 Testing Release (October 2026)  
**Platform:** mobile-first, single-file HTML/CSS/JavaScript prototype  
**Purpose:** live pitch calling, opponent scouting and lightweight game-state tracking for baseball and softball coaches.

## Product approach

Record observed pitch outcomes, learn from current-pitcher and batter history, and provide a transparent suggested pitch. The coach makes the decision. This is not a full scorekeeping application.

## Getting started

1. Open the latest v8 HTML file in a browser. Enter the opposing team and pitchers, including arsenal and throwing hand.
2. Enter the opposing lineup. **ADD & NEXT BATTER** saves and leaves entry open; **ADD & CLOSE** finishes; **ADD TO BENCH** stores an available substitute.
3. Tap **START GAME**. The leadoff batter should be selected and the Call a Pitch screen displayed. **LOAD TEST MODE** supplies a sample five-batter, two-pitcher game.

## Main game workflow

- **Call a Pitch:** adaptive pitch buttons resize for the active pitcher's arsenal. The highlighted recommendation contains pitch, location and a brief reason.
- **Location:** choose actual pitch-ending position on a 17-location grid (9 zone / 8 chase). The current batter's name, handedness and record appear below the perspective control. Switch Catcher/Pitcher Perspective without changing the underlying logged location.
- **Quick results:** BALL, FOUL, CALLED STRIKE and SWINGING STRIKE under the location grid bypass detailed location/result logging and retain unknown location.
- **Detailed results:** choose pitch result after location; foul direction is 3B SIDE, STRAIGHT BACK or 1B SIDE. Ball in play continues to spray location, contact type and OUT/SAFE handling.
- **Dropped third strike:** conditional CALLED/SWINGING choices on detailed result screen at two strikes, subject to first-base and out conditions; resolve SAFE/OUT.
- **Scouting:** Pitch Stats, Heat Map and Spray Chart buttons are present from the first pitch; views without enough data may be disabled. The heat map uses blue for whiffs and red for contact.

## Lineup and game state

The **LINEUP** button is centered in the dark banner between ON BASE and OUT −/+. The lineup highlights the active hitter and shows records such as **2-4, 1 BB** (hits–official at-bats, walks). Edit player information, handedness, batting order and record; use bench substitutions or ADD PLAYER for late arrivals. Substitutes keep their own records and scouting histories.

Base occupancy is manual (3B / 2B / 1B). OUT −/+ supports corrections. OPTIONS includes **Edit Inning**. Pitch types are maintained in **Edit Pitcher**, not in Options. Editing an existing pitcher should preserve their history; creating a new pitcher starts a separate identity.

## Recommendation engine

Rule-based and explanatory. Uses count, batter history, current pitcher's aggregate performance, pitch/zone effectiveness, sequencing, repeated foul timing and runner situation. At three-ball counts it does not recommend exterior chase locations. Treat suggestions as guidance rather than guaranteed outcomes.

## Current limitations

- **Testing release:** JavaScript syntax checks are not equivalent to end-to-end browser or phone testing.
- **No persistent backend:** do not rely on prototype browser state as a permanent record.
- **Not full scoring:** manually maintain bases and correct scoring discrepancies. SAFE on a ball in play may need a manual hit/at-bat correction if it was an error or other non-hit reach.
- **Ruleset variations:** dropped-third-strike and other details should be checked against the league's rules.

## Related documents

- `advance_scouting_book_coach_guide_v8_testing.docx` — game-day walkthrough.
- `advance_scouting_book_version_history_changelog_v8.md` — version history and v8 changes.
- `advance_scouting_book_v8_phone_test_checklist.md` — manual mobile acceptance test.

**Documentation baseline:** `advance_scouting_book_v8_edit_player_handedness_highlight.html`.
