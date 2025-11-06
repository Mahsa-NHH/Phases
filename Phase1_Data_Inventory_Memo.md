**Vehicle Scrapping and Environmental Policy: Phase 1 Data Inventory Memo**

**Author:** Mahsa Gorji\
**Supervisor:** Morten Sæthre\
**Project:** ERC-DEEP — Distributional Effects of Environmental Policy

---

### 1. Objective and Context

This phase maps and assesses Norwegian vehicle scrappage data to evaluate coverage, completeness, and suitability for studying environmental and distributional effects. It uses NPRA registry data and linked odometer and emission records.

---

### 2. Data Sources and Coverage

The main data backbone is the **Norwegian Public Roads Administration (NPRA) motor vehicle registry**, which contains all vehicle registrations and technical characteristics since the early 1980s. Complementary data sources include odometer readings, emissions datasets, and policy variables derived from national and municipal records. This memo highlights the core datasets relevant for Phase 1 analyses.

**Summary of Data Completeness by Vintage**

| Decade | Registry    | Odometer | CO₂                     | NOₓ    |   |
| ------ | ----------- | -------- | ----------------------- | ------ | - |
| 1980s  | Partial     | 0        | 0                       | 0      |   |
| 1990s  | Nearly full | <5%      | 0-10%                   | 0      |   |
| 2000s  | Full        | >60%     | 40-70%                  | 10-60% |   |
| 2010s  | Full        | >95%     | 20-70%                  | 40-60% |   |
| 2020s  | Full        | >90%     | 10–20% (reporting lag)  | 10-40% |   |

The registry achieves near-universal vehicle coverage by the mid-1990s. Emission variables become consistently available after the mid-2000s, coinciding with EU harmonization of CO₂ reporting. Odometer readings reach comprehensive coverage after 2004, reflecting the introduction of digital inspections under the EU’s roadworthiness framework. Consequently, the dataset is robust enough for detailed analysis from approximately 1995 onward.

---

### 3. Scrapping Data Characterization

Phase 1 visual diagnostics focused on understanding the timing and composition of scrapped vehicles. The following figures document scrapping coverage and lifetime dynamics:

- [Fig. 1: scrap_trend_by_fuel_logscale_all20.png](Plot/scrap_trend_by_fuel_logscale_all20.png)
- [Fig. 2: scrap_lifetime_trend_by_year_all20.png](Plot/scrap_lifetime_trend_by_year_all20.png)
- [Fig. 3: scrap_lifetime_by_decade.png](Plot/scrap_lifetime_by_decade.png)
- [Fig. 4: scrap_lifetime_plot_by_fuel.png](Plot/scrap_lifetime_plot_by_fuel.png)
- [Fig. 5: box_lifetime_years_by_fuel.png](Plot/box_lifetime_years_by_fuel.png)
- [Fig. 6: hist_lifetime_years_all_scrapped.png](Plot/hist_lifetime_years_all_scrapped.png)

The long-term evolution of scrappage patterns (Figs. 1–6) shows that gasoline vehicles dominated the Norwegian fleet until around 2010. Diesel scrappage rose sharply through the 2010s and peaked around 2018, reflecting urban diesel restrictions and falling resale values. The number of electric and hybrid scrappages remains low in absolute terms but is increasing rapidly.

Median lifetimes show only modest declines since 2000 (Figs. 2–4): gasoline vehicles average about **16 years** before scrappage, diesel around **16–17 years**, and EVs about **6–7 years**, mainly reflecting their young fleet age rather than premature failure.

The figures by registration decade and scrappage year (Figs. 3–4) reveal clear generational changes: cars registered in the early 1990s tend to survive longer than those from the mid-2000s, with lifetimes shortening more quickly after the 2007–2008 CO₂-based tax reform, which encouraged faster turnover toward newer, cleaner, and more efficient models.

---

### 4. Vehicle Characteristics at Scrapping

The composition of scrapped vehicles provides insight into which types of cars exit the fleet first. Relevant figures include:

