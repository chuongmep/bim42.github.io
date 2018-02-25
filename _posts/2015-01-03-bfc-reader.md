---
id: 745
title: BFC Reader
date: 2015-01-03T10:00:51+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=745
permalink: /2015/01/bfc-reader/
categories:
  - Coordination
tags:
  - .NET
  - BIM Manager
  - Documentation
  - Open BIM
  - Tekla
---
I was talking on [my previous post](http://bim42.com/2014/12/creating-a-report-from-a-bcf-file/) about creating a report from a Open BIM Collaboration Format. This format can be exported from Tekla BIMSight.

I am using the Open BIM Collaboration Format on a daily basis for taking notes during coordination meetings. I am using Tekla BIMSight to create these notes, but any model review solution could do the trick, as long as you can export BCF files from it.

These notes are quite useful for addressing coordination problems, but cannot be seen outside a model.

After the proof of concept I presented to you on my last post, I finally took the time to build a packaged application in order to create a Microsoft Word document from a BCF report.

[<img class="aligncenter size-full wp-image-747" src="http://bim42.com/wp-content/uploads/2015/01/ScreenClip3.png" alt="BCF Reader" width="300" height="400" srcset="https://bim42.com/wp-content/uploads/2015/01/ScreenClip3.png 300w, https://bim42.com/wp-content/uploads/2015/01/ScreenClip3-225x300.png 225w" sizes="(max-width: 300px) 100vw, 300px" />](http://bim42.com/wp-content/uploads/2015/01/ScreenClip3.png)

Aside from minor technical problems, I was most concerned by the possibilities to edit the style of the report before creating it, and avoid the tedious task to clean it up in Word after.

I finally selected a solution mixing Word template and styles. All you have to do after selecting you BCF report is to load a Word template. The application will automatically retrieve all styles in it, and you will be able to select them for each part of your report.
  
These parts are described in the picture below, where every information embedded in the BCF note is written down on the report.

[<img class="aligncenter size-full wp-image-746" src="http://bim42.com/wp-content/uploads/2015/01/DocXExample2.png" alt="Report" width="800" height="828" srcset="https://bim42.com/wp-content/uploads/2015/01/DocXExample2.png 800w, https://bim42.com/wp-content/uploads/2015/01/DocXExample2-290x300.png 290w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/01/DocXExample2.png)

You can then save your report in a new word document.

The application can be downloaded [here](https://bitbucket.org/simonmoreau/bcfreader/downloads/BCFReader.exe), under the MIT licence.

The entire source code is also available on [Bitbucket](https://bitbucket.org/simonmoreau/bcfreader), feel free to use it for your own project.