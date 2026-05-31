# Market context

This page describes where FoamSync sits in the hot-wire CAM landscape.
It does not name specific competitors. The aim is to make the
practical differences clear so an operator evaluating options knows
what to compare against and on what.

## The shape of the current landscape

Hot-wire CNC foam cutting has historically been served by a patchwork
of tools, often assembled from:

- A general-purpose 2D CAD application — for designing the cut
  profiles.
- A dedicated foam-cutting CAM, or a generic CAM with a hot-wire
  post-processor — for translating profiles into machine motion.
- A separate G-code sender — for connecting to the machine and
  streaming the file.
- One or more standalone heater controllers — usually as physical
  hardware bolted on.

For many shops this works, but it costs the operator the time to be
fluent in three or four tools, to maintain the bridges between them,
and to handle 4-axis tapered work as an edge case rather than as the
primary mode. Architectural work — domes, vaults, formwork — is
rarely supported with parametric generators in any of these tools;
operators either build that geometry by hand in CAD or buy bespoke
scripts.

## Where FoamSync is positioned

FoamSync is a single application that covers the operator's full
chain — drawing or parametric input, scene layout, nesting, 4-axis
toolpath, machine control, live cutting — with no external sender,
no separate post-processor, and the heater handled as a first-class
subsystem. The application is built specifically around 4-axis
hot-wire mechanics and around production-floor workflow.

## Practical differences

The following are typical points of friction in assembled
toolchains, and the way FoamSync addresses them.

### A behaving virtual machine, not a static preview

Assembled toolchains can show you a picture of a toolpath. FoamSync
ships a virtual 4-axis machine (Virtual GRBL): selecting the virtual
driver makes the whole application run as if a real cutter were
connected — homing, interpolated jog, full job execution with the wire
animating along the path, live feed override, simulated heater, and the
pre-cut wire-safety pass. This lets a shop evaluate the software, build
and verify a part library, and train operators **before the machine is
on the floor**, then run the same program 1:1 on the real controller.
We are not aware of another hot-wire CAM that ships a behaving virtual
machine rather than a static preview. See
[virtual-machine.md](virtual-machine.md).

### Architectural generators are first-class

Parametric generators for domes (radial, with solid / oculus / no
top-cap), barrel vaults, and building-block walls with rounded
openings are included in the BUILD pack. Architectural foam shops
typically do this work by hand in CAD; FoamSync makes it parametric.

### Wing geometry as a first-class 4-axis problem

NACA-4 generators, tapered wings using independent root and tip
profiles, and spar-slot cut-outs (up to three per wing) with bridge
support. Independent X/Y vs U/V tower motion is the default model —
taper and sweep are normal output, not an exception reached with a
post-processor flag.

### Pre-cut wire-safety check

Before every cut, the wire path is analysed against the machine's
maximum lean angle (set in machine setup). The report includes max
and average wire angle, lean components, violation counts at three
severity levels, and plain-language recommendations. Wire snap is
the most expensive failure mode of a hot-wire CNC; the check exists
to catch paths that would cause it.

### Nesting that understands tilted sweeps

The packer operates on the union of top and bottom contours, so
4-axis tilted sweeps nest correctly — not just their flat outlines.
Per-generator strategies (shelf-row stacking for BUILD parts,
pair-interlock for pipe shells) cluster parts that would pack poorly
on their own.

### Built-in heater control with modal safety

Heater is a first-class subsystem: external, board PWM, or board
PID. Switching from external to a board-driven mode requires an
acknowledgement that confirms fuse, detector, and attended operation.
Standalone heater controllers are common; integrating heat into the
cut application is not.

### Material library that calibrates to your batch

Kerf, feed, and temperature presets per material grade are not just
defaults — Material Cal tunes each preset from a small reference cut
so the next run starts from real batch behaviour. Foam batches vary;
storing per-batch behaviour eliminates the "every fresh batch needs
guessing" cycle.

### Single window

The CAM, the nesting, the toolpath, the machine connection, the DRO,
the jog, the emergency stop, and the live feed override all live in
the same window. No exporting between tools. No separate sender. The
operator does not switch context to deal with the machine.

### Multi-firmware auto-detect

Connect the controller and FoamSync recognises Marlin, GRBL, or
GRBL-H-Par on its own. No manual post-processor profile to pick; no
firmware-specific configuration files to maintain.

### One-tap wire-zero

Setting the wire origin from the current position is a single click —
not a multi-step touch-off ritual managed through an external sender.

### Production-floor controls

The interface is built around what a production operator needs in
front of them: a persistent emergency stop, configurable Quick
Actions, live feed override, structured Quick Lab calibration, and a
log panel with severity levels — all visible without leaving the
window during a cut.

## What FoamSync is not

FoamSync is built specifically for 4-axis hot-wire foam cutters. It
does not target:

- Router or mill CAM.
- 3D-printing slicers.
- General-purpose CAD.

If your shop runs other machines alongside the foam cutter, FoamSync
sits beside the tools that serve those — not above them — and is
responsible only for the foam-cutting chain.

## Next

- [Features](features.md)
- [Workflow](workflow.md)
- [Tiers and packs](tiers-and-packs.md)
