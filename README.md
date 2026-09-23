# Finding Pittsburgh's Best Neighborhood

A data analysis project using public data from the [Western Pennsylvania Regional Data Center (WPRDC)](https://data.wprdc.org) to answer one question: **which Pittsburgh neighborhood offers the best overall quality of life?**

Built as a team project for CMPINF 0010 (Big Ideas in Computing & Information) at the University of Pittsburgh.

**Result: Larimer.** It was the only neighborhood that scored well on all three metrics instead of winning just one.

## Approach

We defined "best" as the neighborhood providing the highest quality of life for its residents, measured with three metrics. Each team member owned one metric from data sourcing through analysis:

| Metric | What we measured | Dataset | Owner |
|---|---|---|---|
| **Mobility** | Total POGOH bike-share docks per neighborhood | [POGOH Station Locations (2025)](https://data.wprdc.org/dataset/station-locations) | Pahul Sachdev |
| **Safety** | Reported criminal incidents per neighborhood | [Pittsburgh Police Incident Data](https://data.wprdc.org/datastore/dump/bd41992a-987a-4cca-8798-fbe1cd946b07?bom=True) | Ayo Osho |
| **Schools** | Public school students enrolled per 1,000 residents | [PPS Enrollment](https://data.wprdc.org/dataset/pittsburgh-public-schools-enrollment) + [ACS 2019–23 Population Estimates](https://data.wprdc.org/dataset/2009-13-and-2019-23-american-community-survey-estimates-for-city-of-pittsburgh-neighborhoods) | Diego Carranza |

## Findings

**Mobility.** Oakland leads by a wide margin with close to 300 docks, followed by Shadyside, the Strip District, and Downtown. Because POGOH only operates in part of the city, any neighborhood that has stations at all has meaningful bike access.

**Safety.** Saint Clair had the fewest reported incidents (25). The Central Business District had the most (7,600+), followed by South Side Flats and Carrick.

**Schools.** Enrollment totals were joined with ACS population estimates to normalize by neighborhood size, producing a students-per-1,000-residents ratio.

**Combining the metrics.** Each metric produced a different winner, so we looked for overlap near the top of all three. Larimer stood out:

- About 50 POGOH docks (solid mobility)
- Third-highest school enrollment relative to population
- A mid-range crime count: not the lowest, but far from the highest

## Limitations

- **Crime is a raw count, not per capita.** Busy commercial areas like Downtown rank worse partly because far more people pass through them than live there.
- **Enrollment density stands in for school quality.** It shows how many families use public schools, not how good those schools are. Test scores or graduation rates would be a stronger measure.
- **Bike docks capture one kind of mobility.** Bus and light-rail access would give a fuller picture.
- **The combination step was qualitative.** A next step would be normalizing each metric to a 0–1 score and ranking neighborhoods by a weighted composite.

## Repository Structure

```
├── Final/            Combined analysis notebook and all datasets
├── Pahul/            Mobility analysis (POGOH bike docks)
├── Diego/            School enrollment + population analysis
└── ayo/              Crime analysis
```

## Running It

```bash
pip install pandas matplotlib jupyter
cd Final
jupyter notebook "Final notebook.ipynb"
```

The crime notebook pulls its data directly from the WPRDC API, so it needs an internet connection.

## Team

- **Pahul Sachdev** ([@pahul-sachdev](https://github.com/pahul-sachdev)): Mobility
- **Diego Carranza** ([@diegocarranza-dex](https://github.com/diegocarranza-dex)): Schools
- **Ayo Osho** ([@aoo60-code](https://github.com/aoo60-code)): Safety

Originally developed in [diegocarranza-dex/Big-Ideas-Project-Group32](https://github.com/diegocarranza-dex/Big-Ideas-Project-Group32).

Tools: Python, pandas, matplotlib, Jupyter
