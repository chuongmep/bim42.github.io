---
id: 556
title: Beam Annotations
date: 2014-09-06T08:00:11+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=556
permalink: /2014/09/beam-annotations/
categories:
  - Revit
tags:
  - Autodesk
  - BIM Manager
  - Documentation
  - Revit
  - Software
  - Tips
---
An article from [Line Shape Space](http://lineshapespace.com/ "Line Shape Space") drive me to the Beam Annotation tools, and the various possibilities to automatically tag a set of beams.
  
The first idea when having to annotate a set of element is the Tag All function, quite efficient, but limited only to a tag by category. Furthermore, this function does not have the possibilities to add different tags on the same object.

![01_TagAll](http://bim42.com/wp-content/uploads/2014/09/01_TagAll.png)

To annotate efficiently a large set of beams, a specific tool exist, Beams Annotations. It functions pretty much like the Tag All command, but with more options.

![02_BeamAnnotations](http://bim42.com/wp-content/uploads/2014/09/02_BeamAnnotations.png)

You start by selecting the set of beams you want to annotate (All beam or only selected one), and if you want to include linked models elements.
  
Things become quite interesting with the other part of the windows, which display a schematic beam with six slots:

![03_AnnotationLocation](http://bim42.com/wp-content/uploads/2014/09/03_AnnotationLocation.png)

This second part allow us to describe where we want to place Structural Framing tags or Spot Elevation on our beam.

Here the possibilities are quite extensive. On every six position of each beam (start, middle, and end, on each side), you can select different options to place a Structural Framing Tag or an Spot Elevation to display top and/or bottom elevation for the beam:

![04_AnnotationType](http://bim42.com/wp-content/uploads/2014/09/04_AnnotationType.png)

To showcase this feature, I create a set of beam, distributed on the same plane:

![05_PlaneBeams](http://bim42.com/wp-content/uploads/2014/09/05_PlaneBeams.png)

In just a few click, I place a tag for every beam along with a nice Spot Elevation displaying the bottom elevation of the beam.

![06_planeTags](http://bim42.com/wp-content/uploads/2014/09/06_planeTags.png)

This tool become extremely powerful when dealing with slopped beams. To showcase this feature, I create a set of beams aligned along a complex surface. To create quickly this kind of beam system, I use Grasshopper with the Hummingbird plug-in. I describe the complete procedure in [one of my older post](http://bim42.com/2012/09/parametric-modeling-in-revit/ "Parametric modeling in Revit").

![07_ComplexeBeams](http://bim42.com/wp-content/uploads/2014/09/07_ComplexeBeams.png)

These beams are displayed as a grid in a plan view:

![08_ComplexeBeamsPlane](http://bim42.com/wp-content/uploads/2014/09/08_ComplexeBeamsPlane.png)

I select the Beam Annotation tool, and add a Spot Elevation at the stating and the ending point of sloped beams, along with a Structural Framing Tag on the middle.

![09_ComplexeBeamsAnnotationLocation](http://bim42.com/wp-content/uploads/2014/09/09_ComplexeBeamsAnnotationLocation.png)

After running the command, Revit add a Structural Framing Tag and two Spot Elevation on every beams in my view:

![10_ComplexeBeamsAnnotated](http://bim42.com/wp-content/uploads/2014/09/10_ComplexeBeamsAnnotated.png)

These annotations place themselves nicely along the beam, and a few adjustments with the setting adjust them perfectly on the view:

![11_ComplexeBeamsAnnotatedDetail](http://bim42.com/wp-content/uploads/2014/09/11_ComplexeBeamsAnnotatedDetail.png)