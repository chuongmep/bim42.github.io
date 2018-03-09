---
id: 864
title: DynaWorks
date: 2015-06-06T11:19:46+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=864
permalink: /2015/06/dynaworks/
categories:
  - Coordination
image: /assets/2015/06/TestSelection.jpg
tags:
  - Automation
  - Coordination
  - Dynamo
  - Navisworks
  - Revit
---
During my researches for improving clash detection, I stumble upon [DynaWorks](http://stuffandbims.blogspot.fr/2014/10/dynaworks-is-here-navisworks-library.html), a great Dynamo package built by Adam Sheather ([@Gytaco](https://twitter.com/Gytaco)).

For those who haven't heard about Dynamo (Is there is any left?), it is a visual programming interface for Revit, pretty much like Grasshopper. Just like Grasshopper, you can improve upon the built-in features with packages from third party developers. DynaWorks is one of these packages, and provides a set of Dynamo nodes for interacting with Navisworks.

After installing it through the package manager, it presents itself with a set of nodes exposing Navisworks main functions.

Along with the package, some examples are provided. The NavisClashesElementUpdate.dyn contains a definition for retrieving clash results from Navisworks, I use it for my first steps with DynaWorks. If, like me, you want to use these definitions with Navisworks 2016, don't forget to use [Adam Sheather's trick](http://stuffandbims.blogspot.fr/2015/05/dynaworks16-release.html) for updating your Dynamo definitions

To use DynaWorks, you first have to create a Navisworks file, and prepare your clash detections. Here, I create a basic detection between Walls (First Clash Item, in Blue) and HVAC elements (Second Clash Item, in Red), and load the resulting NWF file in my Dynaworks definition.

![TestSelection](/assets/2015/06/TestSelection.jpg)

Basically, this definition retrieves every clash result in every clash test, selects one side of the clash detection, gets the involved element, extracts its id and uses it to update the Comment parameter in Revit.

![process](/assets/2015/06/process.jpg)

Simple, but the result is pretty impressive. Instead of painfully getting element Ids in the Navisworks report, DynaWorks retrieves them for us, and updates elements in Revit accordingly. When applying a filter in the Revit view, we get this:

![result](/assets/2015/06/result.jpg)

With some tweak to this initial definition, I was able to implement some king of dynamic clash detection, with a live update of the Navisworks file as we update the Revit model, but converting an entire Revit model in NWC is way too slow to implement this solution in a production environment. Please feel free to [use it](https://bitbucket.org/simonmoreau/clashdetective/downloads/NavisClashesElementUpdateDynamicaly.dyn) if you want to try it by yourself.

DynaWorks contains many other functions to retrieve Navisworks views or selection sets in Revit, and I think this can be the beginning of a great work flow intertwining Revit and Navisworks.