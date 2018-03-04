---
id: 732
title: Creating a report from a BCF file
date: 2014-12-09T20:36:49+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=732
permalink: /2014/12/creating-a-report-from-a-bcf-file/
categories:
  - Coordination
tags:
  - .NET
  - BIM Manager
  - Coordination
  - Documentation
  - Tekla
---
I was talking on a previous post about BIMsight and the possibility to export its notes in the BCF format.

This BIM Collaboration Format (BCF) is a common development by Tekla and Solibri to create a standard for exchanging comments between building models. This format can accelerate dataflow during project review by exchanging only comments without having to rely upon the same format and large data exchange through Internet.

The BCF format is currently supported by Tekla Structures, Tekla BIMsight, ArchiCAD, Kubus BCF Manager, Solibri, Elvis, Kymdata’s CADS Planner softwares, DDS-CAD Viewer and DDS-CAD MEP. There is also plug-ins for Revit and Navisworks.

I am using Tekla BIMSight on a daily basis as an advanced BIM notebook. Every problem is addressed during the daily coordination meeting, and documented using notes in Tekla BIMSight.

![ScreenClip](/assets/2014/12/ScreenClip.png)

But for documentation purpose, I also need a paper-based report, quite old fashioned, but handy when you have to work with people without Tekla BIMSight.

I created a little standalone program for converting BCF files to Word reports. These BCF files are created from my notes in Tekla BIMSight.

A BCF file is actually a compressed file, where every note is stored in its own folder, named with the note GUID:

![ScreenClip-1](/assets/2014/12/ScreenClip-1.png)

In each of these folder, there is three files:

* markup.bcf
* snapshot.png
* viewpoint.bcfv

The markup.bcf file stores all metadata about the note: Its date, its title, its author, its various comment along with their dates, and so on. This is the main source of information for my daily coordination report.

snapshot.png is the first image associated with the note, and an essential part of my report too.

Finally, the viewpoint.bcfv store information about the position of the camera used to capture the snapshot. Since the very point of my report is to work outside the model, I won't use it here.

I use the XSD Schema provided by [Building Smart](http://www.buildingsmart-tech.org/specifications/bcf-releases) to create my C# classes and serialize the markup.bcf file.

To write down this report, I use the great [DocX](http://docx.codeplex.com/) library to create a Word 2010 file.

With this little program, I create automatically a nice Word report from my coordination notes, and can share my comments with everyone who does not have Tekla BIMSight.

![Presentation1](/assets/2014/12/Presentation1.jpg)