---
title: "D2 Sphere and Shapes"
weight: 2
---

## Goal

Build a round part by spinning a sketch, then round off an edge and cut a hole. By the end you will have a small dome (half a sphere) with a flat base, a rounded rim and a hole in the top.

## What you need

Onshape, and your D1 skills (sketch, dimension, extrude). Time: about 40 minutes.

## Steps

### 1. Make a new document

Create a document named "D2 Sphere - (your name)".

{{% checkpoint %}}
**Checkpoint:** blank workspace with three planes.
{{% /checkpoint %}}

### 2. Sketch half a circle

Click the Front plane, then Sketch. Click Line and draw a vertical line starting at the origin and going straight up. Then click the Three point arc tool (in the Circle group or the arc tool in the toolbar). Click the top end of the line, click the point on the right side at the same height as the origin, and drag to curve the arc. Finish with a line along the bottom, from the arc end back to the origin.

{{% checkpoint %}}
**Checkpoint:** you have a closed shape that looks like a quarter circle with the corner at the origin.
{{% /checkpoint %}}

### 3. Set the size

Click Dimension and click the bottom line. Type 30. Press Enter. Click the vertical line and type 30. Press Enter. Make sure the arc is centered on the origin; if the shape is still blue, add a Coincident constraint between the arc center and the origin or ask for help.

{{% checkpoint %}}
**Checkpoint:** the quarter circle is 30 mm in radius and its lines are black.
{{% /checkpoint %}}

### 4. Accept the sketch

Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** Sketch 1 is in the feature list.
{{% /checkpoint %}}

### 5. Revolve

Click Revolve in the toolbar. Click inside the shape for the sketch region. For the axis, click the vertical line on the left. Leave the angle at 360 degrees. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** you have a solid dome. Use the view cube to look at it from the side and from above.
{{% /checkpoint %}}

### 6. Round the rim

Click Fillet in the toolbar. Click the bottom circular edge of the dome. Type 3 for the radius. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** the bottom edge is now smooth and rounded.
{{% /checkpoint %}}

### 7. Cut a hole in the top

Click the Top plane and start a new sketch. Draw a circle centered on the origin and dimension it 6 mm in diameter. Accept the sketch. Click Extrude, click inside the circle, choose Remove, and set the end type to Through all. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** there is a hole straight through the top of the dome.
{{% /checkpoint %}}

### 8. Name your work

Rename Part 1 to "dome".

## Try it

- Change the sphere size: double-click Sketch 1 and change both 30s to 20.
- Change the fillet radius from 3 to 6.
- Make a full sphere by drawing a half circle instead of a quarter circle.
- Make a bowl: use the Shell tool on the dome, click the flat bottom face, and set the thickness to 2.

## What's happening

Revolve spins a flat sketch around a line, like a pot on a potter's wheel. Anything round (a ball, a cup, a bottle) can be made this way. Fillet rounds sharp edges, which also makes a 3D print stronger. Extrude with Remove cuts material away instead of adding it.

## If it doesn't work

- **Revolve gives an error:** the sketch must be closed (no gaps) and the axis must be a straight line on the edge of the shape.
- **The fillet fails:** try a smaller radius, such as 1.
- **You cannot click a face you want:** use the view cube to turn the part, then try again.
- **You made a mistake:** press <kbd>Ctrl+Z</kbd> to undo.

{{% admonition type="note" title="Note" %}}
Menu names and button positions are written from memory and have not been tested yet. Teacher: please check against the live Onshape screen, especially step 2, the arc tool, and step 7.
{{% /admonition %}}
