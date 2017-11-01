---
layout: article
title: Implementing drag and drop
date: 2017-10-31 00:47:00+0200
coverPhoto: https://www.theodo.fr/uploads/blog//2017/04/drag-and-drop-cover1.png
---

![](https://www.theodo.fr/uploads/blog//2017/04/drag-and-drop-cover1.png)
Drag and drop functionality available since api level 11. It's not only supports drag'n drop in your app, but it also allow you multi-window dragging. Basic steps to include this to your app would be:
* Register drop target
* Initiate a drag and drop operation
* Drop target is notified of operation progress  
* Drop target renders as desire
* If content dropped in target, do somethink useful

1. Register drop target is done throw setting ``setOnDragListener()`` on the View. Supply implementation of ``onDrag()`` method  
2. Start a drag operation by calling ``boolean startDrag (ClipData data,
                View.DragShadowBuilder shadowBuilder,
                Object myLocalState,
                int flags)`` or ``onStartDragAndDrop() (7.0+)``  
  * ClipData represents the content being dragged. Created by factory method(e.g. ClipData.newPlainText())
  * View.DragShadowBuilder for what user sees. Pass View to constructor
  * 'Local state' object
  * Flags
3. DragEvent ACTIONS  
  * ``ACTION_DRAG_STARTED``, somewhere, somethink called startDrag(). Return true if u want be drop target.
  * ``ACTION_DRAG_ENTERED``, edge of shadow has crossed edge of drop target
  * ``ACTION_DRAG_LOCATION``, the shadow moved but is still in drop target
  * ``ACTION_DRAG_EXITED``, the shadow left drop target
  * ``ACTION_DROP``, you drop target where user drop data
