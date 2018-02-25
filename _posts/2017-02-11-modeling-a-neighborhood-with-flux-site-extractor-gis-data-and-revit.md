---
id: 1131
title: Modeling a neighborhood with Flux Site Extractor, GIS data and Revit
date: 2017-02-11T20:47:17+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1131
permalink: /2017/02/modeling-a-neighborhood-with-flux-site-extractor-gis-data-and-revit/
categories:
  - Revit
tags:
  - Flux
  - GIS
  - Plugin
  - Revit
---
Since [my last post](http://bim42.com/2017/01/modeling-paris-with-infraworks/), I kept on working on urban development. I particularly think about importing GIS data into our usual authoring tools. My experience with Infraworks was interesting, but it is still difficult to use this data in a Revit model.

The most promising resource out there for creating a context in a Revit model is the [Flux Site Extractor](https://labs.flux.io/extractor/). You select an area, add some features to extract and send them to a Flux project.

<div id="attachment_1132" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/02/01-Flux-Site-EXtractor.png"><img class="size-large wp-image-1132" src="http://bim42.com/wp-content/uploads/2017/02/01-Flux-Site-EXtractor-1024x820.png" alt="" width="584" height="468" srcset="https://bim42.com/wp-content/uploads/2017/02/01-Flux-Site-EXtractor-1024x820.png 1024w, https://bim42.com/wp-content/uploads/2017/02/01-Flux-Site-EXtractor-300x240.png 300w, https://bim42.com/wp-content/uploads/2017/02/01-Flux-Site-EXtractor-768x615.png 768w, https://bim42.com/wp-content/uploads/2017/02/01-Flux-Site-EXtractor-374x300.png 374w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    The Flux Site Extractor interface
  </p>
</div>

After retrieving this data in my Flux Site Project, I use the [Flux Dynamo nodes](https://drive.google.com/file/d/0B_fvbfIWQ5JJMTVLbUtxUGxfZ2M/view?usp=sharing) to get the topography as a mesh, extract the vertices of this mesh as points and use these points to create a toposurface in Revit.

<div id="attachment_1133" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/02/02-Toposurface-from-Flux.png"><img class="size-large wp-image-1133" src="http://bim42.com/wp-content/uploads/2017/02/02-Toposurface-from-Flux-1024x540.png" alt="" width="584" height="308" srcset="https://bim42.com/wp-content/uploads/2017/02/02-Toposurface-from-Flux-1024x540.png 1024w, https://bim42.com/wp-content/uploads/2017/02/02-Toposurface-from-Flux-300x158.png 300w, https://bim42.com/wp-content/uploads/2017/02/02-Toposurface-from-Flux-768x405.png 768w, https://bim42.com/wp-content/uploads/2017/02/02-Toposurface-from-Flux-500x264.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Creating a toposurface from the Flux Site Extractor
  </p>
</div>

Building profiles and heights came from OpenStreetMap, and aren&#8217;t accurate enough to be used for site analysis. But I am using building profiles to draw on a plan view the footprint of every building retreived with Flux. This will help me futher down the road to align my buildings on the toposurface.

<div id="attachment_1134" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/02/03-Buildings-Footprints.png"><img class="size-large wp-image-1134" src="http://bim42.com/wp-content/uploads/2017/02/03-Buildings-Footprints-1024x567.png" alt="" width="584" height="323" srcset="https://bim42.com/wp-content/uploads/2017/02/03-Buildings-Footprints-1024x567.png 1024w, https://bim42.com/wp-content/uploads/2017/02/03-Buildings-Footprints-300x166.png 300w, https://bim42.com/wp-content/uploads/2017/02/03-Buildings-Footprints-768x425.png 768w, https://bim42.com/wp-content/uploads/2017/02/03-Buildings-Footprints-500x277.png 500w, https://bim42.com/wp-content/uploads/2017/02/03-Buildings-Footprints.png 1370w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Buildings footprints drawn in a plan view
  </p>
</div>

I found more accurate data on the parisian buildings on the [APUR Open Data plateform](http://cassini-apur.opendata.arcgis.com/). I download this data as a shapefile containing every building in Paris.

Obviously, this dataset is too large to be imported as it in Revit. I am using [QGIS](http://www.qgis.org/en/site/), an open source GIS application, to extract a subset of this file. To do so, I draw a polygon encompassing the few city blocks I want to retrieve and use the &#8220;Clip&#8221; function to create a new shapefile containing only the selected buildings.

<div id="attachment_1135" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/02/03-Isolate-Buildings-Blocks.png"><img class="size-large wp-image-1135" src="http://bim42.com/wp-content/uploads/2017/02/03-Isolate-Buildings-Blocks-1024x511.png" alt="" width="584" height="291" srcset="https://bim42.com/wp-content/uploads/2017/02/03-Isolate-Buildings-Blocks-1024x511.png 1024w, https://bim42.com/wp-content/uploads/2017/02/03-Isolate-Buildings-Blocks-300x150.png 300w, https://bim42.com/wp-content/uploads/2017/02/03-Isolate-Buildings-Blocks-768x383.png 768w, https://bim42.com/wp-content/uploads/2017/02/03-Isolate-Buildings-Blocks-500x249.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Isolate the propers city blocks
  </p>
</div>

I am using the [DynamoGIS](https://github.com/sharadkjaiswal/DynamoGIS) package to import this shapefile into Revit. These nodes allow me to read the file and extract the shapes of the buildings.

The most difficult thing here was to include inner boundaries in a building shape. These boundaries are not taken into account by the Surface.ByPatch node. I manage to split the first surface (the largest) using the inner curve. This allow me to create the hollowed surface.

<div id="attachment_1136" style="max-width: 1014px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/02/04-Inner-boundaries.png"><img class="size-full wp-image-1136" src="http://bim42.com/wp-content/uploads/2017/02/04-Inner-boundaries.png" alt="" width="1004" height="582" srcset="https://bim42.com/wp-content/uploads/2017/02/04-Inner-boundaries.png 1004w, https://bim42.com/wp-content/uploads/2017/02/04-Inner-boundaries-300x174.png 300w, https://bim42.com/wp-content/uploads/2017/02/04-Inner-boundaries-768x445.png 768w, https://bim42.com/wp-content/uploads/2017/02/04-Inner-boundaries-500x290.png 500w" sizes="(max-width: 1004px) 100vw, 1004px" /></a>
  
  <p class="wp-caption-text">
    Highlight of inner boundaries
  </p>
</div>

The DynamoGIS include nodes to query any value associated with shapes. I am using them to retrieve building heights in the dataset and extrude my buildings at their proper height.

Since it is GIS data, I am using a nice tip from [LandArch](https://landarchbim.com/2016/06/15/import-shapefiles-with-dynamogis/) to move my geometry near the project base point, and make it usable in Revit.

I am using the FamilyInstance.ByGeometry node from the great [Spring nodes](https://dynamonodes.com/2016/01/28/what-is-spring-nodes/) of [Dimitar Venkov](https://twitter.com/5devene?lang=en) to create the buildings as mass families.

[This Dynamo definition](https://drive.google.com/file/d/0B_fvbfIWQ5JJeExWd0szejFtM1k/view?usp=sharing) create a mass family for every building in the shapefile, extruded up to its actual height. Combined with the toposurface created with Flux, this look like an actual neighborhood, where you can think about massing and site integration directly in Revit.

<div id="attachment_1137" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/02/05-Site-integration.png"><img class="size-large wp-image-1137" src="http://bim42.com/wp-content/uploads/2017/02/05-Site-integration-1024x686.png" alt="" width="584" height="391" srcset="https://bim42.com/wp-content/uploads/2017/02/05-Site-integration-1024x686.png 1024w, https://bim42.com/wp-content/uploads/2017/02/05-Site-integration-300x201.png 300w, https://bim42.com/wp-content/uploads/2017/02/05-Site-integration-768x515.png 768w, https://bim42.com/wp-content/uploads/2017/02/05-Site-integration-448x300.png 448w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Site integration of a project
  </p>
</div>

This process still has a few issues. The buildings aren&#8217;t adjusted at the toposurface and aligning them with the toposurface created with the Flux Site Extractor involve some manipulations. I still have some work to do on this process to streamline it, and get a more accurate representation of an existing site.

<div id="attachment_1138" style="max-width: 1010px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/02/06-Site-intégration.png"><img class="size-full wp-image-1138" src="http://bim42.com/wp-content/uploads/2017/02/06-Site-intégration.png" alt="" width="1000" height="601" srcset="https://bim42.com/wp-content/uploads/2017/02/06-Site-intégration.png 1000w, https://bim42.com/wp-content/uploads/2017/02/06-Site-intégration-300x180.png 300w, https://bim42.com/wp-content/uploads/2017/02/06-Site-intégration-768x462.png 768w, https://bim42.com/wp-content/uploads/2017/02/06-Site-intégration-500x300.png 500w" sizes="(max-width: 1000px) 100vw, 1000px" /></a>
  
  <p class="wp-caption-text">
    Another view of the project
  </p>
</div>

&nbsp;