---
id: 88
title: Industry Foundation Classes
date: 2012-06-04T20:54:48+00:00
author: Simon Moreau
layout: post
guid: http://bim42.wordpress.com/?p=88
permalink: /2012/06/industry-foundation-classes/
publicize_results:
  - 'a:2:{s:7:"twitter";a:1:{i:578219192;a:2:{s:7:"user_id";s:5:"bim42";s:7:"post_id";s:18:"209750099994214401";}}s:2:"fb";a:1:{i:589116337;a:2:{s:7:"user_id";s:9:"589116337";s:7:"post_id";s:17:"10150855159261338";}}}'
categories:
  - General BIM
  - IFC
image: /assets/bim42_header.jpg
tags:
  - General
  - IFC
  - industry foundation classes
---
Anyone who has worked in the BIM field may have eared something about Industry Foundation Classes. Yes, you know, this little logo... 

![ifclogo](/assets/2012/06/ifclogo.jpg)

Generally, it appears when we try to export a building model from proprietary software to another. The IFC exchange format allows us to convert files and, with some luck, open them the other software.

But what really is this IFC file format, and why everybody talk about it ?

Developed by [Building Smart](http://buildingsmart.com/), a non-profit association of architects, civil engineers and IT specialists, IFC is a data model specifically designed for building information modeling.

In other terms, it's a series of definitions, explaining how describe any building element in order to make it comprehensible by a computer. But while each BIM software relies upon its own very private data model to define a building, the IFC data model is open, and freely accessible by anyone [here](http://www.buildingsmart-tech.org/ifc/IFC2x4/rc2/html/index.htm).

These definitions create a language readable by a computer, and written as a text file. This file is even readable by human being, and look more or less like this:

{% highlight text %}
#66= IFCCARTESIANPOINT((-17261.0669833266,3274.73863321424,0.));
#68= IFCAXIS2PLACEMENT3D(#66,$,$);
#69= IFCLOCALPLACEMENT(#59,#68);
#70= IFCCARTESIANPOINT((9430.2775637732,0.));
#72= IFCPOLYLINE((#5,#70));
#74= IFCSHAPEREPRESENTATION(#43,'Axis','Curve2D',(#72));
#76= IFCCARTESIANPOINT((9430.2775637732,-100.));
{% endhighlight %}

It's not very convenient, but with some pain, we can find a wall here,

{% highlight text %}
#209= IFCWALLSTANDARDCASE('0EiAvIo0LBOBfvSD8E4HST',#52,'Basic Wall',$,’200 mm’ ,#181,#207,'177171');
{% endhighlight %}

create by an extrusion like that,

{% highlight text %}
#92= IFCEXTRUDEDAREASOLID(#90,#91,#15,8000.);
{% endhighlight %}

and place at the point define like this:

{% highlight text %}
#76= IFCCARTESIANPOINT((9430.2775637732,-100.));
{% endhighlight %}

I have worked some times in order to understand this language, and if I'm still not speaking IFC fluently, I was able to improve myself a little. You will find the result of my work [here](http://www.scribd.com/doc/95909096/Industry-Foundation-Classes).

There is plenty of IFC's approved software, but if everyone is compliant, some are more compliant than other. For example, Revit was well known for its really poor implementation, but I have heard that Autodesk have made great improvement in the 2013 version, I still have to look at it.

For my part, the best implementation I have ever be able to test is the plugin for Grasshopper made by Jon Mirtschin called [Geometry Gym](http://geometrygym.blogspot.fr/). Fully compatible with the latest version of IFC (IFC2x Edition 4 Release Candidate 2), this plug in transform Rhino in a full scale BIM software. This plugin deserve at least a whole article, so I will came back to it.

The IFC model is still in the development part, and is currently in the process of becoming the official International Standard ISO 16739.

If it's not the leading format in the BIM business, the IFC format is a really interesting attempt to create an open exchange standard, and some software like Solibri Model Checker have understood it well enough to use IFC as the only input models format.