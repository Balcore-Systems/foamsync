# Introduction

## What FoamSync is

FoamSync is computer-aided manufacturing (CAM) software for **4-axis
hot-wire CNC foam cutters**. An operator provides a 2D drawing or a
set of parametric inputs; FoamSync produces a 4-axis G-code program
and drives the machine through it.

It is a single Windows application — design generation, scene layout,
nesting, toolpath generation, machine control, and live cutting all
live in one window.

## What "4-axis hot-wire" means

A hot-wire CNC foam cutter typically has two motorised towers, one on
each side of the foam block. Each tower carries the wire on a
two-axis carriage — horizontal **X** and vertical **Y** on the left
tower, horizontal **U** and vertical **V** on the right. When the
towers move independently, the wire can cut a tapered shape with a
different profile on the left and right faces of the block. That
independent two-tower motion is what makes a machine "4-axis" instead
of a flat 2-axis cutter.

The wire heats by Joule effect and slices through closed-cell foam
(EPS, XPS, PU). The cut surface is the wire's lateral profile and the
heat-affected zone around it.

## Who FoamSync is for

- **Architectural and decorative foam** shops cutting domes, vaults,
  building blocks, panels, and mouldings for facade, formwork, and
  stage construction.
- **RC and aerodynamic builders** cutting NACA and tapered airfoils
  with spar slots.
- **Insulation** shops cutting pipe shells and panel stock.
- Operators of in-house or vendor-supplied 4-axis hot-wire machines
  who want a single, supported tool instead of an assembled chain of
  CAD plus CAM plus sender plus standalone heater controller.

## What you do with it

A typical session takes one of two starting points:

1. **Parametric input.** Pick a generator (dome, vault, building,
   NACA, pipe shell, thermal panel), set the parameters (radius,
   span, thickness, chord, panel count), press **Generate**.
2. **SVG import.** Bring in a 2D profile from your CAD; FoamSync
   turns closed contours into cut profiles.

From there:

3. **Scene layout.** Arrange parts on the CAM scene — position,
   rotate, mirror — with auto-nesting on a foam block of declared
   dimensions.
4. **Toolpath.** Generate the 4-axis G-code with the collision check
   and the wire-safety validation pass.
5. **Cut.** Connect the controller, home the machine, dry-run if
   needed, then start. The live DRO, the jog, the emergency stop,
   and the feed override are all in the same window.

The detailed walk-through is in [workflow.md](workflow.md).

## How licensing works

FoamSync is licensed software. A fresh install runs in a **7-day
trial mode** — every feature is previewed for evaluation, real
machines run in virtual mode. To enable production output and
real-machine connections, buy a licence via the Telegram bot and
activate it. Activation is either online (paste the key) or offline
(load a licence file from your distributor). Details:
[activation.md](activation.md).

## What's in this repository

This GitHub repository hosts public documentation and the issue
tracker. The application itself is downloaded from the
[website](https://foamsyncstudio.com/download/).

## Next

- [Installation](installation.md)
- [Activation](activation.md)
- [Features](features.md)
- [Workflow](workflow.md)
