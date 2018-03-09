---
id: 73
title: Justification planes for beam families
date: 2012-05-18T15:15:07+00:00
author: Simon Moreau
layout: post
guid: http://bim42.wordpress.com/?p=73
permalink: /2012/05/justification-planes-for-beam-families/
publicize_results:
  - 'a:2:{s:7:"twitter";a:1:{i:578219192;a:2:{s:7:"user_id";s:5:"bim42";s:7:"post_id";s:18:"203503994520346624";}}s:2:"fb";a:1:{i:589116337;a:2:{s:7:"user_id";s:9:"589116337";s:7:"post_id";s:17:"10150816506111338";}}}'
categories:
  - Revit
image: /assets/2012/05/referencesplanes.jpg
tags:
  - BIM Manager
  - Revit
  - Tips
---
I am still baffled in front of some functionality in Revit families.

One of these is the possibility to create our own justification axis for positioning a beam.

As an example, I design a specific beam, using the “Metric Structural Framing - Beams and Braces” family template.

I draw a little extrusion, and constrain its length. I want have my beam centered on the red dot, so I set the central plane as Reference: Center (Elevation)

![extrusion](/assets/2012/05/extrusion.jpg)

Then I load it into my project and I try different values for the z-direction justification:

![justification](/assets/2012/05/justification.jpg)

As you can see, my beam isn’t centered on the plane set as Reference: Center (Elevation), but keep only its _geometrical_ Top, Center and Bottom as references.

As a workaround, I found out that References Planes can overwrite these geometrical References, but only if they are place outside the geometry. So, I draw two reference planes, I set their References respectively as Top and Bottom, and I place then evenly around the Center Axis of my beam.

![referencesplanes](/assets/2012/05/referencesplanes.jpg)

Then, I load it back in project, and test again the z-direction justification of my beam:

![justification2](/assets/2012/05/justification2.jpg)

OK, it works!

I have also made a lot of trials and mistakes with the different possibilities of these Reference Planes, but I’m still unable to understand some of tricky parts of these functionalities.

And, just in case, if you have any clue where I can find some documentation, please let me know.