# Virtual machine (Virtual GRBL)

> Design, dry-run, and verify a complete 4-axis job — including real
> machine motion, timing, heater behaviour, and wire-safety — **before
> you connect any hardware, or even own a machine.**

This is the feature we lead with, because hot-wire CAM tools generally
don't have it. Most offer, at most, a *static* toolpath preview — a
picture of where the wire would go. FoamSync ships a **behaving virtual
machine**: instead of picking a COM port, you select **VIRTUAL_DRIVER**,
and the entire application acts as if a real 4-axis hot-wire cutter were
connected.

## What it actually does

With the virtual machine connected, FoamSync runs the same way it does
on real hardware:

- **Homing and jogging** — the towers home; the on-screen jog moves the
  wire with smooth, interpolated motion (it travels, it doesn't teleport).
- **Full job execution** — press START and the generated G-code runs
  end to end: the wire animates along the real trajectory, the DRO and
  the live wire-angle update as it moves, and the ETA counts down.
- **Live feed override** — change FEED % mid-run and the simulated wire
  speed changes with it, exactly as the override behaves on a real
  controller.
- **Simulated heater** — the heater warms toward its target and the
  temperature readout ramps, so the thermal side of the workflow is
  visible in dry-run.
- **PAUSE / RESUME / EMERGENCY STOP** — all behave as they would on the
  machine, including the safe-state transitions.
- **Pre-cut wire-safety pass** runs the same way, so you see the
  warning / danger / critical analysis on the virtual run.

In other words it is not an animation of a path — it is a machine that
*responds to the same commands* and reproduces the same workflow
semantics as the real controller it stands in for.

## Why it matters (the commercial case)

- **Evaluate the whole product with zero hardware.** The 7-day trial
  runs real machines in virtual mode, so a prospective buyer can design
  parts, generate toolpaths, and watch a full cut run — and judge
  FoamSync on the complete workflow, not a screenshot.
- **Buy the software before the machine.** Shops planning a hot-wire
  line can build their part library, validate their geometry, and train
  staff while the machine is still on order.
- **Don't tie up the cutter to check a program.** Verify motion,
  timing, nesting, and wire-safety on the virtual machine; commit foam
  and machine-hours only once the run is clean.
- **Train operators with no risk.** New staff learn jogging, zeroing,
  feed override, pausing, and the e-stop on the virtual machine — no
  wasted foam, no broken wire, no damaged stock.
- **Develop offline, run 1:1.** The program you verify virtually is the
  same program the real controller runs. On connect, FoamSync
  auto-detects Marlin, GRBL, or GRBL-H-Par and configures itself — the
  workflow you rehearsed is the workflow you run.

## How to try it

1. Install FoamSync and launch it (the trial is active for 7 days).
2. At the top-right, instead of a COM port choose **VIRTUAL_DRIVER**,
   then **CONNECT**.
3. Generate a part (try the NACA or Dome generator), send it to CAM,
   press **GENERATE TOOLPATH**, then **START**.
4. Watch the wire run the job, change **FEED %** mid-run, try
   **PAUSE / RESUME**, and open the wire-safety report.

When you're ready for the real machine, swap **VIRTUAL_DRIVER** for the
COM port and connect — nothing else about your workflow changes.

## Next

- [Features](features.md)
- [Workflow](workflow.md)
- [Market context](market-context.md)
