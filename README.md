#### MUSA 6950 Final Project

# **Flood Risk Mapping and Socio-Spatial Vulnerability Assessment** 🌊


![Firefly doodle of a map with water, zoomed into a city (like an aerial), and title that says -flood -2](https://github.com/user-attachments/assets/b6b32d64-5695-4d0f-b0f1-33b55b09b5c0)



***

## ✦ Introduction
With the intensification of climate change and urbanization, urban flooding possesses a growing threat for cities globally, especially those located in proximity to hydrological sources. 

While the warming of the atmosphere and oceans are often placed at the forefront of climate change, implications concerning the phenomenon are not limited to increasing temperatures and rather encompass a spectrum of direct and indirect effects. Foremost, metrological conditions, numerous societal sectors, and natural ecosystems will all bear the impact of climate change. Warmer temperature conditions will accelerate the rate of evaporation, thus enhancing the availability of water vapor; this trend will cater towards more probable precipitation and extreme weather events. In combination, rapid urbanization world-wide introduces another point of vulnerability. As such, many urban areas do not retain adequate drainage systems, and the increase in various impervious surfaces (i.e., roads, developed land) will magnify any potential flooding events. In addition, an increase in urban populations places more individuals at risk. 

Nevertheless, historically marginalized groups are often confided to areas with rather poor housing conditions and are segregated to extents within floodplains. Therefore, understanding how land use patterns contribute to general flood risk, and how these risks intersect with various sociodemographic factors, is crucial for developing equitable, climate-resilient cities. 

### ✧ Objective
This project aims to assess the intersection of environmental hazards and social vulnerability in two coastal U.S. cities—Providence, Rhode Island, and Boston, Massachusetts. The goal is to evaluate how flood risk correlates with land use patterns and whether specific sociodemographic groups face disproportionate exposure to inundation hazards.

***

### ✧ Datasets

To conduct this analysis, multiple geospatial were utilized:
- **USGS Digital Elevation Model** (DEM) Tiles
- **NLCD Land Use**
- **City Boundary** Shapefiles: Providence and Boston
- **Hydrology** Shapefiles: Rivers, Oceans, Ponds, etc. 
- **ACS Census Block-Groups**: Race

### ✧ Tools & Software
- **Python**: Hydrological Processing, Raster Analysis, Modeling, Scripting
- **ArcGIS & QGIS**: Data Clipping/Processing, Visualization, Data Collection

## ✦ Methodology

The study sites for this analysis include Providence, Rhode Island and Boston, Massachusetts. The goal was to accomplish the study across two different cities, to equally compare how [coastal] inundation affects varying demographic groups (i.e., assess bias in vulnerability). 

**Preliminary / Exploratory Analysis**
-	Retrieve shapefile boundaries and hydrological features for selected cities  
-	Download DEM for specific areas (via API call in Python / USGS website, *mosaic tiles if needed*)
-	Download Land Use (NLCD)
-	Download Block-Group Level Demographic Data
-	Clip data to study sites, reproject (via rasterio / QGIS)

**Hydrological**
-	Fill in any sinks in DEM data
-	Calculate hydrological parameters (*Flow direction and accumulation*) 
-	Generate HAND Model
- Apply specific threshold (i.e., 0.5, 1, 2, 3, 4, 5 m), to delineate potential flood zones 

**Land Use**
- Determine land use distribution and percent coverage per type
- Spatial overlay (i.e., via rasterstats, zonal_stats, geopandas) 
- Calculate proportion of each land usage within flood zones (*for each inundation threshold*)

**Societal Implications - Demographics**
-	Determine prominent race groups per block-group and total percentage
- Spatial overlay (i.e., via rasterstats, zonal_stats, geopandas) 
-	Calculate proportion of each race group within flood zones (*for each inundation threshold*)

***

## ✦ Key Results & Findings

**General Flooding**
- Providence becomes more flooded at the highest indunation threshold than Boston.
- **Providence**: 0.5 m Threshold = 24.78% v. 5 m Threshold = 74.23%
- **Boston**: 0.5 m Threshold = 24.50% v. 5 m Threshold = 64.69%
- *However, the overall topology and size of the cities need to be factored in*



<img width="476" alt="image" src="https://github.com/user-attachments/assets/f1a52f45-6ad7-4b5d-84e8-0feaddc8f316" />

(*Inundation map for Providence*)

**Flooding v. Land Use**
- For both cities, 'Developed Land' consistently constituded greater portion of the inundated land for all thresholds
- Typically composing >40% of total inundated land

**Flooding v. Demographics**
- In Providence, prominent race in block-groups included White and Hispanic/Latino
- As the inundation threshold increased **White** populations became more vulnerable (i.e., greater portion of those block-groups were covered by simulated inundation)
- In Boston, prominent race in block-groups included White, Hispanic/Latino, Multi-racial, Asian and Black
- As the inundation threshold increased **Hispanic/Latino** and **Black** populations became more vulnerable

***

## ✦ Conclusion & Next Steps

Development alone (i.e., the 'built' environment, etc.) does not “*cause*” flooding in the sense of generating storms, rain, or sea level rise. However, it does increases vulnerability and severity of impacts. Furthermore, local topography plays a crucial role in flood risk.

Racial disparities in flood vulnerability were evident in **Boston** but not in **Providence**, suggesting that the relationship between race and flood risk is shaped by local patterns of segregation, development, and infrastructure investment.

Future resilience efforts should prioritize equitable adaptation, integrating land use planning, green infrastructure, and community-driven strategies to reduce both physical and social vulnerabilities to flooding.

**Future research** should target: 

a) Modeling
- Incorporate more advanced hydrological models
- Test accuracy of models (i.e., HAND) against observed flood records [FEMA] & improving quality

b) Socioeconomic Integration & Broader Replicability
- Checking trends of racial disparities in different cities
- Expanding to other sociodemographic factors (i.e., poverty, ownership, income)

***

### ✧ StoryMap

View the StoryMap for this project here: https://storymaps.arcgis.com/stories/50d78d63ac2e43bca40afc981dfdaa99

