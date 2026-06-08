# Leaflet Performance Overlay

Lightweight frame timing and rendering diagnostics overlay for Leaflet and Esri Leaflet applications.

This sample provides real-time developer-focused insights into:
- interaction smoothness
- tile loading behavior
- frame timing stability
- rendering consistency across environments

---

# 🧭 Overview

Unlike the ArcGIS Maps SDK implementation, Leaflet does not expose an internal renderer loop.

This sample therefore approximates rendering performance using:
- `requestAnimationFrame()`
- tile lifecycle timing
- viewport tile calculations
- interaction stabilization timing

The overlay is intended as a lightweight diagnostics tool for:
- browser comparison
- regression detection
- VDI analysis
- interaction smoothness evaluation

---

# ⚠️ Important Measurement Differences

This implementation is conceptually comparable to the ArcGIS Maps SDK sample, but the measurements are not mathematically identical.

| Framework | Measurement Source |
|---|---|
| ArcGIS Maps SDK | Internal renderer loop |
| Leaflet | Browser animation frame cadence |

Because Leaflet relies on browser-driven rendering:
- FPS values are observational
- frame timings are approximate
- classifications are heuristic-based

The overlay measures perceived interaction responsiveness rather than direct renderer workload timing.

This distinction is important when comparing metrics across frameworks.
