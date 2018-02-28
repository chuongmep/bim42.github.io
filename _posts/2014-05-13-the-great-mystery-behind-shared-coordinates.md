---
id: 349
title: The great mystery behind shared coordinates
date: 2014-05-13T04:53:28+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=349
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
  
&#8211; A Project Base Point (the circle): This is the real center of the current model.
  
Drawing something too far from this origin will display the following message:

![<img class="aligncenter size-full wp-image-355" src="http://bim42.com/wp-content/uploads/2014/05/error.png" alt="error" width="376" height="224" srcset="https://bim42.com/wp-content/uploads/2014/05/error.png 376w, https://bim42.com/wp-content/uploads/2014/05/error-300x178.png 300w" sizes="(max-width: 376px) 100vw, 376px" />](http://bim42.com/wp-content/uploads/2014/05/error.png)

&#8211; A Survey Point (the triangle): This is the position of our project in the real world (yes, you know, the one outside Revit &#8230;).
  
The angle between these two systems of coordinate is called &#8220;Angle to True North&#8221;.

There is three possibilities for automatically positioning a Revit linked model into another:

![<img class="aligncenter size-full wp-image-359" src="http://bim42.com/wp-content/uploads/2014/05/positionning.png" alt="Positionning" width="303" height="131" srcset="https://bim42.com/wp-content/uploads/2014/05/positionning.png 303w, https://bim42.com/wp-content/uploads/2014/05/positionning-300x129.png 300w" sizes="(max-width: 303px) 100vw, 303px" />](http://bim42.com/wp-content/uploads/2014/05/positionning.png)The Center to Center option inserts the &#8220;center&#8221; of our linked model on the &#8220;center&#8221; of the host model. The center is not very well defined, and correspond more or less to the general geometric center of the elements drawn in the model. For example (the linked model is in blue):

![<img class="aligncenter size-full wp-image-354" src="http://bim42.com/wp-content/uploads/2014/05/centertocenter.png" alt="CenterToCenter" width="583" height="490" srcset="https://bim42.com/wp-content/uploads/2014/05/centertocenter.png 583w, https://bim42.com/wp-content/uploads/2014/05/centertocenter-300x252.png 300w" sizes="(max-width: 583px) 100vw, 583px" />](http://bim42.com/wp-content/uploads/2014/05/centertocenter.png)The Origin to Origin option inserts the linked model with its Project Base point aligned with the one of the host model.

![<img class="aligncenter size-full wp-image-357" src="http://bim42.com/wp-content/uploads/2014/05/origin-to-origin.png" alt="Origin to Origin" width="584" height="474" srcset="https://bim42.com/wp-content/uploads/2014/05/origin-to-origin.png 612w, https://bim42.com/wp-content/uploads/2014/05/origin-to-origin-300x243.png 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2014/05/origin-to-origin.png)And finally, the By Shared Coordinates inserts the linked model with the Survey Points overlapping.

![<img class="aligncenter size-full wp-image-353" src="http://bim42.com/wp-content/uploads/2014/05/bysharedcoordinates.png" alt="BySharedCoordinates" width="569" height="488" srcset="https://bim42.com/wp-content/uploads/2014/05/bysharedcoordinates.png 569w, https://bim42.com/wp-content/uploads/2014/05/bysharedcoordinates-300x257.png 300w" sizes="(max-width: 569px) 100vw, 569px" />](http://bim42.com/wp-content/uploads/2014/05/bysharedcoordinates.png)This particular insertion method is especially useful when dealing with multiple buildings on a site.
  
As an example, on this Site model, I have two implantations for two buildings (in magenta). My Survey Point is located on the origin point of the whole site.

![<img class="aligncenter size-full wp-image-362" src="http://bim42.com/wp-content/uploads/2014/05/sitemodel.png" alt="SiteModel" width="584" height="458" srcset="https://bim42.com/wp-content/uploads/2014/05/sitemodel.png 658w, https://bim42.com/wp-content/uploads/2014/05/sitemodel-300x235.png 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2014/05/sitemodel.png)I create my first building, with the Project Base Point and the Survey Point basically at the center of the model.

![<img class="aligncenter size-full wp-image-351" src="http://bim42.com/wp-content/uploads/2014/05/building1.png" alt="Building1" width="514" height="509" srcset="https://bim42.com/wp-content/uploads/2014/05/building1.png 514w, https://bim42.com/wp-content/uploads/2014/05/building1-150x150.png 150w, https://bim42.com/wp-content/uploads/2014/05/building1-300x297.png 300w" sizes="(max-width: 514px) 100vw, 514px" />](http://bim42.com/wp-content/uploads/2014/05/building1.png)I insert roughly this building in my site model, and manually place it on its final location:

![<img class="aligncenter size-full wp-image-356" src="http://bim42.com/wp-content/uploads/2014/05/insertbuilding1.png" alt="InsertBuilding1" width="584" height="418" srcset="https://bim42.com/wp-content/uploads/2014/05/insertbuilding1.png 687w, https://bim42.com/wp-content/uploads/2014/05/insertbuilding1-300x214.png 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2014/05/insertbuilding1.png)I can know share the coordinates of my site model to my first building.
  
This will change the position of the Survey Point in my Builnding1 model:

![<img class="aligncenter size-full wp-image-352" src="http://bim42.com/wp-content/uploads/2014/05/surveypointbuilding1.png" alt="SurveyPointBuilding1" width="584" height="429" srcset="https://bim42.com/wp-content/uploads/2014/05/surveypointbuilding1.png 671w, https://bim42.com/wp-content/uploads/2014/05/surveypointbuilding1-300x220.png 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2014/05/surveypointbuilding1.png)If I repeat the whole process with my second building, the three models will share the same system of coordinates through their Survey Point. By selecting Auto &#8211; By Shared Coordinate on insertion, every model will be placed correctly regarding the others.

It is also possible to manually move the Project Origin Point or the Survey Point. In this case, the small clip button will determine which point is moving regarding the other:
  
In this case, the selected point will be moving:

![<img class="aligncenter size-full wp-image-358" src="http://bim42.com/wp-content/uploads/2014/05/pointmoving.png" alt="PointMoving" width="210" height="155" />](http://bim42.com/wp-content/uploads/2014/05/pointmoving.png)If so, the rest of the model will be moving around the selected point:

![<img class="aligncenter size-full wp-image-360" src="http://bim42.com/wp-content/uploads/2014/05/restmoving.png" alt="RestMoving" width="201" height="160" />](http://bim42.com/wp-content/uploads/2014/05/restmoving.png)The difference can be subtle, don't hesitate to play with it in order to understand how it works.