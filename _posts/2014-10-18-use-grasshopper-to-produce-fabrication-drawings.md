---
id: 657
title: Use Grasshopper to produce fabrication drawings
date: 2014-10-18T15:57:09+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=657
permalink: /2014/10/use-grasshopper-to-produce-fabrication-drawings/
categories:
  - Grasshopper
tags:
  - .NET
  - Automation
  - Documentation
  - Grasshopper
---
I recently have to produce fabrication drawings from a set of panels covering a single curved surface.

These panel were modeled in Rhino 3D, so I decide to extract their boundary curves and use AutoCAD to produce a drawing for every one of them.

I build here an example by extruding a surface between two symmetrical splines.

[<img class="aligncenter size-full wp-image-659" src="http://bim42.com/wp-content/uploads/2014/10/1_BaseSurface.png" alt="1_BaseSurface" width="800" height="211" srcset="https://bim42.com/wp-content/uploads/2014/10/1_BaseSurface.png 800w, https://bim42.com/wp-content/uploads/2014/10/1_BaseSurface-300x79.png 300w, https://bim42.com/wp-content/uploads/2014/10/1_BaseSurface-500x131.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/10/1_BaseSurface.png)

This construction method create a single curved surface, which is the easiest to cover with plane panel, here with the “Quad Panels” component from the LunchBox plugin.

[<img class="aligncenter size-full wp-image-660" src="http://bim42.com/wp-content/uploads/2014/10/2_PanelSurface.png" alt="2_PanelSurface" width="800" height="362" srcset="https://bim42.com/wp-content/uploads/2014/10/2_PanelSurface.png 800w, https://bim42.com/wp-content/uploads/2014/10/2_PanelSurface-300x135.png 300w, https://bim42.com/wp-content/uploads/2014/10/2_PanelSurface-500x226.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/10/2_PanelSurface.png)

Then I extract every panel edge and orient it horizontally on the base XY plane.

[<img class="aligncenter size-full wp-image-661" src="http://bim42.com/wp-content/uploads/2014/10/3_PanelEdges.png" alt="3_PanelEdges" width="800" height="260" srcset="https://bim42.com/wp-content/uploads/2014/10/3_PanelEdges.png 800w, https://bim42.com/wp-content/uploads/2014/10/3_PanelEdges-300x97.png 300w, https://bim42.com/wp-content/uploads/2014/10/3_PanelEdges-500x162.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/10/3_PanelEdges.png)

My objective here is to bake every panel boundary curve on a different layer to be able to sort them separately in AutoCAD. To do so, I use the &#8220;Object Bake&#8221; component from LunchBox. I also use a &#8220;Series&#8221; to create a layer names for each panel. Here the names are only numbers formatted as text.

[<img class="aligncenter size-full wp-image-662" src="http://bim42.com/wp-content/uploads/2014/10/4_BakeEdges.png" alt="4_BakeEdges" width="800" height="390" srcset="https://bim42.com/wp-content/uploads/2014/10/4_BakeEdges.png 800w, https://bim42.com/wp-content/uploads/2014/10/4_BakeEdges-300x146.png 300w, https://bim42.com/wp-content/uploads/2014/10/4_BakeEdges-500x243.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/10/4_BakeEdges.png)

The next step is to add dimensions. Sadly, since native grasshopper dimension does not have any output object, we cannot bake them with the &#8220;Object Bake&#8221;. So I&#8217;m using my own Linear Dimension creation component. As you can see, the code is quite straightforward. I use standard Rhino functions to create my dimensions, and have a small private function for selecting or creating the layer to place our dimension.

<pre class="brush: csharp; title: ; notranslate" title="">private void RunScript(bool Bake, Point3d A,
                        Point3d B, Point3d C, 
                        string Layer, ref object O)
  {

    if (Bake == true)
    {

      Point3d A0 = new Point3d(A.X, A.Y, 0);
      Point3d B0 = new Point3d(B.X, B.Y, 0);

      double a = (B0.X - A0.X) / (B0.Y - A0.Y);
      double Xc = 1;
      double Yc = Xc / a - A0.X / a + A0.Y;

      Point3d C0 = new Point3d(C.X, C.Y, 0);

      Plane refPlane = new Plane(A0, B0, C0);

      double u,v;
      refPlane.ClosestParameter(A0, out u, out v);
      Point2d A2d = new Point2d(u, v);

      refPlane.ClosestParameter(B0, out u, out v);
      Point2d B2d = new Point2d(u, v);

      refPlane.ClosestParameter(C0, out u, out v);
      Point2d C2d = new Point2d(u, v);

      Rhino.Geometry.LinearDimension dimension = 
                  new LinearDimension(refPlane, A2d, B2d, C2d);

      ObjectAttributes dimAtt = new ObjectAttributes();
      dimAtt.LayerIndex = ensureLayer(tag);

      if (Rhino.RhinoDoc.ActiveDoc.
Objects.AddLinearDimension(dimension, dimAtt) != Guid.Empty)
      {
        doc.Views.Redraw();
      }
    }

  }

  // &lt;Custom additional code&gt; 
  private int ensureLayer(string lay)
  {
    int i = doc.Layers.Find(lay, true);
    if(i &lt; 0)
      return doc.Layers.Add(lay, Color.Black);
    else
      return i;
  }
</pre>

With the &#8220;Disc&#8221; component, I retrieve every summit of my panel boundary, and place a dimension between two of these points. I also use an offset of my panel boundary to set up the position of the dimension line.

[<img class="aligncenter size-full wp-image-663" src="http://bim42.com/wp-content/uploads/2014/10/5_LinearDimension.png" alt="5_LinearDimension" width="800" height="263" srcset="https://bim42.com/wp-content/uploads/2014/10/5_LinearDimension.png 800w, https://bim42.com/wp-content/uploads/2014/10/5_LinearDimension-300x98.png 300w, https://bim42.com/wp-content/uploads/2014/10/5_LinearDimension-500x164.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/10/5_LinearDimension.png)

Angular dimensions follow more or less the same principle, with two shift to retrieve the point before and the point after a given submit to create our angle measure.

[<img class="aligncenter size-full wp-image-664" src="http://bim42.com/wp-content/uploads/2014/10/6_AngularDimension.png" alt="6_AngularDimension" width="800" height="198" srcset="https://bim42.com/wp-content/uploads/2014/10/6_AngularDimension.png 800w, https://bim42.com/wp-content/uploads/2014/10/6_AngularDimension-300x74.png 300w, https://bim42.com/wp-content/uploads/2014/10/6_AngularDimension-500x123.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/10/6_AngularDimension.png)

These two dimension components are linked to layer names, so when hitting Bake, each panel curve end up in its layer along with its dimensions. You can see the result below, with every layer displayed and with only one layer visible.

[<img class="aligncenter size-full wp-image-666" src="http://bim42.com/wp-content/uploads/2014/10/7_Result.png" alt="7_Result" width="800" height="941" srcset="https://bim42.com/wp-content/uploads/2014/10/7_Result.png 800w, https://bim42.com/wp-content/uploads/2014/10/7_Result-255x300.png 255w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/10/7_Result.png)

I can now export every curve and its dimensions to a DWG file. This file is edited with an AutoCAD script to paste each layer in a new template file where the titleblock is prepared. It also add the panel number in the titleblock.

[<img class="aligncenter size-full wp-image-665" src="http://bim42.com/wp-content/uploads/2014/10/7_FinalDrawing.jpg" alt="7_FinalDrawing" width="1199" height="962" srcset="https://bim42.com/wp-content/uploads/2014/10/7_FinalDrawing.jpg 1199w, https://bim42.com/wp-content/uploads/2014/10/7_FinalDrawing-300x240.jpg 300w, https://bim42.com/wp-content/uploads/2014/10/7_FinalDrawing-1024x821.jpg 1024w, https://bim42.com/wp-content/uploads/2014/10/7_FinalDrawing-373x300.jpg 373w" sizes="(max-width: 1199px) 100vw, 1199px" />](http://bim42.com/wp-content/uploads/2014/10/7_FinalDrawing.jpg)