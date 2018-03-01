---
id: 694
title: Getting started programming Revit
date: 2014-11-15T12:10:15+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=694
permalink: /2014/11/getting-started-programming-revit/
categories:
  - Revit
tags:
  - .NET
  - BIM Manager
  - Revit
---
I recently had some questions on how to start programing in Revit, so I will present here a simple macro created with the embedded macro editor, SharpDevelop.

As an example, I will create a macro for tagging all wall in a given view. Even if this function already exist through the Tag All command, you will see all the possibilities for creating it with a macro.

This week, we will see how to create a macro and retrieve elements draw in our model.

Let's start it by clicking on the Macro Manager on the Manage tab:

![01-MacroEditor](http://bim42.com/wp-content/uploads/2014/11/01-MacroEditor.png)

This is where you create new function in Revit, called &#8220;Macro&#8221;. These macro are lines of code, conveniently stored in a &#8220;Module&#8221;.

![02-MacroEditor-Interface](http://bim42.com/wp-content/uploads/2014/11/02-MacroEditor-Interface.png)

After creating a new module, and creating a new macro in this module, Revit starts its embedded code editor, called SharpDevelop. This is where we are going to spend most of our time developing Revit macro.

![03-SharpDevelop](http://bim42.com/wp-content/uploads/2014/11/03-SharpDevelop.png)

We can see the name of our macro just after &#8220;public void&#8221; and before a pair of brackets. We will write all our code between these brackets.

Every action done within Revit are made within a document, generally a .rvt or .rfa file. We have to explain this in our macro by retrieving the current document

Let's write this:

<pre class="brush: csharp; title: ; notranslate" title="">Document myDocument;</pre>

With this line, I explain to Revit that something, a variable, called &#8220;myDocument&#8221; is a Revit Document.

Don't forget the trailing &#8220;;&#8221;, it means the end of the line and has to be placed after every instruction line in a Revit macro.

Then, we write this:

<pre class="brush: csharp; title: ; notranslate" title="">myDocument = this.ActiveUIDocument.Document;</pre>

With this line, we explain than myDocument is actually the active document, the Revit document I am currently working with. &#8220;this&#8221; mean here &#8220;this Revit application&#8221;.

To be able to annotate every walls in a view, we have to select this view. Here, we call our view myActiveView and set it to the currently active view, the one you are looking at right now.

<pre class="brush: csharp; title: ; notranslate" title="">View myActiveView = myDocument.ActiveView;</pre>

Now than our Revit document and the view are selected, we have to retrieve walls to be able to annotate them. The Revit API provide us with a great function, the ability to filter element by category, type, class, ...  well, pretty much everything.

First, let's create our filter, with the keyword &#8220;new&#8221;:

<pre class="brush: csharp; title: ; notranslate" title="">FilteredElementCollector filter 
= new FilteredElementCollector(myDocument,myActiveView.Id);</pre>

This &#8220;filter&#8221; will search for every element contained in &#8220;myDocument&#8221; and visible in the view &#8220;myActiveView&#8221;. The &#8220;.Id&#8221; after &#8220;myActiveView&#8221; mean that we use the unique identifier of the view instead of the view itself to create our filter.

We can now use this filter to actually catch some walls. Let's write that:

<pre class="brush: csharp; title: ; notranslate" title="">List&lt;Element&gt;myWalls 
= filter.OfCategory(BuiltInCategory.OST_Walls).ToList();</pre>

We create a list of Revit element named myWalls and retrieve every element of the category Wall (&#8220;BuiltInCategory.OST_Walls&#8221;). The trailing &#8220;.ToList()&#8221; convert our filter into an actual list of elements.

Before going any further, we try this. Back in Revit, we draw four walls and run our macro by selecting it in the Macro Manager and hitting &#8220;Step Into&#8221;. This sends us back to SharpDevelop, with slight changes in the interface, and a yellow highlight on the first line of our macro. This highlight show us which line of our macro is currently executed. Hit &#8220;F11&#8221; two times to pass the first line.

If we pass our cursor on &#8220;myDocument&#8221;, a hint appear, showing us than &#8220;myDocument&#8221; is actually a document.

![05-ocument-Hint](http://bim42.com/wp-content/uploads/2014/11/05-ocument-Hint.png)

Let's hit &#8220;F11&#8221; a few time to pass the last line. Stop right after it. If we pass our cursor on &#8220;myWalls&#8221; and click on the small &#8220;+&#8221; in the highlight, we see the list of walls retrieved by our filter. Everything works as expected, so far.

![06-Walls-Hint](http://bim42.com/wp-content/uploads/2014/11/06-Walls-Hint.png)

We hit &#8220;F5&#8221; to run in a single stroke the remaining line of code and go back into SharpDevelop.

Next week, we will see how to use this list of walls to create a tag for every one of them.