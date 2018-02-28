---
id: 1161
title: Revit plugins updates and new features
date: 2017-04-28T04:54:57+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1161
permalink: /2017/04/revit-plugins-updates-and-new-features/
categories:
  - Revit
  - Uncategorized
tags:
  - .NET
  - Documentation
  - Plugin
  - Revit
---
As usual during this time of the year, I published the new version of my plugins for Revit.

# Align

The big improvement this year is the ability to align any type of elements, annotations or tags. I must thank [Deyan Nenov](https://twitter.com/@didonenov) and his large contribution to the source code for this new feature.

From now on, you can select any kind of element and align or distribute them evenly. This feature use the bounding box of the element in the view as a reference.

<div id="attachment_1164" style="max-width: 2034px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/04/AlignAirTerminal.gif"><img class="wp-image-1164 size-full" src="http://bim42.com/wp-content/uploads/2017/04/AlignAirTerminal.gif" alt="" width="2024" height="1180" /></a>
  
  <p class="wp-caption-text">
    Align or distribute all elements
  </p>
</div>

The Align command is still view-dependent, so using it in section view or in a plan view will not have the same effect on the overall position of a given element. A word of caution however, the align function can be unreliable in a 3D view.

<div id="attachment_1165" style="max-width: 2034px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/04/AlignAirTerminalSection.gif"><img class="wp-image-1165 size-full" src="http://bim42.com/wp-content/uploads/2017/04/AlignAirTerminalSection.gif" alt="" width="2024" height="1180" /></a>
  
  <p class="wp-caption-text">
    View-dependent align functions
  </p>
</div>

Of course, you can still use it to align or distribute your tags and annotations, and it even works with viewports:

<div id="attachment_1167" style="max-width: 2030px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/04/AlignViews.gif"><img class="wp-image-1167 size-full" src="http://bim42.com/wp-content/uploads/2017/04/AlignViews.gif" alt="" width="2020" height="1180" /></a>
  
  <p class="wp-caption-text">
    Align viewports
  </p>
</div>

Along with these improvement, Align now fully support Area tags, and a few bugs have been eliminated. You can now use Align even if on tag without a leader, and multi-leader text are now fully supported, and some selection subtlety have been introduced.

<div id="attachment_1166" style="max-width: 1750px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/04/AlignTag.gif"><img class="wp-image-1166 size-full" src="http://bim42.com/wp-content/uploads/2017/04/AlignTag.gif" alt="" width="1740" height="1224" /></a>
  
  <p class="wp-caption-text">
    Align tags and texts
  </p>
</div>

I haven’t tested it with all categories, if you find something weird, please let me know, I would be happy to fix it.

You can find this new version on the [Autodesk App Store](https://apps.autodesk.com/ACD/en/Detail/Index?id=2903508825431715905&appLang=en&os=Win32_64).

# Room Finishing

Along with the support for Revit 2018, I corrected an issue where a skirting board was created even if the room was not bound by a wall. From now on, Room Finishing will not create a skirting board along room bounding lines.

<div id="attachment_1168" style="max-width: 2030px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/04/RoomFinishes.gif"><img class="wp-image-1168 size-full" src="http://bim42.com/wp-content/uploads/2017/04/RoomFinishes.gif" alt="" width="2020" height="1180" /></a>
  
  <p class="wp-caption-text">
    Support room with room boundary lines
  </p>
</div>

Room Finishing is also available on the [App Store](https://apps.autodesk.com/ACD/en/Detail/Index?id=5641957956279354474&appLang=en&os=Win64).

# Time Stamper

The Time Stamper plugin got a few improvements this year along with the usual bug smashing.

You can now choose between applying your time stamp to every element, or just the one visible in the view. This will give you the ability to filter on which element you want to apply a stamp.

You can also choose to keep or override an existing value, this should help you keep the history of a given element.

A few bugs where corrected, making the creation of the four shared parameters far more reliable. Groups are now supported.

<div id="attachment_1169" style="max-width: 2030px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/04/TimeStamp.gif"><img class="wp-image-1169 size-full" src="http://bim42.com/wp-content/uploads/2017/04/TimeStamp.gif" alt="" width="2020" height="1180" /></a>
  
  <p class="wp-caption-text">
    Support for groups
  </p>
</div>

Time Stamper is now available [here](https://apps.autodesk.com/ACD/en/Detail/Index?id=232313135819866372&appLang=en&os=Win64).

These new versions are now available on the [Autodesk App Store](https://apps.autodesk.com/en/Publisher/PublisherHomepage?ID=200810282052581). Don't hesitate to report any issue you might find in them or ask for improvement.

These plugins are open source, you can find the source code [here](https://github.com/simonmoreau/RoomFinishes), [here](https://bitbucket.org/simonmoreau/align-tag) and [here](https://bitbucket.org/simonmoreau/timestamp). Feel free to use it on your own project or contribute to these projects.