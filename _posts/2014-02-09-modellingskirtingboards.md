---
id: 328
title: Modelling skirting boards
date: 2014-02-09T16:01:10+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=328
permalink: /2014/02/modellingskirtingboards/
publicize_linkedin_url:
  - 'http://www.linkedin.com/updates?discuss=&scope=45913264&stype=M&topic=5838310424743149568&type=U&a=uXcy'
publicize_twitter_user:
  - bim42
publicize_twitter_url:
  - http://t.co/TdylsOzoAE
categories:
  - Revit
tags:
  - .NET
  - Automation
  - Revit
  - Tips
---
One of my current project at work is to develop an application for the creation of a set of detailed drawings for each room of a building.

This set includes a plan view, a ceiling plan, an elevation view per wall and a schedule of furniture. These drawings must include all finishes details, like skirting boards, floor coverings, electrical equipment and so on.

So I came up with this idea for modeling details quickly and created a small application for drawing skirting boards in Revit.

My application uses a user-created wall type on a specific height to model a skirting board all around a previously selected room.

[<img class="aligncenter size-full wp-image-330" alt="Interface" src="http://bim42.com/wp-content/uploads/2014/02/interface.png" width="342" height="551" srcset="https://bim42.com/wp-content/uploads/2014/02/interface.png 342w, https://bim42.com/wp-content/uploads/2014/02/interface-186x300.png 186w" sizes="(max-width: 342px) 100vw, 342px" />](http://bim42.com/wp-content/uploads/2014/02/interface.png)

The development of this application was pretty straightforward, except when it came to placing correctly the skirting board baseline against the finish face of the main wall. Indeed, Revit API does not allow to set up a wall baseline before creating it. And changing it after the creating doesn’t move the wall, only the baseline.

[<img class="aligncenter size-full wp-image-331" alt="WallBaseline" src="http://bim42.com/wp-content/uploads/2014/02/wallbaseline.png" width="584" height="218" srcset="https://bim42.com/wp-content/uploads/2014/02/wallbaseline.png 600w, https://bim42.com/wp-content/uploads/2014/02/wallbaseline-300x112.png 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2014/02/wallbaseline.png)

My workaround was to create a larger wall, change its baseline, then change its wall type to the skirting board type, and finally, change back the wall baseline.

[<img class="aligncenter size-full wp-image-332" alt="workaround" src="http://bim42.com/wp-content/uploads/2014/02/workaround.png" width="584" height="430" srcset="https://bim42.com/wp-content/uploads/2014/02/workaround.png 1000w, https://bim42.com/wp-content/uploads/2014/02/workaround-300x221.png 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2014/02/workaround.png)

This method allows me to place the skirting board baseline along the finish face of the wall.

I also used this example to publish my first application on Autodesk Exchange App.
  
Following the guidelines for publishing allowed me to create a well packaged application, bundled with help file and installer. It is also the opportunity to distribute the application to a larger audience.

The whole publishing process is quite smooth, and the Audesk guys are very helpful.

The app is now available [here](http://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3aroomfinishing_windows32and64%3aen "Room Finishing") for free, and I plan to publish the code on GitHub as well soon.