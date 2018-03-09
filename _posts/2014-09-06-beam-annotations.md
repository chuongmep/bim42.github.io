---
id: 556
title: Beam Annotations
date: 2014-09-06T08:00:11+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=556
permalink: /2014/09/beam-annotations/
categories:
  - Revit
image: /assets/2014/09/11_ComplexeBeamsAnnotatedDetail.jpg
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

![01_TagAll]({{ "/assets/2014/09/01_TagAll.jpg" | absolute_url }})

To annotate efficiently a large set of beams, a specific tool exist, Beams Annotations. It functions pretty much like the Tag All command, but with more options.

![02_BeamAnnotations]({{ "/assets/2014/09/02_BeamAnnotations.jpg" | absolute_url }})

You start by selecting the set of beams you want to annotate (All beam or only selected one), and if you want to include linked models elements.
  
Things become quite interesting with the other part of the windows, which display a schematic beam with six slots:

![03_AnnotationLocation]({{ "/assets/2014/09/03_AnnotationLocation.jpg" | absolute_url }})

This second part allow us to describe where we want to place Structural Framing tags or Spot Elevation on our beam.

Here the possibilities are quite extensive. On every six position of each beam (start, middle, and end, on each side), you can select different options to place a Structural Framing Tag or an Spot Elevation to display top and/or bottom elevation for the beam:

![04_AnnotationType]({{ "/assets/2014/09/04_AnnotationType.jpg" | absolute_url }})

To showcase this feature, I create a set of beam, distributed on the same plane:

![05_PlaneBeams]({{ "/assets/2014/09/05_PlaneBeams.png" | absolute_url }})

In just a few click, I place a tag for every beam along with a nice Spot Elevation displaying the bottom elevation of the beam.

![06_planeTags]({{ "/assets/2014/09/06_planeTags.jpg" | absolute_url }})

This tool become extremely powerful when dealing with slopped beams. To showcase this feature, I create a set of beams aligned along a complex surface. To create quickly this kind of beam system, I use Grasshopper with the Hummingbird plug-in. I describe the complete procedure in [one of my older post](https://www.bim42.com/2012/09/parametric-modeling-in-revit/ "Parametric modeling in Revit").

![07_ComplexeBeams]({{ "/assets/2014/09/07_ComplexeBeams.png" | absolute_url }})

These beams are displayed as a grid in a plan view:

![08_ComplexeBeamsPlane]({{ "/assets/2014/09/08_ComplexeBeamsPlane.jpg" | absolute_url }})

I select the Beam Annotation tool, and add a Spot Elevation at the stating and the ending point of sloped beams, along with a Structural Framing Tag on the middle.

![09_ComplexeBeamsAnnotationLocation]({{ "/assets/2014/09/09_ComplexeBeamsAnnotationLocation.jpg" | absolute_url }})

After running the command, Revit add a Structural Framing Tag and two Spot Elevation on every beams in my view:

![10_ComplexeBeamsAnnotated]({{ "/assets/2014/09/10_ComplexeBeamsAnnotated.jpg" | absolute_url }})

These annotations place themselves nicely along the beam, and a few adjustments with the setting adjust them perfectly on the view:

![11_ComplexeBeamsAnnotatedDetail]({{ "/assets/2014/09/11_ComplexeBeamsAnnotatedDetail.jpg" | absolute_url }})