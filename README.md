# TCP Timing Lab 02  
## Serialization vs Throughput
> Throughput drops. Serialization does not.  

A measurement-driven study showing that serialization delay is fixed while throughput collapses due to time discontinuity (packet gaps).

---

## 📌 Overview

In Lab01, we showed that serialization delay is a fixed physical property.

In this lab, we demonstrate:

> Even when Δt remains constant,  
> **throughput can collapse due to gaps in packet transmission.**

---

## 🧠 Key Insight

> **Throughput is the density of packets over time.**

---

## 📊 Core Evidence

### Fixed Serialization Delay

Δt ≈ 1.23 ms (constant)

---

### Packet Train Disruption

Gaps appear → continuity breaks

---

### Throughput Collapse

↓ drops below 2 Mbps

---

## 🧩 Core Idea

```text
Serialization (fixed)
        ↓
Packet Train (broken by gaps)
        ↓
Throughput Collapse