- [Fig. 7: scrapped_vehicle_characteristics_trend.png](Plot/scrapped_vehicle_characteristics_trend.png)
- [Fig. 8: box_TEKN_CO2_UTSLIPP_by_fuel.png](Plot/box_TEKN_CO2_UTSLIPP_by_fuel.png)
- [Fig. 9: box_TEKN_NOX_UTSLIPP_MGPRKM_by_fuel.png](Plot/box_TEKN_NOX_UTSLIPP_MGPRKM_by_fuel.png)
- [Fig. 10: box_TEKN_MOTORYTELSE_by_fuel.png](Plot/box_TEKN_MOTORYTELSE_by_fuel.png)
- [Fig. 11: box_TEKN_EGENVEKT_by_fuel.png](Plot/box_TEKN_EGENVEKT_by_fuel.png)
- [Fig. 12: box_TEKN_SLAGVOLUM_by_fuel.png](Plot/box_TEKN_SLAGVOLUM_by_fuel.png)
- [Fig. 13: kde_lifetime_years_by_fuel.png](Plot/kde_lifetime_years_by_fuel.png)
- [Fig. 14: kde_TEKN_CO2_UTSLIPP_by_fuel.png](Plot/kde_TEKN_CO2_UTSLIPP_by_fuel.png)
- [Fig. 15: scrap_top_models_bar.png](Plot/scrap_top_models_bar.png)
- [Fig. 16: scrap_brands_trend.png](Plot/scrap_brands_trend.png)

