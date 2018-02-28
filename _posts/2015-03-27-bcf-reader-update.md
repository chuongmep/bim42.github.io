---
id: 804
title: BCF Reader Update
date: 2015-03-27T17:48:07+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=804
permalink: /2015/03/bcf-reader-update/
categories:
  - Coordination
tags:
  - .NET
  - BIM Manager
  - Coordination
  - Open BIM
---
This post is long overdue, but I finally take the time to update my BCF Reader.

![BCFReader-Logo_small](http://bim42.com/wp-content/uploads/2015/03/BCFReader-Logo_small.png)

First of all, I have tested it on a larger set of BCF files, and I hope these will make it more robust, especially if something is wrong within the BCF file. My experiences include files coming from [Tekla BIMSight](http://www.teklabimsight.com/), [Matteo Cominetti's BCFier](http://matteocominetti.com/bcfier/) and [Kubus BIM Collab.](http://www.bimcollab.com/en/default.aspx)

I have to remove the support for Word 97-2003 Documents (*.doc), since the library I use does not support them. I will see how I can integrate them back in a future release.

Among the change, I add a small progress bar to allow you to pour yourself a coffee when dealing with huge quantities of notes.

I also add Status and Verbal Status to the report, just after the date. A more subtle change, the default path to save your report is now the same than the BCF file itself.

I improve the [Readme file](https://bitbucket.org/simonmoreau/bcfreader/overview) to include a small explanation on how to use the BCF Reader.

I spotted some problems with styles in the Word template. To be sure to have all of them available in the BCF Reader, you must write a few lines in your Word template, apply your styles to them, then delete them. This will ensure that you have created these styles in your Word template before using it.

Finally, I want to thank Julien Benoit and François Lahouste for their comments and their files.

As usual, you can download the BCF Reader [here](https://bitbucket.org/simonmoreau/bcfreader/downloads/BCFReader.exe), and check the code [here](https://bitbucket.org/simonmoreau/bcfreader/overview).