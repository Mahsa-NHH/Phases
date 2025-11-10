# Vehicle Scrapping and Environmental Policy

**Phase 2 — Emission Composition and Reconstruction**  
Author: **Mahsa Gorji**  
Supervisor: **Morten Sæthre**  
Project: **ERC-DEEP — Distributional Effects of Environmental Policy**

---

## Objective

This phase outlines the method for reconstructing **CO₂** and **NOₓ** emissions for vehicles in the NPRA registry (`REGTEK_data_25.02.2025.dsv`) that lack these variables—mainly older models. The framework ensures full emission coverage and supports **lifetime emission estimation** when linked with odometer data.

---

## Data Inputs

| Category | Dataset | Key Variables | Purpose |
|-----------|----------|----------------|----------|
| **Main registry (NPRA)** | `npra/REGTEK_data_25.02.2025.dsv` | `TEKN_MERKE`, `TEKN_MODELL`, `TEKN_DRIVSTOFF`, `TEKN_SLAGVOLUM`, `TEKN_EGENVEKT`, `TEKN_CO2_UTSLIPP`, `TEKN_NOX_UTSLIPP_MGPRKM`, `TEKN_VRAKET_DATO`, `TEKN_REG_F_G_N`, `TEKN_KJM` | Core vehicle-level data |
| **Emission reference (OFV)** | `ofv/cars_full.pq` | `brand`, `model`, `regdate`, `fuel`, `co2` | Primary CO₂ source by make–model–year |
| **Fallback (VCA)** | `utility/vca_YYYY.csv` | `Manufacturer`, `Model`, `Fuel Type`, `Engine Capacity`, `WLTP CO2`, `WLTP Metric Combined`, `Emissions NOx [mg/km]` | EU type-approval data for missing cases |
| **Auxiliary mapping** | `REGTEK_data_codes_descriptions_NO.xlsx`, `REGTEK_data_field_descriptions_NO.xlsx`, `npra/REG_brandcodes.csv`, `npra/cartypg.csv` | — | Codebooks and field mappings |
| **Odometer** | `npra/odometer/odometer.csv` | `regnr`, `date`, `km` | Lifetime mileage for emission calculation |

---

## Method Overview

Reconstruction follows four layers: direct match, fallback match, statistical clustering, and validation.

### Direct Match (OFV)

Link NPRA and OFV data by make, model, year, and/or fuel to retrieve CO₂ and NOₓ. Use the mean of multiple matches per make–model–year group.

| NPRA Field | OFV Field | Match Logic |
|-------------|------------|--------------|
| `TEKN_MERKE` | `brand` | string match |
| `TEKN_MODELL` | `model` | string match |
| `TEKN_REG_F_G_N` | `regdate` | first registration in Norway |
| `TEKN_DRIVSTOFF` | `fuel` | harmonized code |

### Fallback (VCA)

Focus on relevant emission columns: **`WLTP CO2`**, **`WLTP Metric Combined`** for CO₂, and **`Emissions NOx [mg/km]`** for NOₓ.

| NPRA Field | VCA Field | Match Logic |
|-------------|------------|--------------|
| `TEKN_MERKE` | `Manufacturer` | string match on brand/make |
| `TEKN_MODELL` | `Model` | string match on model name |
| `TEKN_DRIVSTOFF` | `Fuel Type` | harmonized fuel code |
| `TEKN_SLAGVOLUM` | `Engine Capacity` | numeric match (convert cc → L if needed) |
| `TEKN_EGENVEKT` | — | optional for closer match |

If multiple matches exist, average across the closest engine-size or fuel-type group.

### Cluster-Based Estimation

For cars still missing data, group by **fuel type × engine size × weight**, then assign cluster means of CO₂ and NOₓ.

| Fuel | Engine (L) | Weight (kg) | Avg CO₂ (g/km) | Avg NOₓ (g/km) |
|------|-------------|-------------|----------------|----------------|
| Petrol | ≤1.4 | ≤1100 | 160 | 0.08 |
| Petrol | 1.4–2.0 | 1100–1400 | 180 | 0.09 |
| Diesel | 1.6–2.0 | 1300–1700 | 145 | 0.26 |

## Supplementary Source: SSB Data

SSB (Statistics Norway) vehicle and emission statistics can serve as an auxiliary source to support or cross-check imputed CO₂ and NOₓ values. Historical SSB emission factors by fuel type and year can be used to benchmark cluster averages and ensure realistic levels, especially for pre-1990 vehicles.

### Validation

CO₂ should increase with engine size and weight; diesel cars should emit more NOₓ than petrol; EVs ≈ 0. Anomalies signal matching or clustering issues.

---

## Example Logic

```python
if TEKN_CO2_UTSLIPP is NA:
    match = find_OFV(TEKN_MERKE, TEKN_MODELL, TEKN_REG_F_G_N)
    if not match:
        match = find_VCA(Manufacturer, Model, FuelType, EngineSize_L)
    if not match:
        match = cluster_mean(TEKN_DRIVSTOFF, TEKN_EGENVEKT, TEKN_SLAGVOLUM)
    TEKN_CO2_UTSLIPP = match.CO2
```

| Make | Model | Year | Fuel | CO₂ (g/km) | NOₓ (mg/km) | Source |
|------|--------|------|------|-------------|--------------|---------|
| TOYOTA | COROLLA | 1999 | Petrol | 165 | 90 | OFV |

---

## Linking to Odometer Data

Join `odometer.csv` and NPRA data using `regnr` (odometer) ≈ `TEKN_KJM` (NPRA license plate).

1. Keep valid odometer values only.  
2. Select the **last odometer entry (`date`) before the scrapping date (`TEKN_VRAKET_DATO`)**.  
3. Use CO₂ (`TEKN_CO2_UTSLIPP`) and NOₓ (`TEKN_NOX_UTSLIPP_MGPRKM`) values valid at that date.  
4. Use this `km` value—the total distance driven—to calculate lifetime emissions:  
   - Lifetime CO₂ = `TEKN_CO2_UTSLIPP × km`  
   - Lifetime NOₓ = `TEKN_NOX_UTSLIPP_MGPRKM × km`

This ensures emissions and odometer readings align at the scrapping date for accurate lifetime totals.

---

## Deliverables

- Phase 2 Method Note (this document)  
- Description of imputation and linkage logic  
- Example table and pseudo-code  

---

## Expected Outcome

All scrapped vehicles will have harmonized CO₂ and NOₓ values and lifetime emission estimates, supporting further ERC-DEEP analysis on fleet turnover and environmental policy impacts.

---

