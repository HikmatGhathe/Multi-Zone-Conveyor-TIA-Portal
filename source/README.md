# PLC source code: what is included

The files under chat-reconstructed/ are **source bodies or development drafts preserved from the development conversation** and are not independently importable TIA block exports. They intentionally retain the original local-variable syntax.

- FB_ZoneControl_V2_body.scl — user-supplied Version 2 body of FB1.
- FB_Diverter_V2_body_from_discussion.scl — development draft, not verified against the final FB2.
- tia-export/ — reserved for complete block/interface exports from TIA Portal V21.

## Blocks still requiring actual TIA Portal export

| TIA block | Description |
|---|---|
| Main OB1 | Cyclic scheduling and block calls |
| FB_ZoneControl FB1 | Zone state machine (full interface) |
| FB_Diverter FB2 | Pneumatic diverter |
| FB_Routing FB3 | Barcode routing |
| FB_MachineControl FB4 | Machine supervisory control |
| FC_Zone3Permit FC1 | Receive permit |
| FC_Diagnostics FC2 | Fault aggregation |
| FC_MotorInterlock FC3 | Motor interlock |

Separate instance DBs include DB_Zone1–DB_Zone3, DB_Diverter, DB_Routing and DB_MachineControl. For complete reproducibility, also export the project archive (.zap21). Do not publish employer-owned project files.