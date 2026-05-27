# Do cities actually make people better off?
This project investigates the urban wage premium in London, with a focus on distinguishing between nominal and real earnings.
While workers in cities tend to earn higher wages, this premium may be offset by higher housing costs, commuting expenses, and inflation. Urban economic theory suggests that agglomeration effects increase productivity and wages, but also introduces counteracting forces such as cost of living and congestion.

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

# Methodology
## 1. Baseline model: Nominal Wage
log(wage_it) = β₀ + β₁ London_i + β₂ X_it + ε_it

Where:  X_it = education, skill mix, age, gender
Extensions for consideration: job flexibility (share of hybrid and remote working jobs)

### Assumptions: skill Mix
Skill mix control for differences in the composition of jobs across boroughs, ensuring that observed wage differences are not simply driven by the presence of higher-paying occupations; that is, are people earning more because of where they are, or because of what jobs exist there?

To get to skill mix, we need to first aggrgate the number of people employed by Skill Classification. Each SOC correlates to either a low-, mid- or high-skill classification, based on a classic economic proxy of education, earnings, complexity (cognitive or routine), and training (human capital invetsment) charactoristics. Occupation mix is used as a proxy for skill composition, although note that there are limitations to what we can learn about wages from skill mix alone. The table below details the exact splits:

| SOC Code | Group / Skill | Skill Classification |
|----------|--------|--------|
| 1 | Managers, directors, senior officials | High |
| 2 | Professional occupations | High | 
| 3 | Associate professional & technical | High |
| 4 | Administrative & secretarial | Mid |
| 5 | Skilled trades | Mid |
| 6 | Caring, leisure & service | Low | 
| 7 | Sales & customer service| Low | 
| 8 | Process, plant & machine operatives | Low |
| 9 | Elementary occupations | Low| 

Next, we want to create share of those jobs at Borough-level:
- share_high = high_skill_jobs / total_jobs
- share_mid  = mid_skill_jobs / total_jobs
- share_low  = low_skill_jobs / total_jobs

While occupation-based classifications are widely used for proxy of skill mix, it does simplify heterogeneous roles within occupations and not fully capture task-based (cognitive vs routine) differences in modern labour markets. That is, occupation groups include a spectrum of roles from entry- to top-level within the same ocupation. Additioanlly, skills are not always correlated with wages; such as nurses, with high skills and low / contrained wages.

Exploration for future extension: rethinking Skill in Modern Labour Markets
In light of the definition limitations within ocupation groups, there are also wider limitations relating to the shift in modern work. Alongside the traditional skill mix proxy, It is important to critically assess how shifts in technology, education, and work patterns have weakened the traditional relationship between “skill” and wages.

a. Hypothesis: Technological change may alter the relationship between skill and job availability

Advances in automation and artificial intelligence are likely to reduce demand for routine cognitive and manual tasks, while increasing demand for workers with the skills required to design, manage, and complement these systems. This may result in a labour market characterised by fewer jobs overall in certain categories, but higher skill requirements within remaining roles.

b. Hypothesis: Expansion of education may dilute its signalling value

Access to higher education has expanded significantly in recent decades, increasing the supply of degree-qualified workers. As a result, educational attainment may no longer serve as a clear signal of productivity or earnings potential, particularly where graduate supply outpaces demand for high-skilled roles. This may weaken the relationship between traditional “high-skill” occupations and high wages.

c. Hypothesis: Skill is increasingly defined by adaptability and self-directed learning

Digital technologies have enabled new forms of work that are less tightly tied to formal occupational structures, such as freelance, platform-based, and “creator economy” roles. In these contexts, skills may be better proxied by adaptability, continuous learning, and technical capability, rather than formal occupation or qualification. This challenges the assumption that occupation-based classifications fully capture skill differences in modern labour markets.

### 2. Wage Adjustment
Both real wages and social particpation wages are gaps in the literature, especially at within city level. Real and particaptaion are important for evaluating welfare within the analysis.

#### 2.a Real Adjustment
real_wage = wage / cost_of_living_index

