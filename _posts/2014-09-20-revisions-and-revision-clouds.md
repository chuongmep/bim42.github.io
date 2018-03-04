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

![RevisionCloudProperties](/assets/2014/09/RevisionCloudProperties.png)

These revisions are managed in the Sheets Issues/Revisions panel, and can be seen as issues to be addressed.

![RevisionsPanel](/assets/2014/09/RevisionsPanel.png)

These revisions are displayed in a revision schedule, a table added to the title block family during its creation.

Every revision cloud visible in a sheet have its associated revision displayed in the revision schedule embedded in the tittle bloc. Here, I had a revision cloud on the sheet, its associated revision appears in the revision schedule of the sheet.

![OneRevisions2](/assets/2014/09/OneRevisions2.png)I can also add a revision cloud directly on the view, its revision will also appear on the revision schedule.

![Revision21](/assets/2014/09/Revision21.png) These clouds can be hidden on a per revision basis, in the Revision panel. This command will hide every revision cloud associated with the selected revision. However, it does not remove this revision from the revision schedule.

![HideCloud](/assets/2014/09/HideCloud.png)

![HideRevsion11](/assets/2014/09/HideRevsion11.png) This allows us to keep some kind of history for every issue addressed and resolved, along with their revision cloud, without having our views obscured with outdated revision clouds.

The Per project/Per sheet numbering option allows us to define if we manage our revision numbers for the whole project, or on a per sheet basis.

![Numbering](/assets/2014/09/Numbering.png)

Look at the revision numbers on the following example to understand how this work:

![PerProject](/assets/2014/09/PerProject.png)

![PerSheet](/assets/2014/09/PerSheet.png)

Sadly, Revit does not provided any built-in function for scheduling directly revision clouds, just like we could do with Note Block for annotation symbols. When I need a revision clouds schedule, I use Revit BIMLink from Ideate to export these revision clouds to an Excel datasheet. There is also a free tool from Case Inc. to export cloud data to a CSV file, the Revision Cloud Data Export to Text File, included in Case Revit Add-ins.