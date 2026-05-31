# Support

## Channels

| Channel | Use it for | Response |
|---|---|---|
| [@FoamSync_bot](https://t.me/FoamSync_bot) → `/support` | Activation, billing, urgent questions | Same-day, usually within hours |
| <support@foamsyncstudio.com> | Anything with attachments (logs, screenshots) | 24–48 h |
| [GitHub Issues](https://github.com/Balcore-Systems/foamsync/issues) | Bug reports, feature requests, public discussion | 1–3 days |

Studio-tier customers have **priority support** with an 8-hour
business-day response and an onboarding session in the first week of
purchase.

> [!NOTE]
> A diagnostic bundle attached to your first message is the single
> fastest way to a useful answer — see [below](#filing-a-useful-bug-report).

## Filing a useful bug report

The single most helpful thing you can send is a **diagnostic bundle**:

1. In FoamSync, open **SETUP → DIAGNOSTICS → REPORTS** and use
   **Export Support Bundle**.
2. The dialog writes a report file you can attach to your issue or
   email.
3. Reply with a one-paragraph description of what you were doing
   when the issue happened, what you expected, and what you observed.

The bundle contains:

- Operating system version, application version, installed Pro Packs.
- The tail of the application log (no design files, no G-code).
- Current licence state.
- Machine ID.

It does **not** contain your designs, G-code files, customer data,
or anything else from your project library.

## Common issues

### Activation refused

The Machine ID has changed since the licence was issued (new
motherboard, new disk, the licence was read in a VM). Read the
Machine ID on the actual target machine and request a re-issue.

### Trial banner won't disappear after activation

Restart FoamSync.

### Heater won't reach setpoint

Hardware territory. The **DIAGNOSTICS → Heater test** confirms whether
FoamSync is sending the right signal. If yes, the issue is in the
heater hardware or the power supply. If no, export a diag bundle and
email support.

### G-code rejected by the controller

Confirm FoamSync detected the right firmware on connect
(**SET → MACHINE → Controller**, default **Auto**). Marlin, GRBL, and
GRBL-H-Par use different M-code conventions for heater and motion —
set the controller explicitly if auto-detect guessed wrong.

### Cut comes out under- or over-sized

Re-run [WIRE CAL](features.md#calibration-quick-lab) and confirm the
kerf for the current wire.

### Cut is skewed or trapezoidal

Re-run [MOTION TEST](features.md#calibration-quick-lab) in Quick Lab.
Backlash, square, or lost steps will surface there.

### "Licence file retired" notice on launch

The previous `license.dat` could not be read by the application and
was set aside as `license.dat.obsolete`. Re-activate
([activation.md](activation.md)) — nothing is lost.

## Feature requests

Open a [GitHub issue](https://github.com/Balcore-Systems/foamsync/issues)
with the `enhancement` label. Describe the workflow you're trying to
support, how you handle it today, and what would change for you if
FoamSync supported it natively. Concrete operator stories help us
decide what to prioritise.

## Next

- [FAQ](faq.md)
- [Workflow](workflow.md)
- [Features](features.md)
