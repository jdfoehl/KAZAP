**Mobile UI System - Week 3 (KAZAP!)**



**Project Overview**

KAZAP! is a portrait-mode, Kaboom-inspired prototype where you drag a shield stack to block falling projectiles while Zeus patrols overhead. This Week 3 milestone focused on building a complete mobile UI flow (Main Menu → HUD → Pause/Settings) that stays readable and usable across aspect ratios, with accessibility settings that persist.



**UI Screens Included (complete flow)**



* **Main Menu**



Title screen with Start and Options



Options opens Settings from the Title screen



* **In-Game HUD**



HUD visible during active gameplay



Pause button opens the Pause Menu



* **Pause / Settings**



Pause menu includes Resume / Settings / Quit to Title



The Settings panel is shared between Title and Pause



Back behavior is context-aware:



If Settings was opened from Title, Back returns to Title



If Settings was opened from Pause, Back returns to Pause



**Canvas Configuration**

Scaler Mode: Scale With Screen Size

Reference Resolution: 1920×1080

Match Value: 0.5

Rationale: This keeps UI scaling consistent across phones and tablets without over-stretching on ultra-wide or 4:3 screens. Match 0.5 balances width/height scaling so the layout remains stable at the required ratios. These settings are used across all three UI screens.



**Anchoring Decisions**



* **Main Menu**



Title anchored top-center so it remains visually centered on any width



Start and Options placed as a centered vertical stack for consistent one-handed access



Settings panel centered as an overlay so the interaction zone stays consistent



* **In-Game HUD**



Pause button anchored top-right (infrequent action, kept away from the main thumb zone)



Core gameplay text kept in safe regions so it never drifts off-screen at extreme ratios



* **Pause / Settings**



Full-screen overlay panel for clarity and focus



Button stack and settings controls center-anchored so spacing remains consistent at 16:9, 19.5:9, and 4:3



**Touch Target Sizing**

All interactive elements were kept at or above the 60×60px minimum guideline (with extra padding and spacing to prevent mis-taps). Primary actions (Start/Resume) were intentionally oversized. Spacing between interactive elements was kept at or above ~10px to reduce accidental taps.



**Accessibility Features Implemented (2)**



1. **Text Scaling**



Settings slider scales UI text for readability



Range tuned for mobile: 75% to 125%



125% was chosen because anything larger caused unnecessary overflow and reduced clarity



Persists across sessions via PlayerPrefs



**2. Audio Toggles**



Music toggle mutes/unmutes all AudioSources tagged Music (Title + Gameplay music)



SFX toggle mutes/unmutes all AudioSources tagged SFX (projectile spawn SFX, etc.)



Both toggles persist across sessions via PlayerPrefs



Verified to remain correct through:



gameplay → pause → resume



gameplay → quit to title → start a new run



exiting Play Mode and re-entering Play Mode



**Responsive Design Notes**

Tested UI at the three required aspect ratios:



16:9 (1920×1080 / 1280×720)



19.5:9 (2340×1080 / 2532×1170 style)



4:3 (1024×768 / 2048×1536 style)



Testing these ratios pushed the layout toward centered vertical stacks for menu flow, and corner/safe-region anchors for HUD elements, so nothing drifts or becomes awkwardly spaced on wide or square displays.



**Testing Notes**



Tested in Unity Game View using multiple aspect ratios/resolutions



Verified touch target usability visually across phone/tablet ratios



Verified audio toggles and persistence across full UI flow and play mode restart



**Known Issues**

None observed for UI flow, settings persistence, or audio toggles.



Repo Contents (Week 3)



Main Menu UI + scripts



HUD UI + scripts



Pause/Settings UI + scripts



Accessibility: Text scaling + Music/SFX toggles (persisted)



At least one playable scene demonstrating full UI flow

