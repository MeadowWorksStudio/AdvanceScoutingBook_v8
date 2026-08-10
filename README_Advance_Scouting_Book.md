# Advance Scouting Book

Advance Scouting Book is a mobile-first web app for baseball and softball coaches to use live from the dugout. Its purpose is to help a coach track what has happened against a batter, understand the current game situation, and make a more informed next pitch call without turning the coach into a full-time scorekeeper.

The app is currently an iterative single-file HTML/JavaScript prototype. It is being developed through short feedback cycles with coaches, with features kept simple, transparent, and thumb-friendly for use during games.

## Current Status

**Current milestone:** v6 test iteration

The current v6 test build carries forward the v5 suggestion engine, heat map, spray chart, base occupancy, lineup/pitcher management, and in-game scouting features while testing a faster pitch-entry workflow.

Current v6 test changes include:

- Rebranded from the earlier working name **Dugout Signal** to **Advance Scouting Book**
- Pitch location now means **where the pitch actually ended**
- Removed the separate "Executed as Called?" / command-percentage workflow
- Added **FOUL** as a pitch result
- Fouls count as strikes for strike-percentage purposes
- Repeated fouls on the same pitch in the current at-bat create a timing penalty in the suggestion engine
- Added **DOUBLE PLAY +2** when runners are on base and fewer than two outs
- Added manual **- OUT / + OUT** controls for game-state corrections and outs that happen outside the normal pitch-result workflow
- Preserved the compact **THIS AT-BAT** pitch sequence display
- Adjusted the heat-map legend alignment for a more centered presentation

v6 should still be considered a **testing iteration**, not a finalized release.

## Core Product Idea

Advance Scouting Book is built around a simple loop:

**Record what happened -> learn the hitter -> account for the game situation -> help the coach choose the next pitch.**

The coach remains the pitch caller. The app provides evidence and a transparent recommendation rather than attempting to replace baseball/softball judgment with a black-box model.

## Current Features

### Game setup
- Opposing team name
- Pitching staff
- Pitcher jersey number, throwing hand, and pitch arsenal
- Custom pitch types
- Starting lineup and bench
- Batter jersey number, name, and handedness

### Live pitch calling
- Pitch selection
- Actual pitch location
- Ball / called strike / swinging strike / foul / ball-in-play result logging
- Automatic count tracking
- Automatic outs and inning progression
- Manual base occupancy for 1B / 2B / 3B
- Manual - OUT / + OUT corrections
- Double-play result handling
- Change batter and change pitcher during the game

### Ball-in-play tracking
- Tap where the ball was hit on a field diagram
- Contact type:
  - Ground ball
  - Line drive
  - Fly ball
  - Pop up
- OUT / SAFE result
- Batter spray chart for the current game

### Batter scouting
- Per-batter pitch history
- Strike-percentage information
- Current-at-bat pitch sequence
- Whiff heat map using a 3x3 strike zone plus four chase-corner locations
- Sample-size protection so low-data heat-map cells remain neutral

### Pitch suggestions
The suggestion engine is intentionally rule-based and coach-readable.

It currently considers:

- Count state
- Batter-specific pitch history
- Whiffs
- Strike percentage
- Whether a pitch has already been shown in the current at-bat
- Repeated foul balls and hitter timing
- Runner on third
- Runners in scoring position
- Bases loaded
- Double-play situations
- Ground-ball tendencies

The suggested pitch is displayed directly on the pitch-call button with a short explanation of the signal driving the recommendation.

## Important Product Decisions

- **Observed events over subjective grading.** The current workflow records where the pitch ended rather than asking the coach to grade command on every pitch.
- **Keep clicks down.** Normal pitches should move through the workflow with as few taps as possible.
- **Transparent recommendations.** Suggestions should explain why a pitch is being favored.
- **Coach feedback drives scope.** Features are tested before being treated as permanent or premium.
- **Features earn their gate.** Prototype features remain unlocked while their usefulness is being evaluated.
- **Do not become a full scorekeeping app.** Game-state controls exist to keep Advance Scouting Book synchronized with the game, not to recreate every baseball/softball scoring rule.
- **Effective velocity and tunneling are explicitly deferred.** Do not add them unless that decision is revisited.

## Current Technical Architecture

Advance Scouting Book is currently:

