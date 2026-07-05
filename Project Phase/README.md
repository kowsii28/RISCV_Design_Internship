# Project Phase: RTC IP Study and Interface Migration

## 1. Project Overview
This phase documents the implementation journey of integrating and adapting an RTC (Real-Time Clock) IP.

The work started from studying the reference RTC design from:
- **Reference Repository:** [freecores/rtc](https://github.com/freecores/rtc)

The objective was to:
1. Understand RTC core behavior and register logic.
2. Test the RTC with simulation and verify waveform behavior.
3. Analyze the existing **Wishbone interface**.
4. Rework the interface logic toward **AXI4-Lite** based integration understanding.

---

## 2. Learning-to-Implementation Flow

### Phase A: Reference Study
- Explored the RTC architecture from the FreeCores reference.
- Understood register map, control/status behavior, interrupt/alarm style logic, and bus-facing blocks.
- Identified how Wishbone transactions map to RTC registers.

### Phase B: Simulation and Functional Verification
- Created/used test setup to exercise RTC read/write paths.
- Ran simulation and observed waveform to validate:
  - clock/count progression
  - register write/read behavior
  - control bit impact
  - bus handshake behavior
- Confirmed expected behavior before interface migration attempts.

### Phase C: Wishbone Interface Understanding
- Traced Wishbone signals and transaction flow.
- Documented timing/acknowledgment logic and register access mechanism.
- Built clarity on how bus protocol controls RTC register operations.

### Phase D: AXI4-Lite Interface Adaptation Attempt
- Studied AXI4-Lite protocol and mapped equivalent operations:
  - Wishbone write/read ↔ AXI write/read channels
  - ack-style completion ↔ AXI valid/ready handshakes and response signaling
- Began/implemented interface-side logic changes with minimal disturbance to RTC core internals.
- Focus was on protocol adaptation while preserving RTC functionality.

---

## 3. Reference Documents Used
The following documents were used during this project phase:
- `AXI4 IP Porting with Shakti SoC`
- `IP Porting with Shakti SoC`
- `nexys-a7_rm`
- `rtc_spec`
- `Verilog_IP_Porting_Shakti_SoC`

> These references guided both protocol understanding and practical integration flow.

---

## 4. Technical Scope Covered
- RTC core behavior analysis
- Register-level verification through simulation
- Wishbone protocol transaction tracing
- AXI4-Lite protocol study and interface mapping
- Waveform-based debug and validation

---

## 5. Outcomes
- Gained clear understanding of RTC IP internal flow and bus interaction.
- Validated RTC behavior in simulation and waveform environment.
- Established migration logic path from Wishbone-style access to AXI4-Lite style interfacing.
- Built a reusable approach for similar IP interface adaptation tasks.

---

## 6. Notes
This README captures the structured journey of:
**Understand → Verify → Analyze Interface → Adapt Interface**
for RTC IP integration work.
