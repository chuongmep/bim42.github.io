---
id: 1113
title: Modeling Paris with InfraWorks
date: 2017-01-15T16:32:56+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1113
permalink: /2017/01/modeling-paris-with-infraworks/
categories:
  - General BIM
tags:
  - Civil 3D
  - Civil Engineering
  - Cloud
  - InfraWorks
---
It has been a while since I wanted to play with InfraWorks, but I never had the chance, nor any purpose until recently, when I start to ponder on retrieving existing conditions to integrate future buildings in existing conditions, without having to rely on time-consuming on-site surveys.

When starting with InfraWorks, the easiest way to create a model is to use the Model Builder. This feature use data from OpenStreetMap and Microsoft Bing Maps to create fully featured models, with terrain, roads, orthophoto, and so on.

<div id="attachment_1126" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/01/ModelBuilder.png"><img class="size-large wp-image-1126" src="http://bim42.com/wp-content/uploads/2017/01/ModelBuilder-1024x703.png" alt="The Model Builder interface" width="584" height="401" srcset="https://bim42.com/wp-content/uploads/2017/01/ModelBuilder-1024x703.png 1024w, https://bim42.com/wp-content/uploads/2017/01/ModelBuilder-300x206.png 300w, https://bim42.com/wp-content/uploads/2017/01/ModelBuilder-768x527.png 768w, https://bim42.com/wp-content/uploads/2017/01/ModelBuilder-437x300.png 437w, https://bim42.com/wp-content/uploads/2017/01/ModelBuilder.png 1224w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    The Model Builder interface
  </p>
</div>

Using this Model Builder, I quickly create a complete 3D model of Paris.

<div id="attachment_1125" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/01/InitialModel.jpg"><img class="size-large wp-image-1125" src="http://bim42.com/wp-content/uploads/2017/01/InitialModel-1024x672.jpg" alt="The initial model created from OpenStreetMap" width="584" height="383" srcset="https://bim42.com/wp-content/uploads/2017/01/InitialModel-1024x672.jpg 1024w, https://bim42.com/wp-content/uploads/2017/01/InitialModel-300x197.jpg 300w, https://bim42.com/wp-content/uploads/2017/01/InitialModel-768x504.jpg 768w, https://bim42.com/wp-content/uploads/2017/01/InitialModel-457x300.jpg 457w, https://bim42.com/wp-content/uploads/2017/01/InitialModel.jpg 1280w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    The initial model created from OpenStreetMap
  </p>
</div>

However, this model is not accurate enough for any practical application. For example, the 10-stories building where I live is modeled as a 2 levels building. My idea was to use these buildings for site integration and lighting solar studies, but building heights provided by OpenStreetMap is not reliable enough, I had to find another data source.

