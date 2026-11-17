# Opening the engineering project

The public repository is already online at [Multi-Zone-Conveyor-TIA-Portal](https://github.com/HikmatGhathe/Multi-Zone-Conveyor-TIA-Portal).

## View code and documentation without TIA Portal

GitHub renders the README, SVG diagrams, screenshots, and SCL source-body files directly in the browser. Start from the main README to understand the package flow, zone state machines, routing and diagnostic logic.

## Reproduce the native TIA Portal V21 project

The native TIA project archive is stored only on the author's Windows machine at present; it is not included in this public repository.

To add a reproducible project later:

1. Open the locally authored `Multi_Zone_Conveyor_V21` project in TIA Portal V21.
2. Compile PLC and HMI; save the project.
3. Use **Project → Archive** to generate a `.zap21` archive.
4. Export self-authored SCL source blocks with **Generate source from blocks** for `FB_ZoneControl`, `FB_Diverter`, `FB_Routing`, `FB_MachineControl`, `FC_Diagnostics`, `FC_MotorInterlock` and `FC_Zone3Permit`.
5. Add exported SCL files to `source/tia-export/` and project archive to `tia-portal-project/`.

Do not upload any Amazon-owned source code, production plant addresses, credentials, or employer network details.

The visible diagrams and UI illustration depict the project concept; they are not recorded software runtime results. 
