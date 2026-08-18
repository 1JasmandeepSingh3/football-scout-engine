#  Scout Engine

Scout Engine is a data-driven football (soccer) scouting tool. A Python/pandas/scikit-learn
pipeline turns raw player statistics into ranked recommendations, and a static HTML dashboard
visualizes the results — top scorers, forward archetypes, and clinical efficiency, all in a
neon scoreboard-style UI.

## Overview

Given a pool of player statistics, Scout Engine:

1. **Filters** players by position, max age, and minimum minutes played.
2. **Clusters** forwards into archetypes (Elite Finishers, Creative Forwards, Wide Attackers,
   Pressing Forwards, Box-to-Box Attackers) using `StandardScaler` + `KMeans`.
3. **Scores fit** for each player via cosine similarity against a target statistical profile.
4. **Exports** the results to `scout_data.json`.
5. **Renders** the results across a set of static HTML pages — no backend or server required.

## Features

| | |
|---|---|
|  **Position/age/minutes filtering** | Narrow the player pool to ST, FW, LW, RW, or AM, by max age and minimum minutes played. |
|  **KMeans clustering** | Groups forwards into 5 statistical archetypes. |
|  **Cosine similarity fit scoring** | Ranks players against a target profile. |
|  **In-notebook visualizations** | Bar charts and radar charts via matplotlib. |
|  **Static dashboard** | Four themed HTML pages, powered by Chart.js, reading directly from the exported JSON. |

## Project structure

```
scout-engine/
├── scouting_engine.ipynb          # data pipeline: filter → cluster → score → export
├── scout_data.xlsx, per 90.xlsx   # source player statistics
├── scout_data.json                # processed output consumed by the HTML pages
├── index.html                     # landing page
├── top10score.html                # top 10 goal scorers view
├── recommendations.html           # forward recommendations view
├── clinical.html                  # clinical efficiency view
└── Scout_Engine_Presentation.pptx # project presentation
```

## Tech stack

- **Data pipeline:** Python, pandas, numpy, scikit-learn (`StandardScaler`, `KMeans`,
  `cosine_similarity`), matplotlib, Jupyter
- **Frontend:** static HTML/CSS/JS, [Chart.js](https://www.chartjs.org/) for charts —
  no framework, no build step

## Getting started

**1. Install dependencies**
```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

**2. Run the pipeline**

Open `scouting_engine.ipynb` and run all cells top to bottom. The final cell exports
`scout_data.json`, which powers every page in the dashboard.

**3. View the dashboard**

Open `index.html` directly in a browser, or serve the folder so relative `fetch()` calls
work reliably:
```bash
python -m http.server
```
then visit `http://localhost:8000`.

## Roadmap

- [ ] Configurable target profile from the UI instead of the notebook
- [ ] Additional positions beyond forwards (midfielders, defenders)
- [ ] Multi-season comparison view

## License

No license specified yet — all rights reserved by default until one is added.