I am quite envious of the data used to build Google Maps, which can provide us a 3D model of every building, based on [45-degree aerial imagery](https://googleblog.blogspot.fr/2012/06/never-ending-quest-for-perfect-map.html). But these data are obviously not easily available, and I fall back on open data.

APUR, the Paris Urban Planning Agency provide an [Open Data platform](http://cassini.apur.opendata.arcgis.com/) with a lot of datasets about Paris and its suburbs.

Their &#8220;EMPRISE BATIE PARIS&#8221; dataset contains every building in Paris in Shapefile format. Importing it in InfraWorks is quite easy, but this dataset must be configured to map its values with InfraWorks features.

To do so, it is necessary to map the information contained in the dataset to the property of building objects in InfraWorks.

<div id="attachment_1122" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/01/DataSourceConfiguration.png"><img class="size-large wp-image-1122" src="http://bim42.com/wp-content/uploads/2017/01/DataSourceConfiguration-1024x826.png" alt="Configuring the dataset" width="584" height="471" srcset="https://bim42.com/wp-content/uploads/2017/01/DataSourceConfiguration-1024x826.png 1024w, https://bim42.com/wp-content/uploads/2017/01/DataSourceConfiguration-300x242.png 300w, https://bim42.com/wp-content/uploads/2017/01/DataSourceConfiguration-768x620.png 768w, https://bim42.com/wp-content/uploads/2017/01/DataSourceConfiguration-372x300.png 372w, https://bim42.com/wp-content/uploads/2017/01/DataSourceConfiguration.png 1233w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Configuring the dataset
  </p>
</div>

Some properties, like Roof Height, can be easily filled with data coming from the APUR dataset. However, this dataset is far richer than that, and I wanted some specific information, like construction date, to be imported in InfraWorks as custom properties.

To create these custom fields, I have to edit the &#8220;im.schema.json&#8221; file located in &#8220;%USERPROFILE%\Documents\Autodesk InfraWorks Models\Autodesk 360\modelNumber\modelName.files\unver. Using the indications found [here](https://knowledge.autodesk.com/support/infraworks-360/learn-explore/caas/simplecontent/content/custom-properties-infraworks-360.html), I edit this JSON file to create five custom fields for the &#8220;Building&#8221; class in InfraWorks: Construction Date, Refurbishment Date, IHG (Hight-Rise Building), Roof Height Standard Deviation and Roof Type. These fields are then mapped to the corresponding values found in the APUR dataset, using the Table tab in &#8220;Data Source Configuration&#8221;.

<div id="attachment_1123" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/01/DataSourceConfigurationTable.png"><img class="size-large wp-image-1123" src="http://bim42.com/wp-content/uploads/2017/01/DataSourceConfigurationTable-902x1024.png" alt="Mapping custom fileds" width="584" height="663" srcset="https://bim42.com/wp-content/uploads/2017/01/DataSourceConfigurationTable-902x1024.png 902w, https://bim42.com/wp-content/uploads/2017/01/DataSourceConfigurationTable-264x300.png 264w, https://bim42.com/wp-content/uploads/2017/01/DataSourceConfigurationTable-768x871.png 768w, https://bim42.com/wp-content/uploads/2017/01/DataSourceConfigurationTable.png 906w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Mapping custom fields
  </p>
</div>

Since my data contains the type of roofing material of the building, I create a rule to match the appearance of the building with my dataset. These Roof Type values are integers defining a roofing material for every building.

Using great explanations from [here](http://atlandsend.typepad.com/at-lands-end/2011/12/randomizing-data-in-infrastructure-modeler-for-demos-and-show.html), I create a small script to map these values to a roofing material in InfraWorks, with a switch command on the type of roof described in the dataset.

<pre>//Added by me

switch (SOURCE["C_TOITDOM"])
{
case 0: BUILDINGS.ROOF_MATERIAL = "Material/Roofing/Spanish Tile Brown";
break;
case 1: BUILDINGS.ROOF_MATERIAL = "Material/Roofing/Spanish Tile Brown";
break;
case 2: BUILDINGS.ROOF_MATERIAL = "Material/Roofing/Zinc";
break;
case 3: BUILDINGS.ROOF_MATERIAL = "Material/Roofing/Slate Grey";
break;
case 4: BUILDINGS.ROOF_MATERIAL = "Material/Roofing/Masonry Stone Black";
break;
case 5: BUILDINGS.ROOF_MATERIAL = "Material/Roofing/Grass Augustine";
break;
default: BUILDINGS.ROOF_MATERIAL = "Material/Roofing/Spanish Tile Brown";
}</pre>

&nbsp;

Most of Paris buildings have a very characteristic zinc roof, a material that is not available by default in InfraWorks.

<div id="attachment_1128" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/01/ParisRoofs.png"><img class="size-large wp-image-1128" src="http://bim42.com/wp-content/uploads/2017/01/ParisRoofs-1024x768.png" alt="Typical Parisian roofs" width="584" height="438" srcset="https://bim42.com/wp-content/uploads/2017/01/ParisRoofs-1024x768.png 1024w, https://bim42.com/wp-content/uploads/2017/01/ParisRoofs-300x225.png 300w, https://bim42.com/wp-content/uploads/2017/01/ParisRoofs-768x576.png 768w, https://bim42.com/wp-content/uploads/2017/01/ParisRoofs-400x300.png 400w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Typical Parisian roofs
  </p>
</div>

Using the style palette, I create my own zinc material from a picture and a few settings.

<div id="attachment_1127" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/01/ZincMaterial.png"><img class="size-large wp-image-1127" src="http://bim42.com/wp-content/uploads/2017/01/ZincMaterial-1024x735.png" alt="Creating a custom &quot;Zinc&quot; material" width="584" height="419" srcset="https://bim42.com/wp-content/uploads/2017/01/ZincMaterial-1024x735.png 1024w, https://bim42.com/wp-content/uploads/2017/01/ZincMaterial-300x215.png 300w, https://bim42.com/wp-content/uploads/2017/01/ZincMaterial-768x551.png 768w, https://bim42.com/wp-content/uploads/2017/01/ZincMaterial-418x300.png 418w, https://bim42.com/wp-content/uploads/2017/01/ZincMaterial.png 1135w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Creating a custom &#8220;Zinc&#8221; material
  </p>
</div>

My final experiment was to use the Feature Themes tab to display construction dates for Parisian buildings.

This function allows me to add a color scheme to my buildings to display values, here the construction date.

![FeatureThemes](http://bim42.com/wp-content/uploads/2017/01/FeatureThemes.png)

The result in quite compelling, every building is displayed in color per its construction date.

<div id="attachment_1121" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/01/ConstructionDate.jpg"><img class="size-large wp-image-1121" src="http://bim42.com/wp-content/uploads/2017/01/ConstructionDate-1024x780.jpg" alt="Displaying construction dates" width="584" height="445" srcset="https://bim42.com/wp-content/uploads/2017/01/ConstructionDate-1024x780.jpg 1024w, https://bim42.com/wp-content/uploads/2017/01/ConstructionDate-300x228.jpg 300w, https://bim42.com/wp-content/uploads/2017/01/ConstructionDate-768x585.jpg 768w, https://bim42.com/wp-content/uploads/2017/01/ConstructionDate-394x300.jpg 394w, https://bim42.com/wp-content/uploads/2017/01/ConstructionDate.jpg 1103w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Displaying construction dates
  </p>
</div>

Building models of entire cities is incredibly easy with InfraWorks, and as long as you have correct data sources, it seems to be the perfect tool to re-create the environment for your studies.