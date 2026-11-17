# Multi-Zone Conveyor Routing & Sortation

**Siemens S7-1500 | TIA Portal V21 | SCL | WinCC Unified | Industrial Automation**

**Project developed and implemented during my Amazon Reliability Maintenance Engineering (RME) internship in Horn-Bad Meinberg.** I programmed conveyor control logic using Siemens TIA Portal, SCL and KOP, worked with sensor and motor signals, and commissioned the control work on a real conveyor installation. This repository presents the Multi-Zone Conveyor Routing & Sortation project, including three-zone accumulation, transfer handshakes, barcode routing, a pneumatic diverter, diagnostics, and WinCC Unified visualization.

![3D design visualization of the conveyor, three zones, scanner, pneumatic diverter, and two output lanes](media/illustrations/conveyor-visual-concept.jpg)

*Original conceptual render of the conveyor system and its intended operating layout (not a real-plant photo or runtime capture).*

[Detailed engineering layout](media/illustrations/conveyor-concept.svg)

## What the system does

1. **Zone 1 — Infeed.** Accepts a package request only when the receiving path is available. A photo-eye detects entry.
2. **Zone 2 — Accumulation.** Uses sensor feedback and downstream availability to prevent overfeeding and coordinate transfers.
3. **Zone 3 — Sortation.** Transfers packages into the routing area and coordinates with the diverter.
4. **Barcode routing and pneumatic diverter.** A simulated barcode input selects a destination and the diverter controls package redirection.
5. **Central supervision.** Machine Start/Stop/Reset, automatic mode, individual zone statuses, timeouts, fault codes, and interlocked motor commands.

### Sorting mechanism — detailed view

![Illustrative barcode detection and pneumatic diverter](media/illustrations/sorting-detail-concept.jpg)

*Original conceptual render of the barcode reader, photoelectric sensor, and pneumatic sorting mechanism.*

### HMI concept

![Conceptual HMI screen illustrating zones and operator controls](media/illustrations/hmi-concept.svg)

> **HMI concept:** Example visual design and sample values. The actual WinCC Unified editor screen is linked below.

## Technology

| Area | Implementation |
|---|---|
| PLC | S7-1500 CPU 1511-1 PN (TIA Portal configuration) |
| Engineering | Siemens TIA Portal V21 / STEP 7 |
| Programming | SCL (Structured Control Language), FB/FC architecture and OB1 calls |
| Zone control | Three instances of `FB_ZoneControl` with separate instance DBs |
| Sorting | `FB_Routing`, `FB_Diverter` |
| Machine supervisor | `FB_MachineControl`, `FC_Diagnostics`, `FC_MotorInterlock`, `FC_Zone3Permit` |
| HMI | WinCC Unified PC RT, `Screen_Overview`, S7 communication |

## Software architecture

![PLC program architecture](media/diagrams/architecture.png)

The modular control software organizes repeated zone logic into function blocks with individual instance data blocks. Every zone has the state transitions:

```text
EMPTY (0) -> LOADING (10) -> OCCUPIED (20)
                                       |
                                       v
                              TRANSFERRING (30)
                                       |
                                       v
                                   EMPTY (0)

FAULT (90) <- invalid sensor/state or timeout conditions
```

The zone implementation includes 8-second loading and transfer monitoring, downstream-sensor transfer confirmation, and diagnostic fault reasons. See [architecture and state transitions](docs/architecture.md).

## Browse the source code

- [FB_ZoneControl — SCL state-machine body](source/chat-reconstructed/FB_ZoneControl_V2_body.scl)
- [FB_Diverter — development draft](source/chat-reconstructed/FB_Diverter_V2_body_from_discussion.scl)
- [Source export guide](source/README.md)

The SCL files currently published are the available development text, not the full exported block interfaces. Remaining complete TIA Portal exports and the native `.zap21` project can be added from the author's local engineering project.

## Evidence from the engineering environment

These are real TIA Portal V21 **engineering/configuration screenshots**. They document the actual project work; they are not images of parcels moving through a simulated conveyor.

| PLC software | HMI / PLC communication |
|---|---|
| ![PLC code compiled](media/screenshots/plc-compile-zero-errors.png) | ![PLC and HMI network](media/screenshots/plc-hmi-ethernet-network.png) |
| [Zone 1 FB call](media/screenshots/zone-block-call.png) | [WinCC Unified screen editor](media/screenshots/hmi-screen-editor.png) |
| [Watch table](media/screenshots/watch-table.png) | [HMI connection parameters](media/screenshots/hmi-connection-settings.png) |

## Documentation

- [Signal map and tags](docs/io-and-tags.csv)
- [Architecture details](docs/architecture.md)
- [Functional test scenarios](docs/test-plan.md)
- [Project background](docs/project-background.md)
- [Opening and exporting the native project](PUBLISHING.md)

## Technical verification and scope

PLC program blocks and the WinCC Unified PC Runtime configuration were compiled offline in TIA Portal V21 without reported compilation errors. A complete PLCSIM test run is **not represented by the published material**; the illustrative visuals above should not be interpreted as simulation results. A compilation result alone does not establish functional correctness or safety.

This publicly shared project documentation and code contain no original employer-owned PLC files, internal plant drawings, or proprietary plant-network information. The simulated `SYS_SafetyOK` input is not a safety function, and an HMI Stop command is not an emergency stop. Real equipment would require safety engineering and commissioning validation.

## Author

**Hikmat Ghathe** · B.Sc. Computer Engineering · Industrial Automation / SPS / Embedded C/C++

[GitHub profile](https://github.com/HikmatGhathe)