- A single HTML file with embedded CSS and JavaScript
- Designed mobile-first for phones and tablets
- Hosted for testing through Netlify Drop
- Using browser memory only
- Not connected to a database
- Not using user accounts yet

Because there is no persistent backend, scouting information does not yet reliably survive across sessions/devices. This limits roster reuse, historical opponent scouting, and account-based premium features.

## Planned Backend Phase

Firebase and Supabase have both been identified as realistic backend-as-a-service options.

Persistence would unlock:

- User accounts
- Saved pitching staffs
- Saved opponents and rosters
- Cross-session batter scouting history
- Loading a roster from a previously faced team
- Editing previously loaded rosters
- Merging scouting history when a player changes teams or identifying information
- Historical reports
- Freemium account/subscription behavior

## Platform Roadmap

The preferred path is:

1. Continue validating the mobile web prototype with coaches
2. Validate the app as a Progressive Web App (PWA)
3. Add persistence/backend infrastructure
4. Evaluate native packaging only after the workflow is proven
5. Consider Capacitor or React Native if App Store / Play Store distribution becomes worthwhile

## Freemium Direction

A freemium model is planned, but no feature should be locked before it proves useful.

Leading premium candidates include:

- Historical scouting across games
- Batter whiff heat map
- Rule-based pitch suggestions
- Advanced opponent memory / scouting tools

The current prototype intentionally leaves these features unlocked for evaluation.

## Project Files

The project is maintained with several complementary artifacts:

- **Prototype HTML files** - versioned milestone builds preserved separately
- **Pre-loaded demo build** - sample roster/history for showing the app without setup
- **Coach Walkthrough Guide** - current test instructions and feedback questions
- **Feature Backlog** - one cumulative living document for future work and decisions
- **Version History / Changelog** - milestone history from v1 forward
- **README** - this file; the high-level project orientation and current-state reference

## Versioning Approach

Prototype builds are preserved as milestones rather than overwritten.

The current reconstructed history is:

- **v1** - initial pitch-calling and setup workflow
- **v2** - spray chart, contact type, OUT/SAFE workflow, base occupancy, pitcher numbers
- **v3** - rule-based pitch suggestion engine
- **v4** - batter whiff heat map and larger scouting-panel controls
- **v5** - base-occupancy-aware pitch suggestions and ground-ball fallback logic
- **v6 test iteration** - Advance Scouting Book branding, faster actual-location workflow, manual outs, double plays, fouls, foul-timing suggestion logic, and related UX refinements

See the separate version-history/changelog file for more detail.

## Known Limitations

- No backend or persistent database
- Browser/session-memory limitations
- Batter history is not yet reliably available across devices/sessions
- Per-pitcher statistics can blend when multiple pitchers use the same pitch-type name
- Some current features are still being validated with coaches
- App naming/trademark search is still pending
- Native App Store / Play Store packaging has not been started

## Current Testing Focus

The current test round should answer questions such as:

- Is the Pitch -> Location -> Result workflow fast enough during a real game?
- Does removing command grading make the app clearer?
- Does FOUL logging feel natural?
- Does the repeated-foul timing penalty improve pitch suggestions?
- Are the suggestion reasons understandable and trustworthy?
- Is the THIS AT-BAT sequence useful during live calling?
- Do - OUT / + OUT controls keep the app from getting stuck when the real game changes unexpectedly?
- Is DOUBLE PLAY +2 sufficient without turning the app into a scorekeeper?
- Are the heat map, stats, and spray chart useful enough to justify future premium gating?

## Development Principles

- Make incremental, decision-first changes
- Avoid surprise scope additions
- Keep milestone prototypes separate
- Keep one cumulative backlog
- Maintain the coach guide each testing round
- Maintain a changelog/version history for each new milestone
- Validate JavaScript syntax before delivery
- Prefer surgical edits over unnecessary rewrites
- Explain infrastructure decisions in plain language
- Optimize for real dugout use rather than feature count

## Naming History

The project was originally developed under the working name **Dugout Signal**. Historical files and earlier changelog entries may still use that name.

The current working product name is **Advance Scouting Book**.

A trademark/App Store name search should be completed before public launch or significant branding investment.

## Project Goal

The near-term goal is not to build the largest baseball/softball analytics platform.

It is to answer a narrower question well:

**Can Advance Scouting Book become the tool a coach actually keeps open during a game because it helps make the next pitch call?**
