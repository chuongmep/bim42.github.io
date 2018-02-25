---
id: 864
title: DynaWorks
date: 2015-06-06T11:19:46+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=864
permalink: /2015/06/dynaworks/
categories:
  - Coordination
tags:
  - Automation
  - Coordination
  - Dynamo
  - Navisworks
  - Revit
---
During my researches for improving clash detection, I stumble upon [DynaWorks](http://stuffandbims.blogspot.fr/2014/10/dynaworks-is-here-navisworks-library.html), a great Dynamo package built by Adam Sheather ([@Gytaco](https://twitter.com/Gytaco)).

For those who haven&#8217;t heard about Dynamo (Is there is any left?), it is a visual programming interface for Revit, pretty much like Grasshopper. Just like Grasshopper, you can improve upon the built-in features with packages from third party developers. DynaWorks is one of these packages, and provides a set of Dynamo nodes for interacting with Navisworks.[
  
](http://bim42.com/wp-content/uploads/2015/06/process.jpg) 

After installing it through the package manager, it presents itself with a set of nodes exposing Navisworks main functions.

Along with the package, some examples are provided. The NavisClashesElementUpdate.dyn contains a definition for retrieving clash results from Navisworks, I use it for my first steps with DynaWorks. If, like me, you want to use these definitions with Navisworks 2016, don&#8217;t forget to use [Adam Sheather&#8217;s trick](http://stuffandbims.blogspot.fr/2015/05/dynaworks16-release.html) for updating your Dynamo definitions

To use DynaWorks, you first have to create a Navisworks file, and prepare your clash detections. Here, I create a basic detection between Walls (First Clash Item, in Blue) and HVAC elements (Second Clash Item, in Red), and load the resulting NWF file in my Dynaworks definition.

[<img class="aligncenter size-full wp-image-867" src="http://bim42.com/wp-content/uploads/2015/06/TestSelection.jpg" alt="TestSelection" width="500" height="308" srcset="https://bim42.com/wp-content/uploads/2015/06/TestSelection.jpg 500w, https://bim42.com/wp-content/uploads/2015/06/TestSelection-300x185.jpg 300w, https://bim42.com/wp-content/uploads/2015/06/TestSelection-487x300.jpg 487w" sizes="(max-width: 500px) 100vw, 500px" />](http://bim42.com/wp-content/uploads/2015/06/TestSelection.jpg)

Basically, this definition retrieves every clash result in every clash test, selects one side of the clash detection, gets the involved element, extracts its id and uses it to update the Comment parameter in Revit.

[<img class="aligncenter size-full wp-image-865" src="http://bim42.com/wp-content/uploads/2015/06/process.jpg" alt="process" width="500" height="376" srcset="https://bim42.com/wp-content/uploads/2015/06/process.jpg 500w, https://bim42.com/wp-content/uploads/2015/06/process-300x226.jpg 300w, https://bim42.com/wp-content/uploads/2015/06/process-399x300.jpg 399w" sizes="(max-width: 500px) 100vw, 500px" />](http://bim42.com/wp-content/uploads/2015/06/process.jpg)

Simple, but the result is pretty impressive. Instead of painfully getting element Ids in the Navisworks report, DynaWorks retrieves them for us, and updates elements in Revit accordingly. When applying a filter in the Revit view, we get this:

[<img class="aligncenter size-full wp-image-866" src="http://bim42.com/wp-content/uploads/2015/06/result.jpg" alt="result" width="500" height="305" srcset="https://bim42.com/wp-content/uploads/2015/06/result.jpg 500w, https://bim42.com/wp-content/uploads/2015/06/result-300x183.jpg 300w, https://bim42.com/wp-content/uploads/2015/06/result-492x300.jpg 492w" sizes="(max-width: 500px) 100vw, 500px" />](http://bim42.com/wp-content/uploads/2015/06/result.jpg)

With some tweak to this initial definition, I was able to implement some king of dynamic clash detection, with a live update of the Navisworks file as we update the Revit model, but converting an entire Revit model in NWC is way too slow to implement this solution in a production environment. Please feel free to [use it](https://bitbucket.org/simonmoreau/clashdetective/downloads/NavisClashesElementUpdateDynamicaly.dyn) if you want to try it by yourself.

DynaWorks contains many other functions to retrieve Navisworks views or selection sets in Revit, and I think this can be the beginning of a great work flow intertwining Revit and Navisworks.