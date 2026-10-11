---
title: "D1 First Part"
weight: 1
---

## Goal

Make your first 3D part: a small block with a hole through it, with exact sizes. By the end you will have a part you could 3D print.

## What you need

A Chrome browser and your Onshape account (see the Design page). Time: about 30 to 40 minutes.

## Steps

### 1. Make a document

Sign in to Onshape. Click Create, then Document. Name it "D1 First Part - (your name)".

{{% checkpoint %}}
**Checkpoint:** you see a blank workspace with three planes (Top, Front, Right) and a feature list on the left.
{{% /checkpoint %}}

### 2. Start a sketch

Click the Top plane in the feature list. Then click the Sketch button in the toolbar (a square with a pencil). The view turns to look straight down at the plane.

{{% checkpoint %}}
**Checkpoint:** the toolbar now shows sketch tools like Line, Corner rectangle and Circle.
{{% /checkpoint %}}

### 3. Draw a rectangle

Click Corner rectangle. Click once near the center point (the origin) and click again up and to the right to finish the rectangle.

{{% checkpoint %}}
**Checkpoint:** you see a rectangle that is not yet sized.
{{% /checkpoint %}}

### 4. Set exact sizes

Click the Dimension tool. Click the bottom edge of the rectangle, move the mouse away, click, and type 40. Press Enter. Click the left edge, click, and type 30. Press Enter.

{{% checkpoint %}}
**Checkpoint:** the rectangle is 40 mm wide and 30 mm tall, and its lines turn black. Black means fully fixed. If a line is still blue, add another dimension or ask for help.
{{% /checkpoint %}}

### 5. Add a hole to the sketch

Click Circle. Click near the middle of the rectangle and drag out a circle. Click the Dimension tool, click the circle edge, and type 8 for the diameter. Then dimension the circle center from the left edge (20) and from the bottom edge (15).

{{% checkpoint %}}
**Checkpoint:** the circle is black and sits in the middle of the rectangle.
{{% /checkpoint %}}

### 6. Finish the sketch

Click the green check mark (Accept) at the top right of the sketch.

{{% checkpoint %}}
**Checkpoint:** Sketch 1 appears in the feature list.
{{% /checkpoint %}}

### 7. Extrude into 3D

Click Extrude in the toolbar. Click inside the rectangle but outside the circle. Type 10 for the depth. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** you have a 40 x 30 x 10 mm block with a round hole through it. Use the view cube to turn it and look at it from every side.
{{% /checkpoint %}}

### 8. Name it

Right-click Part 1 in the Parts list and choose Rename. Call it "block". Rename Sketch 1 to "block outline" the same way.

## Try it

- Change the hole size: double-click Sketch 1, change the circle dimension to 12, accept, and watch the part update.
- Add a second hole of your own.
- Change the block thickness by double-clicking the Extrude feature and changing 10 to 5.

## What's happening

A sketch is a flat drawing with exact sizes. Extrude gives it thickness. Every step is saved as a feature in the list, so you can go back and change a number and the whole part updates. This is called parametric design, and it is how real engineers work.

## If it doesn't work

- **The Extrude shows nothing:** make sure you clicked inside the rectangle and that you accepted the sketch first.
- **Lines stay blue:** add a dimension to each one that is still blue.
- **The part looks flat or weird:** use the view cube in the top right and click a corner to see it in 3D.
- **You made a mistake:** press <kbd>Ctrl+Z</kbd> to undo.

{{% admonition type="note" title="Note" %}}
Menu names and button positions are written from memory and have not been tested yet. Teacher: please check against the live Onshape screen.
{{% /admonition %}}
