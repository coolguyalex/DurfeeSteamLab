---
title: "Design Lab Guide"
toc: true
description: "Three projects in Onshape, from a first sketch to a printable enclosure."
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)
  toc: true  = show a contents list at the top

A LAB GUIDE: all the Design lessons on one page. It is built the same way as
resources/arduino/lab-guide.md: one ## heading per lesson with a fixed {#address}, ### headings
inside each lesson, and --- between lessons.
-->

Three projects in Onshape, from a first sketch to a printable enclosure.

## Before you start {#before-you-start}

### Set up

1. Ask in room 3106 which account to use for Onshape (the free Education plan).
2. Go to onshape.com and sign in.
3. Click Create, then Document. Name it with your name and the project, for example "D1 First Part - Sam".
4. Use millimeters. If your document shows inches, change it: click your name (top right), then My account, then Preferences, and set the length unit to millimeters.
5. Save your work often. Onshape saves automatically, but check that the document name appears in your list of documents.

### Five tools you will use

- **Sketch** - a flat drawing made of lines, rectangles and circles.
- **Dimension** - a number that sets an exact size.
- **Extrude** - pushes a flat sketch out into a solid.
- **Revolve** - spins a sketch around a line to make a round solid.
- **Fillet and Shell** - round off edges, and hollow out a solid.

### Moving around

Use the cube in the top right corner to look at your part from the front, top, side or any corner. Click a face of the cube to snap to that view. Scroll to zoom. A mouse makes this easier than the trackpad.

### Good practice

- Always set a size for every sketch line. If a line is blue, it can still move. If it is black, it is fully fixed.
- Name your parts and your sketches so you can find them later.
- Ask before you delete something you didn't make.

### Terms

- **Sketch:** a flat drawing that becomes a 3D shape.
- **Plane:** the flat surface a sketch is drawn on. **Onshape starts with three:** Top, Front and Right.
- **Feature:** one step in building a part, like Extrude or Fillet. Features appear in a list on the left, in order.
- **Part:** the solid object you made.
- **STL:** the file type a 3D printer reads.


---

## D1 First Part {#d1-first-part}

### Goal

Make your first 3D part: a small block with a hole through it, with exact sizes. By the end you will have a part you could 3D print.

### What you need

A Chrome browser and your Onshape account (see the Design page). Time: about 30 to 40 minutes.

### Steps

#### 1. Make a document

Sign in to Onshape. Click Create, then Document. Name it "D1 First Part - (your name)".

{{% checkpoint %}}
**Checkpoint:** you see a blank workspace with three planes (Top, Front, Right) and a feature list on the left.
{{% /checkpoint %}}

#### 2. Start a sketch

Click the Top plane in the feature list. Then click the Sketch button in the toolbar (a square with a pencil). The view turns to look straight down at the plane.

{{% checkpoint %}}
**Checkpoint:** the toolbar now shows sketch tools like Line, Corner rectangle and Circle.
{{% /checkpoint %}}

#### 3. Draw a rectangle

Click Corner rectangle. Click once near the center point (the origin) and click again up and to the right to finish the rectangle.

{{% checkpoint %}}
**Checkpoint:** you see a rectangle that is not yet sized.
{{% /checkpoint %}}

#### 4. Set exact sizes

Click the Dimension tool. Click the bottom edge of the rectangle, move the mouse away, click, and type 40. Press Enter. Click the left edge, click, and type 30. Press Enter.

{{% checkpoint %}}
**Checkpoint:** the rectangle is 40 mm wide and 30 mm tall, and its lines turn black. Black means fully fixed. If a line is still blue, add another dimension or ask for help.
{{% /checkpoint %}}

#### 5. Add a hole to the sketch

Click Circle. Click near the middle of the rectangle and drag out a circle. Click the Dimension tool, click the circle edge, and type 8 for the diameter. Then dimension the circle center from the left edge (20) and from the bottom edge (15).

{{% checkpoint %}}
**Checkpoint:** the circle is black and sits in the middle of the rectangle.
{{% /checkpoint %}}

#### 6. Finish the sketch

Click the green check mark (Accept) at the top right of the sketch.

{{% checkpoint %}}
**Checkpoint:** Sketch 1 appears in the feature list.
{{% /checkpoint %}}

#### 7. Extrude into 3D

Click Extrude in the toolbar. Click inside the rectangle but outside the circle. Type 10 for the depth. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** you have a 40 x 30 x 10 mm block with a round hole through it. Use the view cube to turn it and look at it from every side.
{{% /checkpoint %}}

