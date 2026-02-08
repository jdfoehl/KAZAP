Week 4 Optimization Documentation

Baseline Performance

Device: Android Studio Emulator (Google SDK gphone64 x86_64 / emulator-5554). Development was done on Windows PC; physical device testing was not possible due to owning an iPhone and not having access to Xcode/macOS.

FPS: Not recorded (Profiler capture focused on frame timing and subsystem breakdown)

Frame Time (Profiler Analyzer): Mean 33.45 ms, Max 43.50 ms

Draw Calls (Rendering module): 15

Memory (Memory module): Total Used 309.3 MB (Texture 91.6 MB, Audio 33.4 MB)

Important Pre-Baseline Change (Input System)
Before capturing baseline numbers, the project was switched from “Both” input handling to the New Input System (Unity warning indicated “Both” could impact performance). After the switch, gameplay immediately became smoother and prior issues (notably audio/throttling behavior) resolved. Memory usage also dropped dramatically compared to the earlier mid-week profiling snapshot (~2.19 GB Total Used Memory).

Optimizations Implemented

Background Sprite Import Optimization (Memory / Texture Reduction)

Issue: Higher-than-expected memory usage for a simple prototype, with texture memory notably high.

Solution: Reduce background sprite memory footprint by lowering max size + using platform compression settings.

Implementation: Updated three background sprite assets:

BG Fill: ASTC 8×8

BG Gradient: ASTC 6×6

BG Xanadu: ASTC 6×6

Result (Baseline → After Opt 1):

Total Used Memory: 309.3 MB → 287.2 MB (-22.1 MB)

Texture Memory: 91.6 MB → 71.1 MB (-20.5 MB)

CPU breakdown improved slightly in scripts/render/physics during the sampled frame.

Bolt Object Pooling (Runtime Stability / Reduced Instantiate/Destroy)

Issue: Frequent bolt spawning/despawning can cause spikes and runtime instability due to Instantiate/Destroy overhead.

Solution: Implement object pooling for bolts to reuse instances instead of creating/destroying repeatedly.

Implementation: Added a BoltPool system and updated bolt spawning flow to pull from the pool and return bolts when resolved.

Result (After Opt 1 → After Opt 2):

Mean frame time: 33.44 ms → 33.55 ms (roughly unchanged)

Max frame time: 43.98 ms → 42.54 ms (improved worst frame)

Scripts: 1.93 ms → 1.97 ms (roughly flat)

Physics: 0.03 ms → 0.03 ms (unchanged)

Total Used Memory: 287.2 MB → 287.5 MB (flat)

Practical impact: smoother/cleaner long runs (pooling improves stability even when averages don’t move much).

Performance Comparison (Baseline vs Final After Opt 2)

Metric | Baseline | After Opt 2 | Change
FPS | Not recorded | Not recorded | —
Mean Frame Time (ms) | 33.45 | 33.55 | ~flat
Max Frame Time (ms) | 43.50 | 42.54 | improved
Draw Calls | 15 | 14 | -1
Total Used Memory (MB) | 309.3 | 287.5 | -21.8
Texture Memory (MB) | 91.6 | 71.1 | -20.5

Remaining Issues / Future Optimization

The CPU sample is dominated by Rendering time (~30 ms in captures), so further FPS improvements would likely require reducing render cost (sprite batching/material consistency, atlas use, overdraw reduction, UI layout efficiency).

Measurements were taken on an emulator; next step would be confirming behavior in a development build and (if possible later) validating on a physical Android device.
