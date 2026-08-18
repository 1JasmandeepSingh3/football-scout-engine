# Scout Engine

Scout Engine turns raw player statistics into scouting recommendations. A Jupyter/pandas/scikit-learn
pipeline filters players by position, age, and minutes, then uses KMeans clustering and cosine
similarity to score each player's fit against a target profile. Results export to JSON and render
across a static HTML dashboard.

## Features

- **Filtering** — narrows the player pool by position (ST, FW, LW, RW, AM), max age, and minimum
  minutes played.
- **Clustering** — groups forwards into 5 archetypes (e.g. Elite Finishers, Creative Forwards, Wide
  Attackers, Pressing Forwards, Box-to-Box Attackers) using `StandardScaler` + `KMeans`.
- **Fit scoring** — ranks players by cosine similarity against a target statistical profile.
- **Visualizations** — bar charts and radar charts built with matplotlib inside the notebook.
- **Static dashboard** — four HTML pages (landing, top scorers, recommendations, clinical
  efficiency) that read the exported data, no backend required.

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
  `cosine_similarity`), matplotlib
- **Frontend:** static HTML/CSS/JS, no framework or build step

## Running it

1. Install dependencies:
   ```
   pip install pandas numpy matplotlib scikit-learn
   ```
2. Open `scouting_engine.ipynb` and run all cells. The final cell exports `scout_data.json`,
   which powers the frontend pages.
3. Open `index.html` in a browser (or serve the folder with any static file server) to view the
   dashboard.
