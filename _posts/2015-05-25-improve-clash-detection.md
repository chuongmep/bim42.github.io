---
id: 847
title: Improve clash detection
date: 2015-05-25T13:00:57+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=847
permalink: /2015/05/improve-clash-detection/
categories:
  - Coordination
tags:
  - Autodesk
  - Coordination
  - Navisworks
  - Revit
---
Automatic clash detection produces way too much clashes. Even when running test per level or area, I always end up with thousands of useless clash points.

Tired of painfully grouping and sorting these clashes into something usable, I put aside the whole clash detection subject for a while.

I was drove back to Navisworks while working on specific coordination problems. Instead of clashing entire models one against the other (say, HAVC against Structural), I select only a subset of these models to solve a particular problem. Focusing only on the elements involved in these problems, I was finally getting something out of automatic clash detection.

Solving one problem at a time is of course the solution for an efficient clash detection.

Checking required headroom is a good example of a useful clash detection. The idea here is to highlight every room where a structural framing end up below the vertical clearance set up by the architect. This example suppose than the "Limit Offset" property of the room is set to the required value by the architect.

![clearHeadroom](/assets/2015/05/clearHeadroom.png)

The entire process is based on running a clash test between selections sets created in Navisworks.

My fist selection contains some of the room of the architectural model. The first condition retrieve every room, and the second remove technical area from our selection.

![SelectionSets](/assets/2015/05/SelectionSets.png)

The second selection set retrieve structural framing from the structural model.

Once these two selections are saved as Search Sets in Navisworks, we use them to run a clash test. Since we are focusing on headroom, the Tolerance value is really useful here. We can set it up to 2 cm without regret, knowing than any clash below this value is not an issue in this phase.

This clash test yields 78 results for the entire project. I use the Clash Grouper to group them by room (Selection A), and end up with 55 groups. The best part here is that every one of these groups is a real issue, and do not need any further sorting.

The last part is to export these issues in something practical for the Revit user.

I export the report in HTML (Tabular) to be able to import it in Excel afterward. I use the Get Data From web, and open the report in a nicely formatted Excel spreadsheet.

With some PivotTables, I get the Revit ID of every problematic room, and paste them in the Select By ID function of Revit. I can add a specific value on these rooms and highlight them with a Color Scheme in Revit.

![RoomHightLight](/assets/2015/05/RoomHightLight.png)

From thousands of meaningless clash point to a nice plan highlighting problematic area for a specific problem, I finally find some improvement over my traditional clash detection process. I'm still working on it, and hope to share my progress, as long as there is any to share.