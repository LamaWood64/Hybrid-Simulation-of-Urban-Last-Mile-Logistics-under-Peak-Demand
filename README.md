# 📦 Last-Mile Delivery Network Simulation

A hybrid DES+ABM simulation model analyzing a two-hub last-mile delivery system with 20 customer zones. The model compares performance under normal and peak demand, showing how a +100% order volume affects delivery times, queue lengths, and resource utilization.

---

## 🎯 Key Objectives

- Compare operational efficiency: Normal Day (6 orders/hour per hub) vs Peak Day (12 orders/hour per hub, +100%)
- Identify bottlenecks in last-mile delivery
- Quantify impact of demand surges on service quality
- Provide data-driven recommendations for capacity planning

---

## 🏗️ Model Architecture

**System Flow:**  
Central Warehouse → 2 Micro-Hubs → 20 Customer Zones

- **HUB1:** customers 1–10, 5 couriers  
- **HUB2:** customers 11–20, 5 couriers  

**Agent Classes:**  

- **Order Agents:** customer_id (1–20), hub_id (1–2), creation_time  
- **Resource Pools:** couriers_hub1, couriers_hub2 (5 each)

**Process Flow:**  
`Source → Queue → Seize(Courier) → Delay(Delivery) → Release → Sink`

---

## ⚙️ Key Parameters

- **Delivery Times:** Triangular (4, 10, 20) minutes  
- **Order Rates:**  
  - Normal Day: 0.1 orders/min per hub  
  - Peak Day: 0.2 orders/min per hub (+100%)  
- **Simulation Duration:** 480 min (8h) or 1440 min (24h)

**Metrics Collected:**  

- **Delivery Times:** avg/min/max  
- **Queue Waiting Times:** vs transit times  
- **Courier Utilization:** occupancy and productivity  
- **System Efficiency:** orders delivered/hour, backlog, % undelivered

**Data Collection:**  

- Real-time: TimePlot for queue dynamics  
- Post-simulation: Statistics objects  
- Detailed per-order logging

---

## 🚀 How to Run

**Requirements:**  
- AnyLogic 8+ Professional/University  
- Java 8+ runtime

**Steps:**  

1. Open `LastMileDelivery.ajp`  
2. Select Scenario:  
```java
// Normal Day
order_source_hub1.set_rate(0.1);
order_source_hub2.set_rate(0.1);

// Peak Day
order_source_hub1.set_rate(0.2);
order_source_hub2.set_rate(0.2);
