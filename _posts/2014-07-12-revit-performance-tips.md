---
id: 481
title: Revit Performance Tips
date: 2014-07-12T08:00:24+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=481
permalink: /2014/07/revit-performance-tips/
categories:
  - Revit
tags:
  - Autodesk
  - BIM Manager
  - Revit
---
A regular complain about Revit is its slowness. If this can be a psycological problem coming from people used to the quick reaction time of AutoCAD, it can also become a real problem when working with large models on short deadlines.

I&#8217;m use to separate Revit performance in two parts, opening the model and displaying it:

# Displaying complex views

When a view become too complex for Revit to display it properly, zoom and pan actions become too slow to work properly.

The main rule to avoid this is to display only what you need. Close any unnecessary view, create cropped a view to work in a specific area, and hide every useless element.

Some visual styles need more power to run, keeping everything in Wireframe or Hidden Line can be a good practice. Even with these visual styles, filters with solid fill pattern override can slow down your view. Prefer lines override, or better, no override at all.

Link CAD only on a specific view (Current view only), and limit these insertions to the minimum. Having a bunch of DWG files displayed in every view of your model is bad for Revit performance and your spirit.

![<img class="aligncenter size-full wp-image-486" src="http://bim42.com/wp-content/uploads/2014/07/InserDWG.png" alt="InserDWG" width="763" height="121" srcset="https://bim42.com/wp-content/uploads/2014/07/InserDWG.png 763w, https://bim42.com/wp-content/uploads/2014/07/InserDWG-300x47.png 300w, https://bim42.com/wp-content/uploads/2014/07/InserDWG-500x79.png 500w" sizes="(max-width: 763px) 100vw, 763px" />](http://bim42.com/wp-content/uploads/2014/07/InserDWG.png)

# Loading large models

Another part of the problem lays in the time a model take to open, save and synchronize with its central. This time tends to augment with the size of the Revit file. If the size of a model is not a problem in itself, it can be a symptom of a poorly organized and therefore slow model.

To avoid ending up spending more time watching Revit starting than actually working with it, the main rule is to keep your model tidy.

Start by removing every unused view, family or group. Used wisely, the Purge Unused Element command can be useful here. Don&#8217;t use Revit family content sites. These families ae generally stuffed with heavy materials, complex geometries and parameters you don&#8217;t need. It&#8217;s also a good practice to use families provided by Autodesk with Revit.

Every model should have a starting page, defined in the Manage Project tab.

![<img class="aligncenter size-full wp-image-487" src="http://bim42.com/wp-content/uploads/2014/07/ManageStartingView.png" alt="ManageStartingView" width="102" height="103" />](http://bim42.com/wp-content/uploads/2014/07/ManageStartingView.png)

I generally use a Drafting View to display a handful of information about the opened model.

![<img class="aligncenter size-full wp-image-484" src="http://bim42.com/wp-content/uploads/2014/07/StartingView.png" alt="StartingView" width="899" height="516" srcset="https://bim42.com/wp-content/uploads/2014/07/StartingView.png 899w, https://bim42.com/wp-content/uploads/2014/07/StartingView-300x172.png 300w, https://bim42.com/wp-content/uploads/2014/07/StartingView-500x286.png 500w" sizes="(max-width: 899px) 100vw, 899px" />](http://bim42.com/wp-content/uploads/2014/07/StartingView.png)

If someone complains about a model becoming slower to open each time, ask every user to actually count how much time it take to open it. Having quantified feedback about Revit performance while opening large model can be really useful to prevent model for become unusable.