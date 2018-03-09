---
id: 871
title: Revit categories and classification systems
date: 2015-06-20T13:27:42+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=871
permalink: /2015/06/revit-categories-and-classification-systems/
categories:
  - Revit
image: /assets/2015/06/Assemblycode.jpg
tags:
  - .NET
  - Normalization
  - Revit
---
Standards for classifying building elements have been around for some times, but building information modeling gives us new perspectives for using them.

There is a handful of these classifications currently in use. The [Construction Specifications Institute](http://www.csinet.org/) produce the [MasterFormat](https://en.wikipedia.org/wiki/MasterFormat) and [UniFormat](https://en.wikipedia.org/wiki/Uniformat), used in United States and Canada. The [Construction Project Information Committee](http://www.cpic.org.uk/) in the United Kingdom provides [Uniclass](https://en.wikipedia.org/wiki/Uniclass) and [Uniclass 2](https://en.wikipedia.org/wiki/Uniclass). And the "[Catalogue des articles normalisés](http://www.crb.ch/crbOnline/fr/CRB-Standards/Normpositionen/Katalog.html)" was used in Switzerland even before computers were able to manage it.

Revit provides two built-in type parameters to manage such classification systems, the Assembly Code and the Assembly Description. These parameters allow us to link any Revit type to an existing classification system.

![Assignement](/assets/2015/06/Assignement.jpg)

This classification system can be loaded in Revit through the Assembly Code interface.

![Assemblycode](/assets/2015/06/Assemblycode.jpg)

Autodesk provides us with the Uniformat classification, through the UniformatClassifications.txt. This tab-separated values text file define the classification structure with four columns:

{% highlight text %}
Classification Code - Description - Rank - Revit category Id
{% endhighlight %}

* The Classification Code is the number associated with each item in a given classification. It is linked to the Assembly Code in Revit.
* The Description is the text associated with each item of the classification. Once we add an Assembly Code to a Revit type, this description appears in the Assembly Desciption.
* The Rank define the hierarchy of the item in the classification. This allows Revit to display any linked classification in a tree view.
* Finally, the Revit category Id allows us to create a first mapping between classification items and Revit categories. This allow us to filter by Revit category while assigning Assembly Code.

To create such a mapping, we need the list of Revit categories. To extract this, I run a small routine to write every built-in Revit category to a .csv file. Along the way, I find some interesting properties of these categories. For example, the IsCuttable property list cuttable categories, something I was talking about in a [previous post](https://www.bim42.com/2014/06/understanding-view-range/).

But most important here is an exhaustive list of all Revit categories, along with their Id, a prerequisite to create relations between Revit categories and classifications items.

These relations allows us to filter by category while assigning Assembly Codes.

You can find [here](https://www.bim42.com/wp-content/uploads/2015/06/categories.csv) the .csv file with all Revit categories, along with the code used to create it.

{% highlight c# %}
public void Categories()
{
	Document doc = this.ActiveUIDocument.Document;
	Categories categories = doc.Settings.Categories;
	
	List<string> categoriesList = new List<string>();
	categoriesList.Add(
	"Rank;
	CategoryType;
	Name;Id;
	IsSubCategory;
	IsCuttable;
	IsTagCategory");
	
	foreach( Category c in categories )
	{
		categoriesList.Add(
		"1;"+c.CategoryType.ToString()+";"+
		c.Name+";"+c.Id+";"+";"+c.IsCuttable.ToString()+";"+
		c.IsTagCategory.ToString()
		);
		//Retrive sub categories
		foreach (Category subc in c.SubCategories) {
			categoriesList.Add(
			"2;"+subc.CategoryType.ToString()+";"+
			subc.Name+";"+subc.Id+";"+c.Name+";"+
			subc.IsCuttable.ToString()+";"+
			subc.IsTagCategory.ToString()
			);
		}
	}
	
	string path = @"C:\categories.csv";
	File.WriteAllLines(path,categoriesList.ToArray());
}
{% endhighlight %}