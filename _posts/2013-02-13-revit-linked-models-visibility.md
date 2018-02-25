---
id: 295
title: Revit linked models visibility
date: 2013-02-13T14:05:09+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=295
permalink: /2013/02/revit-linked-models-visibility/
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:278469;i:58;}s:2:"wp";a:1:{i:0;i:2;}}'
publicize_twitter_user:
  - bim42
categories:
  - Revit
tags:
  - Autodesk
  - BIM Manager
  - Coordination
  - Revit
---
A recent request from a client make me think on the different possibilities for displaying a linked MEP model in a general coordination model.

In this project, each discipline is designed in its very own Revit model. These models are linked inside a coordination model for producing synthesis views and drawings. On this model, I need a specific graphical representation for the coordination team, while every team keeps their usual representation on their own model.

<p style="text-align:center;">
  <a href="http://bim42.com/wp-content/uploads/2013/02/modelorganization1.jpg"><img class="aligncenter  wp-image-303" title="Graphicals Representations" alt="" src="http://bim42.com/wp-content/uploads/2013/02/modelorganization1.jpg" width="584" height="475" srcset="https://bim42.com/wp-content/uploads/2013/02/modelorganization1.jpg 4019w, https://bim42.com/wp-content/uploads/2013/02/modelorganization1-300x244.jpg 300w, https://bim42.com/wp-content/uploads/2013/02/modelorganization1-1024x832.jpg 1024w" sizes="(max-width: 584px) 100vw, 584px" /></a>
</p>

This graphical representation must also be editable directly in the compiled model, without having to open every trade model to change color settings.

I firstly set custom Display Settings on each linked model, using an override for every element category.

[<img class="aligncenter size-full wp-image-299" alt="General Override" src="http://bim42.com/wp-content/uploads/2013/02/override.jpg" width="584" height="250" srcset="https://bim42.com/wp-content/uploads/2013/02/override.jpg 718w, https://bim42.com/wp-content/uploads/2013/02/override-300x128.jpg 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2013/02/override.jpg)

If this method works well for most element, it doesn’t change the color of various HVAC and plumbing systems. This is due to the Graphic Overrides set up for each system in the linked model. I didn’t want to remove these overrides which are pretty convenient for setting up visibility settings in trade models.

[<img class="aligncenter size-full wp-image-296" alt="Override by System" src="http://bim42.com/wp-content/uploads/2013/02/intheplbmodel.jpg" width="567" height="603" srcset="https://bim42.com/wp-content/uploads/2013/02/intheplbmodel.jpg 567w, https://bim42.com/wp-content/uploads/2013/02/intheplbmodel-282x300.jpg 282w" sizes="(max-width: 567px) 100vw, 567px" />](http://bim42.com/wp-content/uploads/2013/02/intheplbmodel.jpg)So I decide to use a workaround to define graphical representation in my coordination model.

Each trade model contain a limited amount of worksets, each draftsman working on his own linked model, so I was able to create the same worksets in my compiled model.

[<img class="aligncenter size-full wp-image-298" alt="Worksets in the Coordination Model" src="http://bim42.com/wp-content/uploads/2013/02/incoordinationmodel.jpg" width="584" height="410" srcset="https://bim42.com/wp-content/uploads/2013/02/incoordinationmodel.jpg 642w, https://bim42.com/wp-content/uploads/2013/02/incoordinationmodel-300x210.jpg 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2013/02/incoordinationmodel.jpg)

These worksets can now be used to create filters containing every element of the specified trade.

[<img class="aligncenter size-full wp-image-304" alt="Filtering" src="http://bim42.com/wp-content/uploads/2013/02/filtering.jpg" width="354" height="333" srcset="https://bim42.com/wp-content/uploads/2013/02/filtering.jpg 354w, https://bim42.com/wp-content/uploads/2013/02/filtering-300x282.jpg 300w" sizes="(max-width: 354px) 100vw, 354px" />](http://bim42.com/wp-content/uploads/2013/02/filtering.jpg)

I use these filters to apply specific visibility settings in my coordination model.

This workaround is not very elegant, but it works, and allows me to set up the graphical representation very precisely in my compiled model without having to open each model to edit the visibility settings of a coordination view called in the main model with the “By linked view” function.