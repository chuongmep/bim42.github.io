---
id: 584
title: Revisions and Revision Clouds
date: 2014-09-20T10:49:34+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=584
permalink: /2014/09/revisions-and-revision-clouds/
categories:
  - Revit
tags:
  - Autodesk
  - Coordination
  - Documentation
  - Revit
---
To highlight modifications or issues on Revit drawings, Autodesk provide us with one of the oldest change tracking device, the revision cloud, and a set of high tech features to handle it.

The workflow promoted here is to add a handful of revision clouds wherever they are needed, and link these revision clouds with metadata describing the issue.

In Revit, every revision cloud is associated with a revision, as we can see in the Properties panel of our revision cloud.

![<img class="aligncenter size-full wp-image-594" src="http://bim42.com/wp-content/uploads/2014/09/RevisionCloudProperties.png" alt="RevisionCloudProperties" width="330" height="169" srcset="https://bim42.com/wp-content/uploads/2014/09/RevisionCloudProperties.png 330w, https://bim42.com/wp-content/uploads/2014/09/RevisionCloudProperties-300x153.png 300w" sizes="(max-width: 330px) 100vw, 330px" />](http://bim42.com/wp-content/uploads/2014/09/RevisionCloudProperties.png)

These revisions are managed in the Sheets Issues/Revisions panel, and can be seen as issues to be addressed.

![<img class="aligncenter size-full wp-image-595" src="http://bim42.com/wp-content/uploads/2014/09/RevisionsPanel.png" alt="RevisionsPanel" width="924" height="509" srcset="https://bim42.com/wp-content/uploads/2014/09/RevisionsPanel.png 924w, https://bim42.com/wp-content/uploads/2014/09/RevisionsPanel-300x165.png 300w, https://bim42.com/wp-content/uploads/2014/09/RevisionsPanel-500x275.png 500w" sizes="(max-width: 924px) 100vw, 924px" />](http://bim42.com/wp-content/uploads/2014/09/RevisionsPanel.png)

These revisions are displayed in a revision schedule, a table added to the title block family during its creation.

Every revision cloud visible in a sheet have its associated revision displayed in the revision schedule embedded in the tittle bloc. Here, I had a revision cloud on the sheet, its associated revision appears in the revision schedule of the sheet.

![<img class="aligncenter size-full wp-image-598" src="http://bim42.com/wp-content/uploads/2014/09/OneRevisions2.png" alt="OneRevisions" width="800" height="566" srcset="https://bim42.com/wp-content/uploads/2014/09/OneRevisions2.png 800w, https://bim42.com/wp-content/uploads/2014/09/OneRevisions2-300x212.png 300w, https://bim42.com/wp-content/uploads/2014/09/OneRevisions2-424x300.png 424w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/OneRevisions2.png)I can also add a revision cloud directly on the view, its revision will also appear on the revision schedule.

![<img class="aligncenter size-full wp-image-599" src="http://bim42.com/wp-content/uploads/2014/09/Revision21.png" alt="Revision2" width="800" height="566" srcset="https://bim42.com/wp-content/uploads/2014/09/Revision21.png 800w, https://bim42.com/wp-content/uploads/2014/09/Revision21-300x212.png 300w, https://bim42.com/wp-content/uploads/2014/09/Revision21-424x300.png 424w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/Revision21.png) These clouds can be hidden on a per revision basis, in the Revision panel. This command will hide every revision cloud associated with the selected revision. However, it does not remove this revision from the revision schedule.

![<img class="aligncenter size-full wp-image-601" src="http://bim42.com/wp-content/uploads/2014/09/HideCloud.png" alt="HideCloud" width="697" height="76" srcset="https://bim42.com/wp-content/uploads/2014/09/HideCloud.png 697w, https://bim42.com/wp-content/uploads/2014/09/HideCloud-300x32.png 300w, https://bim42.com/wp-content/uploads/2014/09/HideCloud-500x54.png 500w" sizes="(max-width: 697px) 100vw, 697px" />](http://bim42.com/wp-content/uploads/2014/09/HideCloud.png)

![<img class="aligncenter size-full wp-image-597" src="http://bim42.com/wp-content/uploads/2014/09/HideRevsion11.png" alt="HideRevsion1" width="800" height="566" srcset="https://bim42.com/wp-content/uploads/2014/09/HideRevsion11.png 800w, https://bim42.com/wp-content/uploads/2014/09/HideRevsion11-300x212.png 300w, https://bim42.com/wp-content/uploads/2014/09/HideRevsion11-424x300.png 424w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/HideRevsion11.png) This allows us to keep some kind of history for every issue addressed and resolved, along with their revision cloud, without having our views obscured with outdated revision clouds.

The Per project/Per sheet numbering option allows us to define if we manage our revision numbers for the whole project, or on a per sheet basis.

![<img class="aligncenter size-full wp-image-589" src="http://bim42.com/wp-content/uploads/2014/09/Numbering.png" alt="Numbering" width="167" height="78" />](http://bim42.com/wp-content/uploads/2014/09/Numbering.png)

Look at the revision numbers on the following example to understand how this work:

![<img class="aligncenter size-full wp-image-591" src="http://bim42.com/wp-content/uploads/2014/09/PerProject.png" alt="PerProject" width="800" height="352" srcset="https://bim42.com/wp-content/uploads/2014/09/PerProject.png 800w, https://bim42.com/wp-content/uploads/2014/09/PerProject-300x132.png 300w, https://bim42.com/wp-content/uploads/2014/09/PerProject-500x220.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/PerProject.png)

![<img class="aligncenter size-full wp-image-592" src="http://bim42.com/wp-content/uploads/2014/09/PerSheet.png" alt="PerSheet" width="800" height="352" srcset="https://bim42.com/wp-content/uploads/2014/09/PerSheet.png 800w, https://bim42.com/wp-content/uploads/2014/09/PerSheet-300x132.png 300w, https://bim42.com/wp-content/uploads/2014/09/PerSheet-500x220.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2014/09/PerSheet.png)

Sadly, Revit does not provided any built-in function for scheduling directly revision clouds, just like we could do with Note Block for annotation symbols. When I need a revision clouds schedule, I use Revit BIMLink from Ideate to export these revision clouds to an Excel datasheet. There is also a free tool from Case Inc. to export cloud data to a CSV file, the Revision Cloud Data Export to Text File, included in Case Revit Add-ins.