---
id: 684
title: AutoCAD Civil 3D to Revit
date: 2014-11-08T16:22:16+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=684
permalink: /2014/11/autocad-civil-3d-to-revit/
categories:
  - Autodesk
tags:
  - Autodesk
  - Civil 3D
  - Revit
---
I recently worked with AutoCAD Civil 3D and explored the various possibilities for creating toposurfaces in Revit from Civil 3D objects.

My first impulse was to import the surface as a DWG, and use it to create my toposurface. But a Civil 3D surface object is not identified when imported in Revit.

I use the Extract Object surface function in AutoCAD Civil 3D to transform every surface contour in a 3D polyline.

![<img class="aligncenter size-full wp-image-688" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip-2.png" alt="Extract Contour" width="404" height="412" srcset="https://bim42.com/wp-content/uploads/2014/11/ScreenClip-2.png 404w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-2-294x300.png 294w" sizes="(max-width: 404px) 100vw, 404px" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip-2.png)

Back in Revit, I import my surface as a set of 3D polylines following contours in my AutoCAD Civil Surface.

In the Toposurface tools, I select the imported DWG, and check the layers containing these polylines.

![<img class="aligncenter size-full wp-image-685" src="http://bim42.com/wp-content/uploads/2014/11/ImportFromDWG.png" alt="ImportFromDWG" width="912" height="603" srcset="https://bim42.com/wp-content/uploads/2014/11/ImportFromDWG.png 912w, https://bim42.com/wp-content/uploads/2014/11/ImportFromDWG-300x198.png 300w, https://bim42.com/wp-content/uploads/2014/11/ImportFromDWG-453x300.png 453w" sizes="(max-width: 912px) 100vw, 912px" />](http://bim42.com/wp-content/uploads/2014/11/ImportFromDWG.png)

Revit creates a surface point along every surface contour, and rebuilts our surface.

If you are a Subscription customer, you have access to the LandXML import from Site Designer, recently added to Revit. Start by exporting your AutoCAD Civil 3D surface in LandXML.

![<img class="aligncenter size-full wp-image-689" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip-21.png" alt="ScreenClip [2]" width="370" height="508" srcset="https://bim42.com/wp-content/uploads/2014/11/ScreenClip-21.png 370w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-21-218x300.png 218w" sizes="(max-width: 370px) 100vw, 370px" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip-21.png)

Then use the Site Designer to import it back in Revit.

![<img class="aligncenter size-full wp-image-686" src="http://bim42.com/wp-content/uploads/2014/11/ImportLandXML.png" alt="ImportLandXML" width="1104" height="631" srcset="https://bim42.com/wp-content/uploads/2014/11/ImportLandXML.png 1104w, https://bim42.com/wp-content/uploads/2014/11/ImportLandXML-300x171.png 300w, https://bim42.com/wp-content/uploads/2014/11/ImportLandXML-1024x585.png 1024w, https://bim42.com/wp-content/uploads/2014/11/ImportLandXML-500x285.png 500w" sizes="(max-width: 1104px) 100vw, 1104px" />](http://bim42.com/wp-content/uploads/2014/11/ImportLandXML.png)

The resulting Revit toposurface contains ten times less points than the version created from contour lines, which can be game-changing, especially if your are dealing with large or complex surfaces.

I didn&#8217;t found any free plug-in to import directly LandXML in your Revit model, but if you are of the DIY type, you can use [the example of code](http://thebuildingcoder.typepad.com/blog/2010/01/import-landxml-surface.html "Import LandXML surface") provided by Jeremy Tammik on his blog.

You can also import AutoCAD Civil 3D points directly in Revit. To do so, you first have to change the style of your surface to display all its points.

![<img class="aligncenter size-full wp-image-690" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip-4.png" alt="ScreenClip [4]" width="798" height="364" srcset="https://bim42.com/wp-content/uploads/2014/11/ScreenClip-4.png 798w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-4-300x136.png 300w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-4-500x228.png 500w" sizes="(max-width: 798px) 100vw, 798px" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip-4.png)

Then, extract these points as simple AutoCAD points and convert them to COGO points. Here, make sure to set the Prompt for Description to Automatic, or you will have to type a description for every one of these point, which can be somehow tedious for thousands of points.

![<img class="aligncenter size-full wp-image-691" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip-5.png" alt="Edit Point Creation oprions" width="489" height="445" srcset="https://bim42.com/wp-content/uploads/2014/11/ScreenClip-5.png 489w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-5-300x273.png 300w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-5-329x300.png 329w" sizes="(max-width: 489px) 100vw, 489px" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip-5.png)

Now, you can export the coordinates of these COGO point as a Comma Separated text file, and use this file to create your toposurface in Revit.

![<img class="aligncenter size-full wp-image-687" src="http://bim42.com/wp-content/uploads/2014/11/ImportPoints.png" alt="ImportPoints" width="900" height="480" srcset="https://bim42.com/wp-content/uploads/2014/11/ImportPoints.png 900w, https://bim42.com/wp-content/uploads/2014/11/ImportPoints-300x160.png 300w, https://bim42.com/wp-content/uploads/2014/11/ImportPoints-500x266.png 500w" sizes="(max-width: 900px) 100vw, 900px" />](http://bim42.com/wp-content/uploads/2014/11/ImportPoints.png)

This option is a nice workaround if you don&#8217;t have the possibility to import directly LandXML in your Revit model.