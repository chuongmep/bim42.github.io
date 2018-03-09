---
id: 158
title: Geometry Gym
date: 2012-07-16T22:05:37+00:00
author: Simon Moreau
layout: post
guid: http://bim42.wordpress.com/?p=158
permalink: /2012/07/geometry-gym/
categories:
  - Grasshopper
image: /assets/bim42_header.jpg
tags:
  - Geometry Gym
  - Grasshopper
  - IFC
  - Rhino
  - Tekla
---
I was talking on a [previous article](http://bim42.wordpress.com/2012/06/04/industry-foundation-classes/ "Industry Foundation Classes") about the Grasshopper plugin develop by Jon Mirtschin called Geometry Gym.

This set of tool for building modeling firstly came as a plugin for Rhino, implementing commands for designing structures and linking these models to structural analysis software.

![structdrawrhino](/assets/2012/07/structdrawrhino.jpg)

These tools where integrated as commands in Grasshopper, allowing generating building elements parametrically, a very interesting feature at an early stage of the project.

But for me, the most interesting part of this plugin is its ability to generate IFC files into Grasshopper. A large part of the IFC classes are implemented directly as Grasshopper functions.

![buildingelements](/assets/2012/07/buildingelements.jpg)

By combining these functions, we generate the structure of our IFC file exactly as we want it, and if our favorite BIM software is known for missing some IFC classes, we can still use a workaround by designing yourself your IFC data structure.

Using this plugin requires a little understanding of the IFC data structure, but examples can be found on the Geometry Gym blog, and are quite self-explaining.

Combined with the building modeling tools described above, it provides a powerful way of designing building, especially at the early stage of the project.

Geometry Gym came also with various plugins used as bridges for other BIM software

The plugin for Revit implement a new IFC Import module, especially design to import files generated in Grasshopper. This allows integrating native Revit element from an IFC file.

![geometrygymrevit](/assets/2012/07/geometrygymrevit.jpg)

There is also a direct link with Tekla, use to generate native Tekla elements directly from the Grasshopper model.

If this software need some time to get used to it, and a little knowledge about the IFC Data structure, once taken in hand, it become powerful enough for replace any conventional BIM software, at least at the beginning of a project, and especially for complex shapes and structures.