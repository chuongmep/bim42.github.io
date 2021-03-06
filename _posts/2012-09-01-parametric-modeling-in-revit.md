---
id: 207
title: Parametric modeling in Revit
date: 2012-09-01T16:46:42+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=207
permalink: /2012/09/parametric-modeling-in-revit/
categories:
  - Grasshopper
  - Revit
image: /assets/2012/09/revitbeams.jpg
tags:
  - Grasshopper
  - Plugin
  - Revit
  - Software
---
There is a trendy topic on the Grasshopper forum these days about links between Grasshopper and Revit, and this refers to a more general subject : How to generate parametric geometry in Revit.

Since embedded tools in Revit are mostly oriented toward classical design, workarounds have been developed to create a more complex geometry.

The Revit plug-in Dynamo, developed by Ian Keough, is one of these tools. Starting as an open source side project, it has been integrated into the Autodesk lab to became one of its most popular projects.

This tool is a graphical user interface (GUI) for parametring design directly into Revit. It looks pretty much like Grasshopper, with a canevas where we drag components link together to directly create native Revit elements.

WhiteFeet is also a Revit Plugin, which allow creating native Revit elements from an Excel datasheet. It can be used alone, but I rather use it with Hummingbird, a Grasshopper extension used to generate these Excel datasheets. There is a Grasshopper component for each major Revit command.

![commands1]({{ "/assets/2012/09/commands1.jpg" | absolute_url }})

Designing these element in Grasshopper follow pretty much the same logic than in Revit, with family name and type, points and parameters, except of course for the possibilities offered by natives Grasshopper components.

Here is a little example for generating beams on a double-curved surface from LunchBox.

![caneva1]({{ "/assets/2012/09/caneva1.jpg" | absolute_url }})

Make sure you have the correct Excel 2010 worksheet opened; I struggled for a while before realizing that my Excel version was outdated.

The Hummingbird component writes a few lines in our Excel file, something like that:

![excel]({{ "/assets/2012/09/excel.jpg" | absolute_url }})

Then we go the Add-Ins panel of Revit and start the WhiteFeet Model Builder to import our datasheet. There are a few options to set, with everything quite self-explanatory.

![whitefeetmodelbuilder]({{ "/assets/2012/09/whitefeetmodelbuilder.jpg" | absolute_url }})

The plugin generated smoothly these beams in Revit, with all the requested parameters:

![revitbeams]({{ "/assets/2012/09/revitbeams.jpg" | absolute_url }})

Among Grasshopper plugins, Chameleon allows to create Revit adaptative components directly from Grasshopper. It also includes components to edit Revit parameters directly on the model.

All these plugins, among others, became a very interesting alternative to the average modeling in Revit, and fill the gap between parametric modeling and a more average BIM modelisation.