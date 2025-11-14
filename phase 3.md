# **Phase 3 — Exploratory Analysis Outline (Optional)**

**Objective:**  
Sketch the next analytical directions building on Phase 1’s data mapping. Focus on how emissions, geography, and tax policy jointly shape Norway’s vehicle scrappage and EV transition.

---

### **1️⃣ Emission Intensity Trends in the Scrapped Fleet**

**Goal:** Track how clean the scrapped vehicles have become over time.  
**Data:** `REGTEK_data_25.02.2025.parquet` → CO₂, NOₓ, fuel, registration, and scrap dates.  
**New dataset:** `scrap_lifetime_analysis.csv` — add vehicle lifetime = (scrap date − registration date).  

**Approach:**  
- Aggregate average CO₂ and NOₓ by scrap year and fuel type.  
- Examine how lifetime and emission levels evolve under new policy periods.  

**Expectation:**  
Post-2008 scrapped cars emit less CO₂/NOₓ and show shorter lifetimes as clean-fleet turnover accelerates.

---

### **2️⃣ Regional Variation and Incentive Geography**

**Goal:** Assess how tolls and local conditions affect scrappage and EV adoption.  
**Data:** `muni_route_tollroadprice.csv`, `ownermuni.csv`, `REGTEK_data`,  
`ssb_fuel_prices.csv`, `ssb_electricity_prices.csv`.  

**Approach:**  
- Compute mean toll cost per municipality per year.  
- Merge with EV share (fuel code 5) and mean scrapped CO₂.  
- Compare EV and diesel scrappage trends across high- vs low-toll areas.  

**Expectation:**  
Urban, high-toll regions show faster diesel retirement and higher EV shares; rural areas lag behind.

---

### **3️⃣ Tax Design Shifts and Scrapping Patterns**

**Goal:** Explore how Norway’s tax reform (weight/power → CO₂/NOₓ) changed which cars were scrapped.  
**Data:** `vehicle_taxes.csv`, `REGTEK_data`, `scrap_lifetime_analysis.csv`.  

**Approach:**  
- Tag scrap years by tax regime:  
  - 1980–2006 = traditional;  
  - 2007–08 = transition;  
  - 2009+ = CO₂-based.  
- Compare average scrapped weight, CO₂, NOₓ, and lifetime across regimes.  

**Expectation:**  
After 2008, heavier and dirtier vehicles leave the fleet faster; scrapped lifetimes shorten slightly.

---

### **4️⃣ Integration and Next Steps**

`scrap_lifetime_analysis.csv` becomes the key linking dataset across emissions, geography, and taxation.  
Together, these analyses would show:  
- **Environmental progress** (declining CO₂/NOₓ).  
- **Spatial inequality** (urban vs rural turnover).  
- **Policy effectiveness** (tax and toll incentives accelerating clean-fleet renewal).  

**Deliverable:**  
A short conceptual roadmap — not new plots yet — describing how these analyses would build toward evaluating Norway’s environmental vehicle policy impact.

