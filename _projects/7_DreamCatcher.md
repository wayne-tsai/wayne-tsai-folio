---
layout: page
title: DreamCatcher
description: Intent-Based 5G Network Slice Controller for Automatic Real-Time Quality of Experience Optimization
img: assets/img/banner-dreamcatcher.png
importance: 1
category: work
---
{% include figure.html path="assets/img/banner-dreamcatcher.png" title="DreamCatcher" class="img-fluid rounded z-depth-1" %}
Sponsored by T-Mobile.

**Basic Information**
- Team Size: 3
- Duration: 6-Month (Sep 2025 – Mar 2026)
- My Role: Software Engineer (sole engineer, alongside a PM and designer)

**Problem Addressed**

Modern 5G networks support network slicing — partitioning a physical network into virtual slices with distinct QoS profiles — but realizing this capability's full benefit requires knowing *which slice should be active at any given moment*. Without automatic intent detection, operators rely on static, manually configured policies that cannot respond to real-time traffic changes. The result is degraded quality of experience (QoE) when latency-sensitive workloads like video calls, gaming, or live streaming compete with background traffic on the wrong network slice. DreamCatcher addresses this by making slice management intent-aware and fully automatic.

**Personal Contributions**

As the sole engineer on a cross-functional team of three, I was responsible for the full technical scope of DreamCatcher — from low-level network traffic analysis to user-facing dashboards. I designed and built all four components end-to-end: the Python-based deep packet inspection bridge using NFStream and nDPI, the TypeScript/Ink terminal UI, the Node.js WebSocket telemetry backend, and both React dashboards. I also architected the modular ingest pipeline so each component could run independently or compose into a full-stack live demo, enabling reliable presentations regardless of available hardware.

**Solutions Developed & Impact**

DreamCatcher is a four-component system that detects network intent from live traffic and acts on it in real time — no manual intervention required.

- **Terminal UI (TUI)** — A fullscreen Ink/React terminal application that monitors live traffic via deep packet inspection (NFStream + nDPI), classifies flows by intent (real-time calls, gaming, streaming, background), and triggers WAN priority switches via the pfSense API the moment high-priority traffic is detected. Color-coded flow tables, live metric sparklines, and a timestamped switch log give operators immediate situational awareness.
- **Node.js Backend** — A REST and WebSocket telemetry hub that aggregates live metrics (latency, jitter, packet loss, throughput via ICMP ping) and slice state, pushing a tick every second to connected dashboards. Supports two ingest modes: a built-in 41-second scripted scenario for reliable demos, or live event forwarding from the TUI.
- **Business Dashboard** — A React/Recharts web dashboard showing the measurable QoE improvement after each slice switch: quality-over-time charts with annotated before/after markers, live metric cards, workflow state visualization, and business impact summaries.
- **End-User Dashboard** — A consumer-facing React dashboard for the 5G smart router, displaying current activity, active slice, performance metrics, priority configuration, and an optimization log.

The system handles the full detection-to-action pipeline — Detect → Switch → Stabilize → Cooldown → Revert — in under 3 seconds in demo conditions, and is architected to run each component independently or as a unified full-stack demo.

**Tech Stack**

| Component | Stack |
|---|---|
| Backend | Node.js, Express, WebSocket (`ws`), ICMP ping |
| Business Frontend | React 18, Vite, Recharts |
| User Frontend | React 18, Vite |
| TUI | TypeScript, Ink (React for terminals) |
| Traffic Inspection | Python, NFStream, nDPI, scapy, psutil |

**Learning Outcomes & Reflections**

DreamCatcher pushed me into areas I had not worked in before — real-time network telemetry, deep packet inspection, and the operational realities of 5G slicing infrastructure. Building the TUI with Ink reinforced that terminal interfaces can be as expressive and user-friendly as web dashboards when the data warrants it. Architecting the system to decouple components (each runnable in demo mode without hardware dependencies) was a deliberate choice that paid off repeatedly during stakeholder demos, and it sharpened my instincts for designing software that stays demonstrable even when infrastructure is unavailable. Collaborating as the sole engineer alongside a PM and designer also gave me practice translating product requirements directly into technical decisions without an intermediary.

**Demo Video**

<p align="center">
<iframe width="640" height="360" src="https://www.youtube.com/embed/PLu448h1vno" title="DreamCatcher Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</p>
