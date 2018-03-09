---
id: 481
title: Revit Performance Tips
date: 2014-07-12T08:00:24+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=481
permalink: /2014/07/revit-performance-tips/
categories:
  - Revit
image: /assets/2014/07/StartingView.png
tags:
  - Autodesk
  - BIM Manager
  - Revit
---
A regular complain about Revit is its slowness. If this can be a psycological problem coming from people used to the quick reaction time of AutoCAD, it can also become a real problem when working with large models on short deadlines.

I'm use to separate Revit performance in two parts, opening the model and displaying it:

# Displaying complex views

When a view become too complex for Revit to display it properly, zoom and pan actions become too slow to work properly.

The main rule to avoid this is to display only what you need. Close any unnecessary view, create cropped a view to work in a specific area, and hide every useless element.

Some visual styles need more power to run, keeping everything in Wireframe or Hidden Line can be a good practice. Even with these visual styles, filters with solid fill pattern override can slow down your view. Prefer lines override, or better, no override at all.

Link CAD only on a specific view (Current view only), and limit these insertions to the minimum. Having a bunch of DWG files displayed in every view of your model is bad for Revit performance and your spirit.

![InserDWG](/assets/2014/07/InserDWG.png)

# Loading large models

Another part of the problem lays in the time a model take to open, save and synchronize with its central. This time tends to augment with the size of the Revit file. If the size of a model is not a problem in itself, it can be a symptom of a poorly organized and therefore slow model.

To avoid ending up spending more time watching Revit starting than actually working with it, the main rule is to keep your model tidy.

Start by removing every unused view, family or group. Used wisely, the Purge Unused Element command can be useful here. Don't use Revit family content sites. These families ae generally stuffed with heavy materials, complex geometries and parameters you don't need. It's also a good practice to use families provided by Autodesk with Revit.

Every model should have a starting page, defined in the Manage Project tab.

![ManageStartingView](/assets/2014/07/ManageStartingView.png)

I generally use a Drafting View to display a handful of information about the opened model.

![StartingView](/assets/2014/07/StartingView.png)

If someone complains about a model becoming slower to open each time, ask every user to actually count how much time it take to open it. Having quantified feedback about Revit performance while opening large model can be really useful to prevent model for become unusable.