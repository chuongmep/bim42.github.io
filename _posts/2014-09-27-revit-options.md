---
id: 603
title: Revit Options
date: 2014-09-27T10:00:27+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=603
permalink: /2014/09/revit-options/
categories:
  - Revit
tags:
  - BIM Manager
  - Documentation
  - Revit
  - Schedules
---
Revit options have been a mystery for me for quite a long time, so I decide to write a few lines about it in order to better understand their possibilities.

To do so, let&#8217;s model a small house, nothing fancy, but enough to have some possibilities for evolution. This house is drawn in the Main Model, and will be common to all options.

![<img class="aligncenter size-full wp-image-614" src="http://bim42.com/wp-content/uploads/2014/09/DesignOption_ARC_SomeHouse1.jpg" alt="SomeHouse" width="800" height="517" srcset="https://bim42.com/wp-content/uploads/2014/09/DesignOption_ARC_SomeHouse1.jpg 800w, https://bim42.com/wp-content/uploads/2014/09/DesignOption_ARC_SomeHouse1-300x193.jpg 300w, https://bim42.com/wp-content/uploads/2014/09/DesignOption_ARC_SomeHouse1-464x300.jpg 464w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/DesignOption_ARC_SomeHouse1.jpg)

Now let say I want to _try_ something. I put try on emphasis, because, it&#8217;s really what Design Options are useful for. I open the Design Options editor, and create a new option set, which is automatically populated with a first option. I rename it like this:

![<img class="aligncenter size-full wp-image-604" src="http://bim42.com/wp-content/uploads/2014/09/CreateOptions.png" alt="CreateOptions" width="481" height="522" srcset="https://bim42.com/wp-content/uploads/2014/09/CreateOptions.png 481w, https://bim42.com/wp-content/uploads/2014/09/CreateOptions-276x300.png 276w" sizes="(max-width: 481px) 100vw, 481px" />](http://bim42.com/wp-content/uploads/2014/09/CreateOptions.png)

I select this new option as the current one using the Option drop-down menu on the bottom of the Revit screen, and start modeling a duct layout.

![<img class="aligncenter size-full wp-image-607" src="http://bim42.com/wp-content/uploads/2014/09/FirstLayoutOption.jpg" alt="FirstLayoutOption" width="800" height="453" srcset="https://bim42.com/wp-content/uploads/2014/09/FirstLayoutOption.jpg 800w, https://bim42.com/wp-content/uploads/2014/09/FirstLayoutOption-300x169.jpg 300w, https://bim42.com/wp-content/uploads/2014/09/FirstLayoutOption-500x283.jpg 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/FirstLayoutOption.jpg)

To create a second routing option, I duplicate the first one, and rename it. Every elements of my First Routing Option are now duplicated in my Secondary Routing Option.

![<img class="aligncenter size-full wp-image-605" src="http://bim42.com/wp-content/uploads/2014/09/CreateSecondOption.png" alt="CreateSecondOption" width="481" height="530" srcset="https://bim42.com/wp-content/uploads/2014/09/CreateSecondOption.png 481w, https://bim42.com/wp-content/uploads/2014/09/CreateSecondOption-272x300.png 272w" sizes="(max-width: 481px) 100vw, 481px" />](http://bim42.com/wp-content/uploads/2014/09/CreateSecondOption.png)

I edit these duplicated elements to create a second duct layout. In the process, I realize than families edited during option editing are actually edited for the whole model, so this kind of change will impact every other option.

![<img class="aligncenter size-full wp-image-611" src="http://bim42.com/wp-content/uploads/2014/09/SecondLayoutOption.jpg" alt="SecondLayoutOption" width="800" height="453" srcset="https://bim42.com/wp-content/uploads/2014/09/SecondLayoutOption.jpg 800w, https://bim42.com/wp-content/uploads/2014/09/SecondLayoutOption-300x169.jpg 300w, https://bim42.com/wp-content/uploads/2014/09/SecondLayoutOption-500x283.jpg 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/SecondLayoutOption.jpg)

I have now two different duct layouts in my model, which are displayed when I select one or the other design option in the Design drop down menu.

But these options can also be displayed on a per view basis. As you created some design options, a new panel appear on your Visibility Override, allowing you to select an option to be displayed.

![<img class="aligncenter size-full wp-image-610" src="http://bim42.com/wp-content/uploads/2014/09/OverrideOptions.png" alt="OverrideOptions" width="789" height="612" srcset="https://bim42.com/wp-content/uploads/2014/09/OverrideOptions.png 789w, https://bim42.com/wp-content/uploads/2014/09/OverrideOptions-300x232.png 300w, https://bim42.com/wp-content/uploads/2014/09/OverrideOptions-386x300.png 386w" sizes="(max-width: 789px) 100vw, 789px" />](http://bim42.com/wp-content/uploads/2014/09/OverrideOptions.png)

This can be used to display our two options on the same sheets:

![<img class="aligncenter size-full wp-image-612" src="http://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image1.jpg" alt="Options" width="800" height="566" srcset="https://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image1.jpg 800w, https://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image1-300x212.jpg 300w, https://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image1-424x300.jpg 424w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image1.jpg)

It can also be used to display the metrics of each option side by side to decide which one should be keep. For example, I show here a duct schedule and a duct fitting schedule for each option:

![<img class="aligncenter size-full wp-image-613" src="http://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image2.jpg" alt="Schedule" width="819" height="579" srcset="https://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image2.jpg 819w, https://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image2-300x212.jpg 300w, https://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image2-424x300.jpg 424w" sizes="(max-width: 819px) 100vw, 819px" />](http://bim42.com/wp-content/uploads/2014/09/DesignOption_MEP_Image2.jpg)

These data can give us powerfull insight for choosing an option. Once one of them is validated, the Design Options provides us some tools to integrate our option in the main project.

We first have to Make primary our selected option, here the second one. We can see this one becoming visible from the Main Model option.

![<img class="aligncenter size-full wp-image-608" src="http://bim42.com/wp-content/uploads/2014/09/MakePrimary.jpg" alt="MakePrimary" width="800" height="387" srcset="https://bim42.com/wp-content/uploads/2014/09/MakePrimary.jpg 800w, https://bim42.com/wp-content/uploads/2014/09/MakePrimary-300x145.jpg 300w, https://bim42.com/wp-content/uploads/2014/09/MakePrimary-500x241.jpg 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/MakePrimary.jpg)

Since linked models only display their primary options, you have to make sure that selected option are primary before using it as a reference.

Selecting Accept Primary integrate our primary option in the Main Model option, and delete every other option associated with the Option Set. Our option is now part of our model.