# TCP Timing Lab 02  
## Serialization vs Throughput
> Throughput drops. Serialization does not.  

A measurement-driven study showing that serialization delay is fixed while throughput collapses due to time discontinuity (packet gaps).

---

## 📌 Overview

In Lab01, we showed that **serialization delay is a fixed physical property** of the link.

In this lab, we demonstrate something counterintuitive:

> Even when serialization delay remains constant,
> **throughput can collapse dramatically.**

---

## 🎯 Objective

* To show that:

  * **Serialization delay (Δt)** remains constant
  * **Throughput** varies significantly
* To explain:

  * Why throughput drops even when link speed is unchanged
  * How **packet train discontinuity (gaps)** destroys throughput

---

## 🧠 Key Insight

> **Throughput is not the speed of packets.
> It is the density of packet transmission over time.**

---

## 🧪 Experiment Scenario

* Environment: **10 Mbps FDX**
* Traffic: **Dual-flow curl download**
* Method:

  * Extract one long-lived TCP stream
  * Observe:

    * Inter-frame timing (Δt)
    * Throughput over time

---

## 📊 Evidence 1 — Serialization Delay is Still Fixed

![Serialization Delay Observation](./your-wireshark-image.png)

### Observation

* Frame size: **1518 bytes**
* Inter-frame spacing:

```text
Δt ≈ 0.00123 s (1.23 ms)
```

✔ Matches theoretical serialization delay at 10 Mbps

---

### Interpretation

> The link is still transmitting at full physical rate.

Nothing is “slowing down” at the wire level.

---

## ⚠️ Critical Observation — The Gaps

Inside the same trace:

* Repeated **empty intervals (gaps)** appear
* No data frames are transmitted during these periods

---

## 📊 Evidence 2 — Throughput Collapse

![Throughput Graph](./your-throughput-image.png)

### Observation

* Around **8.3 seconds**:

  * Throughput drops to **< 2 Mbps**
* Sustained oscillation at low throughput level

---

## 🔍 What Changed?

| Factor              | Status       |
| ------------------- | ------------ |
| Link Speed          | ❌ unchanged  |
| Serialization Delay | ❌ unchanged  |
| Frame Size          | ❌ unchanged  |
| Packet Timing (Δt)  | ❌ unchanged  |
| Packet Continuity   | ✅ **broken** |

---

## 💥 Core Explanation

> **Throughput collapses not because packets are slower,
> but because packets stop arriving continuously.**

---

### Visualization

```text
Ideal Packet Train:
|----|----|----|----|----|----|----|

Actual Transmission:
|----|----|      |----|   |----|      |
           gap        gap
```

---

## 🧩 The Real Meaning

This experiment reveals a deeper truth:

> **The network is governed by time structure, not rate.**

---

### Two Layers of Reality

#### 1. Physical Layer (Fixed)

* Serialization delay
* Link speed
* Bit transmission

#### 2. Behavioral Layer (Dynamic)

* ACK clock
* Loss / recovery
* Scheduling gaps
* Flow control

---

## ⚠️ Common Misconception

❌ “Throughput reflects link speed”
❌ “Low throughput means slow transmission”

---

✅ Reality:

> **Throughput = how often packets are sent,
> not how fast a packet is sent**

---

## 📐 Mathematical View

Let:

```text
Serialization Delay = L / R
```

This is constant.

---

But:

```text
Throughput ≈ Data / (Serialization + Idle Time)
```

---

👉 When **Idle Time increases**, throughput collapses.

---

## 🔬 Engineering Insight

These gaps are typically caused by:

* ACK clock disruption
* Packet loss / retransmission
* Receiver window limitation
* Scheduling / queueing behavior

---

> The wire is ready.
> The sender is not.

---

## 🚀 Why This Lab Matters

This lab breaks a critical illusion:

> **Bandwidth is not throughput.**

It lays the foundation for understanding:

* TCP self-clocking
* Congestion control
* ACK-driven transmission
* Throughput anomalies

---

## 🔗 Next Lab

👉 **Lab 03 — ACK Clock**

> If throughput depends on timing,
> what controls that timing?

---

## 📖 Closing Thought

> **A packet takes 1.23 ms to be transmitted.
> But nothing forces the next packet to follow.**

---

## ⭐ Repository Status

Work in progress — diagrams and annotated traces will be refined.
