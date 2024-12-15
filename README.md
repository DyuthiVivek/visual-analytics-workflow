# Visual Analytics workflow

The goal of this task is to understand and evaluate
artist popularity using artist collaboration data, song
streaming metrics from different platforms and predicting
future trends.

Datasets:
- https://www.kaggle.com/datasets/joebeachcapital/30000-spotify-songs?select=spotify_songs.csv

- https://www.kaggle.com/datasets/abdulszz/spotify-most-streamed-songs


- https://www.kaggle.com/datasets/yelexa/spotify200

This workflow revealed that artist popularity is multifaceted
and is influenced by collaboration, cross-genre experimentation, and platform-specific trends. Some of the major takeaways are listed below.

- Collaboration influences popularity: Visualizations of
artist networks revealed a strong correlation between collaboration and popularity. Artists in highly interconnected clusters, particularly those in the central network, tend
to have higher ”count above threshold” values and total
streams.
- Diverse genres and cross-platform success: Popular artists
often diversify their genres, collaborating across different
styles
in Assignment-1.
- Spikes in popularity tied to releases: Time-series data
in Fig 3.6 in Part-2 and Fig 3.8 in Part-
1 highlighted that contemporary artists experience sharp
spikes in popularity tied to major releases. These spikes
are often amplified by playlist inclusions on platforms
like Spotify.
- Clustering based on musical features and streaming metrics: It revealed distinct groups. Popular artists are not
confined to a single genre but often span multiple dimensions of success.
- Forecasting trends by clusters: Predictive modeling for
artist clusters, rather than individual artists, provided
insights into generalized trends. Legacy artists in Cluster
4 are predicted to maintain steady popularity, while others
exhibit variability tied to potential new releases.

## Installation

To install the required Python modules, run the following command:

```bash
pip install -r requirements.txt
```

