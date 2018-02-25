---
id: 972
title: Details Items, subcategories and filled regions
date: 2015-10-11T10:47:04+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=972
permalink: /2015/10/details-items-subcategories-and-filled-regions/
categories:
  - Revit
tags:
  - .NET
  - Automation
  - Documentation
  - Revit
---
I am currently working with multiple detail items to create a set of views for architectural detailing. These Detail Items must comply with a precise standard for color and line weights, and of course, be consistent all over the model.

To implement these requirements, I define a set of subcategories for these detail items. Let see how it works with these two wood windows details.

[<img class="aligncenter size-full wp-image-983" src="http://bim42.com/wp-content/uploads/2015/10/01-WindowsDetailsComponents.jpg" alt="01-WindowsDetailsComponents" width="800" height="337" srcset="https://bim42.com/wp-content/uploads/2015/10/01-WindowsDetailsComponents.jpg 800w, https://bim42.com/wp-content/uploads/2015/10/01-WindowsDetailsComponents-300x126.jpg 300w, https://bim42.com/wp-content/uploads/2015/10/01-WindowsDetailsComponents-500x211.jpg 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/10/01-WindowsDetailsComponents.jpg)

These detail items already contain various subcategories, and I can control the color, weight and patterns of their lines in Visibility Overrides. Here Medium Lines are blue and Light Lines are red. Interesting, but not quite enough.

[<img class="aligncenter size-full wp-image-974" src="http://bim42.com/wp-content/uploads/2015/10/02-LineTypeOverrride.png" alt="02-LineTypeOverrride" width="800" height="489" srcset="https://bim42.com/wp-content/uploads/2015/10/02-LineTypeOverrride.png 800w, https://bim42.com/wp-content/uploads/2015/10/02-LineTypeOverrride-300x183.png 300w, https://bim42.com/wp-content/uploads/2015/10/02-LineTypeOverrride-491x300.png 491w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/10/02-LineTypeOverrride.png)

I open these two detail items, go to Object Styles, and create four new subcategories: Wood, Glass, Sealant and Steel. I also remove the previous subcategories. I can now select all lines in the detail item, and assign corresponding subcategories to these lines. Once these detail items are loaded back in the model, the four Detail Item subcategories are visible in the Graphic Overrides window.

I can now control line color, weight and pattern directly in my model, in the Graphic Overrides window for the current view, or in the Object Styles window to apply these colors to every details in the model.

[<img class="aligncenter size-full wp-image-975" src="http://bim42.com/wp-content/uploads/2015/10/03-OverideByMaterial.png" alt="03-OverideByMaterial" width="800" height="489" srcset="https://bim42.com/wp-content/uploads/2015/10/03-OverideByMaterial.png 800w, https://bim42.com/wp-content/uploads/2015/10/03-OverideByMaterial-300x183.png 300w, https://bim42.com/wp-content/uploads/2015/10/03-OverideByMaterial-491x300.png 491w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/10/03-OverideByMaterial.png)

Sadly, there is no corresponding feature for managing filled region. As you can see in the picture above, the wood pattern is still in black.

In order to change pattern or color in a filled region, you have to edit the detail item and change the filled region style in the family. If you want to edit your wood pattern, you have to open every detail items containing wood, and change the pattern in the family.

To fix this, and be able to edit directly filled region style for every detail item, I create a small piece of code. This function matches model filled region types with those inside the detail item. So if I have a filled region in my Detail Item family with the same name than one in my Revit project, this filled region will take the properties of the one in the project.

[<img class="aligncenter size-full wp-image-977" src="http://bim42.com/wp-content/uploads/2015/10/matchProperties.png" alt="matchProperties" width="800" height="417" srcset="https://bim42.com/wp-content/uploads/2015/10/matchProperties.png 800w, https://bim42.com/wp-content/uploads/2015/10/matchProperties-300x156.png 300w, https://bim42.com/wp-content/uploads/2015/10/matchProperties-500x261.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/10/matchProperties.png)

After running this function, I end up with nicely matching wood pattern, all set up directly in my Revit project.

[<img class="aligncenter size-full wp-image-976" src="http://bim42.com/wp-content/uploads/2015/10/04-OverideFilledRegion.png" alt="04-OverideFilledRegion" width="800" height="337" srcset="https://bim42.com/wp-content/uploads/2015/10/04-OverideFilledRegion.png 800w, https://bim42.com/wp-content/uploads/2015/10/04-OverideFilledRegion-300x126.png 300w, https://bim42.com/wp-content/uploads/2015/10/04-OverideFilledRegion-500x211.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2015/10/04-OverideFilledRegion.png)

As usual, you will find the source code for this solution below, I hope it will help you solve your filled region issues.

<pre class="brush: csharp; title: ; notranslate" title="">public partial class ThisApplication
{
	public void MatchFilledRegion()
	{
		Document doc = this.ActiveUIDocument.Document;
		
		//Find all Filled Region Type, and create a dictonary with it
		Dictionary&lt;string,FilledRegionType&gt; modelFilledRegionTypes =
			new FilteredElementCollector(doc).OfClass(typeof(FilledRegionType)).ToElements().Cast&lt;FilledRegionType&gt;().ToDictionary(e =&gt; e.Name);
		
		//Find all loaded families
		IList&lt;Element&gt; elements = new FilteredElementCollector(doc).OfClass(typeof(Family)).ToElements();
		
		//Get Detail Item category id.
		ElementId detailItemCategoryId = doc.Settings.Categories.get_Item(BuiltInCategory.OST_DetailComponents).Id;
		

		
		//Loop on all loaded families
		foreach (Element familyElement in elements) {
			
			Family family = familyElement as Family;
			
			//Exit the families loop if it isn't a Detail Item Familly
			if (family.FamilyCategory.Id != detailItemCategoryId) continue;

			//Open the family
			Document familyDoc = doc.EditFamily(family);
			string familyPath = Path.Combine(Path.GetTempPath(),family.Name+".rfa");
			
			bool familyEdited = false;
			
			//Find all Filled Region Type in the family
			IList&lt;Element&gt; filledRegionTypes = new FilteredElementCollector(familyDoc).OfClass(typeof(FilledRegionType)).ToElements();
			
			using (Transaction famTx = new Transaction(familyDoc))
			{
				famTx.Start("Edit Filled Region Type");
				
				//Loop on all Filled Region types in the family
				foreach (Element filledRegionTypeElement in filledRegionTypes)
				{
					FilledRegionType filledRegionType = filledRegionTypeElement as FilledRegionType;
					if (modelFilledRegionTypes.ContainsKey(filledRegionType.Name))
					{
						FilledRegionType refFilledRegion = modelFilledRegionTypes[filledRegionType.Name];
						//Change the color
						if (filledRegionType.Color.Red != refFilledRegion.Color.Red
						    || filledRegionType.Color.Blue != refFilledRegion.Color.Blue
						    || filledRegionType.Color.Green != refFilledRegion.Color.Green)
						{
							filledRegionType.Color = refFilledRegion.Color;
							familyEdited = true;
						}
						
						//Change the Background
						if (filledRegionType.Background != refFilledRegion.Background)
						{
							filledRegionType.Background = refFilledRegion.Background;
							familyEdited = true;
						}
						
						//Change line weight
						if (filledRegionType.LineWeight != refFilledRegion.LineWeight)
						{
							filledRegionType.LineWeight = refFilledRegion.LineWeight;
							familyEdited = true;
						}
						
					}
					
				}
				
				famTx.Commit();
			}
			
			if (familyEdited)
			{
				familyDoc.LoadFamily(doc, new FamilyOption());
				familyDoc.Close( false );
			}
			else
			{
				familyDoc.Close( false );
			}
		}
	}
}

public class FamilyOption : IFamilyLoadOptions
{
	public bool OnFamilyFound(bool familyInUse,out bool overwriteParameterValues)
	{
		overwriteParameterValues = true;
		return true;
	}
	
	public bool OnSharedFamilyFound(Family sharedFamily,bool familyInUse, out FamilySource source,out bool overwriteParameterValues )
	{
		source = FamilySource.Family;
		overwriteParameterValues = true;
		return true;
	}
}
</pre>