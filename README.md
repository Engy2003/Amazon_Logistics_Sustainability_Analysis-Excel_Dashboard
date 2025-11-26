# 📦 Amazon Logistics Analysis: Resolving the Speed vs. Sustainability Conflict

![Dashboard Banner](https://github.com/Engy2003/Amazon_Logistics_Sustainability_Analysis-Excel_Dashboard/blob/main/Images/Dashboard.png)

## 📌 The Strategic Challenge
Amazon faces a critical operational paradox that has grown over the last decade: **Operational Speed vs. Environmental Sustainability**. While the company aims for **Net-Zero Carbon by 2040** (The Climate Pledge), balancing hyper-growth with decarbonization remains a massive hurdle.

**The Analysis Scope:**
This project utilizes a **dataset from 2022** containing **43,739 delivery records** to investigate the root causes of this conflict. While this dataset represents a specific historical snapshot, it provides a valuable "micro-cosmos" to model the mechanics of last-mile logistics.

**The Goal:** To analyze this operational data to uncover the hidden trade-offs between delivery speed and carbon footprint, providing data-driven strategies that remain relevant for future network optimization.

---

## 🛠️ Solution Architecture
To derive insights from this dataset, I built an end-to-end analytics pipeline:

* **ETL & Engineering:** Utilized **Excel Power Query (M-Code)** to build a repeatable data cleaning pipeline, solving complex temporal issues (midnight crossing) and engineering geospatial metrics (Haversine Formula).
* **Predictive Modeling (AI):** Deployed **BigML** (Decision Trees) to identify the mathematical drivers of Speed and Emissions, pivoting away from traditional statistical tools to handle real-world noise (Traffic/Weather).
* **Business Intelligence:** Synthesized findings into an interactive **Excel Dashboard** for strategic decision-making.

---

## 🤖 Phase 1: AI-Driven Root Cause Analysis
Before visualizing the data, I used Machine Learning to understand *why* delays and emissions happen.

### 1️⃣ The "Speed" Model (Efficiency)
* **Question:** What actually drives delivery time? Is it just distance?
* **Answer:** The model (**R² = 0.82**) revealed a surprise. **Distance (10%)** is a minor factor. The primary driver is **Category (28.5%)**.
* **Insight:** "Grocery" deliveries are hyper-optimized (avg 26 mins), while "Cosmetics" face massive operational bottlenecks (avg 132 mins).

| Feature Importance | Model Evaluation |
| :---: | :---: |
| ![Time Drivers](https://github.com/Engy2003/Amazon_Logistics_Sustainability_Analysis-Excel_Dashboard/blob/main/Images/First_Model_Field_Importances.png) | ![Time Eval](https://github.com/Engy2003/Amazon_Logistics_Sustainability_Analysis-Excel_Dashboard/blob/main/Images/Evaluation_First_Model.png) |
| *Category & Agent Rating drive speed more than Distance.* | *High accuracy with MAE ~16.9 mins.* |

### 2️⃣ The "Sustainability" Model (Emissions)
* **Question:** Can we isolate the exact source of emissions?
* **Answer:** The model achieved a **Perfect R² (1.00)**.
* **Validation Logic:** This is **not** overfitting; it is a validation of the data engineering process. It proves that the AI successfully "reverse-engineered" the proxy variable logic, confirming that emissions are driven 100% by **Distance** and **Vehicle Choice**, with zero noise from external factors like weather.

| Feature Importance | Model Evaluation |
| :---: | :---: |
| ![Emission Drivers](https://github.com/Engy2003/Amazon_Logistics_Sustainability_Analysis-Excel_Dashboard/blob/main/Images/Second_Model_Field_Importances.png) | ![Emission Eval](https://github.com/Engy2003/Amazon_Logistics_Sustainability_Analysis-Excel_Dashboard/blob/main/Images/Evaluation_Second_Model.png) |
| *Emissions are a pure function of Vehicle & Distance.* | *Validates the proxy variable logic.* |

---

## 📊 Phase 2: The Data Story & Findings
Visualizing the AI findings revealed the core conflict and the solution.

### 📉 The Conflict: Dirty Speed vs. Clean Slowness
The dashboard highlights the trade-off:
* **The Van:** Fastest vehicle (Avg 116 min) ➔ **Highest Polluter (21,588g CO2/trip).**
* **The Bicycle:** Zero Emissions (0g CO2) ➔ **Slower (Avg 127 min).**

### 🚦 The "Golden Scenario" (The Solution)
While Vans are faster on average, the data shows they are extremely vulnerable to congestion.
* In **"Jam" Traffic**, Van efficiency drops by **45.8%**.
* **Critical Finding:** In high-density Metropolitan jams, the **Bicycle** becomes competitive on speed while remaining 100% sustainable.

### ⏳ Hidden Bottlenecks
* The analysis identified a non-logistical delay: An average of **12.20 minutes** is lost in `Preparation_Time` at the store before the driver even begins the journey.

---

## 🚀 Strategic Recommendations
Based on this data-driven analysis, I propose three actionable strategies for Amazon:

1.  **Dynamic "Green" Routing:** Abandon the static dispatch model. Use AI to deploy **Bicycles** specifically in Metropolitan areas during **Rush Hour (Jam)**. In this scenario, they are the optimal vehicle: fastest *and* cleanest.
2.  **Replicate the "Grocery" Blueprint:** The data proves the "Grocery" supply chain is 5x faster than "Cosmetics." Amazon should apply the operational workflows from Grocery to lagging categories.
3.  **Customer-Facing Sustainability:** Leverage the data at checkout. Offer a "Green Choice": *"Get it by 5 PM (Bicycle) and save 21kg of CO2."* This turns sustainability from a cost center into a customer loyalty feature.

---

## 📬 Contact
If you found this analysis interesting, I'd love to discuss it further.

* **Name:** Engy Saeed
* **LinkedIn:** [https://www.linkedin.com/in/engy-saeed2003/](https://www.linkedin.com/in/engy-saeed2003/)
* **Email:** engysead498@gmail.com
