Week 5 Analytics Documentation (Unity Analytics Integration)

Feature Implemented (Option B: Analytics Integration)

This milestone implements Unity Gaming Services Analytics for KAZAP!. The goal is to track a small set of meaningful player events that describe the core gameplay loop and provide clear signals for tuning difficulty, pacing, and retention.

Five gameplay events are instrumented:

run_start
round_start
life_lost
round_complete
run_end

Each event includes parameters that add context (deity, round index, shields, timing, etc.) so the data is actionable rather than just “an event happened.”

Tracked Events + Parameters

run_start
Purpose: Fired when a new run begins from the title screen.

Parameters:
deity (string) – current deity name for the run (ex: Zeus)
starting_shields (int) – number of shields at run start
overall_round_index (int) – run-wide round index at start (typically 1)

round_start
Purpose: Fired when a new round begins.

Parameters:
deity (string) – current deity name
round_within_deity (int) – round number within the current deity’s sequence
overall_round_index (int) – overall round number across the whole run
bolts_per_round (int) – bolt count configured for this round
shields_remaining (int) – shields remaining at round start

life_lost
Purpose: Fired when the player loses a shield (life).

Parameters:
deity (string) – current deity name
cause (string) – cause of life loss (ex: bolt_hit_ground)
round_within_deity (int) – round number within the current deity’s sequence
overall_round_index (int) – overall round number across the whole run
shields_before_loss (int) – shields count immediately before the loss

round_complete
Purpose: Fired when the player successfully completes a round.

Parameters:
deity (string) – current deity name
overall_round_index (int) – overall round number across the whole run
round_within_deity (int) – round number within the current deity’s sequence
round_seconds (number) – time spent in the round (seconds)
shields_lost_this_round (int) – how many shields were lost during the round

run_end
Purpose: Fired when the run ends (game over / run completion endpoint).

Parameters:
deity (string) – current deity name at run end
run_seconds (number) – total run duration (seconds)
overall_round_index_reached (int) – highest overall round index reached during the run

KPIs and Success Metrics Supported (What this Analytics Measures)

Average session length
Measured by: run_seconds (run_end)

Round completion rate and difficulty spikes
Measured by: ratio of round_complete vs round_start grouped by overall_round_index / round_within_deity

Lives lost per round (punishment / frustration rate)
Measured by: life_lost grouped by overall_round_index / round_within_deity

Where runs end / churn point
Measured by: overall_round_index_reached at run_end

Deity-based balancing comparison (if multiple deities are introduced)
Measured by: grouping all events by deity

Verification / Proof of Correct Sending

Unity Analytics Debug Panel (Editor)
Data Collection Active indicator shown during Play Mode. Uploads completed successfully (Upload Finished 204).

Unity Dashboard Event Browser (Production Environment)
All five custom events appear under Valid Events once their schemas were created, parameters assigned, and the events enabled. This confirms that events were received and validated by the Unity Analytics backend.

Note on delayed visibility
The Event Browser UI can lag significantly (often 10–20 minutes). Testing was done by triggering events in Play Mode, confirming upload completion, and waiting until the Event Browser time window caught up to confirm the same events appearing under Valid Events.

Development / Testing Constraints

Development was done on Windows PC. Physical device testing was not possible due to owning an iPhone and not having access to macOS/Xcode, and no Android device being available.

Verification approach for this milestone relied on:
Unity Editor Play Mode + Analytics Debug Panel (confirmed successful uploads)
Unity Dashboard Event Browser (confirmed backend receipt and schema validation)

Android emulator is used primarily for performance profiling and touch interaction validation in other milestones. For this analytics milestone, the critical requirement was verifying events were successfully received and validated in the dashboard, which was confirmed.

Screenshots / Evidence

Evidence images are included in the repository under:

Docs/Week5_Analytics/TestDocs/

This folder contains screenshots showing:
Event Browser with the custom events appearing under Valid Events
Event Manager pages for each custom event showing assigned parameters
Examples of events appearing after a run that triggers the full set (run_start, round_start, life_lost, round_complete, run_end)

Notes / Future Improvements

Add dedicated event for Shake the Heavens usage (if required as a separate KPI rather than inferred from gameplay state).
Add segmentation for new vs returning players if the project expands to multiple sessions/persistence.
Add a lightweight in-game telemetry toggle/consent UI if the project is expanded beyond class scope.
