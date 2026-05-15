---
title: Where Are Meteorites Recorded?
layout: page
---

<link rel="stylesheet" href="assets/css/style.css">

**Author:** Kuan-Cheng Lung  
**Submission:** Individual submission, Group 10  
**Email:** lung4@illinois.edu  

This project visualizes NASA's Meteorite Landings dataset for a public audience. The main focus is where recorded meteorites are located, how large they are, and what patterns become visible when the same records are shown in different ways.

The page includes exploratory visualizations, one main interactive visualization, and contextual views using country/region aggregation, NASA fireball reports, and a meteorite recovery image.

## Data Sources and Analysis Notebook

- [NASA Meteorite Landings](https://data.nasa.gov/dataset/meteorite-landings)  
  Primary dataset for recorded meteorites, including location, year, mass, meteorite class, and record type.

- [NASA Fireball and Bolide Reports](https://data.nasa.gov/dataset/fireball-and-bolide-reports)  
  Contextual dataset for bright atmospheric fireball events.

- [Natural Earth map boundary data](https://www.naturalearthdata.com/)  
  Geographic boundary data used for world map outlines and country/region aggregation.

- [NASA Science — Antarctic Meteorite](https://science.nasa.gov/resource/antarctic-meteorite/)  
  Source for the contextual meteorite recovery image.

- [Analysis notebook](https://github.com/kclung99/kclung99.github.io/blob/main/projects/is445-final/notebooks/is445_final.ipynb)  
  Notebook used to clean the data and generate the visualizations.

## Reading the Data

The main dataset is NASA's Meteorite Landings dataset. It includes location, year, mass, meteorite class, and record type. The Fireball and Bolide Reports dataset is used later as contextual data, and Natural Earth boundary data is used to group meteorite records by country or region.

### Dataset Overview

| Dataset | Role | Raw Records | Clean Records | Time Range | One Row Means |
|---|---:|---:|---:|---:|---|
| Meteorite Landings | Primary dataset | 45,716 | 38,220 | 1399–2101 | One recorded meteorite |
| Fireball Reports | Contextual dataset | 1,061 | 1,060 | 1988–2026 | One bright atmospheric fireball event |

### Main Fields Used

| Field | Dataset | Plain Meaning | Used Later For |
|---|---|---|---|
| `fall` | Meteorite Landings | Whether the meteorite was seen falling or found later | Comparing observed events with later discoveries |
| `year` | Both datasets | The year connected to the record | Showing how records change over time |
| `latitude / longitude` | Both datasets | Where the meteorite or fireball was recorded | Placing records on maps |
| `mass_g` | Meteorite Landings | Meteorite mass in grams | Grouping meteorites by size |
| `recclass` | Meteorite Landings | Scientific meteorite class, such as L6 or H5 | Showing meteorite type in tooltips |
| `impact_energy_kt` | Fireball Reports | Estimated energy of a fireball event in kilotons | Showing the scale of atmospheric events |
| `altitude_km` | Fireball Reports | Height of the fireball event above Earth | Additional fireball context in tooltips |

## Exploratory Visualizations

Before building the main map, I explored a few basic questions about the data. These charts helped decide what the final visualizations should emphasize.

### Exploratory Visualization 1: Record Type Over Time

I first checked whether the dataset mostly contains meteorites that people saw falling or meteorites that were discovered later. This matters because found records can reflect search and recovery patterns, not only natural falling patterns.

The chart shows meteorite records since 1900, grouped by decade and record type. Most records are meteorites that were found later rather than directly observed falling.

<iframe src="charts/meteorite_records_by_decade.html" width="100%" height="470" frameborder="0"></iframe>

### Exploratory Visualization 2: Meteorite Mass

I also checked meteorite mass before using it in the main map. The data contains many small meteorites and a few extremely large ones.

On the raw mass scale, the largest records stretch the axis and make typical records hard to see. The log-scaled view makes the distribution easier to read. Because of this, the main map uses mass categories instead of exact mass values.

<iframe src="charts/meteorite_mass_raw_vs_log.html" width="100%" height="480" frameborder="0"></iframe>

### Exploratory Visualization 3: Fireball Reports Over Time

For contextual data, I looked at NASA's Fireball and Bolide Reports to see how atmospheric fireball events behave over time.

The bars show the number of fireball reports each year, while the line shows total estimated impact energy. The report count is fairly steady in many recent years, but the energy line has a large spike in 2013. This shows that one unusually large event can dominate the total energy for a year even when the number of reports is not unusually high.

<iframe src="charts/fireball_reports_energy_by_year.html" width="100%" height="500" frameborder="0"></iframe>

## Main Interactive Visualization: Meteorite Records Around the World

The main map shows individual meteorite records around the world. Each dot represents one recorded meteorite. Larger and warmer-colored dots represent heavier meteorites, while smaller and cooler-colored dots represent lighter meteorites.

Visible clusters appear in places such as the United States, North Africa, Australia, and Antarctica. These clusters should be read as concentrations of **recorded** meteorites, not necessarily places where meteorites fall more often.

Use the year slider to focus on newer records. Use the size filter to look at one mass category at a time. Hover over a dot to see details such as meteorite name, year, mass, record type, and meteorite class.

The bar chart below the map summarizes records by size category. This helps show counts that are hard to judge from the map alone, especially where many points overlap.

<iframe src="charts/main_meteorite_map_with_size_summary.html" width="100%" height="950" frameborder="0"></iframe>

## Contextual Visualization 1: Country and Region Summary

The first contextual view groups meteorite records by country or region. To create this view, I used Natural Earth boundary data to match meteorite latitude and longitude points to geographic regions.

This aggregation reveals a pattern that is hard to see from the point map alone: Antarctica has a very large number of recorded meteorites. The main map shows the locations, but many Antarctic records overlap visually. The country/region summary makes the total count clearer.

This does not mean meteorites only fall in Antarctica. It shows that recorded meteorite data can be strongly shaped by where meteorites are searched for, recovered, and documented.

<iframe src="charts/country_meteorite_summary.html" width="100%" height="1150" frameborder="0"></iframe>

Visualization created by me. Code: [analysis notebook](https://github.com/kclung99/kclung99.github.io/blob/main/projects/is445-final/notebooks/is445_final.ipynb)

## Contextual Visualization 2: Fireball Reports

The second contextual view uses NASA's Fireball and Bolide Reports dataset. I included this dataset because I expected fireball reports to provide a related comparison to meteorite landing records.

The visualization shows that the two datasets should not be treated as the same thing. Crosses show reported fireball events. Color and size show estimated impact energy, and the linked bar chart summarizes reports by energy category. Many reports appear over oceans as well as land, which is different from the Meteorite Landings dataset.

The main takeaway is that fireball reports are atmospheric observations, while meteorite landing records are recovered or documented objects on the ground. A fireball can be observed without a meteorite later being found.

<iframe src="charts/context_fireball_map_with_energy_summary.html" width="100%" height="850" frameborder="0"></iframe>

Visualization created by me. Code: [analysis notebook](https://github.com/kclung99/kclung99.github.io/blob/main/projects/is445-final/notebooks/is445_final.ipynb)

## Contextual Visualization 3: Meteorite Recovery Image

The third contextual visual is a NASA/JSC/ANSMET image of Antarctic meteorite recovery. I included it to give the reader a concrete sense of what meteorite recovery can look like in the field.

The earlier charts show records, locations, and counts. This image adds a visual example of the real-world object and setting behind the data.

![Antarctic meteorite recovery](charts/morg_and_alex_1280.jpg)

Image source: [NASA Science — Antarctic Meteorite](https://science.nasa.gov/resource/antarctic-meteorite/)

## Write-Up and Takeaways

The main pattern in the Meteorite Landings dataset is that recorded meteorites are not evenly spread across the world. The point map shows visible clusters in places such as the United States, North Africa, Australia, and Antarctica. These clusters make the map interesting, but they also need to be read carefully because the dataset shows recorded meteorites, not every meteorite that has fallen.

The exploratory charts explain two important choices in the visualizations. First, many records are meteorites that were found later rather than directly observed falling, so discovery and recovery matter. Second, meteorite mass varies widely, so exact mass values are difficult to show clearly on a crowded map. Grouping mass into categories makes the main map easier to read while still preserving the basic size pattern.

The contextual visualizations add more context to the main map. The country and region summary shows that Antarctica has many recorded meteorites, a pattern that is harder to see when individual points overlap. The fireball visualization shows a related but different dataset: atmospheric events can be reported over land or ocean, even when no meteorite is recovered. The recovery image gives a concrete example of what meteorite collection can look like in the field.

Overall, the visualizations show that meteorite records are best understood through multiple views. A point map shows location and individual details, a bar chart shows counts by category, and regional aggregation shows patterns hidden by overlap. Together, these views make the dataset more understandable for a public audience.