#### 8. Name it

Right-click Part 1 in the Parts list and choose Rename. Call it "block". Rename Sketch 1 to "block outline" the same way.

### Try it

- Change the hole size: double-click Sketch 1, change the circle dimension to 12, accept, and watch the part update.
- Add a second hole of your own.
- Change the block thickness by double-clicking the Extrude feature and changing 10 to 5.

### What's happening

A sketch is a flat drawing with exact sizes. Extrude gives it thickness. Every step is saved as a feature in the list, so you can go back and change a number and the whole part updates. This is called parametric design, and it is how real engineers work.

### If it doesn't work

- **The Extrude shows nothing:** make sure you clicked inside the rectangle and that you accepted the sketch first.
- **Lines stay blue:** add a dimension to each one that is still blue.
- **The part looks flat or weird:** use the view cube in the top right and click a corner to see it in 3D.
- **You made a mistake:** press <kbd>Ctrl+Z</kbd> to undo.

{{% admonition type="note" title="Note" %}}
Menu names and button positions are written from memory and have not been tested yet. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}


---

## D2 Sphere and Shapes {#d2-sphere-and-shapes}

### Goal

Build a round part by spinning a sketch, then round off an edge and cut a hole. By the end you will have a small dome (half a sphere) with a flat base, a rounded rim and a hole in the top.

### What you need

Onshape, and your D1 skills (sketch, dimension, extrude). Time: about 40 minutes.

### Steps

#### 1. Make a new document

Create a document named "D2 Sphere - (your name)".

{{% checkpoint %}}
**Checkpoint:** blank workspace with three planes.
{{% /checkpoint %}}

#### 2. Sketch half a circle

Click the Front plane, then Sketch. Click Line and draw a vertical line starting at the origin and going straight up. Then click the Three point arc tool (in the Circle group or the arc tool in the toolbar). Click the top end of the line, click the point on the right side at the same height as the origin, and drag to curve the arc. Finish with a line along the bottom, from the arc end back to the origin.

{{% checkpoint %}}
**Checkpoint:** you have a closed shape that looks like a quarter circle with the corner at the origin.
{{% /checkpoint %}}

#### 3. Set the size

Click Dimension and click the bottom line. Type 30. Press Enter. Click the vertical line and type 30. Press Enter. Make sure the arc is centered on the origin; if the shape is still blue, add a Coincident constraint between the arc center and the origin or ask for help.

{{% checkpoint %}}
**Checkpoint:** the quarter circle is 30 mm in radius and its lines are black.
{{% /checkpoint %}}

#### 4. Accept the sketch

Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** Sketch 1 is in the feature list.
{{% /checkpoint %}}

#### 5. Revolve

Click Revolve in the toolbar. Click inside the shape for the sketch region. For the axis, click the vertical line on the left. Leave the angle at 360 degrees. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** you have a solid dome. Use the view cube to look at it from the side and from above.
{{% /checkpoint %}}

#### 6. Round the rim

Click Fillet in the toolbar. Click the bottom circular edge of the dome. Type 3 for the radius. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** the bottom edge is now smooth and rounded.
{{% /checkpoint %}}

#### 7. Cut a hole in the top

Click the Top plane and start a new sketch. Draw a circle centered on the origin and dimension it 6 mm in diameter. Accept the sketch. Click Extrude, click inside the circle, choose Remove, and set the end type to Through all. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** there is a hole straight through the top of the dome.
{{% /checkpoint %}}

#### 8. Name your work

Rename Part 1 to "dome".

### Try it

- Change the sphere size: double-click Sketch 1 and change both 30s to 20.
- Change the fillet radius from 3 to 6.
- Make a full sphere by drawing a half circle instead of a quarter circle.
- Make a bowl: use the Shell tool on the dome, click the flat bottom face, and set the thickness to 2.

### What's happening

Revolve spins a flat sketch around a line, like a pot on a potter's wheel. Anything round (a ball, a cup, a bottle) can be made this way. Fillet rounds sharp edges, which also makes a 3D print stronger. Extrude with Remove cuts material away instead of adding it.

### If it doesn't work

- **Revolve gives an error:** the sketch must be closed (no gaps) and the axis must be a straight line on the edge of the shape.
- **The fillet fails:** try a smaller radius, such as 1.
- **You cannot click a face you want:** use the view cube to turn the part, then try again.
- **You made a mistake:** press <kbd>Ctrl+Z</kbd> to undo.

