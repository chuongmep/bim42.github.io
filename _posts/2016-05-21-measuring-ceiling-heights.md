---
id: 1024
title: Measuring ceiling heights
date: 2016-05-21T11:54:46+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1024
permalink: /2016/05/measuring-ceiling-heights/
categories:
  - Dynamo
tags:
  - Automation
  - Dynamo
  - Revit
  - Tips
---
I recently have to measure the actual headroom of every room in an architectural model, and copy this value in a room parameter.

Instead of checking manually every room, I create a small Dynamo definition, based on the most underrated node in Dynamo, Raybounce.

The Raybounce.ByOriginDirection is basically a laser rangefinder for Dynamo. It works with an origin point and a direction, and give in return the first intersecting element, along with the point of intersection. It is pretty powerful, and its uses range from basic measurements to advanced [Line Of Sight Analysis](https://revitbeyondbim.wordpress.com/2016/03/10/eye-sight-analysis-with-revit-and-dynamo/).

![UsingRaybounce-1](http://bim42.com/wp-content/uploads/2016/05/UsingRaybounce-1.png)

Using DynamoMEP, I retrieve every room in the model, and create a grid of points in each of them. These points are arbitrary spaced 50 cm apart, and serve as origin points for my Raybounce node.

![RetriveRooms](http://bim42.com/wp-content/uploads/2016/05/RetriveRooms.png)

Furthermore, in order to avoid that my laser beams hit the floor, I move my origin points 1 cm above the floor level.

![MoveOriginPoints](http://bim42.com/wp-content/uploads/2016/05/MoveOriginPoints.png)

The Raybounce.ByOriginDirection use these points, a Z vector as a direction and a 3D view. Since only elements visible in this view will be detected, I hide doors and stairs to remove interferences with these elements.

![RayBounce](http://bim42.com/wp-content/uploads/2016/05/RayBounce.png)

Along with the intersection point, the Raybounce.ByOriginDirection return the origin point that I filter out with a boolean mask.

![FilterPoints](http://bim42.com/wp-content/uploads/2016/05/FilterPoints.png)

![Points](http://bim42.com/wp-content/uploads/2016/05/Points.png)

I also make use of the List.Map node to perform any kind of operation (Flatten, Sort ... ) on the sublist containing the points while keeping them grouped by lists corresponding to the original rooms.

![ListMap](http://bim42.com/wp-content/uploads/2016/05/ListMap.png)

I finally calculate the headroom height, and retrieve the shortest one for each room. I pass this value to the Limit Offset parameter of the corresponding room.

![CalculateHeadRoom](http://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom.png)

Initially, every room's Limit Offset is 2m.

![Before](http://bim42.com/wp-content/uploads/2016/05/Before.png)

After running the Dynamo script, every Limit Offset is updated to reflect the actual minimum headroom in each room. Since we have a sloped roof, the minimum headroom is not necessarily the ceiling, but can be the lower part of the roof.

![After](http://bim42.com/wp-content/uploads/2016/05/After.png)

Using the Raybounce node can be quite challenging, especially when it comes to sorting the resulting points, but it is totally worth the effort. You will find [here](https://drive.google.com/file/d/0B_fvbfIWQ5JJY3U4TkduaGUwZkk/view?usp=sharing) the Dynamo definition, feel free to use it for your own project.

This was also the occasion for me to update DynamoMEP for Dynamo 1.0, and add a Grid function to create a nice array of point in a Room or a Space. As usual, you will find these updates in the Dynamo Package Manager.