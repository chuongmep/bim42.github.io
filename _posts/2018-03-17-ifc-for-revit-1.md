---
id: 1261
title: IFC from Revit - Part 1
date: 2018-03-17T19:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1261
permalink: /2018/03/ifc-for-revit-1/
published: true
categories:
  - IFC
image: /assets/2018/03/01 - SelectLevels.jpg
tags:
  - IFC
  - Plugin
  - Revit
description: All the features I wish I knew about before I started exporting IFC from Revit
---

*This is the first part of a two parts post summarizing all the features I wish I knew about before I started exporting IFC from Revit.*

I am working a lot with IFC these days and retrieving the proper values from various authoring software can be a challenge. To check if my IFC requirement are even possible, I have to understand the possibilities offered by theses authoring software. So, I spend quite some time understanding the IFC Exporter for Revit.

# IFC for Revit plugin

If you rely on IFC for your process, you must start by downloading the last version of the IFC for Revit plugin. This plugin seamlessly replaces the built-in IFC module of Revit and bring improvement to the standard IFC import and export. Its source is available on [Source Forge](https://sourceforge.net/projects/ifcexporter/) and you can even propose your own improvement.

This plugin is available on the Autodesk App Exchange:

| Revit Version | Link |
| :--- | :--- |
| Revit 2018 | [https://apps.autodesk.com/RVT/en/Detail/Index?id=6193770166503453647&appLang=en&os=Win64](https://apps.autodesk.com/RVT/en/Detail/Index?id=6193770166503453647&appLang=en&os=Win64) |
| Revit 2017 | [https://apps.autodesk.com/RVT/en/Detail/Index?id=1049118595309324136&appLang=en&os=Win64](https://apps.autodesk.com/RVT/en/Detail/Index?id=1049118595309324136&appLang=en&os=Win64) |
| Revit 2016 | [https://apps.autodesk.com/RVT/en/Detail/Index?id=3754730560173591798&appLang=en&os=Win32\_64](https://apps.autodesk.com/RVT/en/Detail/Index?id=3754730560173591798&appLang=en&os=Win32_64) |
| Revit 2015 | [https://apps.autodesk.com/RVT/en/Detail/Index?id=1636561288646603019&appLang=en&os=Win32\_64](https://apps.autodesk.com/RVT/en/Detail/Index?id=1636561288646603019&appLang=en&os=Win32_64 "Plug-in export IFC from Revit 2015") |

New releases of Revit are now shipped with the last available version of this IFC plugin.

# Selecting which levels to export

Deactivating the « Building Story » parameter on a Revit level remove the corresponding IFCBuildingStorey from the exported IFC file. Elements based on this level are associated with the IfcBuildingStorey immediately below.

![Exporting Revit Levels]({{ "/assets/2018/03/01 - SelectLevels.jpg" | absolute_url }})

This feature allows you to use Revit levels as modelling supports, while keeping all your elements neatly organized in functional building stories after the export.
Furthermore, Revit levels without any element on it are not exported.

# Exporting Revit property

Since [my last post](https://www.bim42.com/2015/04/ifcpropertyset/), the IFC Exporter has made some progress, and new options are available.

## Exporting all Revit properties

Activating the « Export Revit properties » in the Exporter UI send all Revit properties to custom Property Sets named after the parameter group in Revit.

## Creating your own property sets

With a user-created configuration text file, you can create your own Property Sets and fill them with parameters from Revit.
In this configuration file, a first line describes the Property Set: its name, whether it will be associated with Instances (I) or Types (T) and the list of elements for which to create the custom Property Set. The following lines lists all the properties of the Property Set, their names, types and the associated Revit parameters.

Below is an example of the configuration file used to export the Creation and Demolition phase of every wall and roof in a new Property Set named "Phases"

{% highlight text %}
PropertySet:    Phases    I    IfcWall, IfcRoof
    Creation Phase    Text    Phase Created
    Demolition Phase    Text    Phase Demolished
{% endhighlight %}

![Creating custom Property Sets]({{ "/assets/2018/03/02 - CustomPropertySets.jpg" | absolute_url }})

This configuration file is loaded in the "Export user defined property sets" field in the Exporter UI:

![Add the configuration file in the Exporter UI]({{ "/assets/2018/03/02 - CustomPropertySetsMappingFile.jpg" | absolute_url }})

![The new Property Set]({{ "/assets/2018/03/04 - CustomPropertySetsResult.jpg" | absolute_url }})

## Mapping parameters

The mapping text file allows you to send Revit values to any IFC parameter. Each line in this file link a Revit parameter to an IFC one. However, you can only use "official" IFC Parameter, contained in one of the Property Sets [defined in the specification](http://www.buildingsmart-tech.org/ifc/IFC4/final/html/annex/annex-b/alphabeticalorder_psets.htm). Furthermore, the data type of the IFC property must be the same than the Revit parameter. If you need something different than these parameters, you will have to create your own property sets.

Below is an example of the mapping file used to export the Analytic Construction value of every doors to their [Reference](http://www.buildingsmart-tech.org/ifc/IFC4/final/html/schema/ifcsharedbldgelements/pset/pset_doorcommon.htm) value in IFC: 

{% highlight text %}
Pset_DoorCommon    Reference    Analytic Construction
{% endhighlight %}

![Parameters mapping]({{ "/assets/2018/03/05 - ParametersMapping.jpg" | absolute_url }})

This mapping file is then loaded in the "Export user defined property sets" field in the Exporter UI:

![Add the configuration file in the Exporter UI]({{ "/assets/2018/03/06 - ParametersMappingFile.jpg" | absolute_url }})

![The exported properties]({{ "/assets/2018/03/07 - ParametersMappingResult.jpg" | absolute_url }})

# IfcZones

IfcZones are groups of IfcSpaces used to define areas in a building. To create these IfcZones in Revit, two methods are available, one for MEP Spaces and the other for Rooms.

Grouping MEP Spaces with HVAC Zones will create IfcZones in the exported IFC. You can also export the parameters of these HVAC Zones to the PSet_ZoneCommon property set, or any other new property set.

![The exported IfcZones from the HVAC Zones]({{ "/assets/2018/03/08 - IFCZoneFromHVACSpaces.jpg" | absolute_url }})

To create IfcZones from a group of Rooms, you must create a "ZoneName" parameter on these room. Revit will create an IfcZone for every unique "ZoneName" value and assign the room to the corresponding IfcZone. You can also use the "ZoneObjectType" and the "ZoneDescription" parameters to add properties to the resulting IfcZone. More details can be found [here](https://sourceforge.net/p/ifcexporter/wiki/Exporting%20Zones/).

![The exported IfcZones from the rooms]({{ "/assets/2018/03/09 - IFCZoneFromRooms.jpg" | absolute_url }})

Here, you can see the description of the zone, however, the PSet_ZoneCommon is not created.

We also note that even if HVAC Space and Room are both exported to IfcSpace, the exporter add their original category in the Description field in IFC.

In the upcomming second part of this post, we will explore how to add classifications, IfcZones and QuantitySets to your IFC file. Stay tunned !
