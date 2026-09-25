# Ride Knox Ridership Analysis
## Who drove the 2025 decline, and where capacity is strained

### Overview
*Which types of riders drove the 2025 decline in ridership? Where is dock pressure the greatest?*

### Data: 247,967 cleaned trips across 24 stations
Raw files are **not** in this repo (~22 MB, and we believe you should never edit raw data).
We have schemas of our data below, but request `trips_2025.csv` and `stations.xlsx` from the Ride Knox data team.

*Data schemas*

`trips_2025.csv` — one row per trip:
| column                | type     | notes                                 |
| ----------------------| -------- | ------------------------------------- |
| trip_id               | str      | unique, T-series                      |
| start_time / end_time | datetime | stored as text in the raw file        |
| start_station_id      | str      | joins to stations.station_id          |
| start_station_name    | str      | authoritative names in stations.xlsx  |
| end_station_id        | str      | ~3,800 missing (kept and flagged)     |
| rider_type            | str      | member / casual (raw has 6 spellings) |
| bike_type             | str      | classic / electric                    |



`stations.xlsx` — one row per station:
| column                | type     | notes                                 |
| ----------------------| -------- | ------------------------------------- |
| station_id            | str      | unique, T-series                      |
| station_name          | str      | authoritative names                   |
| neighborhood          | str      | broader location stations share       |
| latitude              | float    | Latitude location of each station     |
| longitude             | float    | Longitude location of each station    |
| docks                 | int      | number of docks                       |
| year_installed        | int      | year station was installed            |

### Tools/How to Run: Python, pandas, matplotlib
Install requirements.txt, open analysis.ipynb, Restart & Run All

### Key finding
Of the 10 stations with the most pressure (according to trips per dock), there are four stations in the **UT Campus neighborhood** that are most pressured. However, there is near-idleness observed for both Bearden and Sequoyah Hills stations.
![Station Trips per dock](charts/trips_per_dock_by_station_2025.png)

### Limitations
The decline in casual riders could be a consistent pattern, but we are unable to determine this without having other years to compare with 2025. We also flagged several trips that have no end station recorded, and those trips have been excluding from the analysis in answering these questions. This eliminates some data that may have led us to more genuine and accurate results. Additionally, the decision to exclude rides shorter than two minutes may have dropped 123 valid data points if those were genuine trips where riders took the bikes a very short distance.

### Repo structure
ride-knox-analysis/
├── .git/                  # Internal Git history tracking (hidden)
├── charts/                # Graphs created to visually show results from data analysis
├── scratch                # Temporary files (ignored)
├── .gitignore             # Tells Git which files/folders to completely ignore
├── analysis.ipynb         # All code for analyses
├── COLLAB-LOG.md          # History from current assignment/project
├── image.png              # Screenshot from Part 2
├── README.md              # The front-page introduction and setup guide for this project
├── requirements.txt       # Dependencies/packages required to run the project
├── report.md              # Synthesis of main findings from 2025 analysis
├── WORKLOG.md             # History from previous assignment/project (Assignment 5)