---
id: 987
title: MEP design and Dynamo
date: 2015-10-24T16:36:55+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=987
permalink: /2015/10/mep-design-and-dynamo/
categories:
  - Dynamo
tags:
  - Automation
  - Dynamo
  - Revit
  - Software
---
Most of the work we see with Dynamo involves designing complex parametric geometry. But Dynamo can also help you automate your design and make more informed decisions, even on the most ordinary cubic building.

A lot of tasks of the MEP engineer involves retrieving information from the architectural model and can be automated using Dynamo.

The first task of the MEP engineer is to retrieve rooms from the architectural model and create MEP Spaces from it. The &#8220;Place Spaces Automatically&#8221; Revit function can be useful here, but it is far from enough in many cases. There isn&#8217;t any control on the created spaces, and properties from the room cannot be added to the newly created space.

To improve on this function, I start exploring space creation in Dynamo. There isn&#8217;t much support for Room and Space built in Dynamo. Some package can fill this gap (Lunchbox from Nathan Miller and Clockworks from Andreas Dieckmann) but does not offer a complete solution. Furthermore, we need support for linked files, since architectural rooms are most of time in linked files.

So I create my own Dynamo package, called DynamoMEP. This package contains a set of nodes for creating and working with Room and MEP Space.

[<img class="aligncenter size-full wp-image-989" src="http://bim42.com/wp-content/uploads/2015/10/features.jpg" alt="features" width="332" height="451" srcset="https://bim42.com/wp-content/uploads/2015/10/features.jpg 332w, https://bim42.com/wp-content/uploads/2015/10/features-221x300.jpg 221w" sizes="(max-width: 332px) 100vw, 332px" />](http://bim42.com/wp-content/uploads/2015/10/features.jpg)

I use these custom nodes to create an MEP Space from every Room in a linked architectural project.

I start by retrieving linked rooms using SteamNodes, a great package from Juline Benoit. Using Element.GetFromLinkedFile gives me a list of rooms in the linked file (The Get Document came from the Grimshaw package).

[<img class="aligncenter size-full wp-image-991" src="http://bim42.com/wp-content/uploads/2015/10/RetriveRooms.jpg" alt="RetriveRooms" width="800" height="356" srcset="https://bim42.com/wp-content/uploads/2015/10/RetriveRooms.jpg 800w, https://bim42.com/wp-content/uploads/2015/10/RetriveRooms-300x134.jpg 300w, https://bim42.com/wp-content/uploads/2015/10/RetriveRooms-500x223.jpg 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/10/RetriveRooms.jpg)

Using the Room.FromElement node, I convert these linked elements into Rooms. I can now get their location points, and create my MEP spaces based on these points.

[<img class="aligncenter size-full wp-image-988" src="http://bim42.com/wp-content/uploads/2015/10/CreateSpaces.jpg" alt="CreateSpaces" width="677" height="189" srcset="https://bim42.com/wp-content/uploads/2015/10/CreateSpaces.jpg 677w, https://bim42.com/wp-content/uploads/2015/10/CreateSpaces-300x84.jpg 300w, https://bim42.com/wp-content/uploads/2015/10/CreateSpaces-500x140.jpg 500w" sizes="(max-width: 677px) 100vw, 677px" />](http://bim42.com/wp-content/uploads/2015/10/CreateSpaces.jpg)

Still using the DynamoMEP package, I can retrieve basic properties from these spaces, like their origin point, their associated level and their bounding elements.

[<img class="aligncenter size-full wp-image-990" src="http://bim42.com/wp-content/uploads/2015/10/GetSpaceProperties.jpg" alt="GetSpaceProperties" width="340" height="454" srcset="https://bim42.com/wp-content/uploads/2015/10/GetSpaceProperties.jpg 340w, https://bim42.com/wp-content/uploads/2015/10/GetSpaceProperties-225x300.jpg 225w" sizes="(max-width: 340px) 100vw, 340px" />](http://bim42.com/wp-content/uploads/2015/10/GetSpaceProperties.jpg)

My model has now a matching MEP Space for every room created in the linked model. Since we are using Dynamo, we can have a much more sophisticated workflow, and retrieve specific properties in the rooms to have them added to the newly created space.

DynamoMEP is still in this infancy, and need a lot of improvement, so don&#8217;t hesitate to report any bug or missing feature. You can add an issue on [Github](https://github.com/simonmoreau/DynamoMEP), or post a comment below. I hope to add new features as I develop MEP workflows in Dynamo.

&nbsp;