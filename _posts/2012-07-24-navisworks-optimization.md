---
id: 171
title: Navisworks Optimization
date: 2012-07-24T17:12:43+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=171
permalink: /2012/07/navisworks-optimization/
categories:
  - Coordination
image: /assets/2012/07/image.png
tags:
  - Autodesk
  - Automation
  - Coordination
  - Navisworks
---
Since I have been using Navisworks for clash detection, I have tried to find out how to optimize my results, in order to avoid sorting manually thousands of irrelevant clashes, and export a proper final report.

![image](/assets/2012/07/image.png)

First of all, the model itself seems to be the most important part for clash detection. Modeling all openings in structural elements in order to avoid sorting all meaningless intersections with MEP features is a major prerequisite. But there are many other best practices for modeling in order to make the clash reviewing process easier, such as defining precise modeling rules for structural elements connections (joints between beams and columns, or intersections between columns and slabs).

But still, even with the most carefully designed model, you will probably still have a lot of clashes to sort.

![you-have-677-new-clashes](/assets/2012/07/you-have-677-new-clashes.jpg)

This is when a good workflow for the whole team is important. Some plug-ins, like the Navisworks Keyboard Shortcuts found on [BIM Manager](http://bimmanager.blogspot.fr/2011/12/navisworks-keyboard-shortcuts-for.html), can be very useful at this point. For our part, we used to make a first sort by ourselves, eliminating obviously irrelevant clashes and roughly grouping other ones by location, then transfer to the coordination team for review.

This is when a good clash report is needed, along with the model. The standard html report extract from Navisworks was missing some information, mostly about plan location, and we were asking for an Excel format, so we developed a VB.Net application to exploit results from Navisworks.

We first parse the .xml report in order to extract main information about clashes, such as names, coordinates, trades involved and so on, and then paste them in a formatted Excel template. We also add the Navisworks screenshot.

Using the coordinates of the main 2D grid lines, we are able to automatically identify the localization of the clash, in order to find it easily on the 2D shop drawings if necessary.

With this report and the .nwd “snapshot” of the model, the coordination team was able to work efficiently on these clashes, especially for intricate parts of the building where 2D drawings are almost useless.

I still have to run tests on the 2013 version of Navisworks which integrate 2D grids directly on the model, hoping this will improve our process.