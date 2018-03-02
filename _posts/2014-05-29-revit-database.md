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
  During my first research for exporting the Revit database, I came across the Revit DB Link, a plug-in available at <a title="Autodesk Subscription" href="https://subscription.autodesk.com/">Autodesk Subscription</a> website. This add-in allows to export the Revit database, but also to edit this database and import it back into Revit.
  Using it is pretty easy when you have all the correct software installed.</p># Exporting  First, you have to configure a new connection. After starting the Revit DB Link add-in, select [Select a new connection] in the ODBC panel, and click Export:</p>
  <a href="http://bim42.com/wp-content/uploads/2014/05/linkinterface.png"><img class="aligncenter size-full wp-image-371" src="http://bim42.com/wp-content/uploads/2014/05/linkinterface.png" alt="LinkInterface" width="491" height="290" srcset="https://bim42.com/wp-content/uploads/2014/05/linkinterface.png 491w, https://bim42.com/wp-content/uploads/2014/05/linkinterface-300x177.png 300w" sizes="(max-width: 491px) 100vw, 491px" /></a>Type a name for your export configuration, and select New. Select the SQL Server database, and follow the indication for creating the link file toward your database.
  At this windows, fill in the description of your database, and select the SQL server you want to connect. Here, I am working with an SQL server named SQLEXPRESS:</p>
  <a href="http://bim42.com/wp-content/uploads/2014/05/dbselection.png"><img class="aligncenter size-full wp-image-373" src="http://bim42.com/wp-content/uploads/2014/05/dbselection.png" alt="DBSelection" width="534" height="379" /></a>
  Select a specific database for this export. I have created mine through SQL Management Studio before starting my export. After a summary page, the connection is established.
  The export run smoothly, and I get a bunch of tables, one per Revit category, along with others with a more cryptic name.</p># Using  One of the most obvious application is to create multi-model schedules. Creating a schedule on multiples Revit files can be very tedious, especially with large models. Exporting every Revit files in its own database allow us to merge quantities with a simple UNION SQL command. You just have to make sure to export each new model to a new database to avoid DB link to override previous model export.
  Most parameters editable in Revit can also be changed in the database and imported back in Revit model.
  As an example, you can edit duct width in the database, and import back values to modify the Revit duct sizes:
   <img class="aligncenter size-full wp-image-372" src="http://bim42.com/wp-content/uploads/2014/05/sqledit.png" alt="SQLEDit" width="579" height="172" srcset="https://bim42.com/wp-content/uploads/2014/05/sqledit.png 579w, https://bim42.com/wp-content/uploads/2014/05/sqledit-300x89.png 300w" sizes="(max-width: 579px) 100vw, 579px" />
  Before:
  <a href="http://bim42.com/wp-content/uploads/2014/05/before.png"><img class="aligncenter size-full wp-image-370" src="http://bim42.com/wp-content/uploads/2014/05/before.png" alt="Before" width="584" height="345" srcset="https://bim42.com/wp-content/uploads/2014/05/before.png 745w, https://bim42.com/wp-content/uploads/2014/05/before-300x177.png 300w" sizes="(max-width: 584px) 100vw, 584px" /></a>After:
  <a href="http://bim42.com/wp-content/uploads/2014/05/after.png"><img class="aligncenter size-full wp-image-369" src="http://bim42.com/wp-content/uploads/2014/05/after.png" alt="After" width="584" height="369" srcset="https://bim42.com/wp-content/uploads/2014/05/after.png 715w, https://bim42.com/wp-content/uploads/2014/05/after-300x189.png 300w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  There is also some specific tables to access relations between Revit objects.<br /> For example, the DoorWall table links each door with its hosting wall. The RoomAssociations table allows us to retrieve every elements inserted into a specific room, to create furniture schedules for example.
  Exporting the Revit database to an SQL Server can be a very powerful tool, and provide us new means for creating complex schedules.</p>
