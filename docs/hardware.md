# Supported hardware

## Machine topology

FoamSync is built for a **4-axis hot-wire CNC** with two towers, one
on each side of the foam block. Each tower carries the wire on a
two-axis carriage — **X / Y** on the left tower, **U / V** on the
right. The wire spans between the towers; independent tower motion
produces tapered, swept, and conical cuts. Synced tower motion
produces straight (2-axis-equivalent) cuts.

A **5th rotational axis** is supported optionally — useful for parts
where the block rotates between cuts.

## Controllers and firmware

FoamSync auto-detects the firmware on connect. Supported:

| Firmware | Notes |
|---|---|
| **GRBL** | Common for hot-wire builds. Auto-detected. |
| **GRBL-H-Par** | Hot-wire parallel variant of GRBL. Auto-detected. |
| **Marlin** | Auto-detected. |

If auto-detect picks the wrong firmware or the handshake stalls, you
can set the controller explicitly under
**SET → MACHINE → Controller**.

## Connection

USB serial. FoamSync lists available COM ports in the top bar; press
**CONNECT** to handshake. Common gotchas:

- The wrong COM port is selected. Refresh the port list after
  plugging in.
- Another application is holding the port (Arduino IDE, a previous
  FoamSync instance, another sender). Close it.
- A charge-only USB cable. Use a data-capable cable.
- USB power management dropping the port mid-session. Use a powered
  hub if needed.

## Machine setup values

Configured under **SET → MACHINE**:

- **Tower distance (Z)**, **rail length (X)**, **maximum height (Y)**
  — the physical work envelope, in mm. These bound the work area and
  set the soft limits.
- **Motion** — cut, travel, and return speeds; logic mode;
  approach clearance.
- **Wire and heater** — wire length, maximum wire angle, heater mode.
- **5th axis** — enable if present, with an increment per tick.

## Heater modes

- **External** — operator-driven (dimmer or PSU). FoamSync only
  moves the wire. Recommended starting point.
- **Board PWM** — controller-driven open-loop power %.
- **Board PID** — controller-driven closed-loop to a target
  temperature.

Switching from External to a board-driven mode requires a one-time
safety acknowledgement per release (fuse, detector, attended
operation).

## Materials

Built-in presets:

- **EPS** 15, 25, 40 kg/m³
- **XPS** 30, 45 kg/m³
- **PU** 40 kg/m³

Custom materials accept any density and cut parameters. Each preset
stores kerf, feed, temperature, and power; **MATERIAL CAL** in
Quick Lab tunes the preset to the actual batch.

## Next

- [Features](features.md)
- [Workflow](workflow.md)
