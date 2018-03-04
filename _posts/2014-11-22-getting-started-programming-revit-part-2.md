---
id: 710
title: 'Getting started programming Revit - Part 2'
date: 2014-11-22T23:05:52+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=710
permalink: /2014/11/getting-started-programming-revit-part-2/
categories:
  - Revit
tags:
  - .NET
  - Automation
  - BIM Manager
  - Revit
---
Last week, we started creating macros in Revit, we saw how to get the current Revit document, and retrieved every visible walls in the current view.

We will see today how to create a tag on these walls.

To tag an element in Revit, we need the Create.NewTag() function. This function is called from the current document, named here myDocument. But to work properly, this function needs a few things as inputs.

It first requires a view to place our tag: we will just use the active view, named myActiveView.

It also needs an element to place a tag on. To do so, we will select each one of our walls with a for each loop.

{% highlight c# %}
foreach (Element myElement in myWalls)
{
    //Do something with myElement
}
{% endhighlight %}

It means that for every element contained in our list of wall myWalls, we will perform some action, written between the brackets.

A few options have to be set, like the category of our tag, its orientation and its leader.

Finally, it needs a location point to insert our tag. We want our tag to be placed at the center of our wall, so we will retrieve the baseline of our wall, and create a point in the middle of this baseline:

{% highlight c# %}
//Get our wall
Wall myWall = myElement as Wall;
//Get its location
LocationCurve myWallLocation = myWall.Location as LocationCurve;
//Get starting point
XYZ myWallStartingPoint = myWallLocation.Curve.GetEndPoint(0);
//Get ending point
XYZ myWallEndingPoint = myWallLocation.Curve.GetEndPoint(1);
//Create the middle point
XYZ myWallCenterPoint =(myWallStartingPoint + myWallEndingPoint)/2;
{% endhighlight %}

Know, we have everything we need to create our tag:

{% highlight c# %}
IndependentTag myTag = myDocument.Create.NewTag(
                myActiveView,
                myElement,
                false,
                TagMode.TM_ADDBY_CATEGORY,
                TagOrientation.Horizontal,
                myWallCenterPoint);
{% endhighlight %}

To try this, we need to draw some walls, and load in our model a Wall. We hit F8 to build the macro before running it.

But if we run it, we get the following error:

![ScreenClip](/assets/2014/11/ScreenClip.png)

Its means that we are trying to modifying something inside our model without starting what is called a transaction.

Every modification of our model has to be done within a transaction, a group of modifications that can be discarded. If you remember the list of actions we can cancel in the Revit user interface, each one of them is a transaction that had to be started be before modifying anything in our model.

![ScreenClip-1](/assets/2014/11/ScreenClip-1.png)

So let create a transaction:

We start by defining a scope of our transaction with the keyword using. Every piece of code between the following brackets will use the transaction named tx.

{% highlight c# %}using (Transaction tx = new Transaction(myDocument))
{

}
{% endhighlight %}

Now our transaction is created, we can start it, execute our code, and commit these modifications in our transaction:

{% highlight c# %}using (Transaction tx = new Transaction(myDocument))
{
                tx.Start("Add Tags on walls");

                foreach (Element myElement in myWalls) {
                    //Do something with myElement

                    //Get our wall
                    Wall myWall = myElement as Wall;
                    //Get its location
                    LocationCurve myWallLocation =
                             myWall.Location as LocationCurve;
                    //Get starting point
                    XYZ myWallStartingPoint =
                             myWallLocation.Curve.GetEndPoint(0);
                    //Get ending point
                    XYZ myWallEndingPoint =
                             myWallLocation.Curve.GetEndPoint(1);
                    //Create the middle point
                    XYZ myWallCenterPoint =
                        (myWallStartingPoint + myWallEndingPoint)/2;

                    IndependentTag myTag = myDocument.Create.NewTag(
                             myActiveView,
                             myElement,
                             false,
                             TagMode.TM_ADDBY_CATEGORY,
                             TagOrientation.Horizontal,
                             myWallCenterPoint);
                }

                tx.Commit();
}
{% endhighlight %}

We run it and every walls are tagged.

![ScreenClip-22](/assets/2014/11/ScreenClip-22.png)