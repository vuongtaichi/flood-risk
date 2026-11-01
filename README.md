# Building-level flood risk model: summary site

An interactive summary of the code and results behind the paper:

> **Flood risk differs across scales: Evidence from building- and subdistrict-level assessment in the upstream Yeongsan River Basin, South Korea**
> Vu, Kim, Vuong Tai, Sharma, Dao (manuscript in preparation)

**Main finding:** a subdistrict's flood risk class hides large differences between its buildings. Rating each building separately finds high-risk buildings that subdistrict ratings miss.

## The model

Risk is rated 1–5 at two scales, building and subdistrict:

**R = round(∛(H · E · V))**

| Part | What it measures | Subdistrict | Building |
|---|---|---|---|
| **H** Hazard | Damage-weighted flooded area in one 100-year flood (depth classes weighted 0.066 / 0.153 / 0.608 / 0.988 / 1.0, Jung et al. 2023) | flooded area in the subdistrict | flooded share of a 30 m circle |
| **E** Exposure | Residents in flooded buildings | sum over the subdistrict | residents of the building |
| **V** Vulnerability | Socio-economic vulnerability index (SEVI): PCA of 19 indicators, 5 components | subdistrict SEVI | subdistrict SEVI split by inverse housing price |

Each part is put into quintile classes (1–5) before it is combined.

## Study area and data

- Upstream Yeongsan River basin, South Korea: 118 subdistricts and 166,999 residential buildings. 27,804 buildings in 91 subdistricts lie in the flood zone.
- Data:
  - building register (Dec 2025);
  - housing sale and rent prices;
  - WorldPop 2025 population, corrected to official counts;
  - 100-year flood depth map (floodmap.go.kr);
  - subdistrict socio-economic statistics.

## Key results

| | Buildings | Subdistricts |
|---|---|---|
| Higher risk (R ≥ 4) | 5,261 of 27,804 | 23 of 91 |

- **Within vs between subdistricts:** 68 % of the variation in building risk lies within subdistricts, not between them.
- **Missed by subdistrict ratings:** 1,768 of the 5,261 higher-risk buildings (34 %) are in subdistricts rated 3 or lower.
- **Fixed budget of 5,000 buildings:** a subdistrict-based selection reaches 33 % of higher-risk buildings; a building-based one reaches 95 %.

## The site

Tabs:

1. Model overview and risk map
2. Building vs subdistrict
3. Key assumptions
4. Results
5. Results analysis
6. Open issues
7. Literature

## Files

| File | Purpose |
|---|---|
| `flood-risk-model.html` | The whole site in one file: data, charts and maps |
| `refimg/` | Reference figures for the Literature tab |
| `index.html` | Opens the site from the root address |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

**Hosting:** push this folder to a GitHub repository, then turn on *Settings → Pages → Deploy from branch*. The site needs an internet connection for its fonts and for MathJax 3.2.2.
