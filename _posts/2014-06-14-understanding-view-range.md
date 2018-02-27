---
id: 391
title: Understanding View Range
date: 2014-06-14T08:25:12+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=391
permalink: /2014/06/understanding-view-range/
categories:
  - Revit
tags:
  - Autodesk
  - BIM Manager
  - Revit
  - Visualization
---
Setting up view range regularly came with great stress, and &#8220;why I can&#8217;t see this particular element&#8221; shouts. To explain it to myself (and maybe other), I write a few lines about it.
  
The View Range comes with four elevations, corresponding to the four planes which define a view range:

![<img class="aligncenter wp-image-393 size-full" src="http://bim42.com/wp-content/uploads/2014/06/ViewRangeInterface.png" alt="ViewRangeInterface" width="478" height="303" srcset="https://bim42.com/wp-content/uploads/2014/06/ViewRangeInterface.png 478w, https://bim42.com/wp-content/uploads/2014/06/ViewRangeInterface-300x190.png 300w, https://bim42.com/wp-content/uploads/2014/06/ViewRangeInterface-473x300.png 473w" sizes="(max-width: 478px) 100vw, 478px" />](http://bim42.com/wp-content/uploads/2014/06/ViewRangeInterface.png)These four planes, draw in a section view:

![<img class="aligncenter wp-image-394 size-full" src="http://bim42.com/wp-content/uploads/2014/06/SectionViewPlaneDepth.png" alt="SectionViewPlaneDepth" width="813" height="513" srcset="https://bim42.com/wp-content/uploads/2014/06/SectionViewPlaneDepth.png 813w, https://bim42.com/wp-content/uploads/2014/06/SectionViewPlaneDepth-300x189.png 300w, https://bim42.com/wp-content/uploads/2014/06/SectionViewPlaneDepth-475x300.png 475w" sizes="(max-width: 813px) 100vw, 813px" />](http://bim42.com/wp-content/uploads/2014/06/SectionViewPlaneDepth.png)These planes must stay sorted in the same order, i.e., from up to down: Top, Cut Plane, Bottom and View Depth. Trying to change that order will result in this kind of error message:

![<img class="aligncenter size-full wp-image-396" src="http://bim42.com/wp-content/uploads/2014/06/ViewDepthError.png" alt="ViewDepthError" width="381" height="177" srcset="https://bim42.com/wp-content/uploads/2014/06/ViewDepthError.png 381w, https://bim42.com/wp-content/uploads/2014/06/ViewDepthError-300x139.png 300w" sizes="(max-width: 381px) 100vw, 381px" />](http://bim42.com/wp-content/uploads/2014/06/ViewDepthError.png)

The general idea behind the view range is that every element between the Cut plane and the View Depth is displayed.

On ceiling plan, where there is only three plans, all objects included between the cut plane and the View Depth plane are visible.

Most objects became entirely visible even if a small part of them is between the cut plane and the View Depth:

<div id="attachment_397" style="max-width: 603px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2014/06/Chair.png"><img class="wp-image-397 size-full" src="http://bim42.com/wp-content/uploads/2014/06/Chair.png" alt="Chair" width="593" height="516" srcset="https://bim42.com/wp-content/uploads/2014/06/Chair.png 593w, https://bim42.com/wp-content/uploads/2014/06/Chair-300x261.png 300w, https://bim42.com/wp-content/uploads/2014/06/Chair-344x300.png 344w" sizes="(max-width: 593px) 100vw, 593px" /></a>
  
  <p class="wp-caption-text">
    Cut by the Cut plane
  </p>
</div>

<div id="attachment_398" style="max-width: 597px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2014/06/Chair_NotVisible.png"><img class="wp-image-398 size-full" src="http://bim42.com/wp-content/uploads/2014/06/Chair_NotVisible.png" alt="Chair_NotVisible" width="587" height="519" srcset="https://bim42.com/wp-content/uploads/2014/06/Chair_NotVisible.png 587w, https://bim42.com/wp-content/uploads/2014/06/Chair_NotVisible-300x265.png 300w, https://bim42.com/wp-content/uploads/2014/06/Chair_NotVisible-339x300.png 339w" sizes="(max-width: 587px) 100vw, 587px" /></a>
  
  <p class="wp-caption-text">
    Above the Cut plane
  </p>
</div>

On the other hand, some families, let&#8217;s call them the &#8220;cutable&#8221; ones, change their appearance when cut by the Cut plane, and display the section display of their material. Cutable objects belongs to one of the following categories: Wall, windows, doors, railings, site, Structural column, Structural foundation, Structural Framing, Structural Stiffener, Casework, Columns, Roof, Ceilling, and Floor.
  
In case of an editable cutable family, each geometric element composing this family can be hidden when cut by the Cut plane:

![<img class="aligncenter size-full wp-image-400" src="http://bim42.com/wp-content/uploads/2014/06/WhenCutInViewPlan.png" alt="WhenCutInViewPlan" width="439" height="302" srcset="https://bim42.com/wp-content/uploads/2014/06/WhenCutInViewPlan.png 439w, https://bim42.com/wp-content/uploads/2014/06/WhenCutInViewPlan-300x206.png 300w, https://bim42.com/wp-content/uploads/2014/06/WhenCutInViewPlan-436x300.png 436w" sizes="(max-width: 439px) 100vw, 439px" />](http://bim42.com/wp-content/uploads/2014/06/WhenCutInViewPlan.png)

If the View Depth setting is set to Clip (With or without line) these objects are also cut by the View Depth Plane. For example, with a wall with an edited profile:

![<img class="aligncenter size-full wp-image-413" src="http://bim42.com/wp-content/uploads/2014/06/WallSection.png" alt="WallSection" width="918" height="338" srcset="https://bim42.com/wp-content/uploads/2014/06/WallSection.png 918w, https://bim42.com/wp-content/uploads/2014/06/WallSection-300x110.png 300w, https://bim42.com/wp-content/uploads/2014/06/WallSection-500x184.png 500w" sizes="(max-width: 918px) 100vw, 918px" />](http://bim42.com/wp-content/uploads/2014/06/WallSection.png)

The corresponding view plan, with different Depth Clipping:

![<img class="aligncenter size-full wp-image-402" src="http://bim42.com/wp-content/uploads/2014/06/DepthClipping_NoClip.png" alt="DepthClipping_NoClip" width="997" height="372" srcset="https://bim42.com/wp-content/uploads/2014/06/DepthClipping_NoClip.png 997w, https://bim42.com/wp-content/uploads/2014/06/DepthClipping_NoClip-300x111.png 300w, https://bim42.com/wp-content/uploads/2014/06/DepthClipping_NoClip-500x186.png 500w" sizes="(max-width: 997px) 100vw, 997px" /><img class="aligncenter size-full wp-image-401" src="http://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithoutLine.png" alt="DepthClipping_WithoutLine" width="998" height="420" srcset="https://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithoutLine.png 998w, https://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithoutLine-300x126.png 300w, https://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithoutLine-500x210.png 500w" sizes="(max-width: 998px) 100vw, 998px" />](http://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithoutLine.png) [
  
](http://bim42.com/wp-content/uploads/2014/06/DepthClipping_NoClip.png) ![<img class="aligncenter size-full wp-image-403" src="http://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithLine.png" alt="DepthClipping_WithLine" width="1001" height="376" srcset="https://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithLine.png 1001w, https://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithLine-300x112.png 300w, https://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithLine-500x187.png 500w" sizes="(max-width: 1001px) 100vw, 1001px" />](http://bim42.com/wp-content/uploads/2014/06/DepthClipping_WithLine.png)

Some categories have also specific behaviors. For example, a windows stay visible above the cut plane if the hosting wall is still below the cut plane.

I also note than an Object Syle or an Override does not apply to an object placed below the Bottom plane, or above the top plane for ceiling view. For example, if Furniture Object Style is set to Red, a chair is normally displayed in red in a plan view:

![<img class="aligncenter size-full wp-image-404" src="http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_AboveBottomPlane.png" alt="FurnitureObjectStyle_Plan_AboveBottomPlane" width="415" height="233" srcset="https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_AboveBottomPlane.png 415w, https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_AboveBottomPlane-300x168.png 300w" sizes="(max-width: 415px) 100vw, 415px" />](http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_AboveBottomPlane.png) ![<img class="aligncenter size-full wp-image-405" src="http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_AboveBottomPlane.png" alt="FurnitureObjectStyle_Section_AboveBottomPlane" width="867" height="392" srcset="https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_AboveBottomPlane.png 867w, https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_AboveBottomPlane-300x135.png 300w, https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_AboveBottomPlane-500x226.png 500w" sizes="(max-width: 867px) 100vw, 867px" />](http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_AboveBottomPlane.png)

But when the same chair is placed below the Bottom plane, it become black:

![<img class="aligncenter size-full wp-image-406" src="http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_BelowBottomPlane.png" alt="FurnitureObjectStyle_Plan_BelowBottomPlane" width="405" height="199" srcset="https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_BelowBottomPlane.png 405w, https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_BelowBottomPlane-300x147.png 300w" sizes="(max-width: 405px) 100vw, 405px" />](http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Plan_BelowBottomPlane.png) ![<img class="aligncenter size-full wp-image-407" src="http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_BelowBottomPlane.png" alt="FurnitureObjectStyle_Section_BelowBottomPlane" width="858" height="393" srcset="https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_BelowBottomPlane.png 858w, https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_BelowBottomPlane-300x137.png 300w, https://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_BelowBottomPlane-500x229.png 500w" sizes="(max-width: 858px) 100vw, 858px" />](http://bim42.com/wp-content/uploads/2014/06/FurnitureObjectStyle_Section_BelowBottomPlane.png)

Filters Override, on the contrary, stays active whenever the object is bellow or above the Bottom plane. I don&#8217;t know the reason of such behavior, maybe someone from Autodesk could be able to answer.

Finally, to help users with this view range issues, I create a general section of the building with two different set of dimensions, one for Top height, the other for Cut Plane Height. This section is printed and used as a handout for Revit users to set up themselves their view range on their working views.

![<img class="aligncenter size-full wp-image-408" src="http://bim42.com/wp-content/uploads/2014/06/GeneralSection.png" alt="GeneralSection" width="711" height="518" srcset="https://bim42.com/wp-content/uploads/2014/06/GeneralSection.png 711w, https://bim42.com/wp-content/uploads/2014/06/GeneralSection-300x218.png 300w, https://bim42.com/wp-content/uploads/2014/06/GeneralSection-411x300.png 411w" sizes="(max-width: 711px) 100vw, 711px" />](http://bim42.com/wp-content/uploads/2014/06/GeneralSection.png)

&nbsp;

EDIT : I have found on [Augi](http://www.augi.com/library/understanding-view-range) the solution for objects placed below the Bottom plane. These elements are displayed with the project&#8217;s Beyond> Style Line.

&nbsp;