---
id: 1177
title: A new version of Group Clashes
date: 2017-05-15T09:56:12+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1177
permalink: /2017/05/a-new-version-of-group-clashes/
categories:
  - Coordination
tags:
  - Automation
  - Coordination
  - Navisworks
---
I just updated my Clash Grouper plugin for Navisworks.

The main purpose of this update was to solve some issue encountered by early adopters. The plugin should now be more stable. Many thanks to the users who contributed to this release with their feedback and test models.

I also add some new features to the application, that I will showcase with this example. Detecting clashes in this simple layout of ducts (Selection A, in blue) and pipes (Selection B, in red) yield 8 clashes, spread like this:

<div id="attachment_1179" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/05/1.png"><img class="size-large wp-image-1179" src="https://bim42.com/wp-content/uploads/2017/05/1-1024x475.png" alt="" width="584" height="271" srcset="https://bim42.com/wp-content/uploads/2017/05/1-1024x475.png 1024w, https://bim42.com/wp-content/uploads/2017/05/1-300x139.png 300w, https://bim42.com/wp-content/uploads/2017/05/1-768x356.png 768w, https://bim42.com/wp-content/uploads/2017/05/1-500x232.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    An example of a clash test
  </p>
</div>

# Creating subgroups

Grouping with two condition will now create a first group per the first rule. It will then divide this first group into subgroups, following the second rule.

If we group this example by Selection A (the ducts), we get the following groups, named after the item used to create the group. All clashes involving the same item from selection A are grouped together:

<div id="attachment_1180" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/05/2.png"><img class="size-large wp-image-1180" src="https://bim42.com/wp-content/uploads/2017/05/2-1024x475.png" alt="" width="584" height="271" srcset="https://bim42.com/wp-content/uploads/2017/05/2-1024x475.png 1024w, https://bim42.com/wp-content/uploads/2017/05/2-300x139.png 300w, https://bim42.com/wp-content/uploads/2017/05/2-768x356.png 768w, https://bim42.com/wp-content/uploads/2017/05/2-500x232.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Grouping by Selection A
  </p>
</div>

If we add a new group rule, say, by grid intersection, the plugin will break these groups into subgroup, according to this new rule. Here, it will rename the existing group by adding the nearest grid intersection name, and break the group {Clash 7, Clash 8} into two, each one belonging to a different grid intersection.

<div id="attachment_1181" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/05/3.png"><img class="size-large wp-image-1181" src="https://bim42.com/wp-content/uploads/2017/05/3-1024x475.png" alt="" width="584" height="271" srcset="https://bim42.com/wp-content/uploads/2017/05/3-1024x475.png 1024w, https://bim42.com/wp-content/uploads/2017/05/3-300x139.png 300w, https://bim42.com/wp-content/uploads/2017/05/3-768x356.png 768w, https://bim42.com/wp-content/uploads/2017/05/3-500x232.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Grouping by Selection A and Grids
  </p>
</div>

# Keep existing groups

You can now keep existing groups, so the Group Clashes will run only on the remaining clashes. This open more possibilities for complex workflows to group and sort clash results.

For example, you can group by status, explode the &#8220;Active&#8221; group and keep this &#8220;Approved&#8221; group. After running again the grouping function by level, it will only take into account the clash result, and keep the &#8220;Approved&#8221; group intact, allowing you to focus on &#8220;Active&#8221; group

Another example, if we create manually the following group in our previous clash test:

<div id="attachment_1182" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/05/4.png"><img class="size-large wp-image-1182" src="https://bim42.com/wp-content/uploads/2017/05/4-1024x475.png" alt="" width="584" height="271" srcset="https://bim42.com/wp-content/uploads/2017/05/4-1024x475.png 1024w, https://bim42.com/wp-content/uploads/2017/05/4-300x139.png 300w, https://bim42.com/wp-content/uploads/2017/05/4-768x356.png 768w, https://bim42.com/wp-content/uploads/2017/05/4-500x232.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    An existing group
  </p>
</div>

We can then run a Group by Grid intersection on the remaining clashes to create the following groups for the remaining clashes, without disturbing the existing group.

<div id="attachment_1178" style="max-width: 594px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/05/5.png"><img class="size-large wp-image-1178" src="https://bim42.com/wp-content/uploads/2017/05/5-1024x475.png" alt="" width="584" height="271" srcset="https://bim42.com/wp-content/uploads/2017/05/5-1024x475.png 1024w, https://bim42.com/wp-content/uploads/2017/05/5-300x139.png 300w, https://bim42.com/wp-content/uploads/2017/05/5-768x356.png 768w, https://bim42.com/wp-content/uploads/2017/05/5-500x232.png 500w" sizes="(max-width: 584px) 100vw, 584px" /></a>
  
  <p class="wp-caption-text">
    Remaining clashes are grouped
  </p>
</div>

# Batch grouping

You can now select multiple clash tests to apply the same grouping rules to all of them

<div id="attachment_1183" style="max-width: 339px" class="wp-caption aligncenter">
  <a href="https://bim42.com/wp-content/uploads/2017/05/Batch.gif"><img class="size-full wp-image-1183" src="https://bim42.com/wp-content/uploads/2017/05/Batch.gif" alt="" width="329" height="512" /></a>
  
  <p class="wp-caption-text">
    Batch processing
  </p>
</div>

Along these new features, a few corrections have been made. Some groups where not properly named, this is now corrected, and these groups names should now be more meaningful. Handling missing grids or levels is now better managed, and the application should be generally more stable.

As usual, you will find this new version of Group Clashes on the [Autodesk App Store](https://apps.autodesk.com/NAVIS/en/Detail/Index?id=7544208847822212204&appLang=en&os=Win64). If you want to develop your own grouping rules, you can also find the entire source code on [Github](https://github.com/simonmoreau/GroupClashes).

Happy grouping!