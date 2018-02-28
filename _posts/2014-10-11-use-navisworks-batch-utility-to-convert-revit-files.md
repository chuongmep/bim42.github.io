---
id: 633
title: Use Navisworks Batch Utility to convert Revit files
date: 2014-10-11T10:00:45+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=633
permalink: /2014/10/use-navisworks-batch-utility-to-convert-revit-files/
categories:
  - Coordination
tags:
  - Automation
  - BIM Manager
  - Navisworks
  - Tips
---
A few days ago, I had to convert a large set of Revit files to NWC in order to create a general Navisworks File Set.

I used the Navisworks Batch Utility, accessible through the Navisworks main menu :

![<img class="aligncenter wp-image-642" src="http://bim42.com/wp-content/uploads/2014/10/ScreenClip1.png" alt="Icon" width="99" height="26" />](http://bim42.com/wp-content/uploads/2014/10/ScreenClip1.png)

![<img class="aligncenter wp-image-636 size-full" src="http://bim42.com/wp-content/uploads/2014/10/ScreenClip-12.png" alt="Batch Utility" width="782" height="678" srcset="https://bim42.com/wp-content/uploads/2014/10/ScreenClip-12.png 782w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-12-300x260.png 300w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-12-346x300.png 346w" sizes="(max-width: 782px) 100vw, 782px" />](http://bim42.com/wp-content/uploads/2014/10/ScreenClip-12.png)

You first have to select files to be included in your Navisworks File Set.

To quickly retrieve the list of Revit files to be converted, I'm using the Windows Command Prompt. I was quite afraid of this tool not so long ago, but it is actually pretty simple.

![<img class="aligncenter wp-image-635 size-full" src="http://bim42.com/wp-content/uploads/2014/10/ScreenClip-21.png" alt="Windows Command Prompt" width="837" height="202" srcset="https://bim42.com/wp-content/uploads/2014/10/ScreenClip-21.png 837w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-21-300x72.png 300w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-21-500x120.png 500w" sizes="(max-width: 837px) 100vw, 837px" />](http://bim42.com/wp-content/uploads/2014/10/ScreenClip-21.png)

First, go to the root folder of your project:

<pre class="brush: bash; title: ; notranslate" title="">cd C:\Projects\myRevitProject</pre>

and type :

<pre class="brush: bash; title: ; notranslate" title="">dir /s /b *.rvt &amp;amp;amp;amp;amp;gt;ListRevitFiles.txt</pre>

This line requires a bit of an explanation:

  * _dir_ : command for searching and displaying file in the current directory
  * _/s_ : search in the current directory and all its subdirectories
  * _/b_ (or bare) : remove for each file its metadata to display only the file path
  * _*.rvt_ : search specifically for Revit files
  * _>ListRevitFiles.txt_ : the ‘>’ character allows us to output the result of our research to a text file (here ListRevitFiles.txt) instead of displaying it.

We get the results of our research as text file listing paths to every Revit model contained in our project folder:

<pre class="brush: plain; title: ; notranslate" title="">C:\Projects\myRevitProject\CENTRALS\ARC.rvt
C:\Projects\myRevitProject\CENTRALS\MEP.rvt
C:\Projects\myRevitProject\CENTRALS\STR.rvt
</pre>

Back on the Navisworks Batch Utility, we open this text file to import file paths: File -> Open -> Select ListRevitFiles.txt

![<img class="aligncenter wp-image-638 size-full" src="http://bim42.com/wp-content/uploads/2014/10/ScreenClip-31.png" alt="File List" width="755" height="160" srcset="https://bim42.com/wp-content/uploads/2014/10/ScreenClip-31.png 755w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-31-300x63.png 300w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-31-500x105.png 500w" sizes="(max-width: 755px) 100vw, 755px" />](http://bim42.com/wp-content/uploads/2014/10/ScreenClip-31.png)

As we want to create a single Navisworks File Set (.nwf), we select the &#8220;As Single File&#8221; Tab, and set the path to our future Navisworks File.

![<img class="aligncenter wp-image-639 size-full" src="http://bim42.com/wp-content/uploads/2014/10/ScreenClip-4.png" alt="As Single File" width="765" height="173" srcset="https://bim42.com/wp-content/uploads/2014/10/ScreenClip-4.png 765w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-4-300x67.png 300w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-4-500x113.png 500w" sizes="(max-width: 765px) 100vw, 765px" />](http://bim42.com/wp-content/uploads/2014/10/ScreenClip-4.png)

I also select &#8220;View file on output&#8221; to automatically start Navisworks when conversions are done.

We add a path to a log file in order to know what may happen, and hit &#8220;Run Command&#8221;.

Here, I was confused by the fact that nothing seems to happen, but after checking my computer processes, I was able to see that the Navisworks Scene Convert Server was up and running.

![<img class="aligncenter wp-image-640 size-full" src="http://bim42.com/wp-content/uploads/2014/10/ScreenClip-5.png" alt="Windows Processes" width="943" height="44" srcset="https://bim42.com/wp-content/uploads/2014/10/ScreenClip-5.png 943w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-5-300x13.png 300w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-5-500x23.png 500w" sizes="(max-width: 943px) 100vw, 943px" />](http://bim42.com/wp-content/uploads/2014/10/ScreenClip-5.png)

After a while, Navisworks starts automatically and appends every previously created .nwc file to a new Navisworks File Set.

![<img class="aligncenter wp-image-634 size-full" src="http://bim42.com/wp-content/uploads/2014/10/Project.jpg" alt="Project" width="651" height="430" srcset="https://bim42.com/wp-content/uploads/2014/10/Project.jpg 651w, https://bim42.com/wp-content/uploads/2014/10/Project-300x198.jpg 300w, https://bim42.com/wp-content/uploads/2014/10/Project-454x300.jpg 454w" sizes="(max-width: 651px) 100vw, 651px" />](http://bim42.com/wp-content/uploads/2014/10/Project.jpg)

I am also using this feature to create a NWD file for a set of Revit file.

To do so, you just have to select the &#8220;Multiple file&#8221; tab and define a target folder for the export.

![<img class="aligncenter wp-image-641 size-full" src="http://bim42.com/wp-content/uploads/2014/10/ScreenClip-61.png" alt="As Multiple Files" width="763" height="171" srcset="https://bim42.com/wp-content/uploads/2014/10/ScreenClip-61.png 763w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-61-300x67.png 300w, https://bim42.com/wp-content/uploads/2014/10/ScreenClip-61-500x112.png 500w" sizes="(max-width: 763px) 100vw, 763px" />](http://bim42.com/wp-content/uploads/2014/10/ScreenClip-61.png)

The Navisworks Batch Utility will convert every Revit file to a NWC cache file, and made it a NWD on the run.

&nbsp;