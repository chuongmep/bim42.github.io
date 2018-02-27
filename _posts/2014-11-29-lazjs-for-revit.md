---
id: 724
title: LazJS for Revit
date: 2014-11-29T10:00:13+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=724
permalink: /2014/11/lazjs-for-revit/
categories:
  - Revit
  - Uncategorized
tags:
  - Automation
  - Javascript
  - Revit
---
I recently receive a beta version of [LazJS](http://www.lazjs.com/ "LazJS"), a Javascript editor embedded within Revit.

Even if I more fluent with .NET and C#, I find the initiative quite interesting, especially when you have to quickly develop some small routine within Revit.

After installing it, I click on the ParamJS button to start their embedded editor.

![<img class="aligncenter size-full wp-image-728" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip1.png" alt="LazJS" width="240" height="99" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip1.png)

As an example, I concatenate various parameters of a sheet in the sheet name in order to have them when I print or export it.

I start by selecting a category in the Categories list. Here, you can select multiple categories, but I will only select &#8220;Sheets&#8221; here. When I click on &#8220;Customize&#8221;, LazJS displays every editable parameters of our sheets in the &#8220;Parameters&#8221; list. Since I want to edit the name of my sheet, I select &#8220;Sheet Name&#8221; and save.

![<img class="aligncenter size-full wp-image-727" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip-3.png" alt="ParamJS" width="950" height="561" srcset="https://bim42.com/wp-content/uploads/2014/11/ScreenClip-3.png 950w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-3-300x177.png 300w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-3-500x295.png 500w" sizes="(max-width: 950px) 100vw, 950px" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip-3.png)

I can now drag and drop parameters from the &#8220;Formulas&#8221; list to the &#8220;Editor&#8221; panel. This creates automatically the correct line of code for calling this parameter. I drag some of my sheet parameters, add some &#8220;+&#8221; to concatenate them, and hit Run. We can see the result of my concatenation just below. I hit save, and my modification are added to my model.

![<img class="aligncenter size-full wp-image-726" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip-23.png" alt="Run" width="972" height="557" srcset="https://bim42.com/wp-content/uploads/2014/11/ScreenClip-23.png 972w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-23-300x171.png 300w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-23-500x286.png 500w" sizes="(max-width: 972px) 100vw, 972px" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip-23.png)

If this is the quickest way to edit parameters, LazJS have also a fully functional editor, which allows us to create more elaborate routines.

I use it to create the same concatenation tool than in my previous example, everything came pretty easily with the auto-completion.

![<img class="aligncenter size-full wp-image-725" src="http://bim42.com/wp-content/uploads/2014/11/ScreenClip-11.png" alt="ScreenClip [1]" width="950" height="385" srcset="https://bim42.com/wp-content/uploads/2014/11/ScreenClip-11.png 950w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-11-300x121.png 300w, https://bim42.com/wp-content/uploads/2014/11/ScreenClip-11-500x202.png 500w" sizes="(max-width: 950px) 100vw, 950px" />](http://bim42.com/wp-content/uploads/2014/11/ScreenClip-11.png)

LazJS also provide a set of already existing scripts for inspiration.

Last but not least, LazJS provides functions for exporting and importing data to Excel. These functions are very easy to use, and can replace any plug-in dedicated to exporting and importing data from Excel.

Even if I will keep my habit with C#, the LazJS plug-in seems quite powerful, and far more easy to use than the Revit macro editor, since you don&#8217;t have to handle all the tedious document retrieval and the transaction handling.

The only problem I have to report is an error when I attempt to debug a Revit macro in SharpDevelop after installing LazJS. It is kind of annoying, but I am sure this problem will be addressed when they launch their final version.