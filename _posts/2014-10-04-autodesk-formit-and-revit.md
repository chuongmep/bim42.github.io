---
id: 617
title: Autodesk Formit and Revit
date: 2014-10-04T09:08:56+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=617
permalink: /2014/10/autodesk-formit-and-revit/
categories:
  - Revit
image: /assets/2014/10/ScreenClip.jpg
tags:
  - Autodesk
  - Revit
  - Visualization
---
Autodesk Formit is an example of how far web-based solutions have progressed. Since 3D application need heavy calculation for display, they were generally limited to the heavy client format, until solutions like Autodesk Formit appear.

This 3D sketching tool allow us to quickly create building concept in a web browser or through the mobile app, then further develop this concept in Revit.

Autodesk Formit greets us with a nice introduction screen describing the main functionality.

![ScreenClip]({{ "/assets/2014/10/ScreenClip.jpg" | absolute_url }})

I generally start by setting up the units to metrics.

![ScreenClip-1]({{ "/assets/2014/10/ScreenClip-1.jpg" | absolute_url }})

Afterward, everything is quite easy to use, and look pretty much like a web-based Sketchup. Let draw a little sketch of our main plan:

![ScreenClip-2]({{ "/assets/2014/10/ScreenClip-2.jpg" | absolute_url }})

Extruding this sketch give us the first draft of a building.

We can define levels in our model to calculate gross area for our future building.

![ScreenClip-3]({{ "/assets/2014/10/ScreenClip-3.jpg" | absolute_url }})

These surfaces are updated as we edit the form of our mass:

![FloorArea]({{ "/assets/2014/10/FloorArea.png" | absolute_url }})

Once our model is located, the shadow and Sun and Shadows tool allow us to create a small daylight analysis:

![DaylightAnalysis]({{ "/assets/2014/10/DaylightAnalysis.jpg" | absolute_url }})

While we work, our model is saved to our Autodesk 360 account, in the Drive section. Along the Formit format .axm, a .rvt file appear. This rvt file is automatically converted from our Formit model to be used in Revit. We can download it to continue our design in Revit :

![ScreenClip-9]({{ "/assets/2014/10/ScreenClip-9.jpg" | absolute_url }})

The Formit model appear as an In-Place mass in Revit, which can be edited directly in Revit. Each previously defined levels are also integrated in our Revit model, along with corresponding Mass Floors.

![ScreenClip-10]({{ "/assets/2014/10/ScreenClip-10.jpg" | absolute_url }})

We can enhance our design by using this in place mass to create a Curtain System, some floor and interior divisions. Pretty quickly, we have a fully functional first sketch of our building, with elevation, floor plans and a nice rendering.

![ScreenClip-11]({{ "/assets/2014/10/ScreenClip-11.jpg" | absolute_url }})

My only regret is to have to use the Revit model provided by the Formit conversion. I think it would be more convenient to retrieve a Revit Mass family to be integrated in the Revit template of our choice. We would lose the levels creation, but gain more flexibility for an early stage workflow.