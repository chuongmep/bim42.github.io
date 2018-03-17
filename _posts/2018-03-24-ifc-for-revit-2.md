---
id: 1261
title: IFC from Revit - Part 2
date: 2018-03-24T19:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1261
permalink: /2018/03/ifc-for-revit-2/
published: false
categories:
  - IFC
image: /assets/2018/03/10 - ParameterInIFCParametersGroup.jpg
tags:
  - IFC
  - Plugin
  - Revit
description: All the features I wish I knew about before I started exporting IFC from Revit
---

*This is the second part my post about exporting IFC from Revit.*

# Parameters under the IFC Parameter group

This is one of the neatest trick I have learn while researching for this article and a great example of the ideas behind the IFC Exporter of Revit. If you add a Revit parameter in the « IFC Parameters » group and name it like the ones defined in the Property Sets, Revit map it automatically to its IFC counterpart. This works for Type and Instance parameters.
Here, the Compartmentation property present in the Pset_WallCommon is created without any explicit mapping:

![The Compartmentation property]({{ "/assets/2018/03/10 - ParameterInIFCParametersGroup.jpg" | absolute_url }})

However, you must follow the name and value type defined in the IFC specification, or the parameter will not be exported. These names and values are found [here](http://www.buildingsmart-tech.org/ifc/IFC4/final/html/annex/annex-b/alphabeticalorder_psets.htm).

# Classifications

The IFC specification describe the [Classification](http://www.buildingsmart-tech.org/ifc/IFC2x4/rc2/html/schema/ifcexternalreferenceresource/lexical/ifcclassification.htm) concept, a way of integrating into the IFC file a reference to an existing classification. You can use this to add a broadly known classification like Uniclass or Uniformat, or even integrate your own.

![The Compartmentation property]({{ "/assets/2018/03/10 - ParameterInIFCParametersGroup.jpg" | absolute_url }})

Every element in your IFC file can then be linked to an instance of this classification, called a Reference. The easiest way to create such a classification is to select an Assembly Code for a given type in Revit. The IFC Exporter will then use this code to create a new classification and assign a classification reference to the instance of this type.

![The default classification]({{ "/assets/2018/03/11 - ClassificationDefault.jpg" | absolute_url }})

Even if this Assembly Code is a type parameter, the reference is created for every instance in the IFC file and linked to the actual instance with an IFCRELASSOCIATESCLASSIFICATION. In my case, I used the default Uniformat Classification shipped with Revit. The result can be seen in Solibri Model Viewer, in the Classification tab.

You can also create a type parameter ClassificationCode to create a new classification. It will create a new "Default Classification":

![A new classification]({{ "/assets/2018/03/12 - NewClassificationDefault.jpg" | absolute_url }})

You can also use the Exporter UI to specify the name and other information about your classification. In the Classification Settings, you add the definition of your classification, that will be exported within your IFC file.

![Naming the classification]({{ "/assets/2018/03/13 - MyOwnClassification.jpg" | absolute_url }})

You can also type in a description associated with you Reference code, in the following format:

{% highlight text %}
<Classification_Code>:<Description_Of_The_Code>
{% endhighlight %}

![A description is added to the code]({{ "/assets/2018/03/14 - CodeDescription.jpg" | absolute_url }})

# IFC Export Mapping

The IFC Options interface allows you to map a Revit category to an IFC one. You can also add a PredefinedType to a specific category.

![IFC Export settings]({{ "/assets/2018/03/14a - IfcExportSettings.jpg" | absolute_url }})

# IfcExportAs

If you want to override these general settings for a specific Revit type, or even for a specific element in Revit, you can use the IfcExportAs parameters. Added as an Instance or Type parameters, in the IFC Parameters group, you can use this parameter in different ways to define how you want some object to be exported.

In my example below, the default interface specifies that every mechanical equipment is exported as BuildingElementProxy. However, we add on the boiler its IFC class, IfcBoiler, in the IFCExportAs parameter, and get the corresponding class in the resulting IFC:

![Exporting a specific Revit element]({{ "/assets/2018/03/15 - IfcExportAs.jpg" | absolute_url }})

In BIM Vision, only the parent type is displayed: IfcEnergyConversionDevice

![Export see in BIM Vision]({{ "/assets/2018/03/16 - IfcExportAsBIMVision.jpg" | absolute_url }})

We can also use the IfcExportAs parameter to set the PredefinedType of the object. Here, I select the WATER type from the list of values provided by the [IfcBoilerTypeEnum](http://www.buildingsmart-tech.org/ifc/IFC2x4/rc2/html/schema/ifchvacdomain/lexical/ifcboilertypeenum.htm). The value is exported in the Type value of the IfcBoiler:

![Add a PredefinedType]({{ "/assets/2018/03/17 - PredefiniedType.jpg" | absolute_url }})

However, it seems that the override possibilities are limited for system families. I try with IfcWallType.PLUMBINGWALL on a wall, but the value wasn't exported.

# BaseQuantitites in rooms

Revit will automatically calculate and export [BaseQuantities](http://www.buildingsmart-tech.org/ifc/IFC4/final/html/annex/annex-b/alphabeticalorder_qsets.htm) for the rooms if you select the corresponding option in the Exporter UI:

![Exporting BaseQuantites]({{ "/assets/2018/03/21 - ExportBaseQuantities.jpg" | absolute_url }})

You can manually add to these base quantities with a custom parameter, prefixed with IfcQty:

![Adding new BaseQuantites]({{ "/assets/2018/03/22 - ExportBaseQuantitiesParameter.jpg" | absolute_url }})

Like every other IFC Parameters, make sure to set the proper type, like Area here. Other categories don’t support this feature, so you can only add these IfcQty parameters to the rooms.

The IFC Exporter forum is full of these gems, and I still have a lot to explore. Behind is rather simple interface, the IFC Exporter for Revit hide a lot of functionality and many possibilities for creating IFC files tailored to your needs.