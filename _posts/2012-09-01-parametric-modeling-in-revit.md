---
id: 207
title: Parametric modeling in Revit
date: 2012-09-01T16:46:42+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=207
permalink: /2012/09/parametric-modeling-in-revit/
categories:
  - Grasshopper
  - Revit
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

![<img class="aligncenter size-full wp-image-210" title="Commands" src="http://bim42.com/wp-content/uploads/2012/09/commands1.jpg" alt="" width="145" height="276" />](http://bim42.com/wp-content/uploads/2012/09/commands1.jpg)Designing these element in Grasshopper follow pretty much the same logic than in Revit, with family name and type, points and parameters, except of course for the possibilities offered by natives Grasshopper components.

Here is a little example for generating beams on a double-curved surface from LunchBox.

![<img class="aligncenter size-full wp-image-211" title="Caneva" src="http://bim42.com/wp-content/uploads/2012/09/caneva1.jpg" alt="" width="584" height="228" srcset="https://bim42.com/wp-content/uploads/2012/09/caneva1.jpg 1628w, https://bim42.com/wp-content/uploads/2012/09/caneva1-300x117.jpg 300w, https://bim42.com/wp-content/uploads/2012/09/caneva1-1024x400.jpg 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/09/caneva1.jpg)Make sure you have the correct Excel 2010 worksheet opened; I struggled for a while before realizing that my Excel version was outdated.

The Hummingbird component writes a few lines in our Excel file, something like that:

![<img class="aligncenter size-full wp-image-212" title="Excel" src="http://bim42.com/wp-content/uploads/2012/09/excel.jpg" alt="" width="584" height="92" srcset="https://bim42.com/wp-content/uploads/2012/09/excel.jpg 1288w, https://bim42.com/wp-content/uploads/2012/09/excel-300x47.jpg 300w, https://bim42.com/wp-content/uploads/2012/09/excel-1024x162.jpg 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/09/excel.jpg)Then we go the Add-Ins panel of Revit and start the WhiteFeet Model Builder to import our datasheet. There are a few options to set, with everything quite self-explanatory.

![<img class="aligncenter size-full wp-image-213" title="WhiteFeetModelBuilder" src="http://bim42.com/wp-content/uploads/2012/09/whitefeetmodelbuilder.jpg" alt="" width="584" height="426" srcset="https://bim42.com/wp-content/uploads/2012/09/whitefeetmodelbuilder.jpg 785w, https://bim42.com/wp-content/uploads/2012/09/whitefeetmodelbuilder-300x218.jpg 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/09/whitefeetmodelbuilder.jpg)The plugin generated smoothly these beams in Revit, with all the requested parameters:

![<img class="aligncenter size-full wp-image-214" title="RevitBeams" src="http://bim42.com/wp-content/uploads/2012/09/revitbeams.jpg" alt="" width="584" height="306" srcset="https://bim42.com/wp-content/uploads/2012/09/revitbeams.jpg 1598w, https://bim42.com/wp-content/uploads/2012/09/revitbeams-300x157.jpg 300w, https://bim42.com/wp-content/uploads/2012/09/revitbeams-1024x537.jpg 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/09/revitbeams.jpg)Among Grasshopper plugins, Chameleon allows to create Revit adaptative components directly from Grasshopper. It also includes components to edit Revit parameters directly on the model.

All these plugins, among others, became a very interesting alternative to the average modeling in Revit, and fill the gap between parametric modeling and a more average BIM modelisation.