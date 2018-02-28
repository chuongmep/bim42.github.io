---
id: 1148
title: Building a Forge Web Viewer
date: 2017-03-11T09:10:00+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1148
permalink: /2017/03/building-a-forge-web-viewer/
categories:
  - Autodesk
tags:
  - .NET
  - Autodesk
  - Visualization
  - Web
---
Web-based &#8220;BIM&#8221; solutions are the last big trend, and Autodesk is among the most advanced player in this area with their API offering called Forge.

[Autodesk Forge](https://forge.autodesk.com/) is a product from Autodesk that don't come with a user interface. Instead, it is designed to be used through other software, and especially web-based solutions. Autodesk Forge is also the technology behind most of the web-based product of Autodesk, like [BIM 360 Team](https://team.bim360.com/), [Docs](https://bim360.autodesk.com/docs) or the [A360 Online File Viewer](https://a360.autodesk.com/viewer/).

The community around these products is growing, and new resources and samples are published on an almost daily basis.

Among them, [Augusto Gonzales](https://forge.autodesk.com/author/augusto-goncalves) recently wrote a [comprehensive tutorial](https://forge.autodesk.com/blog/forge-aspnet-zero-hero-30-minutes) to build a small web viewer using Autodesk Forge and ASP.NET. Being more of a .NET programmer, I took on this opportunity to learn more about this new product and build my own web-based Forge viewer.

I start by creating an ASP.NET Core MVC Web Application with this [tutorial](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-mvc-app/). ASP.NET Core being a web framework developed by Microsoft, you can use your C# skills to &#8220;easily&#8221; build web application.

I follow the detailed explanations from Augusto Gonzales to send my model to the Autodesk server for conversion, get an GUID back and use it to display my model in the Forge viewer. The explication on the blog are straightforward, and I won't delve into it. I just had to made some few changes since I am using a different version of the ASP.NET Core framework.

Using technologies from Microsoft, it is easy to publish my application on Azure, the Microsoft cloud hosting solution.

I called the end-result Termite, and it is available [here](http://termiteviewer.azurewebsites.net/).

<div id="attachment_1149" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/03/The-Termite-Web-Viewer.png"><img class="size-large wp-image-1149" src="http://bim42.com/wp-content/uploads/2017/03/The-Termite-Web-Viewer-1024x537.png" alt="" width="584" height="306" srcset="https://bim42.com/wp-content/uploads/2017/03/The-Termite-Web-Viewer-1024x537.png 1024w, https://bim42.com/wp-content/uploads/2017/03/The-Termite-Web-Viewer-300x157.png 300w, https://bim42.com/wp-content/uploads/2017/03/The-Termite-Web-Viewer-768x403.png 768w, https://bim42.com/wp-content/uploads/2017/03/The-Termite-Web-Viewer-500x262.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    The Termite Web Viewer
  </p>
</div>

By default, you see a model of my neighborhood from [my last post](http://bim42.com/2017/02/modeling-a-neighborhood-with-flux-site-extractor-gis-data-and-revit/), but you can also upload your own files. A word of caution, uploading and translating a large model can take quite some time, do not close the windows until your model is displayed on the screen.

I also add some features to the viewer. You can lock the rotation of the view by clicking on the lock icon. I also put in place a very basic section tool. To use the section, click on &#8220;Add a section&#8221; and select a face in the model to create your section.

<div id="attachment_1150" style="max-width: 160px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2017/03/Viewer-Extensions.png"><img class="wp-image-1150 size-thumbnail" src="http://bim42.com/wp-content/uploads/2017/03/Viewer-Extensions-150x150.png" alt="" width="150" height="150" /></a>
  
  <p class="wp-caption-text">
    Viewer Extensions
  </p>
</div>

These features are built as extension of the Autodesk Forge Viewer, are written in JavaScript and run in the browser of the end user.

The source code is available on [GitHub](https://github.com/simonmoreau/Termite). Seasoned web developer will probably find a lot to correct in my application, but I hope to improve with practice

I still have a lot to learn in this area, so you might expect some other web app in the next few weeks.