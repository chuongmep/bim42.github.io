---
id: 144
title: Digital Project Automation
date: 2012-07-01T20:35:58+00:00
author: Simon Moreau
layout: post
guid: http://bim42.wordpress.com/?p=144
permalink: /2012/07/digital-project-automation/
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:1:{s:50:"http://bim42.files.wordpress.com/2012/07/vbnet.jpg";a:6:{s:8:"file_url";s:50:"http://bim42.files.wordpress.com/2012/07/vbnet.jpg";s:5:"width";s:3:"300";s:6:"height";s:3:"156";s:4:"type";s:5:"image";s:4:"area";s:5:"46800";s:9:"file_path";s:0:"";}}s:6:"videos";a:0:{}s:11:"image_count";s:1:"1";s:6:"author";s:8:"11101104";s:7:"blog_id";s:8:"35202242";s:9:"mod_stamp";s:19:"2012-07-01 20:35:58";}'
categories:
  - Digital Project
image: /assets/bim42_header.jpg
tags:
  - .NET
  - Automation
  - Digital Project
---
![vbnet](/assets/2012/07/vbnet.jpg)

Aside from a lot of features, CATIA, and so Digital Project, comes with powerful automation tools.

Knowledge Templates is a programming language interface, tightly integrated into CATIA, allowing adding rules on a design. You can link various geometrical parameters to a single one which will update the whole geometry regarding its value.  For example, we used this functionality to create a rule which change the section of steel beams regarding their position in the whole structure. These rules are part of the CATIA tree and are automatically updated with design changes. You can also use them for calling more complex automation code written in CATVBA.

CATVBA is the programming language of CATIA. Based on VBA, it came with a developing interface looking more or less like the Excel one, and made any development pretty easy. Most of the functions of CATIA and Digital Project have their equivalent in CATVBA, and you can use these tools for any repetitive tasks. We used it to generate the covering panels of a large double curved roof. One panel was design carefully, using four points for its positioning, then duplicate automatically all over the roof, each panel adapting itself on its positioning points.

But as we were running this routine, we struggle with memory load problems, leading our application to crash after too much instantiations. We finally decide to use a .NET application running outside Digital Project to drive it. Most function of CATVBA can be used in .NET, so we rewrite our panels instantiation routine on Visual Studio (the Express version), adding some code to close and restart Digital Project when the memory load became too important. We finally manage to populate properly the whole roof surface with our panels, after running the application for nearly 48 hours (It was a really large roof... ).