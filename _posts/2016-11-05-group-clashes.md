---
id: 1078
title: Group Clashes
date: 2016-11-05T17:05:09+00:00
author: Simon Moreau
layout: post
guid: http://bim42.com/?p=1078
permalink: /2016/11/group-clashes/
categories:
  - Coordination
tags:
  - Autodesk
  - Automation
  - Coordination
  - Navisworks
---
If you have already run some clash detection, you have probably ended up with thousand of clashes, and wondering how you could find something interesting in this mess.

[<img class="aligncenter size-full wp-image-1087" src="http://bim42.com/wp-content/uploads/2016/11/neuro.gif" alt="neuro" width="1000" height="514" />](http://bim42.com/wp-content/uploads/2016/11/neuro.gif)

Furthermore, finding clashes is not really useful in itself. The purpose of clash detection is to be able to find and hopefully solve issues in the design. And we quickly realize that a clash is not an issue in itself, but can be the symptom of an issue. Being able to extract a real issue from a meaningless bunch of clashes is what we are looking for. This is how we can gain some return from clash detection.

To do so, I tend to focus on specific subjects. Instead of running useless clash detections between entire model, I rather focus on specific issues and know beforehand what I am looking for.

For example, instead of running a clash detection between an architectural and a structural model, and end up with thousand of clashes, we can run a clash detection only between architectural rooms and structural concrete beams. As we know which type of element are involved in the clash detection, we can understand what a &#8220;clash&#8221; mean. Here, it means that there is a beam below the ceiling height. Furthermore, we can also group these clashes by room, and immediately highlight the problematic area where we can focus our efforts.

[<img class="aligncenter size-full wp-image-1086" src="http://bim42.com/wp-content/uploads/2016/11/clearHeadroom.png" alt="clearheadroom" width="800" height="470" srcset="https://bim42.com/wp-content/uploads/2016/11/clearHeadroom.png 800w, https://bim42.com/wp-content/uploads/2016/11/clearHeadroom-300x176.png 300w, https://bim42.com/wp-content/uploads/2016/11/clearHeadroom-768x451.png 768w, https://bim42.com/wp-content/uploads/2016/11/clearHeadroom-500x294.png 500w" sizes="(max-width: 800px) 100vw, 800px" />](http://bim42.com/wp-content/uploads/2016/11/clearHeadroom.png)

To help in this regards, I created a plugin for Navisworks Manage to automatically group these clashes. After a beta version published last year, I finally take the time to properly develop a full-fledged application and publish it on the [Autodesk App Store](https://apps.autodesk.com/NAVIS/en/Detail/Index?id=7544208847822212204&appLang=en&os=Win64). It is a fully redesigned Group Clashes Navisworks plugin, with a new interface that integrates seamlessly into the Navisworks interface.

[<img class="aligncenter size-full wp-image-1088" src="http://bim42.com/wp-content/uploads/2016/11/Interface.png" alt="interface" width="694" height="838" srcset="https://bim42.com/wp-content/uploads/2016/11/Interface.png 694w, https://bim42.com/wp-content/uploads/2016/11/Interface-248x300.png 248w" sizes="(max-width: 694px) 100vw, 694px" />](http://bim42.com/wp-content/uploads/2016/11/Interface.png)

The grouping rules have also been redesigned, and now include the following methods :

  * Group by Level: This rule will group clashes according to their nearest level, and name the group after the level.

[<img class="aligncenter size-large wp-image-1083" src="http://bim42.com/wp-content/uploads/2016/11/ByLevels-1024x735.png" alt="bylevels" width="584" height="419" srcset="https://bim42.com/wp-content/uploads/2016/11/ByLevels-1024x735.png 1024w, https://bim42.com/wp-content/uploads/2016/11/ByLevels-300x215.png 300w, https://bim42.com/wp-content/uploads/2016/11/ByLevels-768x551.png 768w, https://bim42.com/wp-content/uploads/2016/11/ByLevels-418x300.png 418w, https://bim42.com/wp-content/uploads/2016/11/ByLevels.png 1600w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/11/ByLevels.png)

  * Group by Grid Intersection: This rule will group clashes according to their nearest grid intersection, and name the group after these grids.

[<img class="aligncenter size-large wp-image-1082" src="http://bim42.com/wp-content/uploads/2016/11/ByGrids-1024x731.png" alt="bygrids" width="584" height="417" srcset="https://bim42.com/wp-content/uploads/2016/11/ByGrids-1024x731.png 1024w, https://bim42.com/wp-content/uploads/2016/11/ByGrids-300x214.png 300w, https://bim42.com/wp-content/uploads/2016/11/ByGrids-768x548.png 768w, https://bim42.com/wp-content/uploads/2016/11/ByGrids-420x300.png 420w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/11/ByGrids.png)

  * Group by Selection A: This rule will group all clashes belonging to an element of the selection A, and name the group after this element. As an example, if a room in Selection A has many clashes with beams in Selection B, all these clashes will be grouped.

[<img class="aligncenter size-large wp-image-1084" src="http://bim42.com/wp-content/uploads/2016/11/BySelectionA-996x1024.png" alt="byselectiona" width="584" height="600" srcset="https://bim42.com/wp-content/uploads/2016/11/BySelectionA-996x1024.png 996w, https://bim42.com/wp-content/uploads/2016/11/BySelectionA-292x300.png 292w, https://bim42.com/wp-content/uploads/2016/11/BySelectionA-768x790.png 768w, https://bim42.com/wp-content/uploads/2016/11/BySelectionA.png 1249w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/11/BySelectionA.png)

  * Group by Selection B: This rule will group all clashes belonging to an element of the selection B, and name the group after this element.

[<img class="aligncenter size-large wp-image-1085" src="http://bim42.com/wp-content/uploads/2016/11/BySelectionB-996x1024.png" alt="byselectionb" width="584" height="600" srcset="https://bim42.com/wp-content/uploads/2016/11/BySelectionB-996x1024.png 996w, https://bim42.com/wp-content/uploads/2016/11/BySelectionB-292x300.png 292w, https://bim42.com/wp-content/uploads/2016/11/BySelectionB-768x790.png 768w, https://bim42.com/wp-content/uploads/2016/11/BySelectionB.png 1249w" sizes="(max-width: 584px) 100vw, 584px" />](http://bim42.com/wp-content/uploads/2016/11/BySelectionB.png)

  * Group by Assigned To, Approved By, and Status: These three rules will use various properties of the clash to group them. As an example, you can use this rule to group all clashes assigned to you.

You can also group with two rules, the first one will rename the clash group created by the second one. This enables various possibilities, like having clashes grouped by a given selection and renamed according to the one assigned to.

Group Clashes can have difficulties in managing clash reports with more than 10 000 clashes. Be smart when you set up your clash tests, and everything will be fine.

Group Clashes is now out of beta, and you will have to pay $10 to download it on the [Autodesk App Store](https://apps.autodesk.com/NAVIS/en/Detail/Index?id=7544208847822212204&appLang=en&os=Win64).

Yet, Group Clashes is also open-source. You can find the entire source code on [Github](https://github.com/simonmoreau/GroupClashes), build your own plugin, and develop your own grouping rules.