{{% admonition type="note" title="Note" %}}
Menu names and button positions are written from memory and have not been tested yet. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}


---

## D3 Enclosure {#d3-enclosure}

### Goal

Design a small box with a lid that holds an Arduino Uno. By the end you will have two parts, a base and a lid, ready to 3D print.

### What you need

Onshape, and your D1 and D2 skills. An Arduino Uno to measure, or use these sizes: the board is about 68.6 mm long and 53.3 mm wide. Time: 60 minutes or more. Do this one over two sessions if you need to.

### Steps

#### 1. Make a new document

Create a document named "D3 Enclosure - (your name)".

#### 2. Sketch the outside of the box

Click the Top plane, then Sketch. Draw a rectangle starting at the origin. Dimension it 78 mm long and 63 mm wide. (That is the board plus 5 mm of room on every side.) Accept the sketch.

{{% checkpoint %}}
**Checkpoint:** a fully black rectangle, 78 x 63.
{{% /checkpoint %}}

#### 3. Extrude the block

Click Extrude and click inside the rectangle. Set the depth to 25. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** a solid block 78 x 63 x 25 mm.
{{% /checkpoint %}}

#### 4. Hollow it out

Click Shell in the toolbar. Click the top face of the block to remove it. Set the thickness to 2. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** the block is now an open-top box with walls 2 mm thick.
{{% /checkpoint %}}

#### 5. Cut a hole for the USB cable

Click the front outside face of the box (the short side where the USB port will be) and click Sketch. Draw a rectangle about 14 mm wide and 12 mm tall, with the bottom edge about 5 mm above the floor. Dimension it. Accept the sketch. Click Extrude, choose Remove, click inside the rectangle, and set the end type to Through all. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** there is an opening in the short wall big enough for a USB cable.
{{% /checkpoint %}}

#### 6. Rename the base

Rename the part to "base".

#### 7. Make the lid

Click the Top plane and start a new sketch. Draw a rectangle 78 x 63 again, from the origin. Accept the sketch. Click Extrude, click inside the rectangle, set the depth to 2, and under "New" choose New part (not Add), so that it makes a separate part. Click the green check mark. Rename this part "lid".

{{% checkpoint %}}
**Checkpoint:** the Parts list shows two parts, base and lid.
{{% /checkpoint %}}

#### 8. Make the lid sit on the box

Sketch on the top face of the lid part. Draw a rectangle slightly smaller than the inside of the box: 72 x 57. Center it on the lid. Extrude it 3 mm upward and join it to the lid (choose Add). This lip fits inside the box walls.

{{% checkpoint %}}
**Checkpoint:** the lid has a small raised lip on one side.
{{% /checkpoint %}}

#### 9. Look at the box and lid

Use the view cube to look at it from every side. Move the lid up (click the Move face or Transform tool) if you want to see inside.

#### 10. Export the file for printing

Right-click the tab or the part in the Parts list. Choose Export. Choose STL as the format. Export "base" and "lid" as separate files, and give them clear names. Bring them to the lab to be printed.

{{% checkpoint %}}
**Checkpoint:** you have two STL files, one for the base and one for the lid.
{{% /checkpoint %}}

### Try it

- Add a hole in the lid for an LED.
- Add text on the lid with your name.
- Make the box taller if you want room for a sensor or battery.
- Combine it with your Microcontrollers work: measure the board you actually used.

### Bridge

Shape changes sound. Build your box, tap it, and record the sound. A different box makes a different sound. You can bring that recording into Pure Data or Data Science.

### What's happening

You started with a plan: a real object with real measurements. You added a margin so the board fits. Shell hollowed the box. Separate parts let a base and a lid print as two pieces. This is the same process used to design phone cases and product housings.

### If it doesn't work

- **Shell removes the wrong face:** undo and click only the top face.
- **The lid and base merge into one part:** undo and choose New part in the Extrude options.
- **The box is too tight:** add 1 mm to each size and try again. Printers are not perfect.
- **You made a mistake:** press <kbd>Ctrl+Z</kbd> to undo.

{{% admonition type="note" title="Note" %}}
Menu names and button positions are written from memory and have not been tested yet. If a step doesn't match what you see, flag it so the page can be fixed. Arduino Uno size is approximate; check against the board you use.
{{% /admonition %}}

