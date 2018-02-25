---
id: 534
title: Coordination with Grasshopper
date: 2014-08-16T08:00:49+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=534
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

[<img class="aligncenter size-full wp-image-538" src="http://bim42.com/wp-content/uploads/2014/08/générale.png" alt="General View" width="793" height="375" srcset="https://bim42.com/wp-content/uploads/2014/08/générale.png 793w, https://bim42.com/wp-content/uploads/2014/08/générale-300x141.png 300w, https://bim42.com/wp-content/uploads/2014/08/générale-500x236.png 500w" sizes="(max-width: 793px) 100vw, 793px" />](http://bim42.com/wp-content/uploads/2014/08/générale.png)

For those who are not familiar with it, Rhinoceros is a 3D modeling software solution, develop by Mc Neel Associate, and broadly used by architects in the early stage of the design. It comes in handy for design complex free-form shapes.

My ceiling surfaces have to be modified to include enough space in the plenum for mechanical equipment, while keeping the ceiling constructible.

I use different models as a reference during my work, coming mostly from Revit. Once exported in DWG, inserting them in Rhino is quite easy. These models show structural concrete and ducts to be integrated in the plenum space.

The next step is to integrate fabrication constrains, in order to keep every ceiling panels constructible while editing them. To do so, I use Grasshopper, the visual programming interface of Rhinoceros.

With a layer pipeline, I extract every panel of the ceiling surface. I then apply the construction rules on these panels, and display the result with a specific presentation in Rhino.

For example, since every panel must be planar, I display every non-flat panel in red, and correct them as soon I see them in Rhino.

[<img class="aligncenter size-full wp-image-539" src="http://bim42.com/wp-content/uploads/2014/08/greenGH.png" alt="IsFlatGH" width="1566" height="548" srcset="https://bim42.com/wp-content/uploads/2014/08/greenGH.png 1566w, https://bim42.com/wp-content/uploads/2014/08/greenGH-300x104.png 300w, https://bim42.com/wp-content/uploads/2014/08/greenGH-1024x358.png 1024w, https://bim42.com/wp-content/uploads/2014/08/greenGH-500x174.png 500w" sizes="(max-width: 1566px) 100vw, 1566px" />](http://bim42.com/wp-content/uploads/2014/08/greenGH.png)

[<img class="aligncenter size-full wp-image-540" src="http://bim42.com/wp-content/uploads/2014/08/greenR3.png" alt="IsFlatRhino" width="740" height="253" srcset="https://bim42.com/wp-content/uploads/2014/08/greenR3.png 740w, https://bim42.com/wp-content/uploads/2014/08/greenR3-300x102.png 300w, https://bim42.com/wp-content/uploads/2014/08/greenR3-500x170.png 500w" sizes="(max-width: 740px) 100vw, 740px" />](http://bim42.com/wp-content/uploads/2014/08/greenR3.png)

I also display the naked edge curves of every panel to identify junction problems between two supposedly contiguous panels.

[<img class="aligncenter size-full wp-image-541" src="http://bim42.com/wp-content/uploads/2014/08/redGH.png" alt="EdgesGH" width="1414" height="368" srcset="https://bim42.com/wp-content/uploads/2014/08/redGH.png 1414w, https://bim42.com/wp-content/uploads/2014/08/redGH-300x78.png 300w, https://bim42.com/wp-content/uploads/2014/08/redGH-1024x266.png 1024w, https://bim42.com/wp-content/uploads/2014/08/redGH-500x130.png 500w" sizes="(max-width: 1414px) 100vw, 1414px" />](http://bim42.com/wp-content/uploads/2014/08/redGH.png)

[<img class="aligncenter size-full wp-image-542" src="http://bim42.com/wp-content/uploads/2014/08/redR3.png" alt="EdgesRhino" width="756" height="240" srcset="https://bim42.com/wp-content/uploads/2014/08/redR3.png 756w, https://bim42.com/wp-content/uploads/2014/08/redR3-300x95.png 300w, https://bim42.com/wp-content/uploads/2014/08/redR3-500x158.png 500w" sizes="(max-width: 756px) 100vw, 756px" />](http://bim42.com/wp-content/uploads/2014/08/redR3.png)

Each ceiling panel needs also some space behind it for its supporting structure. The volume of this structure is modeled in real time using the offset command in Grasshopper. Another constrain is the angle of the panel vertices. After fighting with some angle measure in Grasshopper, I ending up by just counting the number of edge of a panel, displaying it as a color scheme in Rhino, and assuming that the smallest edges count was the better.

[<img class="aligncenter size-full wp-image-537" src="http://bim42.com/wp-content/uploads/2014/08/colorsGH.png" alt="EdgeCountGH" width="1836" height="486" srcset="https://bim42.com/wp-content/uploads/2014/08/colorsGH.png 1836w, https://bim42.com/wp-content/uploads/2014/08/colorsGH-300x79.png 300w, https://bim42.com/wp-content/uploads/2014/08/colorsGH-1024x271.png 1024w, https://bim42.com/wp-content/uploads/2014/08/colorsGH-500x132.png 500w" sizes="(max-width: 1836px) 100vw, 1836px" />](http://bim42.com/wp-content/uploads/2014/08/colorsGH.png)

[<img class="aligncenter size-full wp-image-536" src="http://bim42.com/wp-content/uploads/2014/08/colors3D.png" alt="EdgesCountRhino" width="740" height="252" srcset="https://bim42.com/wp-content/uploads/2014/08/colors3D.png 740w, https://bim42.com/wp-content/uploads/2014/08/colors3D-300x102.png 300w, https://bim42.com/wp-content/uploads/2014/08/colors3D-500x170.png 500w" sizes="(max-width: 740px) 100vw, 740px" />](http://bim42.com/wp-content/uploads/2014/08/colors3D.png)

Once these construction constrains are displayed in real time in the Rhino viewport, I can easily modified the ceiling surface while making sure it still constructible. These modifications are conducted here with basic surface modeling tools, and entirely by hand. But once you have immediate feedback on what you are doing thanks to Grasshopper, editing these surfaces become almost fun.