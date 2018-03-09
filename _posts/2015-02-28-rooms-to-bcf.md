---
id: 783
title: Rooms to BCF
date: 2015-02-28T17:04:48+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=783
permalink: /2015/02/rooms-to-bcf/
categories:
  - Coordination
image: /assets/2015/02/Evernote-Snapshot-20150228-174718.png
tags:
  - .NET
  - Coordination
  - Revit
  - Tekla
---
I am a huge fan of Tekla BIMSight. It's powerfull, it's free and very user-friendly. But like with many other project review solutions, I have difficulties to locate myself in the building while spinning around the 3D model.

It become even more tedious when you have to find a specific room in the model. There is no convenient way to retrieve its by a name or its number or zoom on it quickly.

A solution is to sort the Tekla BIMSight objects browser by Level and by Name to display every room in the model. You can then select a room and start create your clipping planes around it. This is not user-friendly. Furthermore, I haven't always the luxury of working with IFC.

![Object-Browser](/assets/2015/02/Object-Browser.jpg)

This is why I create a small application for creating a BCF note for every room of a building. This Revit plug-in save the location, the dimension and the name of all rooms to a BCF file.

![Evernote-Snapshot-20150228-174718](/assets/2015/02/Evernote-Snapshot-20150228-174718.png)

When opening this file in Tekla BIMSight, we see every room neatly sorted by level in the Notes tab.

![Notes](/assets/2015/02/Notes.jpg)

As you select one of these notes, Tekla BIMSight zoom on the selected room, and create nice clipping planes around it.

![In-Tekla](/assets/2015/02/In-Tekla.jpg)

To do so, I am using [XbimBCF](https://github.com/xBimTeam/XbimBCF "XbimBCF"), a great library for reading and writing BCF files. I just have to adapt it a bit since Tekla BIMSight does not support yet the second version of the BCF format.

This application is now more a proof a concept than an actual solution, but I will try to find the time to clean and share the code.

The BCF concept appears more and more appealing as I work with it. This format allow to develop small utilities like this one very quickly, and will be very useful for many tasks involving project review.