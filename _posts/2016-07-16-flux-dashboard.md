---
id: 1067
title: Flux Dashboard
date: 2016-07-16T15:57:40+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1067
permalink: /2016/07/flux-dashboard/
categories:
  - Dynamo
tags:
  - Dynamo
  - Flux
  - Visualization
---
Since [my last article](http://bim42.com/2015/09/flux/), [Flux](https://flux.io/) has made a lot of progress. Along with their plugins for Excel, Grasshopper and Dynamo, the Flux team has recently released their connectors for Revit and SketchUp. They are also developing [a series of tools](https://labs.flux.io/) that use the Flux platform for calculations or specific collaboration tasks.

Among these tools, [Thomas](https://twitter.com/thomastrinelle) points me to the Live Data Dashboard, a real-time visualization tool for your Flux data.

I have tried various solution for displaying data extracted from a Revit model, from Excel spreadsheet to Tableau, but these solutions generally fell short when it comes to real-time update. The Dashboard can be a solution, since its values always reflect the latest Flux values.

After login with my Flux account into the Flux Dashboard, I was able to select a Data Key from one of my project as a data source for a bar chart.

![<img class="aligncenter size-large wp-image-1071" src="http://bim42.com/wp-content/uploads/2016/07/Image-1024x645.png" alt="Image" width="584" height="368" srcset="https://bim42.com/wp-content/uploads/2016/07/Image-1024x645.png 1024w, https://bim42.com/wp-content/uploads/2016/07/Image-300x189.png 300w, https://bim42.com/wp-content/uploads/2016/07/Image-768x484.png 768w, https://bim42.com/wp-content/uploads/2016/07/Image-476x300.png 476w, https://bim42.com/wp-content/uploads/2016/07/Image.png 1566w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/07/Image.png)

Using properties extracted from the Rooms of one of my project, I tried to display my 951 rooms all at one, and came up with a rather messy chart:

![<img class="aligncenter size-large wp-image-1068" src="http://bim42.com/wp-content/uploads/2016/07/Image-1-1024x735.png" alt="Image [1]" width="584" height="419" srcset="https://bim42.com/wp-content/uploads/2016/07/Image-1-1024x735.png 1024w, https://bim42.com/wp-content/uploads/2016/07/Image-1-300x215.png 300w, https://bim42.com/wp-content/uploads/2016/07/Image-1-768x551.png 768w, https://bim42.com/wp-content/uploads/2016/07/Image-1-418x300.png 418w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/07/Image-1.png)

The problem here is that the Flux dashboard does not support values that are not in a tabular format, with mean you cannot yet use directly the value uploaded from the Revit plugin. Furthermore, the Dashboard does not process any of the data you are feeding in, so you have to prepare your visualization beforehand, in Dynamo or in the Flux Flow.

I go back to the Dynamo plugin, and use a rather simple definition to retrieve all rooms, and regroup key values in nested lists. I use the List.GroupByKey node to regroup rooms’ area per level, and create a list of levels, with the number of room and their area in each level.

![<img class="aligncenter size-full wp-image-1072" src="http://bim42.com/wp-content/uploads/2016/07/List2.png" alt="List2" width="795" height="546" srcset="https://bim42.com/wp-content/uploads/2016/07/List2.png 795w, https://bim42.com/wp-content/uploads/2016/07/List2-300x206.png 300w, https://bim42.com/wp-content/uploads/2016/07/List2-768x527.png 768w, https://bim42.com/wp-content/uploads/2016/07/List2-437x300.png 437w" sizes="(max-width: 795px) 100vw, 795px" />](http://bim42.com/wp-content/uploads/2016/07/List2.png)

I upload these values in a new Flux Data Key, and use this Data Key as a source for a new, and way more interesting Chart Bar.

![<img class="aligncenter size-full wp-image-1069" src="http://bim42.com/wp-content/uploads/2016/07/Image-2.png" alt="Image [2]" width="874" height="790" srcset="https://bim42.com/wp-content/uploads/2016/07/Image-2.png 874w, https://bim42.com/wp-content/uploads/2016/07/Image-2-300x271.png 300w, https://bim42.com/wp-content/uploads/2016/07/Image-2-768x694.png 768w, https://bim42.com/wp-content/uploads/2016/07/Image-2-332x300.png 332w" sizes="(max-width: 874px) 100vw, 874px" />](http://bim42.com/wp-content/uploads/2016/07/Image-2.png)

Once the values are properly sorted in Dynamo, they fit nicely on the graph, and are automatically updated as the values evolve in our Revit model.

Using the same principle, I add a few node to my Dynamo definition, and upload the resulting values to the Dashboard.

![<img class="aligncenter size-large wp-image-1070" src="http://bim42.com/wp-content/uploads/2016/07/Image-3-1024x653.png" alt="Image [3]" width="584" height="372" srcset="https://bim42.com/wp-content/uploads/2016/07/Image-3-1024x653.png 1024w, https://bim42.com/wp-content/uploads/2016/07/Image-3-300x191.png 300w, https://bim42.com/wp-content/uploads/2016/07/Image-3-768x490.png 768w, https://bim42.com/wp-content/uploads/2016/07/Image-3-470x300.png 470w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/07/Image-3.png)

I also try to display geometry in the Flux Viewport, but for some reason, I wasn't able to see anything on the dashboard. I will have to keep trying on this one.

After having built this great dashboard, it is pretty easy to share it, using a Flux Data Key to store it. You just have to make sure everyone has access to all the projects linked to the dashboard.

The Flux Dashboard is a great idea. As long as you use Flux as the main data repository, the Flux Dashboard can display is fair share of information to everyone without having to dig into the models. However, the Flux dashboard is not (yet) an Excel spreadsheet, and won't regroup or sort your data directly, and you still have some work upfront to prepare this data for visualization.