# Do cities actually make people better off?
This project investigates the urban wage premium in London, with a focus on distinguishing between nominal and real earnings.
While workers in cities tend to earn higher wages, this premium may be offset by higher housing costs, commuting expenses, and inflation. Urban economic theory suggests that agglomeration effects increase productivity and wages, but also introduces counteracting forces such as cost of living and congestion. [link.springer.com]

This project aims to quantify:
- Whether London’s wage premium persists after adjusting for cost of living and social inclusion
- How the premium varies within the city (by geography, occupation, income level)

### Research Question
key insights: Does a real urban wage premium exist in London?
- does the London wage premium survives after cost-of-living adjustment?
- Do cities actually increase welfare, or just increase nominal income?

Supporting questions:
- How does the wage premium change with distance from the city centre?
- Is the premium concentrated among high-skill occupations?
- How much of the premium is driven by: location (proximity) and worker characteristics (education, occupation)

### Economic Frameworks
This project tests key mechanisms from urban labour economics:
- Agglomeration effects: Cities increase productivity through density, matching, and spillovers
- Sorting: Higher-ability workers self-select into cities
- Real vs nominal trade-off: Higher wages may be offset by higher living costs

## Methodology
### 1. Baseline Model (Nominal Wages)
log(wage_it) = β₀ + β₁ London_i + β₂ X_it + ε_it

Where:
  X_it = education, occupation, age, gender

### 2. Real Wage Adjustment
real_wage = wage / cost_of_living_index

Cost of living index is built from:
   - Rent (proxy: housing costs)
   - Food (Proxy: Consumer Price Index)
   - Optional: transport + inflation
   - Optional: social participation costs, such as a meal out or movie tickets

### 3. Spatial Gradient Model
log(wage_i) = β₀ + β₁ distance_to_CBD + controls + ε

Tests: Is proximity to economic centre priced into wages?

### 5. Within-City Inequality
Estimate models separately by:
- occupation group (high-skill vs low-skill)
- income decile

### 6. Robustness
- Fixed effects (if panel data available)
- Instrument for density (optional)
- Compare:
    - Inner vs outer London
    - London vs rest of UK
- Compare: Melbourne data

### 7. Extenions:
- Add commuting time to test “functional urban density”
- Extend to Melbourne (cross-city comparison)
- Model remote work impact on wage premium

## Outputs
Charts:
- Wage vs distance from CBD
- Nominal vs real wage comparison
- Wage distribution (London vs non-London)
- Premium by occupation

Tables:
- Regression outputs
- Decomposition (explained vs unexplained wage gap)

## Data Sources
## Data Sources

| Category | Source | Dataset | Description | Key Variables | Use Case | Open Source |
|----------|--------|--------|------------|--------------|----------|------------|
| Labour Market | ONS | ASHE (Annual Survey of Hours and Earnings) | Wage data by occupation and region | Earnings, occupation, region | Wage regressions; regional comparisons | No (restricted microdata; limited public extracts available) |
| Labour Market | ONS | Labour Force Survey (LFS) | Individual-level labour market data | Education, employment status, demographics | Control variables; micro-level analysis | No (microdata restricted; some aggregates open) |
| Labour Market | Nomis (ONS) | Regional labour statistics | Borough and regional labour indicators | Earnings, occupation, employment by sector | Spatial analysis; borough-level decomposition | Yes |
| Cost of Living | ONS / Land Registry | Housing data | Property prices and rental costs | Median rents, house prices | Real wage adjustment; cost-of-living modelling | Yes |
| Cost of Living (Optional) | TfL / ONS | Transport + inflation data | Transport costs and price indices | Travel costs, CPI | Extended cost-of-living adjustment | Partial (transport data often open; CPI open) |
| Spatial | ONS | Geography datasets | Administrative boundaries (borough, MSOA) | Geographic identifiers | Spatial mapping; regional aggregation | Yes |
| Spatial | Constructed | Distance to CBD | Calculated distance to economic centre (e.g. City of London) | Distance measures | Spatial gradient analysis; proximity effects | Yes (derived from open data) || Cost of Living (Social Inclusion) | ONS | CPI – Recreation & Culture | Price index covering leisure activities (e.g. cinema, restaurants, cultural activities) | Price index, subcategory inflation | Proxy for social participation costs; adjust real wages for leisure affordability | Yes |
| Cost of Living (Social Inclusion) | BFI (British Film Institute) | Statistical Yearbook (Cinema data) | Industry data on cinema attendance and market activity | Ticket prices (indirect), admissions, revenue | Proxy for cinema affordability and leisure consumption | Yes |
| Cost of Living (Social Inclusion) | ONS | CPI microdata (price quotes) | Underlying price quotes used for CPI construction | Item-level prices (where available) | Granular proxy for specific leisure costs (e.g. meals out, entertainment) | Partial (restricted detail) |
| Cost of Living (Social Inclusion) | Numbeo (or similar) | Cost of Living datasets | Crowdsourced price data for goods and services by city | Meal prices, cinema tickets, leisure costs | Direct proxy for social inclusion costs (cross-city comparison) | No (paid access for full datasets) |

## Repository Structure (tbd.)

urban-wage-premium-london/
│
├── data/
│   ├── raw/
│   ├── processed/
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_exploration.ipynb
│   ├── 03_modelling.ipynb
│   ├── 04_visualisation.ipynb
│
├── src/
│   ├── data_prep.py
│   ├── feature_engineering.py
│   ├── modelling.py
│
├── outputs/
│   ├── figures/
│   ├── tables/
│
├── README.md
└── requirements.txt

### How to Run (tbd.)
Shellpip install -r requirements.txt
Then run notebooks in order:
1. Data cleaning
2. Exploration
3. Modelling
4. Visualisation
