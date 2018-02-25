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

[<img class="aligncenter size-large wp-image-1036" src="http://bim42.com/wp-content/uploads/2016/05/UsingRaybounce-1-1024x816.png" alt="UsingRaybounce" width="584" height="465" srcset="https://bim42.com/wp-content/uploads/2016/05/UsingRaybounce-1.png 1024w, https://bim42.com/wp-content/uploads/2016/05/UsingRaybounce-1-300x239.png 300w, https://bim42.com/wp-content/uploads/2016/05/UsingRaybounce-1-768x612.png 768w, https://bim42.com/wp-content/uploads/2016/05/UsingRaybounce-1-376x300.png 376w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/05/UsingRaybounce-1.png)

Using DynamoMEP, I retrieve every room in the model, and create a grid of points in each of them. These points are arbitrary spaced 50 cm apart, and serve as origin points for my Raybounce node.

[<img class="aligncenter size-large wp-image-1033" src="http://bim42.com/wp-content/uploads/2016/05/RetriveRooms-1024x341.png" alt="RetriveRooms" width="584" height="194" srcset="https://bim42.com/wp-content/uploads/2016/05/RetriveRooms-1024x341.png 1024w, https://bim42.com/wp-content/uploads/2016/05/RetriveRooms-300x100.png 300w, https://bim42.com/wp-content/uploads/2016/05/RetriveRooms-768x256.png 768w, https://bim42.com/wp-content/uploads/2016/05/RetriveRooms-500x167.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/05/RetriveRooms.png)

Furthermore, in order to avoid that my laser beams hit the floor, I move my origin points 1 cm above the floor level.

[<img class="aligncenter size-full wp-image-1030" src="http://bim42.com/wp-content/uploads/2016/05/MoveOriginPoints.png" alt="MoveOriginPoints" width="917" height="637" srcset="https://bim42.com/wp-content/uploads/2016/05/MoveOriginPoints.png 917w, https://bim42.com/wp-content/uploads/2016/05/MoveOriginPoints-300x208.png 300w, https://bim42.com/wp-content/uploads/2016/05/MoveOriginPoints-768x533.png 768w, https://bim42.com/wp-content/uploads/2016/05/MoveOriginPoints-432x300.png 432w" sizes="(max-width: 917px) 100vw, 917px" />](http://bim42.com/wp-content/uploads/2016/05/MoveOriginPoints.png)

The Raybounce.ByOriginDirection use these points, a Z vector as a direction and a 3D view. Since only elements visible in this view will be detected, I hide doors and stairs to remove interferences with these elements.

[<img class="aligncenter size-full wp-image-1032" src="http://bim42.com/wp-content/uploads/2016/05/RayBounce.png" alt="RayBounce" width="986" height="732" srcset="https://bim42.com/wp-content/uploads/2016/05/RayBounce.png 986w, https://bim42.com/wp-content/uploads/2016/05/RayBounce-300x223.png 300w, https://bim42.com/wp-content/uploads/2016/05/RayBounce-768x570.png 768w, https://bim42.com/wp-content/uploads/2016/05/RayBounce-404x300.png 404w" sizes="(max-width: 986px) 100vw, 986px" />](http://bim42.com/wp-content/uploads/2016/05/RayBounce.png)

Along with the intersection point, the Raybounce.ByOriginDirection return the origin point that I filter out with a boolean mask.

[<img class="aligncenter size-full wp-image-1028" src="http://bim42.com/wp-content/uploads/2016/05/FilterPoints.png" alt="FilterPoints" width="929" height="362" srcset="https://bim42.com/wp-content/uploads/2016/05/FilterPoints.png 929w, https://bim42.com/wp-content/uploads/2016/05/FilterPoints-300x117.png 300w, https://bim42.com/wp-content/uploads/2016/05/FilterPoints-768x299.png 768w, https://bim42.com/wp-content/uploads/2016/05/FilterPoints-500x195.png 500w" sizes="(max-width: 929px) 100vw, 929px" />](http://bim42.com/wp-content/uploads/2016/05/FilterPoints.png)

[<img class="aligncenter size-large wp-image-1031" src="http://bim42.com/wp-content/uploads/2016/05/Points-1024x564.png" alt="Points" width="584" height="322" srcset="https://bim42.com/wp-content/uploads/2016/05/Points-1024x564.png 1024w, https://bim42.com/wp-content/uploads/2016/05/Points-300x165.png 300w, https://bim42.com/wp-content/uploads/2016/05/Points-768x423.png 768w, https://bim42.com/wp-content/uploads/2016/05/Points-500x276.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/05/Points.png)

I also make use of the List.Map node to perform any kind of operation (Flatten, Sort &#8230;) on the sublist containing the points while keeping them grouped by lists corresponding to the original rooms.

[<img class="aligncenter size-large wp-image-1029" src="http://bim42.com/wp-content/uploads/2016/05/ListMap-1024x460.png" alt="ListMap" width="584" height="262" srcset="https://bim42.com/wp-content/uploads/2016/05/ListMap-1024x460.png 1024w, https://bim42.com/wp-content/uploads/2016/05/ListMap-300x135.png 300w, https://bim42.com/wp-content/uploads/2016/05/ListMap-768x345.png 768w, https://bim42.com/wp-content/uploads/2016/05/ListMap-500x224.png 500w, https://bim42.com/wp-content/uploads/2016/05/ListMap.png 1430w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/05/ListMap.png)

I finally calculate the headroom height, and retrieve the shortest one for each room. I pass this value to the Limit Offset parameter of the corresponding room.

[<img class="aligncenter size-large wp-image-1027" src="http://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom-1024x530.png" alt="CalculateHeadRoom" width="584" height="302" srcset="https://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom-1024x530.png 1024w, https://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom-300x155.png 300w, https://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom-768x398.png 768w, https://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom-500x259.png 500w, https://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom.png 1244w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/05/CalculateHeadRoom.png)

Initially, every room&#8217;s Limit Offset is 2m.

[<img class="aligncenter size-large wp-image-1026" src="http://bim42.com/wp-content/uploads/2016/05/Before-1024x398.png" alt="Before" width="584" height="227" srcset="https://bim42.com/wp-content/uploads/2016/05/Before-1024x398.png 1024w, https://bim42.com/wp-content/uploads/2016/05/Before-300x117.png 300w, https://bim42.com/wp-content/uploads/2016/05/Before-768x299.png 768w, https://bim42.com/wp-content/uploads/2016/05/Before-500x194.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/05/Before.png)

After running the Dynamo script, every Limit Offset is updated to reflect the actual minimum headroom in each room. Since we have a sloped roof, the minimum headroom is not necessarily the ceiling, but can be the lower part of the roof.

[<img class="aligncenter size-large wp-image-1025" src="http://bim42.com/wp-content/uploads/2016/05/After-1024x387.png" alt="After" width="584" height="221" srcset="https://bim42.com/wp-content/uploads/2016/05/After-1024x387.png 1024w, https://bim42.com/wp-content/uploads/2016/05/After-300x113.png 300w, https://bim42.com/wp-content/uploads/2016/05/After-768x290.png 768w, https://bim42.com/wp-content/uploads/2016/05/After-500x189.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/05/After.png)

Using the Raybounce node can be quite challenging, especially when it comes to sorting the resulting points, but it is totally worth the effort. You will find [here](https://drive.google.com/file/d/0B_fvbfIWQ5JJY3U4TkduaGUwZkk/view?usp=sharing) the Dynamo definition, feel free to use it for your own project.

This was also the occasion for me to update DynamoMEP for Dynamo 1.0, and add a Grid function to create a nice array of point in a Room or a Space. As usual, you will find these updates in the Dynamo Package Manager.