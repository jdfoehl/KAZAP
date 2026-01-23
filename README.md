KAZAP! (Kaboom-inspired Mobile Prototype) — Week 2 Submission

Overview
KAZAP! is a portrait-mode mobile prototype inspired by classic Kaboom-style reaction gameplay. You control a shield stack to block falling bolts. Difficulty ramps across three rounds through Zeus movement and increased bolt pressure. In Round 3, an accelerometer-based emergency power called “Shake the Heavens” becomes available. It clears active bolts and briefly stuns Zeus/spawning.

Advanced touch controls
The core interaction is touch-and-hold plus drag, using continuous touch tracking rather than simple button taps. The game also gates the start of gameplay until the player grabs/holds the shield stack, then treats release as ending the “holding” state. Touch state has clear visual feedback: the shields change tint while holding and revert on release, and the start prompt appears only during the start gate.

Sensor integration
Shake the Heavens is driven by accelerometer shake input and has a meaningful gameplay effect: it clears all currently active bolts and briefly freezes Zeus and pauses spawning for a tunable duration. Shake detection uses smoothing (Lerp) to reduce jitter and keep the input stable.

Mobile-appropriate design
The game is designed for one-handed play. The primary interaction is a single-thumb drag on the shield stack, with the shake power used as an optional emergency action. The game is locked to portrait orientation (no auto-rotation). UI and center text (taunts, countdown, GO) were sized to remain readable at phone resolutions. Touch target sizing was validated at 1080×1920 portrait using a debug measurement on the smallest interactive object, confirming it meets the minimum touch-target guideline.

Testing and build notes
Target platform: Android
Testing environment: Android Emulator (Pixel 5) and Unity Editor Play Mode

The gameplay loop, round progression, UI flow, and loss/game-over sequences were verified on the emulator. Portrait lock was also verified by rotating the emulator while the game stayed fixed in portrait.

Controls
Start
Tap the Start button.

Shield control (touch)
Touch and hold the shield stack, then drag to block falling bolts. The round begins on the first grab/hold (start gate). Shields tint while holding and revert when released.

Shake the Heavens (Round 3)
Real device: shake the device to trigger the power.
Unity Editor demo: press Space to simulate the shake trigger.

Prototype rules for Shake the Heavens
Unlocked in Round 3
One use per run
Icon indicates readiness (bright when available, dim after use)

Build instructions
Open the Unity project and switch the build platform to Android. Use Build & Run to an Android device or emulator. Orientation is locked to portrait in Player Settings.

Known issues / limitations
Accelerometer shake cannot be physically performed on an emulator, so Shake the Heavens is demonstrated via a dev-key fallback (Space) in the Unity Editor.
Some visuals are placeholders (ground strip, Shake the Heavens icon) while mechanics and input systems are the focus of this prototype milestone.
