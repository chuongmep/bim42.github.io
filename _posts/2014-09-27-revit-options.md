---
id: 603
title: Revit Options
date: 2014-09-27T10:00:27+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=603
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

To do so, let's model a small house, nothing fancy, but enough to have some possibilities for evolution. This house is drawn in the Main Model, and will be common to all options.

![DesignOption_ARC_SomeHouse1](/assets/2014/09/DesignOption_ARC_SomeHouse1.jpg)

Now let say I want to _try_ something. I put try on emphasis, because, it's really what Design Options are useful for. I open the Design Options editor, and create a new option set, which is automatically populated with a first option. I rename it like this:

![CreateOptions](/assets/2014/09/CreateOptions.png)

I select this new option as the current one using the Option drop-down menu on the bottom of the Revit screen, and start modeling a duct layout.

![FirstLayoutOption](/assets/2014/09/FirstLayoutOption.jpg)

To create a second routing option, I duplicate the first one, and rename it. Every elements of my First Routing Option are now duplicated in my Secondary Routing Option.

![CreateSecondOption](/assets/2014/09/CreateSecondOption.png)

I edit these duplicated elements to create a second duct layout. In the process, I realize than families edited during option editing are actually edited for the whole model, so this kind of change will impact every other option.

![SecondLayoutOption](/assets/2014/09/SecondLayoutOption.jpg)

I have now two different duct layouts in my model, which are displayed when I select one or the other design option in the Design drop down menu.

But these options can also be displayed on a per view basis. As you created some design options, a new panel appear on your Visibility Override, allowing you to select an option to be displayed.

![OverrideOptions](/assets/2014/09/OverrideOptions.png)

This can be used to display our two options on the same sheets:

![DesignOption_MEP_Image1](/assets/2014/09/DesignOption_MEP_Image1.jpg)

It can also be used to display the metrics of each option side by side to decide which one should be keep. For example, I show here a duct schedule and a duct fitting schedule for each option:

![DesignOption_MEP_Image2](/assets/2014/09/DesignOption_MEP_Image2.jpg)

These data can give us powerfull insight for choosing an option. Once one of them is validated, the Design Options provides us some tools to integrate our option in the main project.

We first have to Make primary our selected option, here the second one. We can see this one becoming visible from the Main Model option.

![MakePrimary](/assets/2014/09/MakePrimary.jpg)

Since linked models only display their primary options, you have to make sure that selected option are primary before using it as a reference.

Selecting Accept Primary integrate our primary option in the Main Model option, and delete every other option associated with the Option Set. Our option is now part of our model.