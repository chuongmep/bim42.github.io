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


  <a href="http://bim42.com/wp-content/uploads/2016/12/door.png"><img class="wp-image-1101 size-large" src="http://bim42.com/wp-content/uploads/2016/12/door-1024x472.png" alt="Door Type URL parameter" width="584" height="269" srcset="https://bim42.com/wp-content/uploads/2016/12/door.png 1024w, https://bim42.com/wp-content/uploads/2016/12/door-300x138.png 300w, https://bim42.com/wp-content/uploads/2016/12/door-768x354.png 768w, https://bim42.com/wp-content/uploads/2016/12/door-500x230.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Door Type URL parameter
  </p>


As you can see, I type in a relative path to my technical documentation, this allows me to move around the entire "As-built documentation" folder (models and technical sheets in PDF) without breaking the links. I end up with a pretty simple folder structure, with a model at its root, and the technical sheets nicely ordered in one folder per category.


  <a href="http://bim42.com/wp-content/uploads/2016/12/folderstructure.png"><img class="wp-image-1103 size-full" src="http://bim42.com/wp-content/uploads/2016/12/folderstructure.png" alt="The folder structure" width="816" height="366" srcset="https://bim42.com/wp-content/uploads/2016/12/folderstructure.png 816w, https://bim42.com/wp-content/uploads/2016/12/folderstructure-300x135.png 300w, https://bim42.com/wp-content/uploads/2016/12/folderstructure-768x344.png 768w, https://bim42.com/wp-content/uploads/2016/12/folderstructure-500x224.png 500w" sizes="(max-width: 816px) 100vw, 816px" /></a>
  
  <p class="wp-caption-text">
    The folder structure
  </p>


If you click on the small "... " button in Revit, your linked technical document will immediately open in the associate viewer, here, Acrobat Reader.


  <a href="http://bim42.com/wp-content/uploads/2016/12/openTechnicalSheet.png"><img class="size-large wp-image-1107" src="http://bim42.com/wp-content/uploads/2016/12/openTechnicalSheet-1024x452.png" alt="How to open the linked technical sheet" width="584" height="258" srcset="https://bim42.com/wp-content/uploads/2016/12/openTechnicalSheet.png 1024w, https://bim42.com/wp-content/uploads/2016/12/openTechnicalSheet-300x132.png 300w, https://bim42.com/wp-content/uploads/2016/12/openTechnicalSheet-768x339.png 768w, https://bim42.com/wp-content/uploads/2016/12/openTechnicalSheet-500x221.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    How to open the linked technical sheet
  </p>


## Adding a link without Revit

Selecting equipment and material is generally done through spreadsheets or building economy software, and by people who could not be proficient with Revit. Therefore, I have searched for solution to do it outside Revit.
  
The new Flux Scheduler is an application based on Flux, which allows us to create online schedules from data uploaded through the Revit Flux plugin.


  <a href="http://bim42.com/wp-content/uploads/2016/12/fluxScheduler.png"><img class="size-large wp-image-1102" src="http://bim42.com/wp-content/uploads/2016/12/fluxScheduler-1024x493.png" alt="The Flux Scheduler" width="584" height="281" srcset="https://bim42.com/wp-content/uploads/2016/12/fluxScheduler-1024x493.png 1024w, https://bim42.com/wp-content/uploads/2016/12/fluxScheduler-300x145.png 300w, https://bim42.com/wp-content/uploads/2016/12/fluxScheduler-768x370.png 768w, https://bim42.com/wp-content/uploads/2016/12/fluxScheduler-500x241.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    The Flux Scheduler
  </p>


By using this Flux Scheduler, I could upload my doors on Flux, create a door schedule directly on Flux, use Excel to add the URL link, and upload back these values in Revit


  <a href="http://bim42.com/wp-content/uploads/2016/12/InExcel.png"><img class="size-large wp-image-1105" src="http://bim42.com/wp-content/uploads/2016/12/InExcel-1024x475.png" alt="Type the URL in Excel before uploading them in Revit" width="584" height="271" srcset="https://bim42.com/wp-content/uploads/2016/12/InExcel-1024x475.png 1024w, https://bim42.com/wp-content/uploads/2016/12/InExcel-300x139.png 300w, https://bim42.com/wp-content/uploads/2016/12/InExcel-768x356.png 768w, https://bim42.com/wp-content/uploads/2016/12/InExcel-500x232.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Type the URL in Excel before uploading them in Revit
  </p>


## Delivering a Navisworks model

Once exported to Navisworks, the "Link" button will display a small link button on every linked object, which open the linked technical sheet.


  <a href="http://bim42.com/wp-content/uploads/2016/12/linkInNavis.png"><img class="size-large wp-image-1106" src="http://bim42.com/wp-content/uploads/2016/12/linkInNavis-1024x608.png" alt="The link in Navisworks" width="584" height="347" srcset="https://bim42.com/wp-content/uploads/2016/12/linkInNavis.png 1024w, https://bim42.com/wp-content/uploads/2016/12/linkInNavis-300x178.png 300w, https://bim42.com/wp-content/uploads/2016/12/linkInNavis-768x456.png 768w, https://bim42.com/wp-content/uploads/2016/12/linkInNavis-500x297.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    The link in Navisworks
  </p>


However, you must keep your Navisworks model in the same location in your "As-Build Documentation" folder structure as your initial Revit model to keep the relative links functional. In our case, we end up with the following folder structure:


  <a href="http://bim42.com/wp-content/uploads/2016/12/folderstructureNavis.png"><img class="size-full wp-image-1104" src="http://bim42.com/wp-content/uploads/2016/12/folderstructureNavis.png" alt="The folder structure with a Navisworks model" width="816" height="401" srcset="https://bim42.com/wp-content/uploads/2016/12/folderstructureNavis.png 816w, https://bim42.com/wp-content/uploads/2016/12/folderstructureNavis-300x147.png 300w, https://bim42.com/wp-content/uploads/2016/12/folderstructureNavis-768x377.png 768w, https://bim42.com/wp-content/uploads/2016/12/folderstructureNavis-500x246.png 500w" sizes="(max-width: 816px) 100vw, 816px" /></a>
  
  <p class="wp-caption-text">
    The folder structure with a Navisworks model
  </p>


## Delivering an IFC model

If you export this Revit model to IFC, and open it in Solibri Model Viewer, you can display the link, but not click on it. However, by writing a "\" before the link in Revit, Solibri Model Viewer recognize it as link and you can open the technical sheet with a click. This could obviously become problematic in Revit, since when you add this "\", Revit doesn't recognize the link anymore.


  <a href="http://bim42.com/wp-content/uploads/2016/12/solibri_after.png"><img class="size-large wp-image-1108" src="http://bim42.com/wp-content/uploads/2016/12/solibri_after-1024x564.png" alt="The clickable link in Solibri" width="584" height="322" srcset="https://bim42.com/wp-content/uploads/2016/12/solibri_after-1024x564.png 1024w, https://bim42.com/wp-content/uploads/2016/12/solibri_after-300x165.png 300w, https://bim42.com/wp-content/uploads/2016/12/solibri_after-768x423.png 768w, https://bim42.com/wp-content/uploads/2016/12/solibri_after-500x275.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    The clickable link in Solibri
  </p>


Tekla BIMSight, on the other hand, couldn’t recognized any of those links as a clickable item.

As you can see, they are many ways to link documents to a model and retrieve them in a viewer, and a few things could go wrong along the way. So, before starting anything, I would recommend to make sure you can link or embedded documents in your deliverables and structure these deliverables accordingly.