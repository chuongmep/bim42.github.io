---
id: 493
title: Revit Tracking
date: 2014-07-19T08:00:17+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=493
permalink: /2014/07/revit-tracking/
categories:
  - Revit
  - Uncategorized
tags:
  - .NET
  - BIM Manager
  - Plugin
  - Revit
---
My previous post about Revit performance highlighted the need for precise feedback from user about starting and synchronizing time. This is important when dealing with many users, with potentially different configuration and performance. In this case, these loading times can alert you soon enough of a problem with a model.

Having feedback from every user is also important, since you need to detect quickly if any user is having more difficulty to open a file than the average.

You can also compare file size progression with loading time to establish and check your set of good practices for keeping Revit models powerful.

To be more accurate and systematic with these measures, I create a small piece of code to log every opening, synchronizing and closing of Revit model for multiples users.

On startup, the application subscribe to the events triggered on opening, synchronizing or closing a model.

{% highlight c# %}
public RevitLogger( UIControlledApplication a)
{
    ControlledApplication app = a.ControlledApplication;

    //Subscribe to the opening event
    app.DocumentOpening += DocumentOpeningEventHandler;
    app.DocumentOpened += DocumentOpenedEventHandler;

    //Subscribe to the synchronizing event
    app.DocumentSynchronizingWithCentral += DocumentSynchronizingEventHandler;
    app.DocumentSynchronizedWithCentral += DocumentSynchronizedEventHandler;

    //Subscribe to the closing event
    app.DocumentClosing += DocumentClosingEventHandler;
    app.DocumentClosed += DocumentClosedEventHandler;
}

{% endhighlight %}

Subscribing to the starting event and the ending event allow me to track down the time taken by each task.

Afterward, each event handler measure the time taken to perform the task, along with other properties related to the Revit file like its name, its path, if it is workshared, and so on.

For example, to log the opening of a model:

{% highlight c# %}
private void DocumentOpeningEventHandler(
                 object sender,
                 Autodesk.Revit.DB.Events.DocumentOpeningEventArgs args)
{
    //Retrive info about the file
    BasicFileInfo FileInfo = BasicFileInfo .Extract(args.PathName);

    _logReccord = new LogReccord(ReccordType .Open);
    _logReccord.ReccordStarting = DateTime.Now;
}

private void DocumentOpenedEventHandler(
                 object sender,
                 Autodesk.Revit.DB.Events.DocumentOpenedEventArgs args)
{
    _logReccord.ReccordEnding = DateTime.Now;
}

{% endhighlight %}

Here, the LogReccord class allow us to store the information retrieved in the event handler. Once these information are stored, it is pretty easy to collect them and write them down to a csv file.

It is now possible to quickly create very precise graph displaying opening time of different model, compare them and show their evolution along time

![Image](/assets/2014/07/Image.png)

The next step should be to send these information to a shared SQL database in order to retrive data from every users. We should have this way a company-wide tool for keeping track of Revit performance.