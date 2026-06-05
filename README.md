# webmapping-performance-overlay
Lightweight frame timing and performance diagnostics overlay for interactive web mapping applications.

These samples provide developer insights into rendering performance, frame timing, and runtime behavior directly inside your map application.

---

## 🧭 Overview

This project implements a client-side performance overlay that helps developers analyze how their web mapping application behaves under real-world conditions.

It captures and visualizes key rendering metrics such as:

- Frames per second (FPS)
- Frame time (average)
- Percentiles (p50, p95, p99)
- Tile load / rendering activity
- Environment classification (Excellent, Good, Degraded, Poor, Broken)

The overlay is designed as a **developer tool** for diagnostics, debugging, and environment validation.

---

## 🎯 Motivation

Understanding rendering performance in web mapping applications can be difficult, especially in environments such as:

- Virtual Desktop Infrastructure (VDI)
- Systems without GPU acceleration
- WebGL fallback scenarios
- Low-end or constrained devices

This sample provides a **simple and transparent way** to observe:

- frame stability
- interaction behavior (zoom / pan)
- rendering spikes and jitter
- environment-specific performance characteristics

---

## ⚙️ Features

- ✅ Real-time overlay in the map view
- ✅ Frame timing metrics (avg, p50, p95, p99)
- ✅ Tile count tracking
- ✅ Environment classification (heuristic-based)
- ✅ JSON export for offline analysis
- ✅ Lightweight, no dependencies

---

## 📊 Metrics explained

The overlay focuses on **frame latency**, which directly impacts user experience.

### Frame avg
> Average time per frame.

- Represents overall performance
- Sensitive to slow frames (spikes)

---

### p50 (median)
> Typical frame time.

- What users experience most of the time
- Best indicator of baseline smoothness

---

### p95
> Frame latency under load.

- Shows how the system behaves during interaction
- Higher values indicate instability under stress

---

### p99
> Worst-case frame latency.

- Captures rare spikes or freezes
- Useful for detecting jank, not overall performance

---

## 🧠 Interpretation guidelines

| Pattern | Meaning |
|--------|--------|
| p50 low, p95 low | ✅ Stable, smooth |
| p50 low, p95 moderate | ⚠️ Minor slowdowns under load |
| p50 low, p99 high | ⚠️ Occasional spikes |
| p50 high | ❌ Fundamentally slow system |

---

## 🏷️ Environment classification

The overlay classifies performance into:

- **EXCELLENT**: smooth, stable rendering at vsync
- **GOOD**: minor variance, generally smooth
- **DEGRADED**: noticeable frame drops under load
- **POOR**: severe stuttering
- **BROKEN**: rendering stalled or extremely delayed

⚠️ **Important:**  
Classification is based on heuristics and should be interpreted as a guideline, not a strict benchmark.

---

## 🧪 Example use cases

- Compare performance between:
  - local workstation
  - virtual desktop (VDI)
- Detect rendering throttling
- Analyze WebGL vs Canvas fallback behavior
- Investigate zoom / pan performance
- Identify frame spikes and jitter

---

## 🚀 Live Samples

Try the performance overlay directly in your browser:

👉 [Web GL 2.0 Overlay sample](https://esride.github.io/webmapping-performance-overlay/webgl/)

---

## 🧪 How to use the sample

1. Open the demo link above
2. Interact with the map:
   - zoom in/out
   - pan around
3. Observe the overlay in the top corner:
   - FPS and frame timings
   - p50 / p95 / p99 values
   - environment classification
4. Trigger different scenarios:
   - rapid zoom → observe spikes (p99)
   - idle view → observe stable frame timing
5. Use the **Export JSON** button to download performance data

⚠️ **Important:**  
For meaningful results, ensure the view renders at least **~30 frames**.  
Until then, the overlay displays *"Warming up..."*  
Very small views or short interactions may lead to unstable or non-representative metrics.

---

## 💡 What to look for

- ✅ **Stable system**
  - p50 ≈ 16–17 ms
  - p95 < 20 ms
  - smooth interaction

- ⚠️ **Under load**
  - higher p95 during zoom
  - occasional p99 spikes

- ❌ **Constrained environments (e.g. VDI)**
  - high p50 (>100 ms)
  - very high p95/p99
  - low FPS

---

## 🔍 Tip

Open the same sample in different environments to compare performance:

- local workstation
- virtual desktop (VDI)
- low-end devices

This makes it easy to identify rendering bottlenecks and environment constraints.

---

## 🚀 Getting started

1. Add the custom layer / layer view to your map
2. Enable the overlay
3. Interact with the map (zoom, pan)
4. Observe real-time metrics
5. Export JSON for analysis

---

## 📁 Exported data

The overlay supports exporting performance logs as JSON:

```json
{
  "time": "...",
  "fps": "...",
  "avgFrame": "...",
  "p50": "...",
  "p95": "...",
  "p99": "...",
  "tiles": ...,
  "env": "EXCELLENT"
}