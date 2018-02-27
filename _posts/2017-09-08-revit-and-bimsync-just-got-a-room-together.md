---
id: 1217
title: Revit and bimsync Just Got a Room Together!
date: 2017-09-08T18:21:04+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1217
permalink: /2017/09/revit-and-bimsync-just-got-a-room-together/
categories:
  - Revit
tags:
  - bimsync
  - IFC
  - Revit
  - Software
---
This is no mystery that I am [a big fan of bimsync](https://bim42.com/2016/11/why-i-am-now-a-bimsync-fanboy/). But the lack of integration with Revit make things a bit too time consuming than it should be. To start solving this issue, I created a small Revit plugin to upload your model to bimsync in a single click.

You must first log into your bimsync account. After clicking on login, a browser session will open, and bimsync will ask for your credentials and if you want to allow the Revit plugin to be connected to your account. This will grant the plugin access rights to your bimsync account.

<div id="attachment_1219" style="max-width: 1752px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/09/authorize.gif"><img class="wp-image-1219 size-full" src="https://bim42.com/wp-content/uploads/2017/09/authorize.gif" alt="Login into your bimsync account" width="1742" height="1210" /></a>
  
  <p class="wp-caption-text">
    Login into your bimsync account
  </p>
</div>

Once connected, your credential will be safely stored on your computer so you won&#8217;t have to login the next time you open Revit.

You can now upload model to your bimsync account. Select &#8220;Upload&#8221;, select your bimsync project and model, type in the associated comment, select the IFC settings and click on &#8220;Upload&#8221;. After a while, depending on your file size, your Revit model will be uploaded to bimsync.

<div id="attachment_1221" style="max-width: 1752px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/09/upload.gif"><img class="wp-image-1221 size-full" src="https://bim42.com/wp-content/uploads/2017/09/upload.gif" alt="Upload your model to bimsync" width="1742" height="1210" /></a>
  
  <p class="wp-caption-text">
    Upload your model to bimsync
  </p>
</div>

The Setup drop down allows you to select the IFC Export configuration. You can choose a standard &#8220;bimsync&#8221; recommended setup, an existing setup, or create a new one.

After the first export, bimsync project and model ids will be saved in your Revit model, so you won&#8217;t have to select them again the next time. If you are curious, you can find these ids in your Project Information:

<div id="attachment_1223" style="max-width: 936px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/09/projectInfo.png"><img class="size-full wp-image-1223" src="https://bim42.com/wp-content/uploads/2017/09/projectInfo.png" alt="Your Project information" width="926" height="841" srcset="https://bim42.com/wp-content/uploads/2017/09/projectInfo.png 926w, https://bim42.com/wp-content/uploads/2017/09/projectInfo-300x272.png 300w, https://bim42.com/wp-content/uploads/2017/09/projectInfo-768x698.png 768w, https://bim42.com/wp-content/uploads/2017/09/projectInfo-330x300.png 330w" sizes="(max-width: 926px) 100vw, 926px" /></a>
  
  <p class="wp-caption-text">
    Your Project information
  </p>
</div>

To create your own IFC Export setup, you can use the usual IFC Setup Dialog. Select File -> Export -> IFC to open the &#8220;Export IFC&#8221; dialog. Select &#8220;Modify Setup&#8221; to open the &#8220;Modify Setup&#8221; windows, and click on &#8220;New&#8221; to create a new configuration. You can now set everything in this new configuration before selecting OK to close the &#8220;Modify Setup&#8221; windows. You can now safely close the IFC Export dialog without exporting anything, and open again the Upload dialog in the bimsync plugin. Your new configuration will be available in the drop-down.

<div id="attachment_1220" style="max-width: 1954px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/09/editSetup.gif"><img class="wp-image-1220 size-full" src="https://bim42.com/wp-content/uploads/2017/09/editSetup.gif" alt="Edit IFC Export Setup" width="1944" height="1210" /></a>
  
  <p class="wp-caption-text">
    Edit IFC Export Setup
  </p>
</div>
![Edit IFC Export Setup](https://bim42.com/wp-content/uploads/2017/09/editSetup.gif)

You can also go directly to your bimsync account from Revit by clicking on &#8220;Profile&#8221;. This is not very useful, but at least you will be a few clicks nearer to change your profile picture.

Under the hood, the system is quite simple. The plugin will look at your selected IFC Setup and use them to export your Revit model in an IFC file. This file is then zipped and uploaded to bimsync.

![<img class="aligncenter size-full wp-image-1218" src="https://bim42.com/wp-content/uploads/2017/09/Process.png" alt="" width="896" height="206" srcset="https://bim42.com/wp-content/uploads/2017/09/Process.png 896w, https://bim42.com/wp-content/uploads/2017/09/Process-300x69.png 300w, https://bim42.com/wp-content/uploads/2017/09/Process-768x177.png 768w, https://bim42.com/wp-content/uploads/2017/09/Process-500x115.png 500w" sizes="(max-width: 896px) 100vw, 896px" />](https://bim42.com/wp-content/uploads/2017/09/Process.png)

Between exporting to IFC, compressing the file and uploading it to bimsync, the entire process can be rather long. Depending on your model size, computing power and Internet bandwidth, the Upload command can take a few minutes to complete. I am thinking on using the Autodesk service Forge to convert Revit model to IFC online, freeing your computer from this tedious task.

You can already download the plugin on the [Autodesk App Store](https://apps.autodesk.com/RVT/en/Detail/Index?id=3115102317642496559&appLang=en&os=Win64).

As usual, the entire source code is [available on Github](https://github.com/simonmoreau/bimsync4Revit), feel free to use it on your own project. Don&#8217;t hesitate to report on any issue you might have with this plugin, there is always a lot of room for improvement.