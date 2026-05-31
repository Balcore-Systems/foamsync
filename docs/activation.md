# Activation

FoamSync runs in trial mode for the first 7 days after install —
every feature is previewed and real machines run in virtual mode. To
enable production output and connect a real machine, you need a
licence.

## Buying a licence

1. Open [@FoamSync_bot](https://t.me/FoamSync_bot) in Telegram and
   run `/buy`.
2. Step through the bot's prompts:
   - **Tier:** Lite, Pro, or Studio.
   - **Pro Packs** (Pro only): one, two, or all three of
     BUILD / AERO / THERMAL.
   - **Licence type:** monthly, yearly, or perpetual.
   - **Email** — for invoice and key delivery.
   - **Company** name (or "individual") and **country**.
   - **Machine ID** — see below.
   - **Promo code** (optional).
   - **Payment method:** SEPA, USDT, or card where enabled for your
     region.
3. Pay using the bot's instructions.
4. Within an hour (within 24 hours at the worst), the bot delivers
   your licence key in the same chat.

## Your Machine ID

The Machine ID is a 16-character identifier the licence is issued
against. Two ways to read it:

- **In FoamSync.** Open the activation dialog (it appears on launch
  until you're licensed, or click the licence banner). The Machine ID
  is shown at the top with a **COPY** button.
- **Standalone.** Download the **Machine ID** utility from the
  [download page](https://foamsyncstudio.com/download/) and run it on
  the target machine. The window shows the 16-character code with a
  COPY button. Use this when you haven't installed FoamSync yet.

## Activating

There are two paths.

### Online

In FoamSync, open the activation dialog, paste the key into the input
field, and press **ACTIVATE**. The application contacts the licence
server and confirms the activation. Requires an internet connection
at activation time. Once activated, FoamSync runs offline, with
periodic check-ins on subscription tiers.

### Offline — a licence file

For machines that can't reach the licence server (air-gapped
industrial cells, for example), your distributor issues a licence
file bound to the Machine ID. In FoamSync, click
**DROP LICENCE FILE**, pick the file, and the application accepts it.

## Trial banner and renewal

A banner at the top of the window counts down the remaining trial
days, and after activation it warns about upcoming renewal on
subscription tiers:

| Days until expiry | Banner | Real-machine connection |
|---|---|---|
| more than 7 | hidden | yes |
| 4 to 7 | yellow | yes |
| 1 to 3 | orange | yes |
| 0 to −3 (grace) | red | yes |
| beyond grace | activation dialog | no |

Click the banner any time to open the activation dialog. Project data
is not lost after grace — only the real-machine connection is
disabled until you renew.

## Moving the licence to another machine

A licence is issued against a specific Machine ID. To move it, email
[support@foamsyncstudio.com](mailto:support@foamsyncstudio.com) with
your key and the **new** machine's Machine ID. We re-issue against
the new machine. Don't copy `license.dat` between machines — it
won't carry over.

> [!IMPORTANT]
> Replacing major hardware components (motherboard, system disk, the
> network interface used for identification) can change the Machine
> ID. If the licence stops validating after a hardware change,
> contact support with the new Machine ID for a re-issue.

## Troubleshooting

- **"This licence is not valid for this installation."** The Machine
  ID has changed since the licence was issued. Read the current
  Machine ID and request a re-issue.
- **You ran the standalone tool inside a VM or sandbox.** The Machine
  ID won't match the bare-metal machine. Run the tool on the actual
  target.
- **The trial banner doesn't disappear after a successful
  activation.** Restart FoamSync.

## Next

- [Tiers and packs](tiers-and-packs.md)
- [Workflow](workflow.md)
- [Support](support.md)
