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

![modelorganization1](/assets/2013/02/modelorganization1.jpg)

This graphical representation must also be editable directly in the compiled model, without having to open every trade model to change color settings.

I firstly set custom Display Settings on each linked model, using an override for every element category.

![override](/assets/2013/02/override.jpg)

If this method works well for most element, it doesn’t change the color of various HVAC and plumbing systems. This is due to the Graphic Overrides set up for each system in the linked model. I didn’t want to remove these overrides which are pretty convenient for setting up visibility settings in trade models.

![intheplbmodel](/assets/2013/02/intheplbmodel.jpg)

So I decide to use a workaround to define graphical representation in my coordination model.

Each trade model contain a limited amount of worksets, each draftsman working on his own linked model, so I was able to create the same worksets in my compiled model.

![incoordinationmodel](/assets/2013/02/incoordinationmodel.jpg)

These worksets can now be used to create filters containing every element of the specified trade.

![filtering](/assets/2013/02/filtering.jpg)

I use these filters to apply specific visibility settings in my coordination model.

This workaround is not very elegant, but it works, and allows me to set up the graphical representation very precisely in my compiled model without having to open each model to edit the visibility settings of a coordination view called in the main model with the “By linked view” function.