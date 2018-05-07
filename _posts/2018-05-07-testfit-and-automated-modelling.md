---
id: 1264
title: TestFit and Automated Modelling
date: 2018-05-07T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1263
permalink: /2018/05/testfit-and-automated-modelling
published: true
categories:
  - General BIM
image: /assets/2018/05/testFitInterface.jpg
tags:
  - Automation
  - Software
description: An online application to convert Revit files to IFC, powered by Autodesk Forge.
---

[BuildingForge](https://buildingforge.com/), a Dallas-based start-up, recently offered a 14 days trial to their solution, [TestFit](https://testfit.io/). I was quite impressed by their tool and use the opportunity to present it here.

TestFit is a solution to automate massing and capabilities studies. Based on a site, it quickly create residential building based on your specifications.

I start by typing an address in my hometown and display a map of the corresponding neighbourhood. I then click on aerial to get an aerial picture of the land. I then click on "Define" to draw the outline of the site. As soon as the site is defined, a first version of your building appears.

![Site outline]({{ "/assets/2018/05/SiteOutline.gif" | absolute_url }})

You can immediately see a lot of information about your project in the output window: site surface, number of units, distribution in studios, 1 bedroom apartments, 2 bedrooms apartments, garage area...

![Units data]({{ "/assets/2018/05/UnitsData.jpg" | absolute_url }})

You can click on level to switch between levels and see the layout of each level.

If you edit your site boundaries or setback, the entire project is updated in real time, showing impressive performance.

![Edit the building]({{ "/assets/2018/05/EditSiteBoundaries.gif" | absolute_url }})

But this is only a first draft, you can edit it and see the results in real time.

I started by adding a garage on the ground floor. I set up the few parameters of my garage, click on _Enable_, and my garage appear. I then click on _Define_ to set up precisely its position.

The resulting surface, area and number of stalls appear in the output windows.

![Add a garage]({{ "/assets/2018/05/Garage.gif" | absolute_url }})

The same principle can be applied to create specific spaces, like common area on the ground floor. You select _Space_, click on "Add" and set up its area.

![Add common areas]({{ "/assets/2018/05/CommunSpace.gif" | absolute_url }})

Even if the layout of some units seems a bit odd to my French eyes, TestFit is a powerful solution to quickly design residential building. However, this power came at a cost.

3D modelling software solutions fall somewhere on the following graph:

![3D modelling software]({{ "/assets/2018/05/Graph.jpg" | absolute_url }})

They allow more or less freedom over the creation of geometry and the modelling process can be more or less automated. Generally, a great modelling freedom come at the cost of a less automated modelling process. For example, Rhino allows pretty much any shape, but the modelling process is more manual than Revit. On the other hand, Revit is not really made to model something else than a building.

Automation can be extremely useful (modelling an average building with Revit or ArchiCAD is more efficient than doing it in Rhino), but it can also be a drawback when you want to model something that the solution didn't plan (modelling a bridge with Revit). In that case, you generally better off with a more "geometrically free" solution.

TestFit is a great solution but lean too much on the automation side for its own good. It ends up being great when it comes to create the building TestFit had in mind but not so good if you want to do anything else.

However, they keep on improving their solution and I will keep a close eye on them.