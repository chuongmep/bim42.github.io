---
id: 987
title: MEP design and Dynamo
date: 2015-10-24T16:36:55+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=987
permalink: /2015/10/mep-design-and-dynamo/
categories:
  - Dynamo
image: /assets/2015/10/features.jpg
tags:
  - Automation
  - Dynamo
  - Revit
  - Software
---
Most of the work we see with Dynamo involves designing complex parametric geometry. But Dynamo can also help you automate your design and make more informed decisions, even on the most ordinary cubic building.

A lot of tasks of the MEP engineer involves retrieving information from the architectural model and can be automated using Dynamo.

The first task of the MEP engineer is to retrieve rooms from the architectural model and create MEP Spaces from it. The "Place Spaces Automatically" Revit function can be useful here, but it is far from enough in many cases. There isn't any control on the created spaces, and properties from the room cannot be added to the newly created space.

To improve on this function, I start exploring space creation in Dynamo. There isn't much support for Room and Space built in Dynamo. Some package can fill this gap (Lunchbox from Nathan Miller and Clockworks from Andreas Dieckmann) but does not offer a complete solution. Furthermore, we need support for linked files, since architectural rooms are most of time in linked files.

So I create my own Dynamo package, called DynamoMEP. This package contains a set of nodes for creating and working with Room and MEP Space.

![features]({{ "/assets/2015/10/features.jpg" | absolute_url }})

I use these custom nodes to create an MEP Space from every Room in a linked architectural project.

I start by retrieving linked rooms using SteamNodes, a great package from Juline Benoit. Using Element.GetFromLinkedFile gives me a list of rooms in the linked file (The Get Document came from the Grimshaw package).

![RetriveRooms]({{ "/assets/2015/10/RetriveRooms.jpg" | absolute_url }})

Using the Room.FromElement node, I convert these linked elements into Rooms. I can now get their location points, and create my MEP spaces based on these points.

![CreateSpaces]({{ "/assets/2015/10/CreateSpaces.jpg" | absolute_url }})

Still using the DynamoMEP package, I can retrieve basic properties from these spaces, like their origin point, their associated level and their bounding elements.

![GetSpaceProperties]({{ "/assets/2015/10/GetSpaceProperties.jpg" | absolute_url }})

My model has now a matching MEP Space for every room created in the linked model. Since we are using Dynamo, we can have a much more sophisticated workflow, and retrieve specific properties in the rooms to have them added to the newly created space.

DynamoMEP is still in this infancy, and need a lot of improvement, so don't hesitate to report any bug or missing feature. You can add an issue on [Github](https://github.com/simonmoreau/DynamoMEP), or post a comment below. I hope to add new features as I develop MEP workflows in Dynamo.

