---
id: 571
title: Align Tags Revit Plug-In
date: 2014-09-13T09:00:25+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=571
permalink: /2014/09/align-tags-revit-plug-in/
categories:
  - Revit
tags:
  - .NET
  - BIM Manager
  - Revit
---
I just release a new add-in for Revit on the Autodesk App Exchange for aligning and sorting tags on a view.

This tool is based on the Align command you probably already know from a large bunch of software, from PowerPoint to Adobe Illustrator. It is composed of a set of commands to align or distribute tags on a Revit view, and it is pretty easy to use:

[<img class="aligncenter size-full wp-image-574" src="http://bim42.com/wp-content/uploads/2014/09/Commands.png" alt="Commands" width="166" height="244" />](http://bim42.com/wp-content/uploads/2014/09/Commands.png)

To align two or more of tags, just select them, and select one of the direction of the Align command.

For example, with the Align Left command :

[<img class="aligncenter wp-image-573 size-full" src="http://bim42.com/wp-content/uploads/2014/09/AlignBefore.png" alt="Before" width="854" height="359" srcset="https://bim42.com/wp-content/uploads/2014/09/AlignBefore.png 854w, https://bim42.com/wp-content/uploads/2014/09/AlignBefore-300x126.png 300w, https://bim42.com/wp-content/uploads/2014/09/AlignBefore-500x210.png 500w" sizes="(max-width: 854px) 100vw, 854px" />](http://bim42.com/wp-content/uploads/2014/09/AlignBefore.png) [<img class="aligncenter wp-image-572 size-full" src="http://bim42.com/wp-content/uploads/2014/09/AlignAfter.png" alt="After" width="876" height="362" srcset="https://bim42.com/wp-content/uploads/2014/09/AlignAfter.png 876w, https://bim42.com/wp-content/uploads/2014/09/AlignAfter-300x123.png 300w, https://bim42.com/wp-content/uploads/2014/09/AlignAfter-500x206.png 500w" sizes="(max-width: 876px) 100vw, 876px" />](http://bim42.com/wp-content/uploads/2014/09/AlignAfter.png)

Every selected tag is aligned with the left one. The alignment reference point is the tag base point (where their reference planes intersect).

To distribute three or more tags along an axis, select them and specify the direction.

For example, with the Distribute Vertically command:

[<img class="aligncenter size-full wp-image-576" src="http://bim42.com/wp-content/uploads/2014/09/DistributeBefore.png" alt="Before" width="970" height="371" srcset="https://bim42.com/wp-content/uploads/2014/09/DistributeBefore.png 970w, https://bim42.com/wp-content/uploads/2014/09/DistributeBefore-300x114.png 300w, https://bim42.com/wp-content/uploads/2014/09/DistributeBefore-500x191.png 500w" sizes="(max-width: 970px) 100vw, 970px" />](http://bim42.com/wp-content/uploads/2014/09/DistributeBefore.png) [<img class="aligncenter size-full wp-image-575" src="http://bim42.com/wp-content/uploads/2014/09/DistributeAfter.png" alt="After" width="964" height="378" srcset="https://bim42.com/wp-content/uploads/2014/09/DistributeAfter.png 964w, https://bim42.com/wp-content/uploads/2014/09/DistributeAfter-300x117.png 300w, https://bim42.com/wp-content/uploads/2014/09/DistributeAfter-500x196.png 500w" sizes="(max-width: 964px) 100vw, 964px" />](http://bim42.com/wp-content/uploads/2014/09/DistributeAfter.png)

Vertical space between selected tags is distributed evenly among them. The position reference point is still the tag base point.

Under the hood, everything is pretty simple. The application pick up every tag origin point, and sort them along the _View.RightDirection_ or _View.UpDirection_ regarding the direction you select.

Once these origin points are placed along the chosen vector, each _Tag.TagHeadPosition_ is set to its new position.

The entire source code can be found on [Bitbucket](https://bitbucket.org/simonmoreau/align-tag "Align Tags"), my new place of choice for code hosting. Feel free to use it for whatever you want.

The Align Revit add-in is already available for Revit 2014 and 2015 on the [Autodesk App Exchange](https://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3aalign_windows32and64%3aen "Align").