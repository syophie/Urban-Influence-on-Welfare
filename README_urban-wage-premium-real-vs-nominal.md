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
   - Optional: social includion costs, such as a meal out or movie tickets

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


## Housekeeping 
### Repository Structure
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

### How to Run
Shellpip install -r requirements.txt
Then run notebooks in order:
1. Data cleaning
2. Exploration
3. Modelling
4. Visualisation
