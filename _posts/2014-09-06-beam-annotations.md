---
id: 556
title: Beam Annotations
date: 2014-09-06T08:00:11+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=556
permalink: /2014/09/beam-annotations/
categories:
  - Revit
tags:
  - Autodesk
  - BIM Manager
  - Documentation
  - Revit
  - Software
  - Tips
---
An article from [Line Shape Space](http://lineshapespace.com/ "Line Shape Space") drive me to the Beam Annotation tools, and the various possibilities to automatically tag a set of beams.
  
The first idea when having to annotate a set of element is the Tag All function, quite efficient, but limited only to a tag by category. Furthermore, this function does not have the possibilities to add different tags on the same object.

![<img class="aligncenter size-full wp-image-557" src="http://bim42.com/wp-content/uploads/2014/09/01_TagAll.png" alt="01_TagAll" width="424" height="463" srcset="https://bim42.com/wp-content/uploads/2014/09/01_TagAll.png 424w, https://bim42.com/wp-content/uploads/2014/09/01_TagAll-274x300.png 274w" sizes="(max-width: 424px) 100vw, 424px" />](http://bim42.com/wp-content/uploads/2014/09/01_TagAll.png)

To annotate efficiently a large set of beams, a specific tool exist, Beams Annotations. It functions pretty much like the Tag All command, but with more options.

![<img class="aligncenter size-full wp-image-558" src="http://bim42.com/wp-content/uploads/2014/09/02_BeamAnnotations.png" alt="02_BeamAnnotations" width="857" height="623" srcset="https://bim42.com/wp-content/uploads/2014/09/02_BeamAnnotations.png 857w, https://bim42.com/wp-content/uploads/2014/09/02_BeamAnnotations-300x218.png 300w, https://bim42.com/wp-content/uploads/2014/09/02_BeamAnnotations-412x300.png 412w" sizes="(max-width: 857px) 100vw, 857px" />](http://bim42.com/wp-content/uploads/2014/09/02_BeamAnnotations.png)

You start by selecting the set of beams you want to annotate (All beam or only selected one), and if you want to include linked models elements.
  
Things become quite interesting with the other part of the windows, which display a schematic beam with six slots:

![<img class="aligncenter size-full wp-image-559" src="http://bim42.com/wp-content/uploads/2014/09/03_AnnotationLocation.png" alt="03_AnnotationLocation" width="821" height="287" srcset="https://bim42.com/wp-content/uploads/2014/09/03_AnnotationLocation.png 821w, https://bim42.com/wp-content/uploads/2014/09/03_AnnotationLocation-300x104.png 300w, https://bim42.com/wp-content/uploads/2014/09/03_AnnotationLocation-500x174.png 500w" sizes="(max-width: 821px) 100vw, 821px" />](http://bim42.com/wp-content/uploads/2014/09/03_AnnotationLocation.png)

This second part allow us to describe where we want to place Structural Framing tags or Spot Elevation on our beam.

Here the possibilities are quite extensive. On every six position of each beam (start, middle, and end, on each side), you can select different options to place a Structural Framing Tag or an Spot Elevation to display top and/or bottom elevation for the beam:

![<img class="aligncenter size-full wp-image-560" src="http://bim42.com/wp-content/uploads/2014/09/04_AnnotationType.png" alt="04_AnnotationType" width="335" height="455" srcset="https://bim42.com/wp-content/uploads/2014/09/04_AnnotationType.png 335w, https://bim42.com/wp-content/uploads/2014/09/04_AnnotationType-220x300.png 220w" sizes="(max-width: 335px) 100vw, 335px" />](http://bim42.com/wp-content/uploads/2014/09/04_AnnotationType.png)

To showcase this feature, I create a set of beam, distributed on the same plane:

![<img class="aligncenter size-full wp-image-561" src="http://bim42.com/wp-content/uploads/2014/09/05_PlaneBeams.png" alt="05_PlaneBeams" width="800" height="256" srcset="https://bim42.com/wp-content/uploads/2014/09/05_PlaneBeams.png 800w, https://bim42.com/wp-content/uploads/2014/09/05_PlaneBeams-300x96.png 300w, https://bim42.com/wp-content/uploads/2014/09/05_PlaneBeams-500x160.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/05_PlaneBeams.png)

In just a few click, I place a tag for every beam along with a nice Spot Elevation displaying the bottom elevation of the beam.

![<img class="aligncenter size-full wp-image-562" src="http://bim42.com/wp-content/uploads/2014/09/06_planeTags.png" alt="06_planeTags" width="969" height="435" srcset="https://bim42.com/wp-content/uploads/2014/09/06_planeTags.png 969w, https://bim42.com/wp-content/uploads/2014/09/06_planeTags-300x134.png 300w, https://bim42.com/wp-content/uploads/2014/09/06_planeTags-500x224.png 500w" sizes="(max-width: 969px) 100vw, 969px" />](http://bim42.com/wp-content/uploads/2014/09/06_planeTags.png)

This tool become extremely powerful when dealing with slopped beams. To showcase this feature, I create a set of beams aligned along a complex surface. To create quickly this kind of beam system, I use Grasshopper with the Hummingbird plug-in. I describe the complete procedure in [one of my older post](http://bim42.com/2012/09/parametric-modeling-in-revit/ "Parametric modeling in Revit").

![<img class="aligncenter size-full wp-image-563" src="http://bim42.com/wp-content/uploads/2014/09/07_ComplexeBeams.png" alt="07_ComplexeBeams" width="819" height="305" srcset="https://bim42.com/wp-content/uploads/2014/09/07_ComplexeBeams.png 819w, https://bim42.com/wp-content/uploads/2014/09/07_ComplexeBeams-300x111.png 300w, https://bim42.com/wp-content/uploads/2014/09/07_ComplexeBeams-500x186.png 500w" sizes="(max-width: 819px) 100vw, 819px" />](http://bim42.com/wp-content/uploads/2014/09/07_ComplexeBeams.png)

These beams are displayed as a grid in a plan view:

![<img class="aligncenter size-full wp-image-564" src="http://bim42.com/wp-content/uploads/2014/09/08_ComplexeBeamsPlane.png" alt="08_ComplexeBeamsPlane" width="519" height="512" srcset="https://bim42.com/wp-content/uploads/2014/09/08_ComplexeBeamsPlane.png 519w, https://bim42.com/wp-content/uploads/2014/09/08_ComplexeBeamsPlane-300x295.png 300w, https://bim42.com/wp-content/uploads/2014/09/08_ComplexeBeamsPlane-304x300.png 304w" sizes="(max-width: 519px) 100vw, 519px" />](http://bim42.com/wp-content/uploads/2014/09/08_ComplexeBeamsPlane.png)

I select the Beam Annotation tool, and add a Spot Elevation at the stating and the ending point of sloped beams, along with a Structural Framing Tag on the middle.

![<img class="aligncenter size-full wp-image-565" src="http://bim42.com/wp-content/uploads/2014/09/09_ComplexeBeamsAnnotationLocation.png" alt="09_ComplexeBeamsAnnotationLocation" width="823" height="284" srcset="https://bim42.com/wp-content/uploads/2014/09/09_ComplexeBeamsAnnotationLocation.png 823w, https://bim42.com/wp-content/uploads/2014/09/09_ComplexeBeamsAnnotationLocation-300x103.png 300w, https://bim42.com/wp-content/uploads/2014/09/09_ComplexeBeamsAnnotationLocation-500x172.png 500w" sizes="(max-width: 823px) 100vw, 823px" />](http://bim42.com/wp-content/uploads/2014/09/09_ComplexeBeamsAnnotationLocation.png)

After running the command, Revit add a Structural Framing Tag and two Spot Elevation on every beams in my view:

![<img class="aligncenter size-full wp-image-566" src="http://bim42.com/wp-content/uploads/2014/09/10_ComplexeBeamsAnnotated.png" alt="10_ComplexeBeamsAnnotated" width="544" height="516" srcset="https://bim42.com/wp-content/uploads/2014/09/10_ComplexeBeamsAnnotated.png 544w, https://bim42.com/wp-content/uploads/2014/09/10_ComplexeBeamsAnnotated-300x284.png 300w, https://bim42.com/wp-content/uploads/2014/09/10_ComplexeBeamsAnnotated-316x300.png 316w" sizes="(max-width: 544px) 100vw, 544px" />](http://bim42.com/wp-content/uploads/2014/09/10_ComplexeBeamsAnnotated.png)

These annotations place themselves nicely along the beam, and a few adjustments with the setting adjust them perfectly on the view:

![<img class="aligncenter size-full wp-image-567" src="http://bim42.com/wp-content/uploads/2014/09/11_ComplexeBeamsAnnotatedDetail.png" alt="11_ComplexeBeamsAnnotatedDetail" width="557" height="517" srcset="https://bim42.com/wp-content/uploads/2014/09/11_ComplexeBeamsAnnotatedDetail.png 557w, https://bim42.com/wp-content/uploads/2014/09/11_ComplexeBeamsAnnotatedDetail-300x278.png 300w, https://bim42.com/wp-content/uploads/2014/09/11_ComplexeBeamsAnnotatedDetail-323x300.png 323w" sizes="(max-width: 557px) 100vw, 557px" />](http://bim42.com/wp-content/uploads/2014/09/11_ComplexeBeamsAnnotatedDetail.png)