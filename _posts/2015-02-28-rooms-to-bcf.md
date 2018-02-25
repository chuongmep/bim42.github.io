---
id: 783
title: Rooms to BCF
date: 2015-02-28T17:04:48+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=783
permalink: /2015/02/rooms-to-bcf/
categories:
  - Coordination
tags:
  - .NET
  - Coordination
  - Revit
  - Tekla
---
I am a huge fan of Tekla BIMSight. It&#8217;s powerfull, it&#8217;s free and very user-friendly. But like with many other project review solutions, I have difficulties to locate myself in the building while spinning around the 3D model.

It become even more tedious when you have to find a specific room in the model. There is no convenient way to retrieve its by a name or its number or zoom on it quickly.

A solution is to sort the Tekla BIMSight objects browser by Level and by Name to display every room in the model. You can then select a room and start create your clipping planes around it. This is not user-friendly. Furthermore, I haven&#8217;t always the luxury of working with IFC.

[<img class="aligncenter size-full wp-image-786" src="http://bim42.com/wp-content/uploads/2015/02/Object-Browser.png" alt="Object Browser" width="646" height="388" srcset="https://bim42.com/wp-content/uploads/2015/02/Object-Browser.png 646w, https://bim42.com/wp-content/uploads/2015/02/Object-Browser-300x180.png 300w, https://bim42.com/wp-content/uploads/2015/02/Object-Browser-500x300.png 500w" sizes="(max-width: 646px) 100vw, 646px" />](http://bim42.com/wp-content/uploads/2015/02/Object-Browser.png)

This is why I create a small application for creating a BCF note for every room of a building. This Revit plug-in save the location, the dimension and the name of all rooms to a BCF file.

[<img class="aligncenter wp-image-788 size-full" src="http://bim42.com/wp-content/uploads/2015/02/Evernote-Snapshot-20150228-174718.png" alt="Process" width="800" height="268" srcset="https://bim42.com/wp-content/uploads/2015/02/Evernote-Snapshot-20150228-174718.png 800w, https://bim42.com/wp-content/uploads/2015/02/Evernote-Snapshot-20150228-174718-300x101.png 300w, https://bim42.com/wp-content/uploads/2015/02/Evernote-Snapshot-20150228-174718-500x168.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/02/Evernote-Snapshot-20150228-174718.png)

When opening this file in Tekla BIMSight, we see every room neatly sorted by level in the Notes tab.

[<img class="aligncenter size-full wp-image-785" src="http://bim42.com/wp-content/uploads/2015/02/Notes.png" alt="Notes" width="647" height="347" srcset="https://bim42.com/wp-content/uploads/2015/02/Notes.png 647w, https://bim42.com/wp-content/uploads/2015/02/Notes-300x161.png 300w, https://bim42.com/wp-content/uploads/2015/02/Notes-500x268.png 500w" sizes="(max-width: 647px) 100vw, 647px" />](http://bim42.com/wp-content/uploads/2015/02/Notes.png)

As you select one of these notes, Tekla BIMSight zoom on the selected room, and create nice clipping planes around it.

[<img class="aligncenter size-full wp-image-784" src="http://bim42.com/wp-content/uploads/2015/02/In-Tekla.png" alt="In Tekla" width="1366" height="738" srcset="https://bim42.com/wp-content/uploads/2015/02/In-Tekla.png 1366w, https://bim42.com/wp-content/uploads/2015/02/In-Tekla-300x162.png 300w, https://bim42.com/wp-content/uploads/2015/02/In-Tekla-1024x553.png 1024w, https://bim42.com/wp-content/uploads/2015/02/In-Tekla-500x270.png 500w" sizes="(max-width: 1366px) 100vw, 1366px" />](http://bim42.com/wp-content/uploads/2015/02/In-Tekla.png)

To do so, I am using [XbimBCF](https://github.com/xBimTeam/XbimBCF "XbimBCF"), a great library for reading and writing BCF files. I just have to adapt it a bit since Tekla BIMSight does not support yet the second version of the BCF format.

This application is now more a proof a concept than an actual solution, but I will try to find the time to clean and share the code.

The BCF concept appears more and more appealing as I work with it. This format allow to develop small utilities like this one very quickly, and will be very useful for many tasks involving project review.