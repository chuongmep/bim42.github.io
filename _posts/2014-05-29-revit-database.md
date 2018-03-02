---
id: 368
title: Revit Database
date: 2014-05-29T13:34:40+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=368
permalink: /2014/05/revit-database/
geo_public:
  - "0"
publicize_twitter_user:
  - bim42
publicize_twitter_url:
  - http://t.co/lU3OLlU7GE
publicize_linkedin_url:
  - 'http://www.linkedin.com/updates?discuss=&scope=45913264&stype=M&topic=5877773838359490560&type=U&a=z1uM'
categories:
  - Revit
tags:
  - BIM Manager
  - Revit
  - Schedules
  - SQL
---

It has been a while since I want to export a whole Revit project to a database. I had a few prior experiences with MySQL and the SQL management software Toad, but never with the Revit database.

This time, I decide to use the SQL Server, along with its SQL Server Management Studio, the solution developed by Microsoft.

During my first research for exporting the Revit database, I came across the Revit DB Link, a plug-in available at the [Autodesk Subscription](https://subscription.autodesk.com) website. This add-in allows to export the Revit database, but also to edit this database and import it back into Revit.

Using it is pretty easy when you have all the correct software installed.</p># Exporting  First, you have to configure a new connection. After starting the Revit DB Link add-in, select [Select a new connection] in the ODBC panel, and click Export:

![Linking interface](http://bim42.com/wp-content/uploads/2014/05/linkinterface.png)

Type a name for your export configuration, and select New. Select the SQL Server database, and follow the indication for creating the link file toward your database.

At this windows, fill in the description of your database, and select the SQL server you want to connect. Here, I am working with an SQL server named SQLEXPRESS:

![Select Database](http://bim42.com/wp-content/uploads/2014/05/dbselection.png)

Select a specific database for this export. I have created mine through SQL Management Studio before starting my export. After a summary page, the connection is established.

The export run smoothly, and I get a bunch of tables, one per Revit category, along with others with a more cryptic name. 

One of the most obvious application is to create multi-model schedules. Creating a schedule on multiples Revit files can be very tedious, especially with large models. Exporting every Revit files in its own database allow us to merge quantities with a simple UNION SQL command. You just have to make sure to export each new model to a new database to avoid DB link to override previous model export.

Most parameters editable in Revit can also be changed in the database and imported back in Revit model. As an example, you can edit duct width in the database, and import back values to modify the Revit duct sizes:

![Edit SQL](http://bim42.com/wp-content/uploads/2014/05/sqledit.png)

Before:

![Before](http://bim42.com/wp-content/uploads/2014/05/before.png)

After:

![After](http://bim42.com/wp-content/uploads/2014/05/after.png)

There is also some specific tables to access relations between Revit objects. For example, the DoorWall table links each door with its hosting wall. The RoomAssociations table allows us to retrieve every elements inserted into a specific room, to create furniture schedules for example.

Exporting the Revit database to an SQL Server can be a very powerful tool, and provide us new means for creating complex schedules.
