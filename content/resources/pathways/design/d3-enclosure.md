---
title: "D3 Enclosure"
weight: 3
---

## Goal

Design a small box with a lid that holds an Arduino Uno. By the end you will have two parts, a base and a lid, ready for your teacher to 3D print.

## What you need

Onshape, and your D1 and D2 skills. An Arduino Uno to measure, or use these sizes: the board is about 68.6 mm long and 53.3 mm wide. Time: 60 minutes or more. Do this one over two sessions if you need to.

## Steps

### 1. Make a new document

Create a document named "D3 Enclosure - (your name)".

### 2. Sketch the outside of the box

Click the Top plane, then Sketch. Draw a rectangle starting at the origin. Dimension it 78 mm long and 63 mm wide. (That is the board plus 5 mm of room on every side.) Accept the sketch.

{{% checkpoint %}}
**Checkpoint:** a fully black rectangle, 78 x 63.
{{% /checkpoint %}}

### 3. Extrude the block

Click Extrude and click inside the rectangle. Set the depth to 25. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** a solid block 78 x 63 x 25 mm.
{{% /checkpoint %}}

### 4. Hollow it out

Click Shell in the toolbar. Click the top face of the block to remove it. Set the thickness to 2. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** the block is now an open-top box with walls 2 mm thick.
{{% /checkpoint %}}

### 5. Cut a hole for the USB cable

Click the front outside face of the box (the short side where the USB port will be) and click Sketch. Draw a rectangle about 14 mm wide and 12 mm tall, with the bottom edge about 5 mm above the floor. Dimension it. Accept the sketch. Click Extrude, choose Remove, click inside the rectangle, and set the end type to Through all. Click the green check mark.

{{% checkpoint %}}
**Checkpoint:** there is an opening in the short wall big enough for a USB cable.
{{% /checkpoint %}}

### 6. Rename the base

Rename the part to "base".

### 7. Make the lid

Click the Top plane and start a new sketch. Draw a rectangle 78 x 63 again, from the origin. Accept the sketch. Click Extrude, click inside the rectangle, set the depth to 2, and under "New" choose New part (not Add), so that it makes a separate part. Click the green check mark. Rename this part "lid".

{{% checkpoint %}}
**Checkpoint:** the Parts list shows two parts, base and lid.
{{% /checkpoint %}}

### 8. Make the lid sit on the box

Sketch on the top face of the lid part. Draw a rectangle slightly smaller than the inside of the box: 72 x 57. Center it on the lid. Extrude it 3 mm upward and join it to the lid (choose Add). This lip fits inside the box walls.

{{% checkpoint %}}
**Checkpoint:** the lid has a small raised lip on one side.
{{% /checkpoint %}}

### 9. Look at the box and lid

Use the view cube to look at it from every side. Move the lid up (click the Move face or Transform tool) if you want to see inside.

### 10. Export the file for printing

Right-click the tab or the part in the Parts list. Choose Export. Choose STL as the format. Export "base" and "lid" as separate files, and give them clear names. Send them to your teacher. Your teacher will print them.

{{% checkpoint %}}
**Checkpoint:** you have two STL files, one for the base and one for the lid.
{{% /checkpoint %}}

## Try it

- Add a hole in the lid for an LED.
- Add text on the lid with your name.
- Make the box taller if you want room for a sensor or battery.
- Combine it with your Microcontrollers work: measure the board you actually used.

## Bridge

Shape changes sound. Build your box, tap it, and record the sound. A different box makes a different sound. You can bring that recording into the Synthesize or Data Science pathways.

## What's happening

You started with a plan: a real object with real measurements. You added a margin so the board fits. Shell hollowed the box. Separate parts let a base and a lid print as two pieces. This is the same process used to design phone cases and product housings.

## If it doesn't work

- **Shell removes the wrong face:** undo and click only the top face.
- **The lid and base merge into one part:** undo and choose New part in the Extrude options.
- **The box is too tight:** add 1 mm to each size and try again. Printers are not perfect.
- **You made a mistake:** press <kbd>Ctrl+Z</kbd> to undo.

{{% admonition type="note" title="Note" %}}
Menu names and button positions are written from memory and have not been tested yet. Teacher: please check against the live Onshape screen, especially steps 5 to 10. Arduino Uno size is approximate; check against the board you use.
{{% /admonition %}}
