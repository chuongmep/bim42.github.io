---
id: 810
title: IfcPropertySet
date: 2015-04-07T09:38:11+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=810
permalink: /2015/04/ifcpropertyset/
categories:
  - IFC
tags:
  - IFC
  - Open BIM
  - Revit
---
A very interesting feature of the IFC model is the IfcPropertySet . According to the official IFC specification, the IfcPropertySet is &#8220;a container class that holds properties within a property tree&#8221;. This allow to add user-defined properties to IFC elements or types. To make an analogy with Revit, it is pretty much like creating shared parameter.

Since the IFC exporter for Revit is accessible as open source code, [a new exporter](https://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3Aifc2015_windows32and64%3Aen) have been developed, and offer far more control over the creation of IFC files from Revit. One of the improvement is the ability to select Revit properties to be exported as IfcPropertySet.

The default option only export common IFC properties, but you can also export the entire set of Revit properties, or just selected ones, through user-defined property sets.

[<img class="aligncenter size-full wp-image-813" src="http://bim42.com/wp-content/uploads/2015/04/IFCExportProperties.png" alt="IFCExportProperties" width="786" height="291" srcset="https://bim42.com/wp-content/uploads/2015/04/IFCExportProperties.png 786w, https://bim42.com/wp-content/uploads/2015/04/IFCExportProperties-300x111.png 300w, https://bim42.com/wp-content/uploads/2015/04/IFCExportProperties-500x185.png 500w" sizes="(max-width: 786px) 100vw, 786px" />](http://bim42.com/wp-content/uploads/2015/04/IFCExportProperties.png)

To create one, I download [one of the example](http://sourceforge.net/p/ifcexporter/wiki/Notes%20on%20support%20for%20Extended%20FMHandOverView/) coming along with the source code of the new exporter.

In this example, we can see the global syntax for creating user defined property sets.

I use it to create my own PropertySet Definition File, and use it to export Creation Phase and Demolition Phase to a new PropertySet called Phases.

 `PropertySet:     Phases     I     IfcElement<br />
Creation Phase     Text     Phase Created<br />
Demolition Phase     Text     Phase Demolished<br />
` 

In this definition file, we set up the name of the PropertySet, its use (on instances or on types) and the list of elements were we want to apply our properties.
  
Then we add the mapping between IFC (left member) and Revit properties (right member), along with its data type (Text, Real, Integer or Boolean)

We add this file in the IFC Export configuration, and export our IFC file. We can now see these properties appearing under the Phases set :

Before :

[<img class="aligncenter size-full wp-image-812" src="http://bim42.com/wp-content/uploads/2015/04/Before.png" alt="Before" width="1011" height="402" srcset="https://bim42.com/wp-content/uploads/2015/04/Before.png 1011w, https://bim42.com/wp-content/uploads/2015/04/Before-300x119.png 300w, https://bim42.com/wp-content/uploads/2015/04/Before-500x199.png 500w" sizes="(max-width: 1011px) 100vw, 1011px" />](http://bim42.com/wp-content/uploads/2015/04/Before.png)

After :

[<img class="aligncenter size-full wp-image-811" src="http://bim42.com/wp-content/uploads/2015/04/After.png" alt="After" width="1016" height="508" srcset="https://bim42.com/wp-content/uploads/2015/04/After.png 1016w, https://bim42.com/wp-content/uploads/2015/04/After-300x150.png 300w, https://bim42.com/wp-content/uploads/2015/04/After-500x250.png 500w" sizes="(max-width: 1016px) 100vw, 1016px" />](http://bim42.com/wp-content/uploads/2015/04/After.png)

If IFC export and import is still not powerfull enought in many software solutions to enable geometrical modifications directly in the IFC file, there are plenty of opportunities to add metadata to the element, directly in IFC.