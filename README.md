# Vehicle Route Optimization System

This project implements a real-world vehicle route optimization system using Google OR-Tools and OpenStreetMap data via the OSMnx library. It solves a single-depot Traveling Salesman Problem (TSP) based on actual road networks and travel times, and visualizes optimized routes using Plotly and Folium.

## Features

- Uses real geographic road data from OpenStreetMap.
- Computes accurate travel-time-based distance matrices using Dijkstra's algorithm.
- Solves TSP using Google's OR-Tools.
- Visualizes route on a map (Folium).
- Provides animated route progression using Plotly.
- Supports spatial data operations and GeoDataFrame-based manipulation.

## Problem Overview

Given a depot (start location) and a list of retail stores in a city, the goal is to compute the most efficient route that visits all locations exactly once and returns to the start. The optimization is based on **travel time** instead of Euclidean or haversine distance, making the solution more realistic for urban logistics.

---

## Technologies Used

- **Python**
- **Google OR-Tools** – route optimization solver
- **OSMnx** – download and process OpenStreetMap road network
- **NetworkX** – graph algorithms (Dijkstra)
- **Folium** – map visualization
- **Plotly Express** – animated route plotting
- **GeoPandas** – geospatial route segment analysis
- **Pandas / NumPy / Seaborn** – data manipulation and heatmaps

---

## How It Works

### 1. Data Preparation

- Load store location data from CSV (`data/data_stores.csv`).
- Filter to a specific city (e.g., New Delhi).
- Convert lat/lon to node IDs on the OSM road graph.

### 2. Road Network Construction

- Download road network around the depot using `osmnx.graph_from_point()`.
- Add edge speeds and compute `travel_time` weights.
- Map each location to its nearest OSM node.

### 3. Travel Time Matrix

- Use Dijkstra’s algorithm (`networkx.shortest_path_length`) to compute pairwise travel times between nodes.
- Store result in a matrix and visualize as a heatmap using Seaborn.

### 4. Route Optimization

- Use Google OR-Tools' routing solver (`pywrapcp`) to solve TSP.
- Register a custom cost function using the travel-time matrix.
- Extract the optimized route (node order and total travel time).

### 5. Visualization

- Use Folium to display store locations and depot.
- Reconstruct path segments for the optimized route using NetworkX.
- Plot animated route movement in Plotly.
- Explore full route geometry using GeoPandas.

---

## Outputs

- **Total travel time**
- **Ordered list of visited nodes**
- **Static and interactive maps**
- **Animated driver movement (Plotly map animation)**

---


