---
id: 1040
title: Bridge design
date: 2016-06-04T11:20:21+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1040
permalink: /2016/06/bridge-design/
categories:
  - Revit
tags:
  - Autodesk
  - Civil 3D
  - Civil Engineering
  - Dynamo
  - Grasshopper
  - Revit
---
One of my colleague is currently working on bridge design with Revit. I have to admit, my first reaction was more like &#8220;Revit is not fit for bridge modeling, period&#8221;. But after some thought, I found Revit to be a pretty interesting solution to design these kind of infrastructures.

The main issue is that even a simple bridge has a rather complex geometry, with a double-curved alignment and potentially a variable cross section. There is various possibilities to create this kind of geometry in Revit, I will present only one of them here.

This entire article is mostly inspired by the work of [Matthias Stark](https://de.linkedin.com/in/matthiasstark/fr), from Autodesk, and its great [AU 2015 class](http://au.autodesk.com/au-online/classes-on-demand/class-catalog/2015/revit-for-construction/ci11198#chapter=0).

# The alignment

The first issue we ran into while designing our bridge is the inability for Revit to create a real double-curved, 3D curve.
  
This is why I create my alignment in Rhino, and use Grasshopper to create a list of X, Y and Z coordinates that define points along my alignment. Another solution is presented by Matthias Stark in his class, where he is using AutoCAD Civil 3D to export the coordinates of the alignment in an Excel spreadsheet.

Once I have all my coordinates in an Excel file, I use a simple definition in Dynamo to create a series of reference points in a Mass family, and use these points to create a curve representing my alignment.

![<img class="aligncenter size-large wp-image-1050" src="http://bim42.com/wp-content/uploads/2016/06/Alignement-2-716x1024.png" alt="Alignement" width="584" height="835" srcset="https://bim42.com/wp-content/uploads/2016/06/Alignement-2-716x1024.png 716w, https://bim42.com/wp-content/uploads/2016/06/Alignement-2-210x300.png 210w, https://bim42.com/wp-content/uploads/2016/06/Alignement-2-768x1098.png 768w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/Alignement-2.png)

I also make sure that units in my Revit mass family are consistent with the unit of my alignment coordinates points.

# The cross section

To create the cross section shape of my bridge, I use an adaptive family with a single adaptive point, which will be placed on our alignment.

The keep our cross section properly aligned with our bridge axe, I use the &#8220;Orient to&#8221; parameter of the adaptive point. By setting it to &#8220;Global (z) the Host (xy)&#8221;, I make sure than the X and Y axes (Red and Green) will follow my alignment, while the Z axe will stay vertical.

![<img class="aligncenter size-large wp-image-1048" src="http://bim42.com/wp-content/uploads/2016/06/axes-1024x569.png" alt="axes" width="584" height="325" srcset="https://bim42.com/wp-content/uploads/2016/06/axes.png 1024w, https://bim42.com/wp-content/uploads/2016/06/axes-300x167.png 300w, https://bim42.com/wp-content/uploads/2016/06/axes-768x427.png 768w, https://bim42.com/wp-content/uploads/2016/06/axes-500x278.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/axes.png)I make a few try before getting it right, but I was finally able to properly align my adaptive component with the divided path. Since the X (Red) axis will be tangent to the alignment, I had to draw my cross section in the &#8220;Center (Left/Right)&#8221; plane of the adaptive family.

![<img class="aligncenter size-large wp-image-1046" src="http://bim42.com/wp-content/uploads/2016/06/adaptiveFamily-1024x578.png" alt="adaptiveFamily" width="584" height="330" srcset="https://bim42.com/wp-content/uploads/2016/06/adaptiveFamily-1024x578.png 1024w, https://bim42.com/wp-content/uploads/2016/06/adaptiveFamily-300x169.png 300w, https://bim42.com/wp-content/uploads/2016/06/adaptiveFamily-768x433.png 768w, https://bim42.com/wp-content/uploads/2016/06/adaptiveFamily-500x282.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/adaptiveFamily.png)

# Modeling

The rest of the modeling is pretty straightforward. After placing the first adaptive component on a divided path based on our alignment, just select Repeat to place one on every division point, then decompose the Repeat pattern and create a form.

![<img class="aligncenter size-large wp-image-1043" src="http://bim42.com/wp-content/uploads/2016/06/repeat-1024x540.png" alt="repeat" width="584" height="308" srcset="https://bim42.com/wp-content/uploads/2016/06/repeat-1024x540.png 1024w, https://bim42.com/wp-content/uploads/2016/06/repeat-300x158.png 300w, https://bim42.com/wp-content/uploads/2016/06/repeat-768x405.png 768w, https://bim42.com/wp-content/uploads/2016/06/repeat-500x263.png 500w, https://bim42.com/wp-content/uploads/2016/06/repeat.png 1374w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/repeat.png)

![<img class="aligncenter size-large wp-image-1042" src="http://bim42.com/wp-content/uploads/2016/06/form-1024x527.png" alt="form" width="584" height="301" srcset="https://bim42.com/wp-content/uploads/2016/06/form-1024x527.png 1024w, https://bim42.com/wp-content/uploads/2016/06/form-300x155.png 300w, https://bim42.com/wp-content/uploads/2016/06/form-768x396.png 768w, https://bim42.com/wp-content/uploads/2016/06/form-500x258.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/form.png)

To create the cavity inside the bridge deck, I use the same divided path to place two cavity profiles (right and left) and create two void forms to cut into the bridge deck.

![<img class="aligncenter size-large wp-image-1045" src="http://bim42.com/wp-content/uploads/2016/06/voidForms-1024x534.png" alt="voidForms" width="584" height="305" srcset="https://bim42.com/wp-content/uploads/2016/06/voidForms-1024x534.png 1024w, https://bim42.com/wp-content/uploads/2016/06/voidForms-300x156.png 300w, https://bim42.com/wp-content/uploads/2016/06/voidForms-768x400.png 768w, https://bim42.com/wp-content/uploads/2016/06/voidForms-500x261.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/voidForms.png)

# Section View

The main issue with this mass family is around dimensions. If you try to add dimensions directly on the Mass family in a section view, these dimensions will be anchored on the wrong point.

![<img class="aligncenter size-large wp-image-1041" src="http://bim42.com/wp-content/uploads/2016/06/firstSection-1024x518.png" alt="firstSection" width="584" height="295" srcset="https://bim42.com/wp-content/uploads/2016/06/firstSection-1024x518.png 1024w, https://bim42.com/wp-content/uploads/2016/06/firstSection-300x152.png 300w, https://bim42.com/wp-content/uploads/2016/06/firstSection-768x389.png 768w, https://bim42.com/wp-content/uploads/2016/06/firstSection-500x253.png 500w, https://bim42.com/wp-content/uploads/2016/06/firstSection.png 1292w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/firstSection.png)

To be able to create section view anyway, I am using the adaptive component loaded in the Mass family. I make it visible in the project and draw a detail line along one of them. This detail line allows me to draw a section view perfectly aligned with my adaptive component

![<img class="aligncenter size-large wp-image-1044" src="http://bim42.com/wp-content/uploads/2016/06/sectionView-1024x667.png" alt="sectionView" width="584" height="380" srcset="https://bim42.com/wp-content/uploads/2016/06/sectionView-1024x667.png 1024w, https://bim42.com/wp-content/uploads/2016/06/sectionView-300x195.png 300w, https://bim42.com/wp-content/uploads/2016/06/sectionView-768x500.png 768w, https://bim42.com/wp-content/uploads/2016/06/sectionView-461x300.png 461w, https://bim42.com/wp-content/uploads/2016/06/sectionView.png 1599w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/sectionView.png)

Since my section is perfectly aligned with my profile, it appears in the view and can be used as a reference for the dimensions. I temporary hide my mass family, place the necessary dimensions and show again the mass.

With this workaround, I was able to create a simple section view, with the proper dimensions.

![<img class="aligncenter size-large wp-image-1051" src="http://bim42.com/wp-content/uploads/2016/06/section-1024x421.png" alt="section" width="584" height="240" srcset="https://bim42.com/wp-content/uploads/2016/06/section-1024x421.png 1024w, https://bim42.com/wp-content/uploads/2016/06/section-300x123.png 300w, https://bim42.com/wp-content/uploads/2016/06/section-768x316.png 768w, https://bim42.com/wp-content/uploads/2016/06/section-500x206.png 500w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/06/section.png)

Matthias Stark also present in his class an entire detailing process using Dynamo, and that I still have to explore this part. But his approach to bridge modeling allows me to create a great first draft, and I will keep on digging this solution.