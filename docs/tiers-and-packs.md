# Tiers and packs

FoamSync has three tiers — **Lite**, **Pro**, **Studio** — and three
Pro Packs you mix on Pro. Current prices live on the
[pricing page](https://foamsyncstudio.com/pricing/).

## Tier matrix

| | Lite | Pro | Studio |
|---|---|---|---|
| Machine seats | 1 | 1 | 3 |
| Base CAM core | ✓ | ✓ | ✓ |
| Pro Packs | — | pick 1–3 | all 3 included |
| CRM webhook integration | — | — | ✓ |
| Priority support | — | — | ✓ |
| Onboarding session | — | — | ✓ |
| Perpetual option | ✓ | ✓ per pack | — (subscription only) |

## Base CAM core (every tier)

These capabilities are in every tier, including Lite:

- 4-axis G-code post-processor (synced X/Y on one tower; independent
  U/V on the other).
- Collision check and pre-cut wire-safety validation.
- Auto-nesting on the union of top and bottom profiles.
- On-screen real-machine jog; 4-axis DRO with an optional 5th
  rotational axis; one-tap wire-zero from the current position.
- Heater control: external, board PWM, board PID.
- Material library with EPS / XPS / PU presets and custom materials.
- SVG import and manual G-code editing.
- Diagnostic export for support.
- Auto-detect for Marlin, GRBL, and GRBL-H-Par.
- Quick Lab calibration (status / pre-flight / motion / wire kerf /
  material).
- Live feed override during a cut.

Lite has the CAM core only — no parametric generators. SVG import is
the route in for custom shapes.

## Pro Packs

Same price per pack; bundle two or three for a discount (see the
[pricing page](https://foamsyncstudio.com/pricing/)).

### BUILD — architectural generators

- **Dome** — radial dome split into rings × sectors, with a solid /
  oculus / no top-cap, optional lock recesses, and an exterior reveal
  rabbet.
- **Vault** — barrel vault with custom span, height, and arch profile.
- **Building** — building-block walls with rounded-corner openings.

### AERO — 4-axis airfoils

- **NACA-4** airfoil generator (any chord and thickness).
- **Cylinder or tapered** wings using independent root and tip
  profiles.
- **Up to 3 spar slots per wing** (main / rear / aux), rectangular or
  round, with bridge support.
- **4-axis tilted cuts** with independent X/Y vs U/V motion.

### THERMAL — insulation generators

- **Pipe shell** unfolder for cylindrical insulation jackets, with a
  **pair-interlock nester** so two half-shells pack into one full
  circle's footprint.
- **Thermal panel** with half-lap rabbet side joints and optional
  back mounting channels, auto-nested across the block.

## Studio extras

- **3 machine seats** — install on up to three machines under one
  licence.
- **CRM webhook integration** — push customer and job records to your
  own CRM through a webhook.
- **Priority support** with an onboarding session in the first week
  of purchase.

## Upgrading

Pay only the difference. Email
[support@foamsyncstudio.com](mailto:support@foamsyncstudio.com) or
the bot with your current key and the target tier; we quote the
upgrade.

## Trial

Every install starts with the 7-day trial: all features previewed,
output for evaluation, real machines virtual. Activate any tier to
remove the limits.

## Next

- [Features](features.md)
- [Workflow](workflow.md)
