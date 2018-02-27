---
id: 192
title: From Grasshopper to Tekla
date: 2012-08-19T19:23:30+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=192
permalink: /2012/08/from-grasshopper-to-tekla/
categories:
  - Grasshopper
tags:
  - Geometry Gym
  - Grasshopper
  - Steel Detailing
  - Tekla
---
I keep on trying the Grasshopper Plugin Geometry Gym, and one of our current projects made me search more extensively in the Tekla export module.

It presents itself as a set of tools to create beams, plates, bolts and welds. There is also a TeklaBakeStructure component to send our Grasshopper geometry to Tekla.

Creating beams is pretty easy, all you need is a BeamProfileProperty before, where you set all Tekla parameters of your expected beam. Then you just link your wireframe lines to the beam component.

![<img class="aligncenter size-full wp-image-193" title="Beam" src="http://bim42.com/wp-content/uploads/2012/08/beam.jpg" alt="" width="584" height="429" srcset="https://bim42.com/wp-content/uploads/2012/08/beam.jpg 1001w, https://bim42.com/wp-content/uploads/2012/08/beam-300x220.jpg 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/08/beam.jpg)

I struggled for a while to set the Insertion Point property in order to set the position of the beam axis before realizing that I only had to right-click on the parameter to set it. I finally extracted it to keep it visible.

The plate component is also quite simple, with a polyline as input and more or less the same set of property as for beams.

![<img class="aligncenter size-full wp-image-194" title="PlateBasic" src="http://bim42.com/wp-content/uploads/2012/08/platebasic.jpg" alt="" width="584" height="510" srcset="https://bim42.com/wp-content/uploads/2012/08/platebasic.jpg 750w, https://bim42.com/wp-content/uploads/2012/08/platebasic-300x262.jpg 300w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/08/platebasic.jpg)

To link two parts together, and so create a Tekla assembly, you have to create a group of bolts (or a weld), then assign it to the main part with the specific input, and add to the assembly all secondary parts you need. I am not sure if it is realistic to create assembly for a whole project directly in Grasshopper, but maybe I am missing some point here. My current project involves a lot of connexions, so I will keep on exploring these features.

![<img class="aligncenter size-full wp-image-196" title="Assembly" src="http://bim42.com/wp-content/uploads/2012/08/assembly1.jpg" alt="" width="584" height="489" srcset="https://bim42.com/wp-content/uploads/2012/08/assembly1.jpg 2857w, https://bim42.com/wp-content/uploads/2012/08/assembly1-300x251.jpg 300w, https://bim42.com/wp-content/uploads/2012/08/assembly1-1024x857.jpg 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/08/assembly1.jpg)

&nbsp;

To exploit a model imported in Rhino, Jon Mirchtin has developed two specific components call Reverse Engineer. You can use it to retrieve beams or plates properties from geometry. Here is an example of a plate recreated from a standard Rhino Closed PolySurface.

![<img class="aligncenter size-full wp-image-197" title="ReverseEngineering" src="http://bim42.com/wp-content/uploads/2012/08/reverseengineering.jpg" alt="" width="584" height="185" srcset="https://bim42.com/wp-content/uploads/2012/08/reverseengineering.jpg 1477w, https://bim42.com/wp-content/uploads/2012/08/reverseengineering-300x95.jpg 300w, https://bim42.com/wp-content/uploads/2012/08/reverseengineering-1024x325.jpg 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/08/reverseengineering.jpg)

Once all you profiles and other parts are created into Grasshopper, you can export them. Just run Tekla, start a new project, and click on the TeklaBakeStructure component on your Grasshopper canvas.

![<img class="aligncenter size-full wp-image-198" title="Bake" src="http://bim42.com/wp-content/uploads/2012/08/bake.jpg" alt="" width="196" height="66" />](http://bim42.com/wp-content/uploads/2012/08/bake.jpg)

Your model is now export in your Tekla project.

![<img class="aligncenter size-full wp-image-199" title="Tekla" src="http://bim42.com/wp-content/uploads/2012/08/tekla.jpg" alt="" width="584" height="353" srcset="https://bim42.com/wp-content/uploads/2012/08/tekla.jpg 1921w, https://bim42.com/wp-content/uploads/2012/08/tekla-300x181.jpg 300w, https://bim42.com/wp-content/uploads/2012/08/tekla-1024x619.jpg 1024w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2012/08/tekla.jpg)

This plug in fill one of the most lack in the Tekla functionalities, the ability to create complex shape quickly. With this module, it became pretty easy to adapt a lot of beam on a double-curved roof, and create them in Tekla.