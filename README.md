# Reserving netting tool

Single-file HTML tool (`netting_tool.html`) that rebuilds the reserve netting ladder
(gross → net of external retro → net of internal quota share, by UWY) from the
`Input_Netting_*.xlsx` workbook. Everything runs in the browser; no file leaves the machine.

## Layout

| Path | Content | In git |
|---|---|---|
| `netting_tool.html` | the tool (open it in Edge/Chrome) | yes |
| `inputs/` | quarterly input workbooks and comparison (Q-1) files | folder only, `*.xls*` ignored |
| `analyses/` | ladders exported from the tool, reviewed/adjusted results | folder only, `*.xls*` ignored |

## Quarter-on-quarter movements

1. Load the input workbook (drop it on the page or **Choose files…**).
2. **Compare period…** → the Q-1 *all combinations* export of this tool
   (e.g. `Q2_netting_tool_extraction_24_September.xlsx`). Every ladder gets Δ GULR / Δ NULR / Δ NNULR.
3. Optional, UK branch: **UK as presented…** (in the comparison bar) → a ladder file holding the
   Q-1 UK figures as presented in the UK deck. Use it when policies moved between UK and Lux since
   Q-1. For every UK view that file contains, its ratios replace the main Q-1 file's; every other
   view (Total, UK views it does not contain) keeps the main file. The note above the ladder and
   the export subtitles say which file each Δ is against.

The UK file uses the export layout: a header row with `LoB`, `Level`, `Basis`, `Branch`, `UWY`,
`GULR`, `NULR`, `NNULR` (other columns are ignored, non-UK rows are skipped).
`inputs/Q2_UK_presented.xlsx` is the Q2 2026 one: ALL, DCTOT, ENTOT and PRTOT, MBE, UK branch,
backed out of `analyses/netting_all_combinations_Q3vsQ2_UKQ2presented.xlsx` as Q3 ratio − Δ.

## Check done for Q3 2026

With `Input_Netting_v2_Q3.xlsx` (and `v2.1`, whose data sheets are identical):

- main Q-1 file only → matches `netting_all_combinations_Q3vsQ2.xlsx` exactly (1,224 rows × 18 columns);
- plus `Q2_UK_presented.xlsx` → matches `netting_all_combinations_Q3vsQ2_UKQ2presented.xlsx` (max difference 4e-16).
