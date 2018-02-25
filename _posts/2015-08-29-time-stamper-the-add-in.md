---
id: 929
title: Time Stamper, the Add-In
date: 2015-08-29T11:29:46+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=929
permalink: /2015/08/time-stamper-the-add-in/
categories:
  - Coordination
tags:
  - BIM Manager
  - Coordination
  - Documentation
  - Revit
---
There is no easy way to override the color of an entire Revit link. Since most of my work involves linking Revit model from various subcontractors, this is something I miss badly.

Until recently, I was still using some [workset hack](http://bim42.com/2013/02/revit-linked-models-visibility/) to create filters on linked models. These filters were allowing me to display linked model with my color of choice.

But relying on workset leave much to be desired, and I have to find another solution.

I recently came up with [a different solution](http://bim42.com/2015/07/model-timestamp/), where each model element know where they came from.

The idea is to add file name, date and version in shared parameters on every model element. I created the corresponding Revit Add-In, and it is now available on the [Autodesk App Exchange](https://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3Atimestamps_windows64%3Aen).

This application will:

  * Ask for identification information
  * Create four shared parameters on every category
  * Fill these shared parameters with identification information

The code itself is pretty easy, but there is a lot of applications.

First, it becomes easy to create filters on linked model. These filters allow us to display each linked model with a different color.

[<img class="aligncenter size-full wp-image-930" src="http://bim42.com/wp-content/uploads/2015/08/ColorsByModel.png" alt="ColorsByModel" width="707" height="800" srcset="https://bim42.com/wp-content/uploads/2015/08/ColorsByModel.png 707w, https://bim42.com/wp-content/uploads/2015/08/ColorsByModel-265x300.png 265w" sizes="(max-width: 707px) 100vw, 707px" />](http://bim42.com/wp-content/uploads/2015/08/ColorsByModel.png)

But it also enables us to tag the origin of every element, like we can see in the following screenshot.

[<img class="aligncenter size-full wp-image-931" src="http://bim42.com/wp-content/uploads/2015/08/IdentifyElements.png" alt="IdentifyElements" width="800" height="482" srcset="https://bim42.com/wp-content/uploads/2015/08/IdentifyElements.png 800w, https://bim42.com/wp-content/uploads/2015/08/IdentifyElements-300x181.png 300w, https://bim42.com/wp-content/uploads/2015/08/IdentifyElements-498x300.png 498w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/08/IdentifyElements.png)

You can create a linked models schedule, with date and version.

[<img class="aligncenter size-full wp-image-932" src="http://bim42.com/wp-content/uploads/2015/08/LinkedFilesSchedule.png" alt="LinkedFilesSchedule" width="800" height="336" srcset="https://bim42.com/wp-content/uploads/2015/08/LinkedFilesSchedule.png 800w, https://bim42.com/wp-content/uploads/2015/08/LinkedFilesSchedule-300x126.png 300w, https://bim42.com/wp-content/uploads/2015/08/LinkedFilesSchedule-500x210.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/08/LinkedFilesSchedule.png)

To help you create filters and tags with these parameters, you will find [here](http://bim42.com/wp-content/uploads/2015/08/BIM42_SharedParameters.txt) the shared parameter text file. Please also note that the application uses a list of categories to create the four shared parameters. You will find this list [here](http://bim42.com/wp-content/uploads/2015/08/categories.txt).

I hope this application will help you in your work, don&#8217;t hesitate to share your suggestions in the comments.