---
id: 527
title: Room Finishes Update
date: 2014-08-09T04:39:58+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=527
permalink: /2014/08/room-finishes-update/
categories:
  - Revit
tags:
  - .NET
  - Automation
  - Revit
  - Software
---
A new version of my Revit plug-in Room Finishes is available on the Autodesk App Exchange.

This major update integrate a new feature for creating floor finishes. The main idea is to create a floor that follow the general outline of a room, at a given height offset from the room level.

The first application is to model quickly floor finishes inside every selected room. Just select a floor type, a height offset and the plug-in will model a finish floor on every selected room.

[<img class="aligncenter size-full wp-image-528" src="http://bim42.com/wp-content/uploads/2014/08/CreateInterface.png" alt="CreateInterface" width="286" height="513" srcset="https://bim42.com/wp-content/uploads/2014/08/CreateInterface.png 286w, https://bim42.com/wp-content/uploads/2014/08/CreateInterface-167x300.png 167w" sizes="(max-width: 286px) 100vw, 286px" />](http://bim42.com/wp-content/uploads/2014/08/CreateInterface.png)

We can see here the floor created with the previous parameters:

[<img class="aligncenter size-full wp-image-531" src="http://bim42.com/wp-content/uploads/2014/08/ResultDetail.png" alt="ResultDetail" width="772" height="333" srcset="https://bim42.com/wp-content/uploads/2014/08/ResultDetail.png 772w, https://bim42.com/wp-content/uploads/2014/08/ResultDetail-300x129.png 300w, https://bim42.com/wp-content/uploads/2014/08/ResultDetail-500x215.png 500w" sizes="(max-width: 772px) 100vw, 772px" />](http://bim42.com/wp-content/uploads/2014/08/ResultDetail.png)

The whole idea came when I have to model an insulation just under the slab for more than a thousand of rooms. Luckily, these rooms where correctly modeled, with their upper limit set just below the upper slab.

[<img class="aligncenter size-full wp-image-532" src="http://bim42.com/wp-content/uploads/2014/08/RoomHeight.png" alt="RoomHeight" width="959" height="390" srcset="https://bim42.com/wp-content/uploads/2014/08/RoomHeight.png 959w, https://bim42.com/wp-content/uploads/2014/08/RoomHeight-300x122.png 300w, https://bim42.com/wp-content/uploads/2014/08/RoomHeight-500x203.png 500w" sizes="(max-width: 959px) 100vw, 959px" />](http://bim42.com/wp-content/uploads/2014/08/RoomHeight.png)

So I wrote a small piece of code for creating a floor with the same boundaries than the selected rooms. Just like my previous plug-in for creating skirting board, you just have to select a type of floor to create, enter the desired height and the application will create the floor in the selected rooms.

In my problem, the distance between the room level and the upper slab could change, so I introduce an additional feature, the ability to select one of the parameter of the room to define the height of the floor.

[<img class="aligncenter size-full wp-image-530" src="http://bim42.com/wp-content/uploads/2014/08/ParamSelector.png" alt="ParamSelector" width="248" height="83" />](http://bim42.com/wp-content/uploads/2014/08/ParamSelector.png)

Since my rooms are modeled from slab to slab, I just have to select the Unbounded Height room parameter to create insulation at the correct elevation.

[<img class="aligncenter size-full wp-image-529" src="http://bim42.com/wp-content/uploads/2014/08/InsultationResult.png" alt="InsultationResult" width="841" height="418" srcset="https://bim42.com/wp-content/uploads/2014/08/InsultationResult.png 841w, https://bim42.com/wp-content/uploads/2014/08/InsultationResult-300x149.png 300w, https://bim42.com/wp-content/uploads/2014/08/InsultationResult-500x248.png 500w" sizes="(max-width: 841px) 100vw, 841px" />](http://bim42.com/wp-content/uploads/2014/08/InsultationResult.png)

I am also using it to draw a temporary floor at the ceilling height in every room of a project. This temporary floor is used to run a clash detection to check if every HVAC objects are correctly placed above the drop-ceiling height.

The application is already available in the [Autodesk App Exchange](http://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3aroomfinishing_windows32and64%3aen "Autodesk App Exchange"). If you already have installed Room Finishes, just download the update from the same link.

I also finally clean up my code and upload it on GitHub for everyone to see. The source code is freely available [here](https://github.com/simonmoreau/RoomFinishes "GitHub") as a Visual Studio 2012 solution. Feel free to download and use it for any of your own application. I would be delighted if you can use it for something useful.