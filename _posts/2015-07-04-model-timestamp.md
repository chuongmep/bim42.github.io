---
id: 891
title: Model Timestamp
date: 2015-07-04T11:35:39+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=891
permalink: /2015/07/model-timestamp/
categories:
  - Revit
tags:
  - .NET
  - Coordination
  - Plugin
  - Revit
  - Schedules
---
As we receive models from subcontractors or partners, we need to integrate them in a coordination model.

The coordination model files structure look like this.[<img class="aligncenter size-full wp-image-892" src="http://bim42.com/wp-content/uploads/2015/07/filestructure.jpg" alt="filestructure" width="1366" height="768" srcset="https://bim42.com/wp-content/uploads/2015/07/filestructure.jpg 1366w, https://bim42.com/wp-content/uploads/2015/07/filestructure-300x169.jpg 300w, https://bim42.com/wp-content/uploads/2015/07/filestructure-1024x576.jpg 1024w, https://bim42.com/wp-content/uploads/2015/07/filestructure-500x281.jpg 500w" sizes="(max-width: 1366px) 100vw, 1366px" />](http://bim42.com/wp-content/uploads/2015/07/filestructure.jpg)

In the coordination model, we use linked views and model specific overrides to fine tune model display. To keep these settings when a linked model is updated, we just override the previous liked file with its new version. This process implies to rename the file each time we receive a new version from a subcontractor. So when we receive a file named with a date or a version, we rename it along some quality control checks.

[<img class="aligncenter size-full wp-image-895" src="http://bim42.com/wp-content/uploads/2015/07/process.jpg" alt="process" width="1366" height="768" srcset="https://bim42.com/wp-content/uploads/2015/07/process.jpg 1366w, https://bim42.com/wp-content/uploads/2015/07/process-300x169.jpg 300w, https://bim42.com/wp-content/uploads/2015/07/process-1024x576.jpg 1024w, https://bim42.com/wp-content/uploads/2015/07/process-500x281.jpg 500w" sizes="(max-width: 1366px) 100vw, 1366px" />](http://bim42.com/wp-content/uploads/2015/07/process.jpg)

But we also have to follow which model version we are linking in our coordination model. Renaming files is great to keep the link alive, but we lost the original name in the process.

To keep track of the version of the linked file, I create some kind of timestamp on every object of a given model. This application writes version information on four shared parameters, common to every object.

Once in the coordination model, these shared parameters allows us to know from which version a given element came from.

[<img class="aligncenter size-full wp-image-893" src="http://bim42.com/wp-content/uploads/2015/07/IdentificationData.jpg" alt="IdentificationData" width="1565" height="596" srcset="https://bim42.com/wp-content/uploads/2015/07/IdentificationData.jpg 1565w, https://bim42.com/wp-content/uploads/2015/07/IdentificationData-300x114.jpg 300w, https://bim42.com/wp-content/uploads/2015/07/IdentificationData-1024x390.jpg 1024w, https://bim42.com/wp-content/uploads/2015/07/IdentificationData-500x190.jpg 500w" sizes="(max-width: 1565px) 100vw, 1565px" />](http://bim42.com/wp-content/uploads/2015/07/IdentificationData.jpg)

They can also be used to create filters to highlight the origin of each element in a view.

I also find some very interesting side effects. For example, I create a linked models schedule with a multi-category schedule displaying only the four shared parameters.

[<img class="aligncenter size-full wp-image-894" src="http://bim42.com/wp-content/uploads/2015/07/LinkedModelSchedules.jpg" alt="LinkedModelSchedules" width="768" height="212" srcset="https://bim42.com/wp-content/uploads/2015/07/LinkedModelSchedules.jpg 768w, https://bim42.com/wp-content/uploads/2015/07/LinkedModelSchedules-300x83.jpg 300w, https://bim42.com/wp-content/uploads/2015/07/LinkedModelSchedules-500x138.jpg 500w" sizes="(max-width: 768px) 100vw, 768px" />](http://bim42.com/wp-content/uploads/2015/07/LinkedModelSchedules.jpg)

My only concern is the performance of such an application. I run it on the Revit MEP example file, and it take 31 seconds, regeneration included. It could easily handle a larger model, but the user will then need some patience as the application run.

You will find below a piece of code I use to write values on every elements of the model. This code does not include any interface, but I hope to be able to publish a packaged version anytime soon.

&nbsp;

<pre class="brush: csharp; title: ; notranslate" title="">public void ModelTimeStamp()
{
	Document doc = this.ActiveUIDocument.Document;
	
	using (Transaction tx = new Transaction(doc)) {

		tx.Start("Model TimeStamp");

		//Create a list of category
		CategorySet myCategories = CreateCategoryList(doc, this.Application);

		//Retrive all model elements
		FilteredElementCollector collector = new FilteredElementCollector(doc);
		IList&lt;ElementFilter&gt; categoryFilters = new List&lt;ElementFilter&gt;();

		foreach (Category category in myCategories)
		{
			categoryFilters.Add(new ElementCategoryFilter(category.Id));
		}

		ElementFilter filter = new LogicalOrFilter(categoryFilters);

		IList&lt;Element&gt; elementList = collector.WherePasses(filter).WhereElementIsNotElementType().ToElements();

		//Add the value to all element
		if (elementList.Count &gt; 0)
		{
			foreach (Element e in elementList)
			{
				WriteOnParam("Date", e, DateTime.Now.ToShortDateString());
				WriteOnParam("Version", e, "First Release");
				WriteOnParam("FileName", e, "SubContractors Model");
				WriteOnParam("Trade", e, "HVAC");
			}
		}

		tx.Commit();
	}

}

private void WriteOnParam(string paramName, Element e, string value)
{
	IList&lt;Parameter&gt; parameters = e.GetParameters(paramName);
	if (parameters.Count != 0)
	{
		Parameter p = parameters.FirstOrDefault();
		if (!p.IsReadOnly)
		{
			p.Set(value);
		}
	}
}

private CategorySet CreateCategoryList(Document doc, Autodesk.Revit.ApplicationServices.Application app)
{
	CategorySet myCategorySet = app.Create.NewCategorySet();
	Categories categories = doc.Settings.Categories;

	foreach (Category c in categories)
	{
		if (c.AllowsBoundParameters && c.CategoryType == CategoryType.Model)
		{
			myCategorySet.Insert(c);
		}
	}

	return myCategorySet;
}
</pre>