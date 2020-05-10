---
id: 1273
title: The Bimsync Revit plugin
date: 2020-05-09T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1273
permalink: /2020/05/bimsync-revit-plugin
published: true
categories:
  - bimsync
image: /assets/2020/05/bimsyncPLugin.png
tags:
  - bimsync
description: The new Revit plugin for Bimsync
---

A new Bimsync Revit plugin has been published on the Autodesk App Store. I am still a [big fan of Bimsync](https://bim42.com/2016/11/why-i-am-now-a-bimsync-fanboy/) and use it daily to review models and exchange documents and questions. But the lack of integration with Revit was making it difficult for designer to create and answer issues when working within Revit. This is now a problem solved thank to this new plugin.

Made by yours truly, it allows you to use all the features of the Bimsync issues without leaving the Revit interface.

Once logged in, you will be able to select a Bimsync project and an issue board. All issues from this board will be displayed with basic info like title, type and status.

![The list of issues]({{ "/assets/2020/05/MainView.png" | absolute_url }})

You can filter these issues with the search bar above the list. This will allow you to select issue based on the requester, the assignee, the due date or any other property of the issue. You can also type some text to search for a specific text in the issue title or description.

![The search bar]({{ "/assets/2020/05/searchBar.gif" | absolute_url }})

By clicking on any issue in the list, you can open the issue page and edit anything: title, description, status, type... You can add labels by searching through the available labels in your project.

Comments on the issue will appears below, and the Camera icon will allow you to zoom to the viewpoint of any comment created in a Bimsync model. This will create a new Revit 3D view, perspective or orthographic depending on the source viewpoint.

![The search bar]({{ "/assets/2020/05/zoom.gif" | absolute_url }})

You can also add any number of new comments to your issue. When a Revit 3D view is open, any new comment will save the viewpoint, allowing you to zoom to the same exact location in Bimsync. If any other view is open, the plugin will add a nice screenshot to the new comment.

You can also use the plugin to upload your Revit model as an IFC file to Bimsync. This feature will export your model to IFC, compress the resulting file and upload it to the selected Bimsync model as a new revision.

![The search bar]({{ "/assets/2020/05/upload.gif" | absolute_url }})

You can select any IFC export configuration before uploading your model, allowing you to fine tune how you want to export your model. To create a new IFC export setup, use the IFC export menu, create a new setup and close the menu before exporting the model to IFC. You can also use the \<Bimsync Setup\>, a setup build specifically for Bimsync, with the following options:

| Setting        | Value           |
| ------------- |-------------|
|IFCVersion|IFCVersion.IFC2x3CV2|
|SpaceBoundaries|1|
|ActivePhaseId|ElementId.InvalidElementId|
|ExportBaseQuantities|true|
|SplitWallsAndColumns|false|
|VisibleElementsOfCurrentView|false|
|Use2DRoomBoundaryForVolume|false|
|UseFamilyAndTypeNameForReference|true|
|ExportInternalRevitPropertySets|true|
|ExportIFCCommonPropertySets|true|
|Export2DElements|false|
|ExportPartsAsBuildingElements|true|
|ExportBoundingBox|false|
|ExportSolidModelRep|false|
|ExportSchedulesAsPsets|false|
|ExportUserDefinedPsets|false|
|ExportUserDefinedPsetsFileName|""|
|ExportLinkedFiles|false|
|IncludeSiteElevation|true|
|UseActiveViewGeometry|false|
|ExportSpecificSchedules|false|
|TessellationLevelOfDetail|0|
|StoreIFCGUID|true|
|ExportRoomsInView|true|

I learnt a great deal while building this plugin. I owe some special thanks to [Petr Mitev](https://twitter.com/mitevpi) for his [Revit WPF Template](https://github.com/mitevpi/revit-wpf-template) and [Jeremy Clark](https://twitter.com/jeremybytes) for his [Pluralsight course on dependency injection](https://app.pluralsight.com/library/courses/using-dependency-injection-on-ramp).

This plugin is already available for free on the Autodesk App Store. It will replace my old Bimsync plugin that I will no longer maintain.