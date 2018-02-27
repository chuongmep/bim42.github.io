---
id: 753
title: Parametric Bridge
date: 2015-01-10T18:13:24+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=753
permalink: /2015/01/parametric-bridge/
categories:
  - Grasshopper
tags:
  - BIM Manager
  - Civil Engineering
  - Grasshopper
---
_Today, I introduce you Louis-Marie Borione, one of my colleague and friend, to talk about his work with Grasshopper for civil engineering._

Hi everyone, I am a BIM Manager in a large infrastructure engineering company in France, and I thank BIM42 to give me the opportunity the present you my work on parametric Bridge.

I recently worked on a preliminary design for a bridge in the Middle East. When starting looking at conceptual design drawings I came with the impression that we would have to make a lot of hypothesis.

![<img class="aligncenter size-full wp-image-755" src="http://bim42.com/wp-content/uploads/2015/01/Bridge.png" alt="Bridge" width="1496" height="577" srcset="https://bim42.com/wp-content/uploads/2015/01/Bridge.png 1496w, https://bim42.com/wp-content/uploads/2015/01/Bridge-300x116.png 300w, https://bim42.com/wp-content/uploads/2015/01/Bridge-1024x395.png 1024w, https://bim42.com/wp-content/uploads/2015/01/Bridge-500x193.png 500w" sizes="(max-width: 1496px) 100vw, 1496px" />](http://bim42.com/wp-content/uploads/2015/01/Bridge.png)

For example the height above ground at bridge ends is not dimensioned . The idea was to produce any kind of BIM model of this bridge therefore I first thought of using Rhinoceros and Grasshopper.

So I listed all of my hypothesis:

![<img class="aligncenter size-full wp-image-758" src="http://bim42.com/wp-content/uploads/2015/01/GH.png" alt="GH" width="1600" height="900" srcset="https://bim42.com/wp-content/uploads/2015/01/GH.png 1600w, https://bim42.com/wp-content/uploads/2015/01/GH-300x169.png 300w, https://bim42.com/wp-content/uploads/2015/01/GH-1024x576.png 1024w, https://bim42.com/wp-content/uploads/2015/01/GH-500x281.png 500w" sizes="(max-width: 1600px) 100vw, 1600px" />](http://bim42.com/wp-content/uploads/2015/01/GH.png)

And I started building the wireframe model:

![<img class="aligncenter size-full wp-image-759" src="http://bim42.com/wp-content/uploads/2015/01/Rhino.png" alt="Rhino" width="1600" height="860" srcset="https://bim42.com/wp-content/uploads/2015/01/Rhino.png 1600w, https://bim42.com/wp-content/uploads/2015/01/Rhino-300x161.png 300w, https://bim42.com/wp-content/uploads/2015/01/Rhino-1024x550.png 1024w, https://bim42.com/wp-content/uploads/2015/01/Rhino-500x269.png 500w" sizes="(max-width: 1600px) 100vw, 1600px" />](http://bim42.com/wp-content/uploads/2015/01/Rhino.png)

And the final model:

![<img class="aligncenter size-full wp-image-757" src="http://bim42.com/wp-content/uploads/2015/01/FinalModel.png" alt="FinalModel" width="1600" height="860" srcset="https://bim42.com/wp-content/uploads/2015/01/FinalModel.png 1600w, https://bim42.com/wp-content/uploads/2015/01/FinalModel-300x161.png 300w, https://bim42.com/wp-content/uploads/2015/01/FinalModel-1024x550.png 1024w, https://bim42.com/wp-content/uploads/2015/01/FinalModel-500x269.png 500w" sizes="(max-width: 1600px) 100vw, 1600px" />](http://bim42.com/wp-content/uploads/2015/01/FinalModel.png)

Then I had to produce cross sections, longitudinal sections and plan views. I tried to do it within Rhinoceros but the result wasn’t good enough. Additionally some cross beam had a different shape, and using Grasshopper it is difficult to customize some elements.

My next idea was to be able to transfer this model to Revit. After a quick tour on Google, I found the grasshopper plugin Hummingbird. Using Hummingbird plugin for Grasshopper you export geometry from Grasshopper to an Excel Spreadsheet and using Hummingbird plugin for Revit you import that Excel Spreadsheet.

![<img class="aligncenter size-full wp-image-754" src="http://bim42.com/wp-content/uploads/2015/01/BrideFinal.png" alt="BrideFinal" width="1600" height="860" srcset="https://bim42.com/wp-content/uploads/2015/01/BrideFinal.png 1600w, https://bim42.com/wp-content/uploads/2015/01/BrideFinal-300x161.png 300w, https://bim42.com/wp-content/uploads/2015/01/BrideFinal-1024x550.png 1024w, https://bim42.com/wp-content/uploads/2015/01/BrideFinal-500x269.png 500w" sizes="(max-width: 1600px) 100vw, 1600px" />](http://bim42.com/wp-content/uploads/2015/01/BrideFinal.png)

At the end the process became quite complicated. When changing in input value in Grasshopper it took more 30 minutes to populate that changes to Revit.

I finally thought about using Dynamo to create directly a parametric model of the bridge within Revit. Unfortunately Dynamo is quite hard to use and I think it would make a great subject for a future post on BIM 42.

_Thank you so much for this content, and I must say I totally agree with you about Dynamo, I should already have started to work with it._