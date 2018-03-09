---
id: 684
title: AutoCAD Civil 3D to Revit
date: 2014-11-08T16:22:16+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=684
permalink: /2014/11/autocad-civil-3d-to-revit/
categories:
  - Autodesk
image: /assets/2014/11/ImportPoints.jpg
tags:
  - Autodesk
  - Civil 3D
  - Revit
---
I recently worked with AutoCAD Civil 3D and explored the various possibilities for creating toposurfaces in Revit from Civil 3D objects.

My first impulse was to import the surface as a DWG, and use it to create my toposurface. But a Civil 3D surface object is not identified when imported in Revit.

I use the Extract Object surface function in AutoCAD Civil 3D to transform every surface contour in a 3D polyline.

![ScreenClip-2](/assets/2014/11/ScreenClip-2.jpg)

Back in Revit, I import my surface as a set of 3D polylines following contours in my AutoCAD Civil Surface.

In the Toposurface tools, I select the imported DWG, and check the layers containing these polylines.

![ImportFromDWG](/assets/2014/11/ImportFromDWG.jpg)

Revit creates a surface point along every surface contour, and rebuilts our surface.

If you are a Subscription customer, you have access to the LandXML import from Site Designer, recently added to Revit. Start by exporting your AutoCAD Civil 3D surface in LandXML.

![ScreenClip-21](/assets/2014/11/ScreenClip-21.jpg)

Then use the Site Designer to import it back in Revit.

![ImportLandXML](/assets/2014/11/ImportLandXML.jpg)

The resulting Revit toposurface contains ten times less points than the version created from contour lines, which can be game-changing, especially if your are dealing with large or complex surfaces.

I didn't found any free plug-in to import directly LandXML in your Revit model, but if you are of the DIY type, you can use [the example of code](http://thebuildingcoder.typepad.com/blog/2010/01/import-landxml-surface.html "Import LandXML surface") provided by Jeremy Tammik on his blog.

You can also import AutoCAD Civil 3D points directly in Revit. To do so, you first have to change the style of your surface to display all its points.

![ScreenClip-4](/assets/2014/11/ScreenClip-4.jpg)

Then, extract these points as simple AutoCAD points and convert them to COGO points. Here, make sure to set the Prompt for Description to Automatic, or you will have to type a description for every one of these point, which can be somehow tedious for thousands of points.

![ScreenClip-5](/assets/2014/11/ScreenClip-5.jpg)

Now, you can export the coordinates of these COGO point as a Comma Separated text file, and use this file to create your toposurface in Revit.

![ImportPoints](/assets/2014/11/ImportPoints.jpg)

This option is a nice workaround if you don't have the possibility to import directly LandXML in your Revit model.