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

![1](http://bim42.com/wp-content/uploads/2012/10/1.png)

In order to have our NURBS path curve understood by Revit, we approximate it into a set of lines and arcs, using the specific Geometry Gym component.

![2](http://bim42.com/wp-content/uploads/2012/10/2.png)

We create an ggIFCElementParameter component to give a pretty name to our wall.

![3](http://bim42.com/wp-content/uploads/2012/10/3.png)

In order to create the multy-layer structure, we add two materials, both of them linked to a MaterialLayer component where we define the thickness of each layer. These component are merged into a MaterialLayerSet, itself link to a wall type.

![4](http://bim42.com/wp-content/uploads/2012/10/4.png)

The IFC class used by Revit for generating walls is the IFCWallStandardCase, so we use this component in our Grasshopper definition. We link all these components to our IFC Wall Standard Case, had a height parameter, and bake the whole think.

![5](http://bim42.com/wp-content/uploads/2012/10/5.png)

The resulting IFC file contains a pretty good wall, with every expected parameter. We check it in my favorite IFC viewer, the Solibri Model checker.

Once imported in Revit, using the embedded plugin, it creates a generic component looking like our wall. It appears in a schedule with the family name and type as set, but it’s still not an editable Revit wall.

I generally use the massing tool to create walls in Geometry Gym. I create a simple IFCExtrudedAreaSolid (for example) from a base NURBS curve, and then import it in Revit to generate a mass.

![6](http://bim42.com/wp-content/uploads/2012/10/6.png)

&nbsp;

![7](http://bim42.com/wp-content/uploads/2012/10/7.png)

I can now use this mass to create my curved walls in Revit, along with the floors slabs. This method need an additional step (creating the wall from the Revit mass faces), but create native Revit walls.

![8](http://bim42.com/wp-content/uploads/2012/10/8.png)

As I write these lines, a new version of the IFC Import plugin for Revit have been posted on the Geometry Gym [blog](http://ssi.wikidot.com/downloads "Geometry Gym"), I still have to review the improvement.