Week 6: Polish & Launch Preparation

POLISH ELEMENTS ADDED

1. Screen Effects + Accessibility Controls

Implemented: title “impact” shake + zoom/flash transition, life-loss climax flash + camera/world shake, readable blink patterns for key messaging

Player Control: FLASH and SHAKE settings (FULL / REDUCED / OFF) in SettingsPanel

Notes: Effects are brief and tuned for readability; settings included for motion/flash sensitivity

2. Particle Effects

Shield Intercept Shrapnel: spawns at the exact intercept point (top/mid/bottom shield hit location)

Curtain Call Impact Shrapnel: run-complete projectile rain impacts spawn stylized shrapnel bursts

Performance considerations: particles are short-lived; frequent effects use lightweight bursts (no heavy persistent emitters)

3. Audio Improvements (SFX + Music Flow)

Added/expanded SFX across key events: deity entrance suite, intro vocals, countdown/go, shield intercept, life-loss pop chain + culmination, grant sequence, run-complete sequence

Music flow: title music, gameplay music, and dedicated run-complete music swap

SFX toggle compliance: intercept deflect routed through SFX-tagged/shared source so Settings toggle correctly mutes

4. Haptics (Best-effort Prototype)

Implemented: life-loss climax triggers vibration (toggleable)

Player Control: HAPTICS toggle in SettingsPanel

Notes: Verified via editor/debug call path; physical device verification limited by available hardware/testing environment

5. Platform Preparation

App interruptions: implemented auto-pause on focus loss/backgrounding using InterruptionHandler + PauseController

Safe areas: safe-area fitter updated + UI adjusted for cutout/rounded-corner device layout; menus use full-bleed background while UI remains safe

6. Power Unlock Presentation

“God Stunner” (formerly Heavenly Shake): unlock presentation from deity hand → power bar slot + instructional text

Effect: stuns deity + clears projectiles (screen reset tool)

Input: device shake gesture on mobile; editor key path for development/testing

MARKETING ASSETS

App Icon

Design: bold “KAZAP!” wordmark with lightning bolt accent over a clean cyan gradient (high contrast, readable at small sizes)

Sizes: 1024×1024 master exported; adaptive + legacy/round icons assigned in Unity Player Settings

Screenshots

Count: 5 (max)

Platform: Android 1080×1920 portrait

Content: title screen, deity beam entrance, intro line, gameplay chaos with intercept particles, run-complete curtain call

Feature Graphic (Android)

1024×500 banner created using in-game deity visuals + title mark with screentone texture background

Pre-Launch Checklist Status (Prototype)

Technical: mostly complete; emulator-tested; physical low-end device + battery session not tested

Content: placeholder deity sprites + unlicensed music/SFX (prototype only; planned replacement)

Platform-specific: adaptive icons assigned; release signing not performed (prototype build)

Known Issues for Launch / Not Launch-Ready Items

Placeholder deity/projectile sprites currently not original/licensed (planned replacement)

Music/SFX are prototype placeholders and not licensed for commercial release

No privacy policy included (analytics enabled; would be required for real app store submission)

Release signing + full device performance/battery testing not completed
