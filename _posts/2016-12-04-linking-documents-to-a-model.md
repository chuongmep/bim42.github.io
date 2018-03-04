---
id: 1100
title: Linking documents to a model
date: 2016-12-04T18:52:33+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1100
permalink: /2016/12/linking-documents-to-a-model/
categories:
  - Coordination
tags:
  - Autodesk
  - Documentation
  - IFC
  - Navisworks
  - Revit
---
These days, there is a lot of ideas around using a building information model for facilities management. Among these ideas, a recurring theme is to integrate documents, mostly technical sheets, directly into the model.

Aside from the fact that I don't see how a model build to design, analyse, and coordinate a building could be use directly in facilities management, there is also some non-trivial technical problems to overcome to have any documents properly linked to your model, whether you are using Revit, Navisworks, or an IFC viewer.

Below is a list of these technical problems, and some though on how to solve them.

## Adding a link in Revit

Adding a link in Revit is fairly straightforward, you just have to use a "URL" parameter (shared or built in), and type in your link. Since a technical sheet is generally the same for every building element of a given type, it makes more sense to me to add it in a type parameter.

![Door](/assets/2016/12/door.png)
Door Type URL parameter

As you can see, I type in a relative path to my technical documentation, this allows me to move around the entire "As-built documentation" folder (models and technical sheets in PDF) without breaking the links. I end up with a pretty simple folder structure, with a model at its root, and the technical sheets nicely ordered in one folder per category.

![Folder Structure](/assets/2016/12/folderstructure.png)
The folder structure

If you click on the small "... " button in Revit, your linked technical document will immediately open in the associate viewer, here, Acrobat Reader.

![Open in Revit](/assets/2016/12/openTechnicalSheet.png)
How to open the linked technical sheet

## Adding a link without Revit

Selecting equipment and material is generally done through spreadsheets or building economy software, and by people who could not be proficient with Revit. Therefore, I have searched for solution to do it outside Revit.

The new Flux Scheduler is an application based on Flux, which allows us to create online schedules from data uploaded through the Revit Flux plugin.

![Flux Scheduler](/assets/2016/12/fluxScheduler.png)
The Flux Scheduler

By using this Flux Scheduler, I could upload my doors on Flux, create a door schedule directly on Flux, use Excel to add the URL link, and upload back these values in Revit:

![In Excel](/assets/2016/12/InExcel.png)
Type the URL in Excel before uploading them in Revit

## Delivering a Navisworks model

Once exported to Navisworks, the "Link" button will display a small link button on every linked object, which open the linked technical sheet.

![Navisworks](/assets/2016/12/linkInNavis.png)
The link in Navisworks

However, you must keep your Navisworks model in the same location in your "As-Build Documentation" folder structure as your initial Revit model to keep the relative links functional. In our case, we end up with the following folder structure:

![Folders in Navis](/assets/2016/12/folderstructureNavis.png)
The folder structure with a Navisworks model

## Delivering an IFC model

If you export this Revit model to IFC, and open it in Solibri Model Viewer, you can display the link, but not click on it. However, by writing a "\" before the link in Revit, Solibri Model Viewer recognize it as link and you can open the technical sheet with a click. This could obviously become problematic in Revit, since when you add this "\", Revit doesn't recognize the link anymore.

![Solibri](/assets/2016/12/solibri_after.png)
The clickable link in Solibri

Tekla BIMSight, on the other hand, couldn’t recognized any of those links as a clickable item.

As you can see, they are many ways to link documents to a model and retrieve them in a viewer, and a few things could go wrong along the way. So, before starting anything, I would recommend to make sure you can link or embedded documents in your deliverables and structure these deliverables accordingly.