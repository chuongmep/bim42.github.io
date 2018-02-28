---
id: 899
title: Align Tags Update
date: 2015-07-11T12:29:02+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=899
permalink: /2015/07/align-tags-update/
categories:
  - Revit
tags:
  - Autodesk
  - Plugin
  - Revit
  - Software
---
This is a long overdue update, but I finally take the time to prepare my Align Tag plug-in for Revit 2016.

Along with the annual clean up and bug fixes, I also add a new feature called Arrange Tags. This will automatically arrange all tags with a leader all around the active view.

![<img class="aligncenter size-full wp-image-900" src="http://bim42.com/wp-content/uploads/2015/07/Buttons.png" alt="Buttons" width="334" height="568" srcset="https://bim42.com/wp-content/uploads/2015/07/Buttons.png 334w, https://bim42.com/wp-content/uploads/2015/07/Buttons-176x300.png 176w" sizes="(max-width: 334px) 100vw, 334px" />](http://bim42.com/wp-content/uploads/2015/07/Buttons.png)

This function is slightly different from the previous ones since you don't need to select any tags before running it. Just click on Arrange Tags, and every tag will be neatly placed on each side of the active view.

![<img class="aligncenter size-full wp-image-912" src="http://bim42.com/wp-content/uploads/2015/07/arrangeTaganimation1.gif" alt="arrangeTaganimation" width="700" height="337" />](http://bim42.com/wp-content/uploads/2015/07/arrangeTaganimation1.gif)

This function works great on small views, like local sections or callouts. Don't expect too much on plan views, you will be disappointed.

How it work?

The main idea behind Arrange Tag is to find on the left or the right of the view the nearest available space to place a tag. Once every tags are neatly placed on each side of the view, a second subroutine check every tag leaders and uncross them.

![<img class="aligncenter size-full wp-image-902" src="http://bim42.com/wp-content/uploads/2015/07/process1.jpg" alt="process" width="560" height="960" srcset="https://bim42.com/wp-content/uploads/2015/07/process1.jpg 560w, https://bim42.com/wp-content/uploads/2015/07/process1-175x300.jpg 175w" sizes="(max-width: 560px) 100vw, 560px" />](http://bim42.com/wp-content/uploads/2015/07/process1.jpg)

This feature use an opinionated way to organize tags on a view, and it probably won't please everybody. I created it specifically to place tags on section views, and it follows my own drafting rules. That being said, I hope you will find it useful.

The application is available on [Autodesk App Exchange](https://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3aalign_windows32and64%3aen). If you don't mind fumbling into my code, you will also find the entire solution on [Bitbucket](https://bitbucket.org/simonmoreau/align-tag), fell free to use it for your own projects.