# Features

A capability reference. Tier dependencies are noted per item; the
[tiers and packs](tiers-and-packs.md) page has the matrix view.

## Generators

### SHAPES (every tier)

Primitive shapes and **SVG import**. Any 2D drawing brought in as SVG
becomes cut profiles — closed contours map to cuts. Manual G-code
editing is also available from this mode.

### BUILD pack — architectural

- **Dome generator.** A radial dome divided into rings × sectors.
  Configure the outer radius, wall thickness, ring count, and sector
  count. Choose a **solid** top-cap, an **oculus** (open top), or
  **no** cap. Optional **lock recesses** and an **exterior reveal
  rabbet** for visible joints. The preview shows the dome in 3D and a
  plan view, together with a material bill (panels, blocks, edging
  metres).
- **Vault generator.** A barrel vault with custom **span**, **height**,
  and arch profile. The building length defines the number of ring
  panels.
- **Building generator.** Building-block walls with
  **rounded-corner openings**.

### AERO pack — 4-axis airfoils

- **NACA-4 airfoil generator.** Any 4-digit code, chord, and
  thickness. Configurable point density for the profile.
- **Cylinder or tapered wings.** A tapered wing uses different
  **root** and **tip** profiles (for example, NACA 8612 root, NACA
  4408 tip); FoamSync sweeps the wire between them.
- **Spar-slot cut-outs** with **bridge support** — pockets for wing
  spars, with uncut bridges so the plug stays in place during the
  cut.
- **Up to 3 spar slots per wing** (main / rear / aux), each
  rectangular or round, with **bridge support** keeping the plug in
  place during the cut.

### THERMAL pack — insulation

- **Pipe-shell unfolder.** Cylindrical insulation jackets unrolled
  into flat cut profiles, with a **pair-interlock nester** so two
  half-shells pack into the footprint of a single full circle.
- **Thermal panel generator.** A panel with optional **half-lap
  rabbet** side joints and optional **back mounting channels**
  (count, depth, width). Auto-nested across the block; the preview
  shows the panel count per block and the joint / channel geometry.

## CAM core (every tier)

### Scene management

The CAM scene is the list of parts on the current block. Parts arrive
from a generator (**Send to CAM**) or from your library. You can
**add**, **duplicate**, **delete**, or **clear**; you can load the
selected profile onto the right tower for an independent 4-axis cut;
you can save the whole scene to your library for recall.

### REPLACE / ADD / CANCEL dispatch

When you send parts from a generator and the CAM scene already has
parts, FoamSync asks:

- **REPLACE** — clear the scene and load only the new block.
- **ADD** — keep the existing parts and consolidate the new block
  onto the same physical foam block.
- **CANCEL** — leave the CAM scene as it is.

No silent overwrites and no silent merges.

### Transforms

- **X-Pos / Y-Offset / Height** — position and size on the block.
- **ROT 90°** — rotate the part.
- **MIRROR H / MIRROR V** — mirror horizontally or vertically.
- **SWAP L ↔ R (4-AXIS)** — swap which tower cuts which profile on a
  tapered or asymmetric part.

### Auto-nesting

The packer operates on the **union of top and bottom contours**, so
tilted 4-axis sweeps nest correctly — not just the flat outline.
Per-generator strategies (shelf-row stacking for BUILD parts,
pair-interlock for pipe shells) pack tighter than naive single-part
nesting. Re-nest any time with **RE-NEST**.

### Collision check

If two parts overlap in the cut volume, FoamSync highlights the
collision zones in the 3D viewport (translucent red boxes). Resolve
the overlap — move or re-nest parts — before cutting.

### Wire-safety validation

A pre-cut pass against the machine's maximum wire angle (set in
machine setup). The report includes:

- **Status** — SAFE, or a warning at one of three severity levels.
- **Max and average wire angle**, **max strain**, and the horizontal
  / vertical components of the lean.
- **Violation counts** — warnings (over the limit), danger
  (over 1.5× the limit), critical (over 2× the limit).
- **Recommendations** — plain-language next steps.

A SAFE result means the path stays within the wire's safe lean for
your span. Anything above the limit is flagged with diagnostics
before motion.

### Toolpath generation

Press **GENERATE TOOLPATH** to produce the dense 4-axis path; the 3D
viewport fills with the wire trajectory. The **JOB** status reads
IDLE / READY / DANGER (review required) with line counts and an ETA.

