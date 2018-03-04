---
id: 534
title: Coordination with Grasshopper
date: 2014-08-16T08:00:49+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=534
permalink: /2014/08/coordination-with-grasshopper/
categories:
  - Grasshopper
tags:
  - Coordination
  - Grasshopper
  - Rhino
  - Visualization
---
I recently coordinate a complex ceiling with the concrete structure and mechanical equipment. This ceiling is composed of flat panels, with no particular pattern or general repetitive shape. These panels are modeled as a set of surfaces in Rhinoceros 3D.

![générale](/assets/2014/08/générale.png)

For those who are not familiar with it, Rhinoceros is a 3D modeling software solution, develop by Mc Neel Associate, and broadly used by architects in the early stage of the design. It comes in handy for design complex free-form shapes.

My ceiling surfaces have to be modified to include enough space in the plenum for mechanical equipment, while keeping the ceiling constructible.

I use different models as a reference during my work, coming mostly from Revit. Once exported in DWG, inserting them in Rhino is quite easy. These models show structural concrete and ducts to be integrated in the plenum space.

The next step is to integrate fabrication constrains, in order to keep every ceiling panels constructible while editing them. To do so, I use Grasshopper, the visual programming interface of Rhinoceros.

With a layer pipeline, I extract every panel of the ceiling surface. I then apply the construction rules on these panels, and display the result with a specific presentation in Rhino.

For example, since every panel must be planar, I display every non-flat panel in red, and correct them as soon I see them in Rhino.

![greenGH](/assets/2014/08/greenGH.png)

![greenR3](/assets/2014/08/greenR3.png)

I also display the naked edge curves of every panel to identify junction problems between two supposedly contiguous panels.

![redGH](/assets/2014/08/redGH.png)

![redR3](/assets/2014/08/redR3.png)

Each ceiling panel needs also some space behind it for its supporting structure. The volume of this structure is modeled in real time using the offset command in Grasshopper. Another constrain is the angle of the panel vertices. After fighting with some angle measure in Grasshopper, I ending up by just counting the number of edge of a panel, displaying it as a color scheme in Rhino, and assuming that the smallest edges count was the better.

![colorsGH](/assets/2014/08/colorsGH.png)

![colors3D](/assets/2014/08/colors3D.png)

Once these construction constrains are displayed in real time in the Rhino viewport, I can easily modified the ceiling surface while making sure it still constructible. These modifications are conducted here with basic surface modeling tools, and entirely by hand. But once you have immediate feedback on what you are doing thanks to Grasshopper, editing these surfaces become almost fun.