---
id: 263
title: My Revit experience
date: 2012-11-04T21:34:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=263
permalink: /2012/11/my-revit-experience/
categories:
  - General BIM
  - Revit
image: /assets/2012/11/basic3dshape.png
tags:
  - Autodesk
  - Digital Project
  - Revit
  - Software
---
I previously dealt with some issues regarding the use of Digital Project. These problems arrose mostly because CATIA is not suitable for the AEC industry. Even if Digital Project is adapted to the building construction techniques, the main core, CATIA, is still a product aimed at industrial products.

Furthermore, Digital Project needs large resources both in time and money for designing anything. It can be perfectly acceptable for mass-produced objects or very complex buildings, but when it comes to more average construction projects, we have to find another solution.

I was wondering if I would be able to create all the precast pieces of a stone-like facade on Revit, and see what differences we can find.

Here is a little demonstration of concept for designing intricate geometry and casting drawing in Revit

Designing a specific part with the basic tool from the Revit family (extrusion and boolean operations) is not very difficult, and I quickly got the design of one of the arc over the door.

![basic3dshape](/assets/2012/11/basic3dshape.png)

Anyway, some limitations already appears. Due to the void form created as boolean, it is impossible to merge the arc with the superior part, and a join remains.

![boolean](/assets/2012/11/boolean.png)

Furthermore, there is at least one piece I was not able to draw properly a double-curved arch.

I insert my Revit family in a new project, and add a few dimensions and a section line.

![elevation](/assets/2012/11/elevation.png)

A main problem appears when I am trying to extract a section of the curved part. If I get the section, I cannot add dimensions to it.

![section2](/assets/2012/11/section2.png)

Finally, there is no embedded tool for extracting the position of the center of gravity. This information can probably be extracted using another software or the API, but we are seeking for a process developed entirely with Revit.

All these limitations made me think that Revit is not powerful enough to efficiently design intricate elements. Even if possibilities for creating complex 3D models are enough for most of the precast elements, there are still too many limitations for using it in production. I am waiting for the next releases of Revit to overcome these issues.