Min cost of living index considers:
   - Rent (proxy: housing costs)
   - Food (Proxy: Consumer Price Index)

#### 2.a Scoial Particpation Adjustment
social_wage = wage / social_cost_of_living_index

social_cost_of_living_index also considers:
   - Transport (tbc)
   - Inflation (tbc)
   - Social participation, such as a meal out or movie tickets (tbc)

### 3. Spatial Gradient Model
log(wage_i) = β₀ + β₁ distance_to_CBD + controls + ε

Tests: Is proximity to economic centre priced into wages?

### 4. Within-City Inequality
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

## Data
Build and test the approach on 2 or 3 Borough's, from a manual download of querries. To scale and ensure that the analysis is easy to update and replicate, I will switch to an API querry (if available) to importing data in a systematic way

### Approach
The aim is to process various data extracts into a single table, linking agregated metrics at a London Borough-level and year:
- Office of National Statitics (ONS): Avg. wage, Employment (Occupation mix, Gender-mix)
- Land Registry: Median rent, House price

The table I am trying to contruct will look like this: 
note: Still yet to scope the housing data, to ensure timeseries and Borough alignment.
| Year | Borough | Avg. Wage (nominal) | Median Rent | Ocupation Mix | Gender Mix |
|----------|--------|--------|------------|------------|------------|
| Keep timeseries if available. Most of the ONS data extracts have a timeseries back to 2004.  | Will need to check whether the different data sources use the same Borough definitions / meshblocks. ONS has 32 Boroughs. | tbc | tbc | Employment share by Borough, aggregated into high, mid, and low-skill from occupation SOC codes. Exact assumptions detailed below | Employment share by gender, already aggregated by the data extract.|

### Assumptions: Skill mix

#### Dataset details
SKill mix is constructed using Standard Occupational Classification (SOC) data from Nomis. Jobs are grouped into high-, mid-, and low-skill categories based on major occupation groups. The skill mix variables will be used to adjust london wage comparisons and compare inner to outer Boroughs. Skill mix will use estimates from the latest and historical ONS Labour Market Household Survey, which is split by both Borough and Gender.

Link: https://data.london.gov.uk/dataset/employment-by-occupation-type-and-gender-borough-2z05n/
Source: Office of National Statitsics (ONS)
Data: Employment rate by Inducstry, Borough
Release: Jan 2025 to Dec 2025
Coverage: Yearly from 2004 to 2025
File name: employment-by-occ-and-gender-SIC2020.xls 

Feilds required for Occupation Skills
- Greater London Borough's (32)
- Occupation by SOC major group (9)
- Number of people employed (aggregated metric)

The data is also split by Gender. Build the inital tables in a way that we can use to also control for gender.

#### Assuptions detail: aggregating Ocupation into a Skill Classification


### Job flexibility by skill mix
I also want to explore the effects of job flexibility. Especislly since the new world of hybrid working, I want to see whether pepople in high skilled / earning jobs also have higher flexibility to live in cheaper and less connected areas, doubling down on the beneifts of high wage, which lower skilled and service jobs would not have the luxery.

#### Dataset details


#### Assuptions detail: aggregating Ocupation into a Skill Classification


### Job Densitity by Borough
tbc.

### Household mix
To weight the scoial participation costs to cover all family memebers / dependents.
hypotheisis: London workers have fewer dependents, and therefore could contribute to higher disposable income.

Download borough-level house price index OR aggregated London dataset:
- Price Paid Data (CSV)
- UK House Price Index (CSV)


#### Cost of living (food), transport and social participation

TfL provides Unified API (requires key), to pull: 
- journey times
- accessibility data
- network stats



# Housekeeping
## Repository Structure (tbd.)
urban-wage-premium-london/
01. data = raw and cleaned datasets
02. notebooks = analysis and modelling workflows
03. src = reusable functions and scripts
04. outputs = figures and final tables

### How to Run (tbd.)
Shellpip install -r requirements.txt
Then run notebooks in order:
1. Data cleaning
2. Exploration
3. Modelling

# Apendix
## Table of all related sources
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

4. Visualisation
