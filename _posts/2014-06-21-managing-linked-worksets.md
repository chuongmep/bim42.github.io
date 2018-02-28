---
id: 435
title: Managing linked worksets
date: 2014-06-21T10:00:42+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=435
permalink: /2014/06/managing-linked-worksets/
categories:
  - Revit
tags:
  - .NET
  - Autodesk
  - Automation
  - BIM Manager
  - Revit
---
A pretty powerful function in Revit is the ability to manage worksets in a linked Revit file.

![<img class="aligncenter size-full wp-image-443" src="http://bim42.com/wp-content/uploads/2014/06/LinkedFiles.png" alt="LinkedFiles" width="773" height="610" srcset="https://bim42.com/wp-content/uploads/2014/06/LinkedFiles.png 773w, https://bim42.com/wp-content/uploads/2014/06/LinkedFiles-300x236.png 300w, https://bim42.com/wp-content/uploads/2014/06/LinkedFiles-380x300.png 380w" sizes="(max-width: 773px) 100vw, 773px" />](http://bim42.com/wp-content/uploads/2014/06/LinkedFiles.png)

In the Manage Link window, selecting the Manage Worksets open a list of user worksets in the linked file. These linked worksets can be opened or closed through the same interface.

![<img class="aligncenter size-full wp-image-444" src="http://bim42.com/wp-content/uploads/2014/06/LinkedWorkset.png" alt="LinkedWorkset" width="648" height="458" srcset="https://bim42.com/wp-content/uploads/2014/06/LinkedWorkset.png 648w, https://bim42.com/wp-content/uploads/2014/06/LinkedWorkset-300x212.png 300w, https://bim42.com/wp-content/uploads/2014/06/LinkedWorkset-424x300.png 424w" sizes="(max-width: 648px) 100vw, 648px" />](http://bim42.com/wp-content/uploads/2014/06/LinkedWorkset.png)

It is a project setting, so elements in the closed workset will be hidden everywhere in our host model.

It allow us to load only the part of the linked project that really interesting us. For example, as a mechanical engineer, I generally don't need to display furniture from the architectural model. Closing the related workset can save me significant loading time.

The most common application of this feature is to hide linked grids and references planes.When new workset are created, every level and grid goes into the &#8220;Shared Levels and Grids&#8221; default workset. This behavior should not be changed, since it allows us to easily hide linked levels and grids in our current model.

<div id="attachment_442" style="max-width: 783px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2014/06/before.png"><img class="size-full wp-image-442" src="http://bim42.com/wp-content/uploads/2014/06/before.png" alt="Before closing linked &quot;Shared Levels and Grids&quot; workset " width="773" height="478" srcset="https://bim42.com/wp-content/uploads/2014/06/before.png 773w, https://bim42.com/wp-content/uploads/2014/06/before-300x185.png 300w, https://bim42.com/wp-content/uploads/2014/06/before-485x300.png 485w" sizes="(max-width: 773px) 100vw, 773px" /></a>
  
  <p class="wp-caption-text">
    Before closing linked &#8220;Shared Levels and Grids&#8221; workset
  </p>
</div>

<div id="attachment_441" style="max-width: 655px" class="wp-caption aligncenter">
  <a href="http://bim42.com/wp-content/uploads/2014/06/After.png"><img class="size-full wp-image-441" src="http://bim42.com/wp-content/uploads/2014/06/After.png" alt="Before closing linked &quot;Shared Levels and Grids&quot; workset" width="645" height="418" srcset="https://bim42.com/wp-content/uploads/2014/06/After.png 645w, https://bim42.com/wp-content/uploads/2014/06/After-300x194.png 300w, https://bim42.com/wp-content/uploads/2014/06/After-462x300.png 462w" sizes="(max-width: 645px) 100vw, 645px" /></a>
  
  <p class="wp-caption-text">
    After closing linked &#8220;Shared Levels and Grids&#8221; workset
  </p>
</div>

I also place reference planes and scope boxes in this workset, to be able to hide them as easily. But selecting all reference planes and scope boxes of a model to place them in the correct workset can a tedious business. To change this, I wrote a few line of code for set up every Scope Box, and Reference plane to the correct workset :

<pre class="brush: csharp; title: ; notranslate" title="">public void SetGridWorkset()
{
	Document doc = this.ActiveUIDocument.Document;

	//Select the shared grid workset
	IList&lt;Workset&gt; worksetList =
		new FilteredWorksetCollector(doc)
			.OfKind(WorksetKind.UserWorkset)
				.ToWorksets();
	int sharedGridWorksetId=0;

	foreach (Workset workset in worksetList) {
		if (workset.Name.Contains("Shared Levels and Grids"))
		{
			sharedGridWorksetId = workset.Id.IntegerValue;
		}
	}

	if( sharedGridWorksetId == 0 ) return;

	//Reference planes
	List&lt;Element&gt; elements =
		new FilteredElementCollector(doc)
			.OfCategory(BuiltInCategory.OST_CLines)
				.ToElements().ToList();
	//Scope box
	List&lt;Element&gt; scopeBoxes =
		new FilteredElementCollector(doc)
			.OfCategory(BuiltInCategory.OST_VolumeOfInterest)
				.ToElements().ToList();
	elements.AddRange(scopeBoxes);

	using (Transaction tx = new Transaction(doc)) {
		tx.Start("Change Workset");

		foreach (Element e in elements) {

			//Retrive workset parameter
			Parameter wsparam =
				e.get_Parameter(BuiltInParameter.ELEM_PARTITION_PARAM );
			if( wsparam == null ) continue;

			//set workset to Shared Levels and Grids
			wsparam.Set(sharedGridWorksetId);
		}

		tx.Commit();
	}
}
</pre>

This piece of code is inspired from the work of Jeremy Tamick, available [here](http://thebuildingcoder.typepad.com/blog/2013/01/change-element-workset.html), thanks to him.