Install [gephi](https://gephi.org/) 


### Steps to Execute  

### Part-1
### 1. Visualizations
`artist.twbx` is a Tableau workbook with the visualizations. The images are in `images-part1/`.

The images are:
  - 3.1 - Bar Chart depicting the top 20 artists based on average track popularity. X axis - Track popularity, Y axis - Artist name
  - 3.2 - Bar Chart depicting the top 20 artists based on count above threshold. X axis - Count above threshold, Y axis - Artist name
         Count above threshold is a calculated field quantify how many tracks an artist has with a popularity score greater than a specific threshold (75th percentile of track popularity)

Marks and channels used for 3.1 and 3.2 - Bars, grouped by artist and length of the bar shows popularity/count, with artists labeled on the Y-axis.
Reason: Bar charts make it easy to compare the top artists based on the selected measure (average popularity, count above threshold).

  - 3.3 - Scatter plot for count above threshold vs track count per artist. Each point represents an artist. Artists have been grouped into tiers (lesser known, mid-tier, popular) <br>
          • count above threshold ≥ 13 - top tier artist <br>
          • count above threshold ≥ 2 - mid tier artist <br>
          • count above threshold < 2 - lesser known artist <br>
  - 3.4 - Scatter plot for average track popularity vs track count per artist. Each point represents an artist. Artists have been grouped into tiers (lesser known, mid-tier, popular) <br>
          • average track popularity ≥ 75 - top tier artist <br>
          • average track popularity ≥ 50 - mid tier artist <br>
          • average track popularity < 50 - lesser known artist <br>
  - 3.5 - Scatter plot for relationship between the two different popularity measures, grouped by artist tier. X axis - Track popularity, Y axis - count above threshold. Each point represents an artist.

Marks and channels used for 3.3, 3.4, 3.5 - Points, grouped by artist and position on the X and Y axes for the artist's popularity/track count, grouped by tiers. Each tier is represented by a colour.
Reason: Scatter plots clearly show trends and outliers, highlighting relationships between popularity measures and track count.

  - 3.6 - Heatmap for songs by top artists, genre-wise. Darker the colour more the songs released by the artist for the genre.

Marks and channels used for 3.6 - Colour gradient, grouped by artist and genre, darker colour intensity represents more songs.
Reason: Heatmaps effectively show song distribution across genres, emphasizing concentration of releases by artists

  - 3.6.1 to 3.6.6 - Tree map for the top songs genre wise, grouped by artist. Darker the colour, more the top songs released by the artist for the genre. <br>
          Note - In the report, only 3.6.1 and 3.6.2 were displayed to contrast between two genres <br>
          3.6.1 - EDM <br>
          3.6.2 - R&B <br>
          3.6.3 - Latin <br>
          3.6.4 - Pop <br>
          3.6.5 - Rap <br>
          3.6.6 - Rock <br>
Marks and channels used for 3.6.1 to 3.6.6 - coloured blocks representing artists' song counts and colour intensity reflects the number of top songs by an artist in a genre.
Reason: Treemaps give an overview of artists' dominance within genres.

  - 3.7  - Plot of 3 musical features for top artists (acousticness, danceability, loudness) taken as an average over all the songs of the artist. Polygon marks are chosen to help visualize how an artist’s song features compare to others.

Marks and channels used for 3.7 - Polygons, with vertices representing feature averages (acousticness, danceability, loudness) and different colours used for different features
Reason: Polygons allow easy comparison of multiple musical features for different artists.

  - 3.8 - Line chart of artist popularity trends for the top 7 artists. Line charts are ideal for visualizing changes over time, helping us see trends in how artists maintain or lose popularity. By focusing on a few top artists, this chart avoids overcrowding and clearly shows shifts over years.
  - 3.9 - Line chart for number of popular songs released year-wise, grouped by artist popularity tier

Marks and channels used for 3.8 and 3.9 - Lines, with points representing artist popularity over time or the number of popular songs per year. Colour is used in 3.9 to differentiate between different artist tiers.
Reason: Line charts are best for showing trends over time


### Part-2
### 2. Generate Artist Popularity Data  
Run `count_above_threshold.py` to process `spotify_songs.csv` and generate `artists.csv`.  
This file contains the calculated artist popularity metrics required for further analysis.  

### 3. Visualize Artist Collaboration Network  
Download the file from https://www.kaggle.com/datasets/yelexa/spotify200. 

Run `graph_visualizations.py` to process collaboration data and generate the following:  
  - `cleaned_regional_data.csv`: Artist collaboration data used in the forecasting model.  
  - `filtered_nodes.csv` and `filtered_edges.csv`: Input files for graph visualizations in Gephi.  

### 4. **Graph Visualizations**:  
  The Gephi project (`collab_graph.gephi`) contains the network visualizations of artist collaborations using `filtered_nodes.csv` and `filtered_edges.csv`.  
  - **Graph Images**:  
    - `3.2.png`, `3.3.png`, `3.4.png`, and `3.5.png`: Various views of the artist collaboration network.  
    - `3.5.png` is a zoomed-in version of `3.5.1.png` for better clarity.  

### 5. Generate Clustering and Forecasting Visualizations  
Run `models.py` to generate the following visualizations:  
- **Line Graph (Artist Popularity Over Time)**:  
  - `3.6.png`: Trends in artist popularity over time.  

- **Clustering Model Visualizations**:  
  - `3.7.png`, `3.8.png`, and `3.9.png`: Visual representations of artist clusters (K-Means) after PCA.  

- **Forecasting Model Visualizations**:  
  - `3.10.png`, `3.11.png`, `3.12.png`, `3.13.png`, and `3.14.png`: Forecasting results for each cluster using the Prophet forecasting model.  


The input files are:
- `spotify_songs.csv`: Dataset used for calculating artist popularity.  
- `final.csv`: File for collaboration analysis and graph generation.  
- `Spotify Most Streamed Songs.csv`: File with playlist and chart data across different platforms.

The files generated are:
- `artists.csv`: Contains artist popularity metrics.  
- `cleaned_regional_data.csv`: Collaboration data for forecasting.  
- `filtered_nodes.csv` and `filtered_edges.csv`: Files for Gephi network visualizations.  

The images are in `images-part2/`.
The images generated are:
- Unrolled visual analytics feedback loop: `3.1.png` 
- Collaboration graphs: `3.2.png` to `3.5.png` (and `3.5.1.png`).  
- Line graph (popularity trends): `3.6.png`.  
- Clustering visualizations: `3.7.png` to `3.9.png`.  
- Forecasting visualizations: `3.10.png` to `3.14.png`.  

Gephi Project:  
- `collab_graph.gephi`: View graphs of artist collaborations in Gephi.

Report:
Task-3 in the first and second parts in `Report.pdf` describe the workflow and the inferences.