---
id: 192
title: From Grasshopper to Tekla
date: 2012-08-19T19:23:30+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=192
permalink: /2012/08/from-grasshopper-to-tekla/
categories:
  - Grasshopper
tags:
  - Geometry Gym
  - Grasshopper
  - Steel Detailing
  - Tekla
---
I keep on trying the Grasshopper Plugin Geometry Gym, and one of our current projects made me search more extensively in the Tekla export module.

It presents itself as a set of tools to create beams, plates, bolts and welds. There is also a TeklaBakeStructure component to send our Grasshopper geometry to Tekla.

Creating beams is pretty easy, all you need is a BeamProfileProperty before, where you set all Tekla parameters of your expected beam. Then you just link your wireframe lines to the beam component.

![beam](/assets/2012/08/beam.jpg)

I struggled for a while to set the Insertion Point property in order to set the position of the beam axis before realizing that I only had to right-click on the parameter to set it. I finally extracted it to keep it visible.

The plate component is also quite simple, with a polyline as input and more or less the same set of property as for beams.

![platebasic](/assets/2012/08/platebasic.jpg)

To link two parts together, and so create a Tekla assembly, you have to create a group of bolts (or a weld), then assign it to the main part with the specific input, and add to the assembly all secondary parts you need. I am not sure if it is realistic to create assembly for a whole project directly in Grasshopper, but maybe I am missing some point here. My current project involves a lot of connexions, so I will keep on exploring these features.

![assembly1](/assets/2012/08/assembly1.jpg)
To exploit a model imported in Rhino, Jon Mirchtin has developed two specific components call Reverse Engineer. You can use it to retrieve beams or plates properties from geometry. Here is an example of a plate recreated from a standard Rhino Closed PolySurface.

![reverseengineering](/assets/2012/08/reverseengineering.jpg)

Once all you profiles and other parts are created into Grasshopper, you can export them. Just run Tekla, start a new project, and click on the TeklaBakeStructure component on your Grasshopper canvas.

![bake](/assets/2012/08/bake.jpg)

Your model is now export in your Tekla project.

![tekla](/assets/2012/08/tekla.jpg)

This plug in fill one of the most lack in the Tekla functionalities, the ability to create complex shape quickly. With this module, it became pretty easy to adapt a lot of beam on a double-curved roof, and create them in Tekla.