# FAQ

## What is FoamSync?

CAM software for 4-axis hot-wire CNC foam cutters. See
[introduction.md](introduction.md).

## What does it run on?

Windows 10 / 11 (x64). USB-connected controllers running Marlin,
GRBL, or GRBL-H-Par. See [hardware.md](hardware.md).

## Do I need to know G-code to use it?

No. The parametric generators produce the G-code; you press
**GENERATE TOOLPATH** and then **START**. Manual G-code editing is
available if you want it, but it isn't required for any of the
supplied generators.

## Can I import SVG?

Yes, on every tier. Closed contours in an SVG become cut profiles in
the CAM scene.

## Can I import formats other than SVG?

Not in 1.0. SVG covers most operator workflows for 2D profile import.
If your shop has a strong need for another format, open a
[GitHub issue](https://github.com/Balcore-Systems/foamsync/issues)
with the use case.

## How is the trial limited?

The 7-day trial previews every feature for evaluation. The
application runs in virtual mode and output is intended for
evaluation rather than production. Activate a paid tier to enable
production output and to connect a real machine.

## How does activation work?

Buy a licence via [@FoamSync_bot](https://t.me/FoamSync_bot), then
paste the key into the activation dialog (online) or load a licence
file from your distributor (offline). See [activation.md](activation.md).

## What's a Machine ID?

A 16-character identifier shown in the activation dialog (and in the
standalone Machine ID tool). It identifies the install for licensing.

## Can I move my licence to a new machine?

Yes — email <support@foamsyncstudio.com> with your key and the new
machine's Machine ID. We re-issue against the new machine. Don't
try to copy `license.dat` between machines.

## What happens after my subscription expires?

There is a short offline-grace window during which the application
still runs. After that grace, real-machine connection is disabled
until you renew; project data is not lost.

## Can I have more than one machine seat?

Yes — Studio tier ships three seats. Pro and Lite are single-seat.

## What firmware does the auto-detect support?

Marlin, GRBL, and GRBL-H-Par. See [hardware.md](hardware.md). If your
firmware isn't supported, open an issue.

## Does FoamSync drive the wire heater?

It can. Pick one of three modes per machine: **external** (you drive
heat), **board PWM**, or **board PID**. See
[features.md → Heater control](features.md#heater-control-every-tier).

## How does kerf work?

**WIRE CAL** in Quick Lab measures kerf from a reference cube. The
CAM transformer sizes parts using the measured kerf, so what comes
out matches what was generated. See
[features.md → Calibration](features.md#calibration-quick-lab).

## How are airfoils tapered?

Configure separate root and tip profiles in the NACA generator (for
example, NACA 8612 at the root and NACA 4408 at the tip). FoamSync
sweeps the wire between them in 4-axis. See
[features.md → AERO pack](features.md#aero-pack--4-axis-airfoils).

## How is wire safety checked?

A pre-cut pass against the maximum wire angle you set in
**SET → WIRE**. The report shows max and average angle, lean
components, and violation counts at three severity levels with
recommendations. See
[features.md → Wire-safety validation](features.md#wire-safety-validation).

## Where do I report bugs and request features?

[GitHub Issues](https://github.com/Balcore-Systems/foamsync/issues).
For activation or billing, use the
[Telegram bot](https://t.me/FoamSync_bot). For anything with logs
and screenshots, email <support@foamsyncstudio.com>.

## Does FoamSync work offline?

Yes, after activation. Online activation requires an internet
connection at the moment you activate. For machines that can't reach
the licence server at all, your distributor issues a licence file you
load offline.

## Where can I see prices?

[foamsyncstudio.com/pricing](https://foamsyncstudio.com/pricing/).

## Next

- [Tiers and packs](tiers-and-packs.md)
- [Workflow](workflow.md)
- [Support](support.md)