## Virtual machine — Virtual GRBL (every tier)

A built-in, **behaving** virtual 4-axis hot-wire machine. Select
**VIRTUAL_DRIVER** instead of a COM port and the whole application runs
as if a real cutter were connected — not a static preview, but a machine
that responds to the same commands:

- Homing and smooth interpolated jog.
- Full job execution: START runs the G-code end to end, the wire
  animates along the real path, the DRO and live wire-angle update, the
  ETA counts down.
- Live **FEED %** override changes the simulated wire speed.
- Simulated heater warm-up with a live temperature readout.
- **PAUSE / RESUME / EMERGENCY STOP** and the pre-cut wire-safety pass
  behave exactly as on hardware.

It lets you evaluate the product, build and verify a part library, and
train operators with no machine attached — then run the same program
1:1 on the real controller. Full page: [virtual-machine.md](virtual-machine.md).

## Machine control (every tier)

### Connection

Pick the COM port and press **CONNECT**. FoamSync handshakes, detects
the firmware (**Marlin**, **GRBL**, or **GRBL-H-Par**), and
configures itself. The log streams connection events with severity
(ERR / WARN / OK / INFO / DEBUG).

### Live DRO

A four-axis (or 4+5 with the optional rotational axis) DRO shows the
live position of each axis. The machine state (ON / READY / RUN /
ALARM), the live wire angle, and the active heater mode are visible
alongside.

### On-screen jog

Arrow keys move the machine. **STEP** selects how far each press
travels (1 / 10 / 50 mm). **⌂** homes the machine.

### Quick Actions

Configurable shortcuts plus four built-ins:

- **ZERO** — set the wire origin from the current position in one
  tap.
- **RETRACT** — back the wire off the part.
- **PARK** — send the towers to a safe parked position.
- **HEATER** — toggle or open heat control.

### Emergency stop

A persistent red **EMERGENCY STOP** bar across the top of the window
halts everything immediately. After an e-stop, home the machine
before continuing.

### Cut control

- **START** — begin the cut. If the JOB banner reads DANGER, START
  opens the review first so you confirm the flagged path.
- **PAUSE** — hold motion mid-cut; resume from where you stopped.
- **STOP** — end the job.
- **FEED %** — override the feed rate live (slow to 50 % through a
  tricky section, for example) without regenerating.

## Heater control (every tier)

Three modes, selectable per machine:

- **External** — you drive the heater (dimmer or PSU); FoamSync only
  moves the wire. This is the recommended default.
- **Board PWM** — the controller drives the heater open-loop at a
  power %.
- **Board PID** — the controller holds a target temperature,
  closed-loop.

Switching from External to a board-driven mode requires a one-time
safety acknowledgement per release (fuse, detector, attended
operation).

## Material library (every tier)

Built-in presets for **EPS** (three grades), **XPS** (two grades),
and **PU**, plus your own **custom** materials. Each preset stores
kerf, feed, temperature, and power. The **Material Cal** step in
Quick Lab tunes each preset to the actual foam batch from a small
reference cut, so the next run starts from real batch behaviour.

## Calibration (Quick Lab)

A five-step structured calibration that persists between sessions:

1. **STATUS** — driver, firmware, licence, and the last pre-flight
   result.
2. **SETUP CHECK** — pre-flight checklist (E-stop, wire tension,
   fuse, foam stock).
3. **MOTION TEST** — square check, travel limits, backlash per axis.
4. **WIRE CAL** — kerf calibration from a reference cube measured at
   eight points.
5. **MATERIAL CAL** — tune the active material from a small reference
   cut, scored on five quality axes.

## Library

A built-in library stores generated scenes and parts for later
recall. Each entry is versioned so you can replay an older version;
the library accepts new parts from any generator.

## Diagnostics

- **Diag bundle export.** A single click exports a diagnostic report
  (system info, application log tail, current state, Machine ID) you
  can send to support.
- **Pre-flight banner.** Quick Lab steps surface at the top of the
  window when an action requires them.
- **Live log.** A scrolling panel shows every action with severity
  (ERR / WARN / OK / INFO / DEBUG).

## Studio tier extras

- **Three machine seats.**
- **CRM webhook integration** — push customer and job records to your
  own CRM through a webhook.
- **Priority support** with onboarding.

## Next

- [Workflow](workflow.md)
- [Tiers and packs](tiers-and-packs.md)
- [Supported hardware](hardware.md)
