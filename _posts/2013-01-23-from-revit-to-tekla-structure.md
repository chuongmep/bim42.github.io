---
id: 285
title: From Revit to Tekla Structure
date: 2013-01-23T21:42:59+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=285
permalink: /2013/01/from-revit-to-tekla-structure/
categories:
  - Revit
image: /assets/2013/01/teklanativeelements.jpg
tags:
  - .NET
  - IFC
  - Revit
  - Tekla
---
After a long absence, I am back wishing you all the best for 2013, a year full of opportunities and crazy BIM projects.

During a meeting dedicated to a BIM process, I realized how convenient a direct link between Revit and Tekla could be. Most architects draw with Revit (for average buildings), but it is not enough for producing shop drawing for the construction site.

Being able to retrieve Revit structural elements and integrate them as native Tekla elements could really speed up the production of structural drawings.

Tekla comes with two plug-ins, one for exporting Revit models to Tekla, the other to import Tekla-generated .ifcZip files.

I  quickly drew a few walls in Revit and exported them using the associated command.

![revitwalls]({{ "/assets/2013/01/revitwalls.jpg" | absolute_url }})

It created an .IFCZip file tailored for the Tekla IFC Import function.

I inserted it as a Reference Model in Tekla. The resulting geometry looks pretty, but wall openings and walls with an edited profile are missing.

In order to use this Tekla model for the production of structural drawings, native Tekla elements are needed, so I used the Tekla Macro Convert IFC element to generate them from this Reference Model.

![teklanativeelements]({{ "/assets/2013/01/teklanativeelements.jpg" | absolute_url }})

As you can see, some dimension were lost during the conversion process.

These limitations made me think of another kind of link between these two software, and I started a few months ago to write my own Revit plug-in in order to recreate structural beams and walls in Tekla.

Here is a first overview of this plug-in with an interface for mapping Revit families to Tekla profiles.

![pluginui]({{ "/assets/2013/01/pluginui.jpg" | absolute_url }})

I was able to import a few beams and some walls with my plug-in. The whole thing is in a very early stage, and still incredibly buggy, but I hope to be able to fix it and create something both stable and useful. By now I am trying to recreate walls with an edited profile or hosted openings.

I will keep you updated on my research.