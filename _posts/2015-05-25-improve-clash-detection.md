---
id: 847
title: Improve clash detection
date: 2015-05-25T13:00:57+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=847
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

Checking required headroom is a good example of a useful clash detection. The idea here is to highlight every room where a structural framing end up below the vertical clearance set up by the architect. This example suppose than the &#8220;Limit Offset&#8221; property of the room is set to the required value by the architect.

![<img class="aligncenter size-full wp-image-848" src="http://bim42.com/wp-content/uploads/2015/05/clearHeadroom.png" alt="clearHeadroom" width="800" height="470" srcset="https://bim42.com/wp-content/uploads/2015/05/clearHeadroom.png 800w, https://bim42.com/wp-content/uploads/2015/05/clearHeadroom-300x176.png 300w, https://bim42.com/wp-content/uploads/2015/05/clearHeadroom-500x294.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/clearHeadroom.png)

The entire process is based on running a clash test between selections sets created in Navisworks.

My fist selection contains some of the room of the architectural model. The first condition retrieve every room, and the second remove technical area from our selection.

![<img class="aligncenter size-full wp-image-850" src="http://bim42.com/wp-content/uploads/2015/05/SelectionSets.png" alt="SelectionSets" width="1871" height="504" srcset="https://bim42.com/wp-content/uploads/2015/05/SelectionSets.png 1871w, https://bim42.com/wp-content/uploads/2015/05/SelectionSets-300x81.png 300w, https://bim42.com/wp-content/uploads/2015/05/SelectionSets-1024x276.png 1024w, https://bim42.com/wp-content/uploads/2015/05/SelectionSets-500x135.png 500w" sizes="(max-width: 1871px) 100vw, 1871px" />](http://bim42.com/wp-content/uploads/2015/05/SelectionSets.png)

The second selection set retrieve structural framing from the structural model.

Once these two selections are saved as Search Sets in Navisworks, we use them to run a clash test. Since we are focusing on headroom, the Tolerance value is really useful here. We can set it up to 2 cm without regret, knowing than any clash below this value is not an issue in this phase.

This clash test yields 78 results for the entire project. I use the Clash Grouper to group them by room (Selection A), and end up with 55 groups. The best part here is that every one of these groups is a real issue, and do not need any further sorting.

The last part is to export these issues in something practical for the Revit user.

I export the report in HTML (Tabular) to be able to import it in Excel afterward. I use the Get Data From web, and open the report in a nicely formatted Excel spreadsheet.

With some PivotTables, I get the Revit ID of every problematic room, and paste them in the Select By ID function of Revit. I can add a specific value on these rooms and highlight them with a Color Scheme in Revit.

![<img class="aligncenter size-full wp-image-849" src="http://bim42.com/wp-content/uploads/2015/05/RoomHightLight.png" alt="RoomHightLight" width="2000" height="600" srcset="https://bim42.com/wp-content/uploads/2015/05/RoomHightLight.png 2000w, https://bim42.com/wp-content/uploads/2015/05/RoomHightLight-300x90.png 300w, https://bim42.com/wp-content/uploads/2015/05/RoomHightLight-1024x307.png 1024w, https://bim42.com/wp-content/uploads/2015/05/RoomHightLight-500x150.png 500w" sizes="(max-width: 2000px) 100vw, 2000px" />](http://bim42.com/wp-content/uploads/2015/05/RoomHightLight.png)

From thousands of meaningless clash point to a nice plan highlighting problematic area for a specific problem, I finally find some improvement over my traditional clash detection process. I&#8217;m still working on it, and hope to share my progress, as long as there is any to share.[
  
](http://bim42.com/wp-content/uploads/2015/05/clearHeadroom.png)