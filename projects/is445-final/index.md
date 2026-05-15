---

title: Where Are Meteorites Recorded?

---

# Where Are Meteorites Recorded?

**Author:** Kuan-Cheng Lung  
**Submission:** Individual submission, Group 10  
**Email:** lung4@illinois.edu  

This project visualizes NASA's Meteorite Landings dataset for a public audience. It starts with a short data overview to explain the main fields, including location, year, mass, meteorite class, and record type. It then uses exploratory charts to show basic patterns in the dataset before moving into the main visualizations.

The central visualization is an interactive world map of recorded meteorites. Each point represents one meteorite record, and color and dot size show mass category. A linked bar chart summarizes the selected records by size category.

The contextual visualizations add background for reading the main map. NASA fireball report data is used to show a related atmospheric-event dataset, while a country/region aggregation shows patterns that are hidden when many individual meteorite points overlap. A contextual recovery image is also included to show that meteorite records can be shaped by field collection and recovery work, not only by where meteorites fall.

## Data Sources

This project uses one primary dataset, two contextual sources, and map boundary data.

- **Primary dataset:** NASA Meteorite Landings dataset. This dataset contains known meteorite records and includes fields such as meteorite class, mass, fall/found status, year, latitude, and longitude.  
  Source: [NASA Open Data Portal — Meteorite Landings](https://data.nasa.gov/dataset/meteorite-landings)

- **Contextual dataset:** NASA Fireball and Bolide Reports. This dataset summarizes bright fireball and bolide events detected by U.S. Government sensors. It is used as a related but different type of space-object record: atmospheric observations rather than recovered meteorites.  
  Source: [NASA Open Data Portal — Fireball and Bolide Reports](https://data.nasa.gov/dataset/fireball-and-bolide-reports)

- **Contextual image:** NASA/JSC/ANSMET Antarctic meteorite recovery image. This image is used to provide field-recovery context for meteorite records.  
  Source: [NASA Science — Antarctic Meteorite](https://science.nasa.gov/resource/antarctic-meteorite/)

- **Map boundary data:** Natural Earth country boundary data, accessed through the Vega datasets / Altair mapping tools and GeoPandas for country-level aggregation.  
  Source: [Natural Earth](https://www.naturalearthdata.com/)

## Data and Field Overview

The tables below summarize the datasets and explain the fields used in the visualizations.

<iframe src="charts/dataset_overview_table.html" width="100%" height="220" frameborder="0"></iframe>

<iframe src="charts/field_guide_table.html" width="100%" height="360" frameborder="0"></iframe>

The field guide is included so the visualizations can be read without needing to inspect the original dataset columns. In particular, `mass_g` is used to create size categories, while `recclass` refers to the scientific meteorite class.