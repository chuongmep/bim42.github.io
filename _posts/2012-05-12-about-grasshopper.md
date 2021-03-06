---
id: 47
title: About Grasshopper
date: 2012-05-12T16:37:54+00:00
author: Simon Moreau
layout: post
guid: http://bim42.wordpress.com/?p=47
permalink: /2012/05/about-grasshopper/
categories:
  - Grasshopper
image: /assets/2012/05/intrograsshopper13.jpg
tags:
  - Grasshopper
  - Rhino
---
Did you ever try using Rhino? I know, I know, it's not a BIM software, it's just able to make pretty 3D drawings and nice pictures. But, as I have already said, nice pictures are still the best way to sell the BIM, and Rhino is actually a great software.

Apart from its capacities to design every shape you can imagine and its user friendly interface, Rhino come with a lot of plugin which make it really powerful.

Among these plugins, my favorite is Grasshopper. It's a graphical interface for designing parametric shapes in Rhino. In other word, instead of simply drawing what you imagine, you explain to Grasshopper what you're imagining, and it designs it for you.

As an illustration, here is the interface of Grasshopper, alongside with Rhino. Pretty, isn't it? The red surface in Rhino is the visualization of what we are designing in Grasshopper by wiring these little boxes together.

![intrograsshopper13]({{ "/assets/2012/05/intrograsshopper13.jpg" | absolute_url }})

As an example, we can start by generating twenty points randomly:

![intrograsshopper2_c]({{ "/assets/2012/05/intrograsshopper2_c.jpg" | absolute_url }})

Then we use them to draw twenty circles:

![intrograsshopper3_c]({{ "/assets/2012/05/intrograsshopper3_c.jpg" | absolute_url }})

And finally, we extrude each circle to create cylinders:

![intrograsshopper4_c]({{ "/assets/2012/05/intrograsshopper4_c.jpg" | absolute_url }})

And the best part is that we can still edit anything you want.

If you want fewer cylinders, just change the number of origin points:

![intrograsshopper5_c]({{ "/assets/2012/05/intrograsshopper5_c.jpg" | absolute_url }})

Or change the circle’s radius:

![intrograsshopper6_c]({{ "/assets/2012/05/intrograsshopper6_c.jpg" | absolute_url }})

The possibilities are almost endless, and, shame on me, I start to think that this little plugin can even be more powerful than the almighty CATIA. At least, it's far less expensive, since it came freely with a license for Rhino.

You can find a lot of help on the [Grasshopper forum](http://www.grasshopper3d.com/), and a beginners Guide [here](http://www.liftarchitects.com/journal/2009/3/25/the-grasshopper-primer-second-edition.html). I’m also very fond of the [Grasshopper Learning Material](http://www.schwartz.arch.ethz.ch/Vorlesungen/ParamTE/Dokumente/GrasshopperWorkspace.pdf?lan=en?dianr=14) made by [Woo Jae Sung](http://woojsung.com/)

Grasshopper has its own plugins and developing interface, which make it even more useful. I will probably talk again about these plugins, some of them has become a full part of our BIM workflow.