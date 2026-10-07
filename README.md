# ACCREU_energy_demand_datasets
The dataset was produced by CMCC in the context of the ACCREU project. Further information on the folder structure, file naming convention and data format is provided below.

**Author:** Francesco Colelli, CMCC Foundation ([francesco.colelli@cmcc.it](mailto:francesco.colelli@cmcc.it))
**Produced within:** ACCREU (Assessing Climate Change Risk in EUrope), Horizon Europe
**Version:** 1.0 (2026)

**Public Accelerator folder:**  [View ACCREU energy demand datasets](links_DT1.html)

## Summary

This dataset contains country-level projections of **final energy demand and energy expenditures** associated with climate-change adaptation, together with estimates of **thermal power-plant exposure to extreme heat** and the resulting predicted additional outages in Europe.

It is intended to support analysis of adaptation-driven energy demand, adaptation costs and climate-related impacts on power generation at country/region level. The dataset was produced by the CMCC Foundation in the context of the ACCREU project.

## Citation

> Colelli, Francesco. (2026). *CMCC Climate Adaptation Energy Dataset* (Version 1.0). Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX

## License

- **Data:** This dataset is licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.

## Repository Contents (Metadata only)

This GitHub repository hosts **only** the metadata (this README and the data access page). The data files reside on the IIASA Accelerator platform (see link above).

## Folder Structure (on Accelerator)

```text
CMCC_energy/
├─ annual_energy_demand/
│  ├─ accreu_energy_demand_adaptation_country.csv
│  ├─ accreu_sectoral_energy_demand_adaptation_country.csv
│  └─ accreu_sectoral_energy_demand_adaptation_country_by_service.csv
└─ power_generation_outages/
   └─ heat_outages_thermal_EU.csv
```

---

# Dataset Documentation

## 1. `annual_energy_demand`

Annual projections of final energy demand and energy expenditures by country/region, for a baseline and for climate-change adaptation. The three files contain the same information at decreasing levels of aggregation.

| File | Content |
|---|---|
| `accreu_sectoral_energy_demand_adaptation_country_by_service.csv` | Demand and expenditures by country/region, **sector and energy service** |
| `accreu_sectoral_energy_demand_adaptation_country.csv` | Demand and expenditures by country/region and **sector**, aggregated across energy services |
| `accreu_energy_demand_adaptation_country.csv` | Demand and expenditures by country/region, **aggregated across sectors** |

### Variables

Long (tidy) format, comma-separated.

| Column | Description |
|---|---|
| `ISO3` | ISO 3166-1 alpha-3 country code |
| `Region` | Country or region name |
| `Scenario` | Climate/adaptation scenario |
| `Variable` | Energy-demand or expenditure variable (see definitions below) |
| `Year` | Year of the projection |
| `Value` | Numerical value |
| `Unit` | Unit of `Value` |

### Definitions

| Term | Definition |
|---|---|
| **Final Energy** | Projected final energy demand, estimated with a statistical model. |
| **Expenditures** | Energy expenditures, computed with 2023 end-use prices by region, in 2015 USD PPP, from the [IEA End-Use Prices Data Explorer](https://www.iea.org/data-and-statistics/data-tools/end-use-prices-data-explorer?tab=Yearly+prices). |
| **Baseline** | Reference level with **no climate change and no adaptation**, covering all energy services in the sectors considered. |
| **Adaptation** | **Additional** energy demand or expenditures due to adaptation only (i.e. on top of the Baseline, not a total). |
| **Electricity / Fossil Fuels** | Final-energy carrier. Fossil Fuels = coal + oil + gas. |
| **Sectors** | Residential, commercial, industry and agriculture. Aggregated files report the total of these sectors. |

**Total demand under adaptation** = `Baseline` + `Adaptation`.

## 2. `power_generation_outages`

Exposure of thermal power plants to extreme heat in Europe, and the additional outages predicted from increased exposure.

### File: `heat_outages_thermal_EU.csv`

| Indicator | Description |
|---|---|
| `Power plant - days T>98th\|Historical\|<Technology>` | Annual power-plant-days with daily mean temperature above the 98th percentile, historical period |
| `Power plant - days T>98th\|Future\|<Technology>` | Same indicator, future period |
| `Predicted additional number of outages\|Future\|<Technology>` | Additional outages per year in the country, due to the increase in heat exposure from the historical to the future period |
| `Power_plant_exposed_number` | Number of power plants in the country exposed to these conditions |

### Definitions

- **Power-plant-day:** one power plant exposed on one day to a daily mean temperature above the 98th percentile. A value of 100 means 100 power-plant-days of exposure in the year (e.g. 10 plants × 10 days).
- **Historical / Future:** the periods over which exposure is computed.
- **Technology:** the power-generation technology of the plants.
- **Per-plant averages:** divide exposure or outage indicators by `Power_plant_exposed_number`.

---

## Notes for users

- Always read `Value` together with its `Unit`, `Year`, `Scenario` and `Region`.
- `Adaptation` values are increments over `Baseline`, not totals. Do not sum them across scenarios.
- **Combining with the ACCREU cooling-cost dataset** (residential AC investment, Falchetta): this dataset already includes residential cooling energy expenditures. Use only the investment components of the cooling-cost dataset to avoid double counting electricity.
- The modelling methodology is documented in the associated ACCREU deliverables.

## Data Sources

- Energy prices: [IEA End-Use Prices Data Explorer](https://www.iea.org/data-and-statistics/data-tools/end-use-prices-data-explorer?tab=Yearly+prices), 2023 regional prices.

## Contact

Francesco Colelli, CMCC Foundation, [francesco.colelli@cmcc.it](mailto:francesco.colelli@cmcc.it)

## Funding Acknowledgement

This work was supported by the **Assessing Climate Change Risk in Europe (ACCREU)** project, funded by the European Commission under the **Horizon Europe** programme (grant agreement No. 101081358).

**Project website:** [ACCREU Website](https://www.accreu.eu/)
