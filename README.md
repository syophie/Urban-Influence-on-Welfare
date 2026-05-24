# Urban-Influence-on-Earnings
Exploration of urban labour market economics, with a focus on the urban wage premium and the mechanisms through which cities influence earnings. It combines economic theory (agglomeration, sorting, matching) with applied data analysis to understand how location drives productivity, wage dispersion, and labour market outcomes.

## Gaps in literature: 
### 1: Does access to dense labour markets (firms, industries, networks) matter more than physical location in explaining wage differences?
The literature largely explains higher urban wages via:
- Agglomeration economies (productivity, spillovers, density)
- Sorting (higher-ability workers choose cities)

But, the literture still struggles to separate physical proximity (being in London CBD) vs functional proximity (working in a high-density network / firm ecosystem), which is increasingly relevant post-COVID and the new world of hybrid work.

### 2: After adjusting for rent, transport, and inflation, does the urban wage premium still exist?
The literature exaplains urban wages:
- Urban wages are higher
- But cost of living and congestion offset gains

However, many analyses still focus on nominal wages, without taking purchasing power and social inclusion costs into account.

### 3: Is the urban wage premium increasing inequality within cities?
_Specifically: do low-skill workers benefit from city density, Or is the premium concentrated in high-skill roles? _
 
The literature exaplains urban wages:
- are higher on average
- often scale with city size (superlinear scaling)

But, there is less emphasis on distribution within the city. Some studies suggest differences by occupation (e.g., white-collar vs blue-collar), but modern, service-heavy cities like London or Melbourne are still largely underexplored. 

## Approach: baseline
### Base line regression: 
log(wage) = β₀ + β₁ urban_density + β₂ skills + β₃ occupation + ε
- Instrument density using historical transport links
- Seperate firm and location effects
- Compare pre/post remote work period

Regression additions:
- Job density
- commuting access
- Distace to CBD
- Other access barriers, such as internet or technology access for remote or hybrid work

### Descriptive analysis

Visulise:
- Wage vs distance from CBD
- Wage vs city size (log scale)
- Real vs nominal wage plots

## Data sources: 
Some data sources to explore, or replicate with dummy data if unable to acess Open Source.

| Geography | Source | Dataset | Description | Key Variables | Use Case | Open Source |
|----------|--------|--------|------------|--------------|----------|------------|
| London | ONS (Office for National Statistics) | ASHE (Annual Survey of Hours and Earnings) | Wage data by occupation, region | Earnings, occupation, region | Wage regressions; urban vs non-urban comparison | No (restricted microdata; limited public extracts available) |
| London | ONS (Office for National Statistics) | Labour Force Survey (LFS) | Individual-level labour market data | Education, employment status, demographics | Control variables; micro-level analysis | No (microdata restricted; some aggregates open) |
| London | ONS | Travel-to-Work Areas (TTWA) | Geographic definitions of labour markets | Commuting zones, employment flows | Define labour markets; spatial comparisons | Yes |
| London | Nomis (ONS portal) | Regional labour statistics | Clean local labour market data | Earnings, employment by sector, occupation | Borough-level analysis; spatial decomposition | Yes |
| London | Land Registry + ONS | Housing data | Property prices and rental costs | Median rents, house prices | Real wage adjustment; cost-of-living modelling | Yes |
| London | OpenStreetMap / Transport APIs | Transport & accessibility data | Commute times and connectivity | Travel time, accessibility, distance | Functional urban density; spatial accessibility analysis | Yes |
| Melbourne | ABS (Australian Bureau of Statistics) | Census (TableBuilder) | National census microdata | Earnings, occupation, commuting patterns | Cross-sectional wage analysis; spatial patterns | Partial (aggregates open; detailed microdata restricted) |
| Melbourne | HILDA Survey | Panel dataset | Longitudinal household survey | Individual wages, employment history | Panel regressions; controlling for sorting (fixed effects) | No (restricted access) |
| Melbourne | AURIN | Urban spatial datasets | Integrated spatial data platform | Jobs density, housing, infrastructure | Agglomeration and density measures | Partial (free with registration) |
| Melbourne | CoreLogic (or similar) | Property data | Housing market data | House prices, rents | Cost-of-living adjustment; real wages analysis | No (commercial dataset) |

