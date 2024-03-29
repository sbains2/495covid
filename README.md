# GEOG 495 LAB 03

## This repository contains two GeoJSON converted files from COVID-19 shapefile statistics in the United States and displays summary statistics, such as case rates, deaths, and case counts.

### Map1.html description:
Map1.html contains COVID-19 case rate data in the US by county, displayed in choropleth values. Javascript code implements a
hover functionality that displays the number of deaths, as well as the corresonding county name.

__Potential users of this map include public health officials, researchers and academics, as well as the general public to understand the holistic
takeaway of COVID case rate distribution in the United States.__

__Data sources for this map include__

Case Count Data: The COVID-19 case count data is sourced from the U.S. Census Bureau's Explore Census Data platform. The specific dataset used is available at Census.gov.

Conversion of data to GeoJSON: mapshaper. (2024). Mapshaper.org. https://mapshaper.org/

Basemap: Mapbox: Maps, Navigation, Search, and Data. (2023). Mapbox.com. https://www.mapbox.com/

Querying and Formatting the GeoJSON data: Mapbox. (2024). geojson.io | powered by Mapbox. Geojson.io. https://geojson.io/#map=2/0/20

Projection Transformation: The map projection is transformed to Albers equal-area projection using Mapbox's projection-albers-usa API. This ensures accurate representation of area and preserves spatial relationships in the visualization.


### Map2.html description:
Map2.html conveys proportional density of COVID-19 case counts across US counties using a proportional symbol map. The size of the circles corresponds to the number of cases reported in each county, having larger circles showing higher case counts. JavaScript code enables users to view county-level information, including case counts and corresponding county names, by hovering over the circles.

__Potential users of this map include public health officials, researchers, policymakers, and individuals interested in understanding the spatial distribution of COVID-19 cases at a county level.__

Data sources for this map include:

Case/Death Data: covid-19-data/live/us-counties.csv at 43d32dde2f87bd4dafbb7d23f5d9e878124018b8
   nytimes/covid-19-data. (2024). GitHub.
   https://github.com/nytimes/covid-19-data/blob/43d32dde2f87bd4dafbb7d23f5d9e878124018b8/live/us-counties.csv

Case Count Data: The COVID-19 case count data is sourced from the U.S. Census Bureau's Explore Census Data platform. The specific dataset used is available at Census.gov.

Basemap: Mapbox provides the basemap used in this visualization. Mapbox is a platform offering mapping and location data services. More information can be found at Mapbox.com.

Projection Transformation: The map projection is transformed to Albers equal-area projection using Mapbox's projection-albers-usa API. This ensures accurate representation of area and preserves spatial relationships in the visualization.

Querying and Formatting the GeoJSON data: Mapbox. (2024). geojson.io | powered by Mapbox. Geojson.io. https://geojson.io/#map=2/0/20



‌Important Functions:

                map.on('mousemove', 'covid-rates-choropleth', (e) => {
                    const countyProperties = e.features[0].properties;
                    const deaths = countyProperties.deaths || 0;
                    map.getCanvas().style.cursor = 'pointer';
                    popup.setLngLat(e.lngLat)
                        .setHTML(`<strong>${countyProperties.county}, ${countyProperties.state}</strong><br>Deaths: ${deaths}`)
                        .addTo(map);
                });

                map.on('mouseleave', 'covid-rates-choropleth', () => {
                    map.getCanvas().style.cursor = '';
                    popup.remove();
                });
            })
            .catch(error => {
                console.error('Error fetching data:', error);

This function is an event listener that triggers when the mouse moves over or leaves a specific layer on the map called 'covid-rates-choropleth' and for map2.html: 'covid-counts-symbols'.

When the mouse moves over the layer, it retrieves information about the county and state from the features of the layer where the mouse is located. It then displays this information, along with the number of deaths/cases in that county, in a popup that follows the mouse pointer.

When the mouse leaves the layer, it removes the popup and resets the cursor style to its default state.

If any errors occur during the execution of this function, it logs the error message to the console for debugging purposes.

