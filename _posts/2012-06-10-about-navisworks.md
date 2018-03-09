---
id: 106
title: About Navisworks
date: 2012-06-10T17:43:59+00:00
author: Simon Moreau
layout: post
guid: http://bim42.wordpress.com/?p=106
permalink: /2012/06/about-navisworks/
categories:
  - Coordination
  - General BIM
image: /assets/2012/06/navisworks.jpg
tags:
  - Autodesk
  - BIM Manager
  - Coordination
  - Navisworks
---
Navisworks is the 3D design review software included in the Autodesk BIM solution. I'm working with it for some times now, and I have finally found it pretty useful, especially while working with synthesis teams.

![navisworks]({{ "/assets/2012/06/navisworks.jpg" | absolute_url }})

I'm using it mainly for models presentation and clash detection, but it had also a integrated 4D planning function (the TimeLiner) and some model review and annotation features.

While I was working with this software, I was really missing a revision tracking system.

As we are running our clash detection, new revisions of models came, and have to be integrated in the compiled Navisworks model. To do so, we just append the new model in the software. But, if we keep the same model name from one revision to another, we quickly lost track of which revision we are dealing with. And if we change the name, adding a revision number for example, Naviswork do not include it a revision, but like a totally new model, and we lost the history of clash instances previously founded and sorted.

The only workaround I have found is to overwrite the old revision, keep it in a separate folder and rename it. Not very convenient, but we get used to it.

Once this kind of revision tracking is settled down, we can run our clash detection. Sort results is the most painful task, as we quickly have more than a thousand of clash, most irrelevant or duplicates.

I have also tried the free viewer, called Navisworks Freedom, for visualization purposes, but functions included are too poor to be are real viewer. I hopping than the Live Section Tool, included in the full version of Navisworks, will also be integrated in the free viewer to create a real solution for review and coordination.

I was also able to develop some interesting extensions, mostly for exporting clash reports to Excel or Revit, in order to improve our workflow. I will try to describe these plugins more extensively on a next post.