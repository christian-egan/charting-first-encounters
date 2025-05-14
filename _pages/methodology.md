---
layout: page
title: Methodology
permalink: methodology
show-title: true
---
# Data Collection
My data derived from Chapters IV and V of Vancouver's *A Voyage of Discovery to the North Pacific Ocean, and Round the World,* as this was the scope of my original incarnation of the project and served as a managable size to introduce myself to spatial analysis and ArcGIS Pro. 

To collect my data, I carefully read through Chapter IV, writing down instances where Vancouver gives his precise location (either via coordinates or the naming prominent geographical features). Because none of Vancouver’s encounters with native peoples were given exact coordinates, I was forced to estimate where each location was on a map. Using my close reading of the chapter, Vancouver’s description of the geography around him, and cross-referencing with satellite images on Google Maps, I was able to approximate where each of the twenty-two listed encounters took place. While there is an inherent degree of imprecision in my methodology, further limited by the frequent lack of clear geospatial information in Vancouver’s work, I am nonetheless confident that each point on my map is within several hundred feet of its true location. This data was placed into a .csv file to be uploaded to ArcGIS.

Chapter V's data consisted of detailed accounts of the region's resources. I simply took careful note of what Vancouver described and where so that I could eventually input this data into my resource regions.

While Vancouver's writing is the first existent written account of Puget Sound's native peoples, it is important to keep in mind that he was writing from a decidedly settler-colonial mindset. While there is some degree of objectivity in his descriptions, the inherent nature of European source describing Indigenous culture cannot be ignored, and this is something that I had to consider throughout my project.

# Step by Step
Below is a brief overview of how my project took shape, using screenshots of key milestones to visualize the process.

![mosaic](https://github.com/user-attachments/assets/b1c94c8f-9784-499a-bf69-b4293ce053cd)
Here, a Digital Terrain Model (DTM) from the Washington State Lidar Portal was uploaded, which includes all of the necessary elevation data to track how the terrain affected Indigenous movement from place to place. White portions have a higher elevation, whereas dark portions are lower. As presented, no meaningful analysis can take place given the mosaic-like pattern of the data. In order to proceed, I needed smooth the raster (i.e., create a unified raster).

![smooth](https://github.com/user-attachments/assets/c2b5fe7d-1c42-42e7-aaef-90448cb6a02b)
Once the raster is unified, as seen above, ArcGIS will consider the totality of the DTM data as one, rather than segments whose elevation varies relative to themselves. I could now create a cost raster using the Cost Distance tool. This effectively uses topography to calculate how difficult it would be to move through a given patch of terrain. This is the crux of a cost-distance analysis. I took this opportunity to create my resource regions, taking the form of pink polygons, as well.

![slope](https://github.com/user-attachments/assets/02ff2244-32fe-4077-9eab-895ffa80a085)
Pictured here is the cost raster, wherein green land is easier to traverse and red is more difficult. With the resource regions set, and the .csv file containing the locations of native encounters uploaded, I was almost ready to perform a cost-distance analysis. First, however, I used a shapefile to clip the raster around the coastline. Otherwise, water would be detected as land. Once the raster was clipped, the Least Cost Path tool was used to chart, with the topography in mind, the easiest route between two points.

![lines](https://github.com/user-attachments/assets/cd1f9ae9-39d6-4f9e-bb5d-20f04fe9e348)
Seen here is the initial Least Cost Path rendering, zoomed to show how a straight line is the most expedient path between the given points. As points get further apart and cross more rugged ground, these lines reveal paths that are otherwise unintuitive at a glance, but were likely known to ad used by Indigenous peoples. Thereafter, the appearance and symbology of these lines could be adjusted to as to make a neater presentation.

![lcp](https://github.com/user-attachments/assets/00923299-4b75-4e14-9825-312c502c1b02)
These are the final two lines that resulted from the Least Cost Path Analysis. The blue line covers solely land routes, whereas the red line includes sea routes as well. Altogether, these lines demonstrate the degree of interconnectedness between Indigenous peoples in the region and the ease by which they might have interacted. From here, I used the Summarize Within tool to visualize the proximity of native sites to resource regions. A larger visualization of this, as well as information about layouts and final renders of the map, can be found on the [New Map page](https://christian-egan.github.io/charting-first-encounters/newmap).
