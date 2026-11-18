[README (4).md](https://github.com/user-attachments/files/35058130/README.4.md)
# Wireline PCE Training Simulator — V15

**S. Siddhu | SOGE | Central**

An interactive, single-file HTML/SVG training simulator for wireline pressure control equipment (PCE): rig-up, pressure testing, running procedures, depth correlation and well-control contingencies. The well physics respond live to every input.

> **Training use only.** This simulator does not replace the approved well program, service-company procedures, agency SOPs or governing regulations. Default cable, PCE-margin and tool-weight values are placeholders. Enter values from the actual equipment specifications.

## Files

| File | Description |
|---|---|
| `Wireline_Rigup_Simulator_V15.html` | The simulator, a self-contained HTML file |
| `Wireline_PCE_Simulator_V15_User_Guide.docx` | Full user guide (19 pages) |

## Quick start

1. Open `Wireline_Rigup_Simulator_V15.html` in any modern browser. No install or internet connection is needed.
2. Pick a **Tool Mode** and **PCE Configuration**, or load a preset on the **Well** tab.
3. Press the numbered steps on the **Run** tab in order. Read the **Operational Briefing** after each step.
4. Review results on the **Analysis** tab and export the session from the **Event Log** tab.

Nothing is saved between sessions. Export the event log if you need a record.

## Tool modes

| Mode | Mode action | Key requirements |
|---|---|---|
| Logging string (CCL/GR) | Record log pass | Pack-off allowed on a dead well |
| CBL / VDL | Record CBL pass | Pack-off allowed on a dead well |
| Perforating — casing gun | Fire gun | Arming checklist, full lubrication, depth correlation |
| CIBP set | Set CIBP | Drift confirmed; arming step only if the setting tool uses an explosive power charge |
| Dump bailer | Dump cement on plug | A plug must exist; repeat runs build the cap |
| Gauge ring / junk basket | Drift run | Confirms drift for the CIBP run |

## Standard sequence (full lubricator)

Verify barrier → (Arm) → Rig up → Pressure test low/high & bleed → Equalize across CSO → Open CSO & RIH → Correlate → Mode action → POOH → Close CSO & bleed

## Key rules enforced

- **Pack-off / stubby lubricator:** logging and CBL only, on a dead well with no surface pressure.
- **Perforating:** always fully lubricated.
- **Lubricator length:** rig-up is blocked if the tool string plus the length margin exceeds the usable lubricator length.
- **Pressure test:** the high test is MASP plus a margin and must not exceed the PCE rated working pressure.
- **CSO interlock:** the CSO will not open while there is a pressure differential across it. Bleed is denied while the CSO is open on a pressured well.
- **Pump-out:** RIH is blocked if the tool weight does not exceed lubricator pressure × cable area + friction.

## Physics summary

| Item | Basis |
|---|---|
| Hydrostatic at zone | `0.052 × MW × wet column` |
| SICP / kill weight | `PP − HP_eff`; kill weight = `PP_EMW + margin` |
| MASP | `max(WHP, PP − gas gradient × depth)` |
| Surge / swab | Burkhardt effective annular velocity; Bingham slot flow over the tool-string length only |
| Line tension | Buoyed cable + tool weight − `P_lub × cable area` ± friction |

Typical logging tools in casing see about 1 psi of surge/swab. Tight-clearance runs, such as through tubing, see tens of psi. The method is described in full in the user guide (Section 9). Verify it against Burkhardt (1961) and Bourgoyne et al., *Applied Drilling Engineering*, Ch. 4.

## Depth correlation

Each run starts with a hidden 3–12 ft counter error. The trainee enters a shift (`corrected = counter + shift`) using one of three methods:

- **Log tie-in:** compare collars on the reference log and the current CCL pass.
- **Depth datum:** compare the reference-log KB elevation with today's zero reference elevation.
- **Tag:** compare the recorded PBTD or plug depth with the counter reading at the tag.

A residual of ±1 ft or less is accepted.

## Contingencies

Influx, bullhead kill, bleed PCE, CSO jam, cable part, stuck on POOH (work line or pull to the weak point), grease/pack-off seal loss with WL BOP closure, casing restriction, gun misfire, premature CIBP set.

## Presets

Baseline · Live well · Depleted zone · Through-tubing · Underbalanced perforating · P&A chain

## Scoring

The score starts at 100 and loses 10 points per trainee violation. Examples: opening the CSO against a pressure differential, swabbing an overbalanced well into an influx, an off-depth shot or plug, or exceeding tension limits. Export the log as `.txt` or print it to PDF.

## Changes from V14

- Surge/swab is now integrated over the tool length, not the well depth, so the magnitudes are much smaller.
- The depth counter's zero is the wellhead flange, matching the depth ruler.
- Kick pressure is calculated from the inputs instead of a fixed 1,450 psi.