Across decades, the average scrapped car has become heavier and more powerful (Figs. 7–14), mirroring Norway’s shift toward larger vehicle classes such as SUVs and plug-in hybrids. Electric vehicles have the lowest engine displacement and relatively low weight, while gas-, CNG-, and ethanol-fueled vehicles are the largest and heaviest. At scrappage, CO₂ and NOₓ emissions follow predictable fuel-type patterns: gasoline vehicles emit more CO₂, diesel vehicles emit far more NOₓ, and EVs produce nearly zero emissions.
Additional figures (Figs. 15–16) summarize scrappage patterns by vehicle brand and model. Volkswagen’s Passat and Golf, and Toyota Corolla appear most frequently due to their long-standing presence in the Norwegian fleet. Brand-level trends show Ford, Opel, and Volkswagen consistently dominating scrappage volumes since the 1990s. These patterns mirror long-term registration data from NPRA and OFV, confirming that the most sold brands over decades also account for the largest share of vehicles retired from the fleet [(OFV, The Norwegian Car Market 2024)](https://opplysningsraadet-for-veitrafikk-ofv.s3.amazonaws.com/pdf/Bil%C3%A5ret-2024_Norwegian-Car-Market-2024_English-version.pdf).
---

### 5. Linkage and Data Completeness

A crucial task in Phase 1 was to assess how well technical and usage datasets link across time. The following figures document completeness trends and missingness patterns:

- [Fig. 17: odometer_coverage_trend.png](Plot/odometer_coverage_trend.png)
- [Fig. 18: plot_phase1_missingness_corrected.png](Plot/plot_phase1_missingness_corrected.png)
- [Fig. 19: emission_data_completeness_trend_by_year.png](Plot/emission_data_completeness_trend_by_year.png)
- [Fig. 20: emission_data_completeness_trend_by_decade.png](Plot/emission_data_completeness_trend_by_decade.png)
- [Fig. 21: emission_missing_vintages_plot.png](Plot/emission_missing_vintages_plot.png)
- [Fig. 22: emission_all_emission_variables_trend.png](Plot/emission_all_emission_variables_trend.png)

Odometer coverage (Fig. 17) rose sharply after the early 2000s, coinciding with the rollout of the centralized vehicle inspection database. By 2010, over 90% of scrapped vehicles included at least one odometer reading, enabling reliable lifetime usage estimates.

Emission data completeness improves with vehicle vintage (Figs. 19–22): both CO₂ and NOₓ values begin to appear in the late 1990s and become systematic through the 2000s, consistent with the implementation of Euro 3 and subsequent EU type-approval reporting requirements. Missingness diagnostics (Fig. 18) confirm that vehicles lacking emission data are primarily older gasoline models and smaller vehicles, reflecting early data gaps rather than selective reporting.

**Overview of External Datasets to Fill Emission Gaps**\
To achieve complete emission coverage in later analyses, additional datasets are available:

- **OFV registration files** (1994–2022) providing CO₂ and NOₓ by make–model–year.
- **VCA certification data** (`utility/vca_YYYY.csv`) containing type-approval emission values linked to Euro standards.
- **Cluster-based imputation approach**: where specific model data are missing, CO₂ and NOₓ will be approximated based on engine displacement, curb weight, and fuel type (details developed in Phase 2).

---

### 6. Policy and Incentive Mapping

The Norwegian policy environment experienced major shifts between the 1980s and 2020s, which have direct implications for scrapping incentives. The following plots summarize these developments:

- [Fig. 23: tax_components_timeline.png](Plot/tax_components_timeline.png)
- [Fig. 24: fuel_price_trend.png](Plot/fuel_price_trend.png)
- [Fig. 25: map_toll_costs_2023_lines_fixed.png](Plot/map_toll_costs_2023_lines_fixed.png)
- [Fig. 26: toll_map_animation_better.webm](Plot/toll_map_animation_better.webm)
- [Fig. 27: scatter_ev_vs_toll.png](Plot/scatter_ev_vs_toll.png)
- [Fig. 28: toll_vs_income_scatter.png](Plot/toll_vs_income_scatter.png)
- [Fig. 29: ev_share_and_models_trend.png](Plot/ev_share_and_models_trend.png)
- [Fig. 30: ev_model_count_trend.png](Plot/ev_model_count_trend.png)

**Tax Policy Evolution:** Prior to 2008, registration taxes were primarily determined by vehicle weight, engine displacement, and horsepower. The 2007–2008 reform introduced CO₂ and NOₓ as explicit components, dramatically altering consumer incentives. The reform coincides with a visible decline in average emission intensities and accelerated replacement of high-emission diesel models. [Fig. 23](Plot/tax_components_timeline.png) illustrates this structural break, showing how fiscal instruments were redirected toward environmental objectives.

**Fuel Prices and Running Costs:** [Fig. 24](Plot/fuel_price_trend.png) shows that fuel prices have risen steadily over time. Diesel prices, which were lower for many years, started to climb faster after 2015 when new taxes removed their earlier cost advantage. Combined with rising maintenance costs and reduced residual values, this contributed to higher diesel scrappage rates in the late 2010s.

**Toll and Geographic Variation:** Spatial variation in toll charges is evident in [Figs. 25–26](Plot/map_toll_costs_2023_lines_fixed.png). Municipal differences in toll exemptions for EVs created heterogeneous adoption incentives. [Figs. 27–28](Plot/scatter_ev_vs_toll.png) confirm that EV penetration correlates positively with both higher toll costs and higher average income levels, reflecting the distributional patterns DEEP aims to explore further.

**EV Market Expansion:** [Figs. 29–30](Plot/ev_share_and_models_trend.png) trace the rapid increase in EV availability from fewer than 10 models in 2010 to over 100 by 2022. This expansion overlaps precisely with the policy reform period, providing an important contextual variable for future empirical modeling.

---

### 7. Summary and Next Steps

Phase 1 provides a comprehensive overview of the Norwegian scrapping dataset, identifying both its strengths and its remaining limitations. The analysis demonstrates that:

- The NPRA registry offers complete coverage of vehicle registration and scrappage from the 1990s onward.
- Odometer linkage is robust post-2004, enabling lifetime distance estimation.
- Emission completeness is high after 2008; earlier vintages can be reconstructed using OFV and VCA data.
- The evolution of fiscal instruments—from weight- and power-based to CO₂- and NOₓ-based taxation—correlates with marked shifts in fleet composition.
- Toll and fuel tax variation introduces clear spatial heterogeneity relevant for distributional analysis.

With these foundations, Phase 2 will focus on **emission composition and reconstruction**. This will involve developing an imputation framework for CO₂ and NOₓ among older vehicles, leveraging model-level data, type-approval sources, and cluster-based estimation. The goal is to generate a harmonized emission dataset that enables computation of lifetime emissions for all scrapped vehicles, forming the analytical bridge to policy impact evaluation.

---

**Deliverable:** Phase 1 Data Inventory Memo (completed)\
**Next Deliverable:** Phase 2 Method Note — *Emission Composition and Reconstruction*
