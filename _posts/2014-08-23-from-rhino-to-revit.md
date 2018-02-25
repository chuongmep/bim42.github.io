---
id: 546
title: From Rhino to Revit
date: 2014-08-23T08:00:02+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=546
permalink: /2014/08/from-rhino-to-revit/
categories:
  - Revit
tags:
  - Autodesk
  - Grasshopper
  - Revit
  - Rhino
  - Visualization
---
My previous post was describing how I use Grasshopper to modify a complex ceiling surface in Rhino. Once this surface is correctly modeled by taking into account constrains set by the actual construction of the ceiling (space taken by structural framing, planarity, maximal angle &#8230;), I have to create construction documentation from it.

I need to produce drawings from the 3D models of the ceiling to make it understandable by someone who will built it.

Revit will be our software of choice here. The power of Revit resides in its ability to efficiently produce drawings from a model. To be able to represent our Rhino surface on 2D drawings, we first have to create a Revit model from the Rhino surface.

After some trials and errors with the DWG export options of Rhino, I ended up exporting my surfaces as an ACIS (.sat) file, with the default Autocad export configuration.

[<img class="aligncenter size-full wp-image-551" src="http://bim42.com/wp-content/uploads/2014/08/satExport.png" alt="satExport" width="347" height="157" srcset="https://bim42.com/wp-content/uploads/2014/08/satExport.png 347w, https://bim42.com/wp-content/uploads/2014/08/satExport-300x135.png 300w" sizes="(max-width: 347px) 100vw, 347px" />](http://bim42.com/wp-content/uploads/2014/08/satExport.png)

I import this .sat file in a new Conceptual Mass family in Revit. The positioning is set to Origin to Origin to place our ceiling in its correct position regarding the origin of the massing family.

[<img class="aligncenter size-full wp-image-549" src="http://bim42.com/wp-content/uploads/2014/08/MassingFamily.png" alt="MassingFamily" width="860" height="522" srcset="https://bim42.com/wp-content/uploads/2014/08/MassingFamily.png 860w, https://bim42.com/wp-content/uploads/2014/08/MassingFamily-300x182.png 300w, https://bim42.com/wp-content/uploads/2014/08/MassingFamily-494x300.png 494w" sizes="(max-width: 860px) 100vw, 860px" />](http://bim42.com/wp-content/uploads/2014/08/MassingFamily.png)

I insert this family in my Revit project, and use two dimensions to place it at the origin of the project.

[<img class="aligncenter size-full wp-image-552" src="http://bim42.com/wp-content/uploads/2014/08/ceilingPlan.png" alt="ceilingPlan" width="522" height="508" srcset="https://bim42.com/wp-content/uploads/2014/08/ceilingPlan.png 522w, https://bim42.com/wp-content/uploads/2014/08/ceilingPlan-300x291.png 300w, https://bim42.com/wp-content/uploads/2014/08/ceilingPlan-308x300.png 308w" sizes="(max-width: 522px) 100vw, 522px" />](http://bim42.com/wp-content/uploads/2014/08/ceilingPlan.png)

This massing family allow us to create a curtain system by face, by selecting every face of our mass. I use it to create two curtain system, each one with a specific purpose.

[<img class="aligncenter size-full wp-image-548" src="http://bim42.com/wp-content/uploads/2014/08/Command.png" alt="Command" width="177" height="175" />](http://bim42.com/wp-content/uploads/2014/08/Command.png)

The first one is populated only with curtain panel to represent the finish face of our ceiling. Since every panel fit a face of our massing family, we don&#8217;t need to add any subdivision into this grid. Curtain panels are 100 mm thick, and have a 50 mm offset to place their finish face along the surface of the curtain system.

I create another curtain system to model the structural element of our ceiling. This curtain system is populated with specifically designed mullion, and without any curtain panel. These mullions represent the supporting elements of our ceiling, and are modeled along the border line of each panel.

[<img class="aligncenter size-full wp-image-550" src="http://bim42.com/wp-content/uploads/2014/08/Profile.png" alt="Profile" width="800" height="340" srcset="https://bim42.com/wp-content/uploads/2014/08/Profile.png 800w, https://bim42.com/wp-content/uploads/2014/08/Profile-300x127.png 300w, https://bim42.com/wp-content/uploads/2014/08/Profile-500x212.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/08/Profile.png)

Creating a specific curtain system to model mullions allows a greater control over the elements, and does not interfere with the previously created curtain panels.

Once these panels and structure are modeled, Revit will gladly create any needed section view, with all required graphic styles and tags.

[<img class="aligncenter size-full wp-image-547" src="http://bim42.com/wp-content/uploads/2014/08/Ceilling.png" alt="Ceilling" width="5065" height="3639" srcset="https://bim42.com/wp-content/uploads/2014/08/Ceilling.png 5065w, https://bim42.com/wp-content/uploads/2014/08/Ceilling-300x215.png 300w, https://bim42.com/wp-content/uploads/2014/08/Ceilling-1024x735.png 1024w, https://bim42.com/wp-content/uploads/2014/08/Ceilling-417x300.png 417w" sizes="(max-width: 5065px) 100vw, 5065px" />](http://bim42.com/wp-content/uploads/2014/08/Ceilling.png)

Every element is also fully documented, and therefore schedulable, allowing us to extract information like the surface of every panel, or the length of the structural framing.

I will enjoying my summer break for the next few weeks, and will put BIM 42 on hold. Next post in September!