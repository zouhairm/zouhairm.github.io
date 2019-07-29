---
layout: proj
author: zouhair
image: projects/divethedata.jpg
imageLink: https://www.divethedata.com
tags: [webdev, datavisualization]
title: Dive The Data
venue: Mozambique, 2018
contributors: Dan Vallentyne
description: An Interactive Data Visualization tool for sightings of Marine MegaFauna.
  
links:
  - title: Dive The Data
    url: https://www.divethedata.com
  - title: DanVallentyne
    url: http://danvallentyne.com/work/divethedata/
  - title: MarineMegaFauna
    url: https://marinemegafauna.org

featured: true
---
This was a project during my volunteering with the Marine Megafauna Foundation (MMF). In collaboration with Dan, we prototyped and built a website to help dive centers interested in contributing to citizen science highlight their data.

MMF studies and protects mantas, and other megafauna in both of these countries. Amongst their many programs, they dive with partner organizations providing research assistants who act as naturalists on dive boats. Staff at some of these dive centers began collecting sightings data on the animals they were seeing and asked MMF to help manage the data entry and storage.

We decided to build a project around the data as a pilot for a citizen science database. The goal is for it to grow into an open database for dive centers around the world to contribute sightings to. Currently, the database tracks 30 species from three regions: Tofo in Mozambique, and the Bali and Komodo Islands of Indonesia. Each region has several dive centers that contribute to the sightings data. Sightings are tracked to the dive site, and over time trends at the different dive sites become apparent in the data.

The data is visualized using <a href="https://plot.ly">Plotly</a> and <a href="https://plot.ly/products/dash/">Dash</a>. Three Plotly cross graphs, meaning what you select in one graph is reflected in the other two, make it possible to explore the data. 
