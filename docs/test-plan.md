# PLC + HMI test plan (not yet executed)

**Status:** Proposed verification tests. S7-PLCSIM V21 was not yet available at the time of repository publication. A successful compile does not imply these checks passed.

| ID | Test | Expected outcome | Status |
|---|---|---|---|
| TC-01 | Power-up | Motors stopped, stable idle state | Not run |
| TC-02 | Auto + Start | Run permission only with valid permissives | Not run |
| TC-03 | Zone 1 arrival | Occupied state after photo-eye goes true | Not run |
| TC-04 | Zone 2 blocked | Back-pressure prevents unsafe transfer | Not run |
| TC-05 | Zone 1 to Zone 2 handover | Confirm downstream detection and upstream clearing | Not run |
| TC-06 | Loading over 8 seconds | Fault code 10 | Not run |
| TC-07 | Transfer over 8 seconds | Fault code 20 | Not run |
| TC-08 | Occupied sensor disappears | Fault code 30 | Not run |
| TC-09 | Invalid zone state | Fault code 40 | Not run |
| TC-10 | Unexpected package | Fault code 50 | Not run |
| TC-11 | Diverter positioning abnormal | Command inhibited and fault handling verified | Not run |
| TC-12 | STOP during transfer | Controlled stop, no unrequested restart | Not run |
| TC-13 | Reset from HMI | Fault reset only under allowed conditions | Not run |
| TC-14 | Restart after fault | Explicit Start required | Not run |
| TC-15 | HMI short command pulses | Correct PLC recognition | Not run |
| TC-16 | Barcode destination A/B | Correct routing and diverter target | Not run |

Future evidence: attach screenshots of watch tables and recorded results, plus a short Runtime/PLCSIM demonstration. Do not infer operational safety from software tests alone.