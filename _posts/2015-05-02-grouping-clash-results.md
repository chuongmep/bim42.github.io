---
id: 834
title: Grouping clash results
date: 2015-05-02T14:25:41+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=834
permalink: /2015/05/grouping-clash-results/
categories:
  - Coordination
tags:
  - .NET
  - Autodesk
  - Automation
  - Coordination
  - Navisworks
---
In any given building model, there is a number of issues to be addressed. A large part of these issues are what we call &#8220;hard clashes&#8221;, when a building component physically penetrate the space occupied by another building component. In these case, two or more building elements compete for the same volume.

Finding these clashes is now quite simple thanks to clash detection software that detect geometrical interferences between elements of a building model.

But after having a hard time finding these issues through coordination sections hand-drawn from plans, we now face the inverse problem and end up with too many clashes in our models. Running a simple clash detection can quickly yield thousands of clashes, making the entire process nearly useless.

Furthermore, a clash only represent a geometrical intersection between two elements, and is more a part of an issue than the issue itself. We have to group these clashes to be able to extract meaningful issues from the meaningless clashes.

Grouping these clashes is generally a manual task, and the user have to run through thousands of clashes to sort them in relevant groups.

While trying to automate this tedious task, I run across the examples provided as part of the Autodesk Navisworks Software Development Kit. These examples include a nice Clash Grouper plugin for Navisworks, enabling various method for grouping clash results.

![<img class="aligncenter size-full wp-image-839" src="http://bim42.com/wp-content/uploads/2015/05/grouplashes.png" alt="groupClashes" width="800" height="377" srcset="https://bim42.com/wp-content/uploads/2015/05/grouplashes.png 800w, https://bim42.com/wp-content/uploads/2015/05/grouplashes-300x141.png 300w, https://bim42.com/wp-content/uploads/2015/05/grouplashes-500x236.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/grouplashes.png)

As an example, I run a clash detection between the blue Selection A and the green Selection B, and get seven clashes, shown here as red dot:

![<img class="aligncenter size-full wp-image-841" src="http://bim42.com/wp-content/uploads/2015/05/Ungrouped.png" alt="Ungrouped" width="800" height="593" srcset="https://bim42.com/wp-content/uploads/2015/05/Ungrouped.png 800w, https://bim42.com/wp-content/uploads/2015/05/Ungrouped-300x222.png 300w, https://bim42.com/wp-content/uploads/2015/05/Ungrouped-405x300.png 405w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/Ungrouped.png)

With the Clash Grouper, I can group these clashes by grid intersection:

![<img class="aligncenter size-full wp-image-836" src="http://bim42.com/wp-content/uploads/2015/05/groupByGrid.png" alt="groupByGrid" width="800" height="593" srcset="https://bim42.com/wp-content/uploads/2015/05/groupByGrid.png 800w, https://bim42.com/wp-content/uploads/2015/05/groupByGrid-300x222.png 300w, https://bim42.com/wp-content/uploads/2015/05/groupByGrid-405x300.png 405w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/groupByGrid.png)

I can also group them by cluster analysis, where we search for the optimum grouping solution given the expected number of groups:

![<img class="aligncenter size-full wp-image-835" src="http://bim42.com/wp-content/uploads/2015/05/groupByCluster.png" alt="groupByCluster" width="800" height="593" srcset="https://bim42.com/wp-content/uploads/2015/05/groupByCluster.png 800w, https://bim42.com/wp-content/uploads/2015/05/groupByCluster-300x222.png 300w, https://bim42.com/wp-content/uploads/2015/05/groupByCluster-405x300.png 405w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/groupByCluster.png)

I also add my own method for grouping clash against a specific set. I use this to group all clash belonging to a single element in one of the two selection sets.

![<img class="aligncenter size-full wp-image-840" src="http://bim42.com/wp-content/uploads/2015/05/grouplashesEdited.png" alt="grouplashesEdited" width="800" height="377" srcset="https://bim42.com/wp-content/uploads/2015/05/grouplashesEdited.png 800w, https://bim42.com/wp-content/uploads/2015/05/grouplashesEdited-300x141.png 300w, https://bim42.com/wp-content/uploads/2015/05/grouplashesEdited-500x236.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/grouplashesEdited.png)

Here, I group by element from the Selection A (blue)

![<img class="aligncenter size-full wp-image-837" src="http://bim42.com/wp-content/uploads/2015/05/groupBySelectionA.png" alt="groupBySelectionA" width="800" height="593" srcset="https://bim42.com/wp-content/uploads/2015/05/groupBySelectionA.png 800w, https://bim42.com/wp-content/uploads/2015/05/groupBySelectionA-300x222.png 300w, https://bim42.com/wp-content/uploads/2015/05/groupBySelectionA-405x300.png 405w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/groupBySelectionA.png)

Here, I group by elements from the selection B (green)

![<img class="aligncenter size-full wp-image-838" src="http://bim42.com/wp-content/uploads/2015/05/groupBySelectionB.png" alt="groupBySelectionB" width="800" height="593" srcset="https://bim42.com/wp-content/uploads/2015/05/groupBySelectionB.png 800w, https://bim42.com/wp-content/uploads/2015/05/groupBySelectionB-300x222.png 300w, https://bim42.com/wp-content/uploads/2015/05/groupBySelectionB-405x300.png 405w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/05/groupBySelectionB.png)

If elements from one set are more relevant for the end user, the final clash report is clearer for this user when clashes are grouped against this set.

This plug-in enables a lot of possibilities for sorting clash detection results in a meaningful report, and will become a full-time member of my coordination toolbox.

To install this plug-in, you can copy-paste the ClashDetective.ADSK.dll file available [here](https://bitbucket.org/simonmoreau/clashdetective/downloads) in a new ClashDetective.ADSK folder in C:\Program Files\Autodesk\Navisworks Manage 2016\Plugins. You can also see my edited version of the example code [here](https://bitbucket.org/simonmoreau/clashdetective).