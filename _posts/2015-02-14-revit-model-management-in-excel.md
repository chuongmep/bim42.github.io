---
id: 773
title: Revit model management in Excel
date: 2015-02-14T13:55:17+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=773
permalink: /2015/02/revit-model-management-in-excel/
categories:
  - Revit
tags:
  - .NET
  - BIM Manager
  - Revit
---
Model management can involve some tedious tasks. Cleaning up the mess created by an unruly user when he import all categories of an old Revit model is probably the most tedious of these tasks.

When someone import elements from another model, we quickly end up with thousand of view templates, filters, and other user created views which can become totally unmanageable.

Here come the BIM Manager, who spend two tedious days sorting these views and campaigning against view proliferation.

To help address this problem, I create a small piece of code for exporting every view, template and filter to three CSV files.

![<img class="aligncenter size-full wp-image-777" src="http://bim42.com/wp-content/uploads/2015/02/csvFiles.png" alt="CSV Files" width="218" height="64" />](http://bim42.com/wp-content/uploads/2015/02/csvFiles.png)

To read these files in a meaningful way, I use PowerPivot in Excel to create some kind of a small database, with two relationships :

![<img class="aligncenter size-full wp-image-775" src="http://bim42.com/wp-content/uploads/2015/02/relationships.png" alt="Relationships" width="800" height="596" srcset="https://bim42.com/wp-content/uploads/2015/02/relationships.png 800w, https://bim42.com/wp-content/uploads/2015/02/relationships-300x224.png 300w, https://bim42.com/wp-content/uploads/2015/02/relationships-403x300.png 403w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/02/relationships.png)

We can then create tables displaying how filters and views are used, like how many filters are used, or where the templates are applied.

![<img class="aligncenter size-full wp-image-774" src="http://bim42.com/wp-content/uploads/2015/02/filtersUsage.png" alt="Filters Usage" width="415" height="334" srcset="https://bim42.com/wp-content/uploads/2015/02/filtersUsage.png 415w, https://bim42.com/wp-content/uploads/2015/02/filtersUsage-300x241.png 300w, https://bim42.com/wp-content/uploads/2015/02/filtersUsage-373x300.png 373w" sizes="(max-width: 415px) 100vw, 415px" />](http://bim42.com/wp-content/uploads/2015/02/filtersUsage.png)

![<img class="aligncenter size-full wp-image-776" src="http://bim42.com/wp-content/uploads/2015/02/templateUsage.png" alt="Templates Usage" width="318" height="222" srcset="https://bim42.com/wp-content/uploads/2015/02/templateUsage.png 318w, https://bim42.com/wp-content/uploads/2015/02/templateUsage-300x209.png 300w" sizes="(max-width: 318px) 100vw, 318px" />](http://bim42.com/wp-content/uploads/2015/02/templateUsage.png)

Once loaded in the PowerPivot tool, this data allows us to quickly identify which template or filter are used and delete the unwanted ones.

The entire source code is available below, please feel free to use it for your own projects.

<pre class="brush: csharp; title: ; notranslate" title="">public void ExportViewTemplatesList()
{
	Document doc = this.ActiveUIDocument.Document;
			
	//find all view
	IEnumerable&lt;View&gt; views = 
from elem in new FilteredElementCollector(doc).OfClass(typeof(View))
let view = elem as View
select view;
			
	//Create a text file for exporting
	List&lt;string&gt; lines = new List&lt;string&gt;();
	//Add the first line
	lines.Add("TemplateName");
			
	foreach (View view in views) {
		if (view.IsTemplate)
		{
			lines.Add(view.Name);
		}
	}
			
	lines = lines.Distinct().ToList();
	string exportpath = @"templates.csv";
	File.WriteAllLines(exportpath,lines.ToArray(),Encoding.UTF8);
}

public void ExportFiltersList()
{
	Document doc = this.ActiveUIDocument.Document;
			
	//find all filters
	IEnumerable&lt;ParameterFilterElement&gt; filters = 
from elem in new FilteredElementCollector(doc)
.OfClass(typeof(ParameterFilterElement))
let filter = elem as ParameterFilterElement
select filter;
			
	//Create a text file for exporting
	List&lt;string&gt; lines = new List&lt;string&gt;();
	//Add the first line
	lines.Add("FilterName");
			
	foreach (ParameterFilterElement filter in filters) 
	{
		lines.Add(filter.Name);
	}
			
	lines = lines.Distinct().ToList();
	string exportpath = @"filters.csv";
	File.WriteAllLines(exportpath,lines.ToArray(),Encoding.UTF8);
}

public void ExportViewsList()
{
	Document doc = this.ActiveUIDocument.Document;
			
	//find all view
	IEnumerable&lt;View&gt; views = 
from elem in new FilteredElementCollector(doc).OfClass(typeof(View))
let view = elem as View
select view;
			
	//Create a text file for exporting
	List&lt;string&gt; lines = new List&lt;string&gt;();
	//Add the first line
	lines.Add("ViewName;ViewType;IsTemplate;"
		+"TemplateName;LevelName;FilterName");
			
	foreach (View v in views) 
	{
		Level level = v.GenLevel;	
		string levelName = "";
		if (level != null)
		{
			levelName  =  level.Name;
		}
		
		//Get view filters
		ICollection&lt;ElementId&gt; filterIds;
		try {
			filterIds = v.GetFilters();
		} catch (Autodesk.Revit.Exceptions.InvalidOperationException) {
			filterIds = new List&lt;ElementId&gt;() ;
		}
				
		string templateName = "";
				
		if (v.ViewTemplateId.IntegerValue != -1)
		{
			templateName  =  doc.GetElement(v.ViewTemplateId).Name;
		}
				
		string viewinfos =
			v.ViewName + ";" +
			v.ViewType + ";" +
			v.IsTemplate.ToString()  + ";" +
			templateName  + ";" +
			levelName;
				
		if (filterIds.Count != 0)
		{
			foreach (ElementId filterId in filterIds)
			{
				string filterName = doc.GetElement(filterId).Name;
				string line  = viewinfos   + ";" + filterName;
				lines.Add(line);
			}
		}
		else
		{
			lines.Add(viewinfos);
		}
	}
			
	string exportpath = @"views.csv";
	File.WriteAllLines(exportpath,lines.ToArray(),Encoding.UTF8);
}
</pre>