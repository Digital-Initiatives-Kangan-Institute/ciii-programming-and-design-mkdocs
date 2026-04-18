# Fused Deposition Modeling (FDM) Printing

## What is FDM Printing?
FDM stands for **Fused Deposition Modeling**, and it’s the most common and accessible form of 3D printing used in schools, makerspaces, and homes.
It works by **melting a plastic filament** and **depositing it layer by layer** to build up a 3D object from the bottom to the top.

Imagine squeezing toothpaste onto a surface in a specific pattern — each new layer stacks on the previous one until the shape is complete. That’s essentially how FDM printing works, but with melted plastic instead of toothpaste!

## Main Parts of an FDM 3D Printer 
Most FDM printers have a similar setup. Here are the key components: 

- **Filament Spool** – The roll of plastic filament that feeds into the printer.
- **Extruder** – Pulls in the filament and pushes it through a heated nozzle.
- **Hotend and Nozzle** – The filament is melted here and precisely deposited layer by layer.
- **Print Bed** – The flat surface where the model is built. Some are heated to help prints stick better.
- **Stepper Motors and Belts** – Move the print head and bed along the X, Y, and Z axes for accurate positioning.
- **Cooling Fans** – Help solidify the plastic quickly so each layer can support the next.

![FDM Printer Parts Legend](../assets/fdm-printer-parts.png){ width=600 }

## What is Filament?
**Filament** is the **plastic material** that a **3D printer melts and uses to build objects**.

In **FDM (Fused Deposition Modeling)** 3D printing, the filament comes in the form of a **long, thin strand of plastic** wound onto a spool — it looks a bit like thick fishing line or wire.

During printing, the filament is **fed into the printer’s extruder**, where it’s **heated until it melts**, then **squeezed out through a nozzle** to form each layer of the model.

![Filament Spools](../assets/filament-spools.png){ width=500 }

### Filament Sizes
Most FDM printers use filament that’s either:

- 1.75 mm in diameter (the most common), or
- 2.85 mm (used by some brands)

!!! warning
    **It’s important to match the filament size to your printer’s specifications.**

## The FDM Printing Process 
Here’s how a print usually happens:

1. **Design Your Model**
    - You start by creating or downloading a 3D model file (usually in .STL format).

2. **Slice the Model**
    - The 3D model is processed in slicing software (like OrcaSlicer, Bambu Studio or PrusaSlicer), which converts it into layers and creates instructions (called G-code) for the printer to follow.

3. **Prepare the Printer**
    - Load the filament, level the bed (to make sure the nozzle is at the correct height), and preheat the nozzle and bed.

4. **Print the Object**
    - The printer lays down the filament layer by layer, following the G-code path.

5. **Cool and Remove the Print**
    - Once complete, the print bed cools down and you can carefully remove the finished model.

## Advantages of FDM Printing
- **Affordable** – FDM printers and materials are relatively low-cost.
- **Easy to Learn** – Great for beginners and classrooms.
- **Wide Material Choice** – You can print with PLA, PETG, ABS, and many others.
- **Customizable** – Easy to adjust print settings for speed, strength, and quality.

## Challenges and Tips
While FDM printing is user-friendly, it can take some practice to get great results. 
Here are a few common challenges and how to handle them:
- **Poor Bed Adhesion**: Make sure the print bed is level and clean. Using glue stick or painter’s tape can help PLA stick better.
- **Warping**: Use a heated bed (especially for ABS) and avoid drafts in the room.
- **Stringing or Blobs**: Adjust temperature or retraction settings in the slicer.
- **Layer Shifting**: Check that belts are tight and the printer is on a stable surface.

## Class Activity 
What are some FDM filament materials? What are advantages and disadvantages with them?