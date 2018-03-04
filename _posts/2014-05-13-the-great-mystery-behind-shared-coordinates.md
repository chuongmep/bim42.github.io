---
id: 349
title: The great mystery behind shared coordinates
date: 2014-05-13T04:53:28+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=349
permalink: /2014/05/the-great-mystery-behind-shared-coordinates/
publicize_linkedin_url:
  - 'http://www.linkedin.com/updates?discuss=&scope=45913264&stype=M&topic=5871844462954586112&type=U&a=xL68'
publicize_twitter_user:
  - bim42
publicize_twitter_url:
  - http://t.co/7BreB1ivzB
categories:
  - Revit
tags:
  - BIM Manager
  - Revit
  - Survey Point
  - Tips
---
To make thinks clear for myself and for some of my colleagues, I play with some models in order to understand how Revit coordinates works. Here is the result of my work.

Every Revit model contains two systems of coordinates, represented by two points:

* A Project Base Point (the circle): This is the real center of the current model.

Drawing something too far from this origin will display the following message:

![error](/assets/2014/05/error.png)

* A Survey Point (the triangle): This is the position of our project in the real world (yes, you know, the one outside Revit ... ).

The angle between these two systems of coordinate is called "Angle to True North".

There is three possibilities for automatically positioning a Revit linked model into another:

![positionning](/assets/2014/05/positionning.png)

The Center to Center option inserts the "center" of our linked model on the "center" of the host model. The center is not very well defined, and correspond more or less to the general geometric center of the elements drawn in the model. For example (the linked model is in blue):

![centertocenter](/assets/2014/05/centertocenter.png)

The Origin to Origin option inserts the linked model with its Project Base point aligned with the one of the host model.

![origin-to-origin](/assets/2014/05/origin-to-origin.png)

And finally, the By Shared Coordinates inserts the linked model with the Survey Points overlapping.

![bysharedcoordinates](/assets/2014/05/bysharedcoordinates.png)

This particular insertion method is especially useful when dealing with multiple buildings on a site.

As an example, on this Site model, I have two implantations for two buildings (in magenta). My Survey Point is located on the origin point of the whole site.

![sitemodel](/assets/2014/05/sitemodel.png)

I create my first building, with the Project Base Point and the Survey Point basically at the center of the model.

![building1](/assets/2014/05/building1.png)

I insert roughly this building in my site model, and manually place it on its final location:

![insertbuilding1](/assets/2014/05/insertbuilding1.png)

I can know share the coordinates of my site model to my first building.

This will change the position of the Survey Point in my Builnding1 model:

![surveypointbuilding1](/assets/2014/05/surveypointbuilding1.png)

If I repeat the whole process with my second building, the three models will share the same system of coordinates through their Survey Point. By selecting Auto - By Shared Coordinate on insertion, every model will be placed correctly regarding the others.

It is also possible to manually move the Project Origin Point or the Survey Point. In this case, the small clip button will determine which point is moving regarding the other:

In this case, the selected point will be moving:

![pointmoving](/assets/2014/05/pointmoving.png)

If so, the rest of the model will be moving around the selected point:

![restmoving](/assets/2014/05/restmoving.png)

The difference can be subtle, don't hesitate to play with it in order to understand how it works.