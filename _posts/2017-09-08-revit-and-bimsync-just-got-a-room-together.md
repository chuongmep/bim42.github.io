---
id: 1217
title: Revit and bimsync Just Got a Room Together!
date: 2017-09-08T18:21:04+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1217
permalink: /2017/09/revit-and-bimsync-just-got-a-room-together/
categories:
  - Revit
image: /assets/2017/09/authorize.gif
tags:
  - bimsync
  - IFC
  - Revit
  - Software
---
This is no mystery that I am [a big fan of bimsync](https://bim42.com/2016/11/why-i-am-now-a-bimsync-fanboy/). But the lack of integration with Revit make things a bit too time consuming than it should be. To start solving this issue, I created a small Revit plugin to upload your model to bimsync in a single click.

You must first log into your bimsync account. After clicking on login, a browser session will open, and bimsync will ask for your credentials and if you want to allow the Revit plugin to be connected to your account. This will grant the plugin access rights to your bimsync account.

![authorize]({{ "/assets/2017/09/authorize.gif" | absolute_url }})
Login into your bimsync account

Once connected, your credential will be safely stored on your computer so you won't have to login the next time you open Revit.

You can now upload model to your bimsync account. Select "Upload", select your bimsync project and model, type in the associated comment, select the IFC settings and click on "Upload". After a while, depending on your file size, your Revit model will be uploaded to bimsync.

![upload]({{ "/assets/2017/09/upload.gif" | absolute_url }})
Upload your model to bimsync

The Setup drop down allows you to select the IFC Export configuration. You can choose a standard "bimsync" recommended setup, an existing setup, or create a new one.

After the first export, bimsync project and model ids will be saved in your Revit model, so you won't have to select them again the next time. If you are curious, you can find these ids in your Project Information:

![projectInfo]({{ "/assets/2017/09/projectInfo.jpg" | absolute_url }})
Your Project information

To create your own IFC Export setup, you can use the usual IFC Setup Dialog. Select File -> Export -> IFC to open the "Export IFC" dialog. Select "Modify Setup" to open the "Modify Setup" windows, and click on "New" to create a new configuration. You can now set everything in this new configuration before selecting OK to close the "Modify Setup" windows. You can now safely close the IFC Export dialog without exporting anything, and open again the Upload dialog in the bimsync plugin. Your new configuration will be available in the drop-down.

![editSetup]({{ "/assets/2017/09/editSetup.gif" | absolute_url }})
Edit IFC Export Setup

You can also go directly to your bimsync account from Revit by clicking on "Profile". This is not very useful, but at least you will be a few clicks nearer to change your profile picture.

Under the hood, the system is quite simple. The plugin will look at your selected IFC Setup and use them to export your Revit model in an IFC file. This file is then zipped and uploaded to bimsync.

![Process]({{ "/assets/2017/09/Process.jpg" | absolute_url }})

Between exporting to IFC, compressing the file and uploading it to bimsync, the entire process can be rather long. Depending on your model size, computing power and Internet bandwidth, the Upload command can take a few minutes to complete. I am thinking on using the Autodesk service Forge to convert Revit model to IFC online, freeing your computer from this tedious task.

You can already download the plugin on the [Autodesk App Store](https://apps.autodesk.com/RVT/en/Detail/Index?id=3115102317642496559&appLang=en&os=Win64).

As usual, the entire source code is [available on Github](https://github.com/simonmoreau/bimsync4Revit), feel free to use it on your own project. Don't hesitate to report on any issue you might have with this plugin, there is always a lot of room for improvement.