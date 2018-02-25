---
id: 248
title: Walls in Geometry Gym
date: 2012-10-15T20:31:01+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=248
permalink: /2012/10/walls-in-geometry-gym/
categories:
  - Grasshopper
  - IFC
tags:
  - Geometry Gym
  - Grasshopper
  - IFC
  - Plugin
  - Revit
---
A recent webinar about interoperability between Grasshopper and Revit make me look again on these tools, particularly for importing walls, In fact, I generally test these kinds of tools with a set a beams, more or less intricate, but never with walls, so I decide to generate a set of walls using the Geometry Gym IFC Importer for Revit.

Using Geometry Gym require at least some basic knowledge of the IFC structure. In fact, using this tool can be a really good starting point for studying the model behind Industry Foundation Classes.

Any IFC building object must be included in a (IFC) building, itself included in a (IFC) project, both of them must have a GUID and a name. So we start by placing these components on the Grasshopper’s caneva.

[<img class="aligncenter size-full wp-image-249" title="1" alt="" src="http://bim42.com/wp-content/uploads/2012/10/1.png" height="271" width="584" srcset="https://bim42.com/wp-content/uploads/2012/10/1.png 1142w, https://bim42.com/wp-content/uploads/2012/10/1-300x139.png 300w, https://bim42.com/wp-content/uploads/2012/10/1-1024x475.png 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/10/1.png)

In order to have our NURBS path curve understood by Revit, we approximate it into a set of lines and arcs, using the specific Geometry Gym component.

[<img class="aligncenter size-full wp-image-251" title="2" alt="" src="http://bim42.com/wp-content/uploads/2012/10/2.png" height="232" width="458" srcset="https://bim42.com/wp-content/uploads/2012/10/2.png 458w, https://bim42.com/wp-content/uploads/2012/10/2-300x151.png 300w" sizes="(max-width: 458px) 100vw, 458px" />](http://bim42.com/wp-content/uploads/2012/10/2.png)

We create an ggIFCElementParameter component to give a pretty name to our wall.

[<img class="aligncenter size-full wp-image-252" title="3" alt="" src="http://bim42.com/wp-content/uploads/2012/10/3.png" height="318" width="514" srcset="https://bim42.com/wp-content/uploads/2012/10/3.png 514w, https://bim42.com/wp-content/uploads/2012/10/3-300x185.png 300w" sizes="(max-width: 514px) 100vw, 514px" />](http://bim42.com/wp-content/uploads/2012/10/3.png)

In order to create the multy-layer structure, we add two materials, both of them linked to a MaterialLayer component where we define the thickness of each layer. These component are merged into a MaterialLayerSet, itself link to a wall type.

[<img class="aligncenter size-full wp-image-253" title="4" alt="" src="http://bim42.com/wp-content/uploads/2012/10/4.png" height="215" width="584" srcset="https://bim42.com/wp-content/uploads/2012/10/4.png 1716w, https://bim42.com/wp-content/uploads/2012/10/4-300x110.png 300w, https://bim42.com/wp-content/uploads/2012/10/4-1024x377.png 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/10/4.png)

The IFC class used by Revit for generating walls is the IFCWallStandardCase, so we use this component in our Grasshopper definition. We link all these components to our IFC Wall Standard Case, had a height parameter, and bake the whole think.

[<img class="aligncenter size-full wp-image-254" title="5" alt="" src="http://bim42.com/wp-content/uploads/2012/10/5.png" height="733" width="584" srcset="https://bim42.com/wp-content/uploads/2012/10/5.png 968w, https://bim42.com/wp-content/uploads/2012/10/5-238x300.png 238w, https://bim42.com/wp-content/uploads/2012/10/5-815x1024.png 815w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/10/5.png)

The resulting IFC file contains a pretty good wall, with every expected parameter. We check it in my favorite IFC viewer, the Solibri Model checker.

Once imported in Revit, using the embedded plugin, it creates a generic component looking like our wall. It appears in a schedule with the family name and type as set, but it’s still not an editable Revit wall.

I generally use the massing tool to create walls in Geometry Gym. I create a simple IFCExtrudedAreaSolid (for example) from a base NURBS curve, and then import it in Revit to generate a mass.

[<img class="aligncenter size-full wp-image-255" title="6" alt="" src="http://bim42.com/wp-content/uploads/2012/10/6.png" height="270" width="584" srcset="https://bim42.com/wp-content/uploads/2012/10/6.png 788w, https://bim42.com/wp-content/uploads/2012/10/6-300x138.png 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/10/6.png)

&nbsp;

[<img class="aligncenter size-full wp-image-256" title="7" alt="" src="http://bim42.com/wp-content/uploads/2012/10/7.png" height="624" width="584" srcset="https://bim42.com/wp-content/uploads/2012/10/7.png 664w, https://bim42.com/wp-content/uploads/2012/10/7-280x300.png 280w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/10/7.png)

I can now use this mass to create my curved walls in Revit, along with the floors slabs. This method need an additional step (creating the wall from the Revit mass faces), but create native Revit walls.

[<img class="aligncenter size-full wp-image-257" title="8" alt="" src="http://bim42.com/wp-content/uploads/2012/10/8.png" height="650" width="584" srcset="https://bim42.com/wp-content/uploads/2012/10/8.png 819w, https://bim42.com/wp-content/uploads/2012/10/8-269x300.png 269w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/10/8.png)

As I write these lines, a new version of the IFC Import plugin for Revit have been posted on the Geometry Gym [blog](http://ssi.wikidot.com/downloads "Geometry Gym"), I still have to review the improvement.