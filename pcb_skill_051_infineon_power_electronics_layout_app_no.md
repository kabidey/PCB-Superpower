# SKILL: Infineon Power Electronics Layout App Notes

## Skill Metadata
- **ID**: 51
- **Category**: silicon_vendor
- **Source**: Infineon Power Electronics Layout App Notes
- **URL**: https://www.infineon.com/
- **Description**: Crucial architectural frameworks for high-power switching loops, covering MOSFET/IGBT gate drivers and heat-sink planes.
- **Soul**: The power switching - MOSFETs and IGBTs are not switches, they are controlled explosions.
- **Complexity**: Intermediate
- **Confidence Threshold**: 0.7

## MENTAL MODEL (How to Think Like This Expert)
### The Infineon Power Electronics Layout App Notes Perspective

**Core Belief:** The power switching - MOSFETs and IGBTs are not switches, they are controlled explosions.

**How This Expert Sees the World:**
- Every PCB is a power delivery network first, a collection of components second
- The invisible (electromagnetic fields) matters more than the visible (traces and pads)
- Manufacturing is not a downstream activity; it is a co-design constraint from day one
- Cost is not a spreadsheet column; it is a physical property of every trace width and via choice
- Testability is not an afterthought; it is a design requirement as critical as functionality

**Decision Framework:**
1. **First Principles:** Start with physics (Maxwell, Ohm, Fourier), not rules of thumb
2. **Quantitative Rigor:** Every decision has a number behind it; if you can't calculate it, you don't understand it
3. **Manufacturing Reality:** The factory doesn't care about your simulation; it cares about what it can build repeatably
4. **Economic Truth:** The cheapest board that works is the most expensive board that fails in the field
5. **Testability Mandate:** If you can't test it, you can't ship it; if you can't ship it, you don't have a product

**Cognitive Biases to Avoid:**
- **Simulation Blindness:** "It works in SPICE" does not mean it works in copper
- **DRC Complacency:** "DRC clean" does not mean "design good"
- **Copy-Paste Syndrome:** "This worked on the last board" does not mean it works on this one
- **Cost Myopia:** Optimizing BOM cost while ignoring yield loss is not optimization, it's gambling
- **Test Neglect:** Adding test points at the end is like adding seatbelts after the crash

**When to Activate This Skill:**
- When the design challenge maps to power delivery network
- When quantitative rigor is required, not just qualitative guidance
- When manufacturing constraints are real and non-negotiable
- When the cost of failure exceeds the cost of over-engineering


## OPERATIONAL SYSTEM (How to Execute Like This Expert)
### Phase 1: Contextual Intelligence Gathering

**Before Any Action, Ask:**
1. What is the DESIGN STAGE? (Concept / Schematic / Layout / Review / Manufacturing)
2. What is the PRIMARY CONSTRAINT? (Cost / Performance / Schedule / Reliability / Compliance)
3. What is the FAILURE COST? (Prototype rework vs. Field recall vs. Safety incident)
4. What is the MANUFACTURING TARGET? (JLCPCB / PCBWay / Eurocircuits / In-house)
5. What is the TEST STRATEGY? (Flying probe / Bed-of-nails / Functional / Burn-in)
6. What is the VOLUME? (1 / 10 / 100 / 1000 / 10000+ units)
7. What is the ENVIRONMENT? (Lab / Consumer / Industrial / Automotive / Aerospace / Medical)
8. What is the LIFECYCLE? (6 months / 2 years / 10 years / 25 years)

**If user cannot answer these:** The design is not ready for this skill. Request clarification.

### Phase 2: Domain-Specific Deep Analysis

**Core Technical Analysis (from Infineon Power Electronics Layout App Notes):**

**Power Delivery & Thermal Deep Dive:**

1. **PDN Impedance Target:**
   - Z_target = V_ripple_max / (0.5 × I_transient_max)
   - Example: 1.0V rail, 50mV ripple, 5A transient
     Z_target = 0.050 / (0.5 × 5) = 20 mΩ
   - Verify across frequency: 1 kHz to 100 MHz

2. **Capacitor Network Design:**
   - Bulk: 100-470 μF, ESR < 50 mΩ, handles < 100 kHz
   - Mid-range: 1-10 μF, ESR < 10 mΩ, handles 100 kHz - 10 MHz
   - High-frequency: 0.01-0.1 μF, ESL < 1 nH, handles > 10 MHz
   - Ultra-high-frequency: 0.001-0.01 μF, ESL < 0.5 nH, handles > 100 MHz
   - Placement: closest to power pin, vias directly to planes

3. **Loop Inductance Minimization:**
   - L_loop ≈ 2×h×ln(2s/d) where h = via height, s = via spacing, d = via diameter
   - Target: < 1 nH for high-frequency decoupling
   - Best practice: capacitor on SAME side as IC, vias directly to planes

4. **Thermal Analysis:**
   - θ_JA = θ_JC + θ_CS + θ_SA
   - ΔT = P × θ_JA
   - T_J = T_A + ΔT
   - If T_J > T_J_max: add thermal vias, heatsink, or improve airflow
   - Thermal via grid: 1 via per 1-2 mm² of thermal pad

5. **Current Capacity (IPC-2152):**
   - I = k × ΔT^b × A^c where k=0.048, b=0.44, c=0.725
   - Example: width=10 mils, thickness=1.37 mils (1 oz), ΔT=10°C
     A = 13.7 mils², I = 0.048 × 10^0.44 × 13.7^0.725 = 0.97 A

### Phase 3: Quantitative Verification

**Verification Checklist (from Infineon Power Electronics Layout App Notes):**
- [ ] All calculations verified with second method or tool
- [ ] Design rules checked against manufacturer capabilities
- [ ] Signal integrity simulation performed (if applicable)
- [ ] Thermal analysis completed (if applicable)
- [ ] EMC pre-compliance assessment (if applicable)
- [ ] DRC/ERC passes with zero violations
- [ ] 3D clearance check clean
- [ ] BOM cost within budget
- [ ] Test point coverage ≥ 80%
- [ ] Documentation complete

### Phase 4: Decision Documentation

**Every Decision Must Be Documented With:**
1. **What was decided** (specific choice)
2. **Why it was decided** (engineering rationale)
3. **How it was verified** (calculation, simulation, measurement)
4. **What could go wrong** (risk assessment)
5. **What the backup plan is** (contingency)


## FAILURE UNIVERSE (What Can Go Wrong & How to Survive)
### The Failure Modes of Infineon Power Electronics Layout App Notes

**Class 1: Design Errors (Your Fault)**

| Failure | Root Cause | Detection | Recovery | Prevention |
|---------|-----------|-----------|----------|------------|
| Thermal runaway | Insufficient heat dissipation | Thermal camera, thermocouple | Add heatsink, improve airflow, reduce load | Calculate θ_JA, design thermal path |
| Voltage droop | High PDN impedance at load transient | Oscilloscope, PDN measurement | Add capacitors, widen power traces | Calculate Z_target, design capacitor network |
| Capacitor resonance | ESL too high for frequency | Impedance analyzer, simulation | Use smaller package, multiple parallel caps | Calculate f_SRF, select appropriate capacitors |
| Inductor saturation | Current exceeds saturation current | Oscilloscope, efficiency measurement | Use larger inductor, reduce load | Calculate peak current, select inductor with margin |
| MOSFET overheating | Insufficient gate drive, slow switching | Thermal camera, efficiency measurement | Improve gate drive, add snubber | Calculate switching losses, design thermal path |

**Class 2: Manufacturing Errors (Their Fault, Your Problem)**

| Failure | Root Cause | Detection | Recovery | Prevention |
|---------|-----------|-----------|----------|------------|
| Layer misregistration | Drilling/etching tolerance stackup | Cross-section, electrical test | Rework (limited), scrap | Tight tolerance spec, qualified manufacturer |
| Delamination | Moisture, inadequate cure, thermal stress | Visual, acoustic microscopy | None (scrap) | Proper storage, qualified laminate, thermal profiling |
| Plating void | Contamination, inadequate agitation | Cross-section, electrical test | Rework (limited), scrap | Qualified process, incoming inspection |
| Solder mask defect | Incomplete cure, contamination | Visual inspection | Rework (limited), scrap | Qualified process, visual inspection |
| Silkscreen error | Wrong legend, poor adhesion | Visual inspection | Rework (limited), scrap | Artwork verification, qualified process |
| Wrong material | Substituted laminate, wrong Dk | Impedance test, Dk measurement | Scrap | Incoming inspection, material certification |
| Drill breakout | Drill wander, misregistration | Visual inspection, electrical test | Rework (limited), scrap | Tight tolerance, qualified manufacturer |

**Class 3: Field Failures (Everyone's Nightmare)**

| Failure | Root Cause | Detection | Recovery | Prevention |
|---------|-----------|-----------|----------|------------|
| Infant mortality | Manufacturing defect, weak component | Burn-in, field returns | RMA, repair, recall | Burn-in, accelerated life test, DFM |
| Random failure | Component degradation, thermal cycling | Field returns, warranty claims | RMA, repair, redesign | Derating, thermal management, component selection |
| Wear-out failure | End of component life | Predictive maintenance, field returns | Replace, redesign | Life prediction, preventive maintenance |
| ESD damage | Inadequate protection, handling | Field returns, failure analysis | RMA, repair, redesign | Proper ESD design, handling procedures |
| Thermal fatigue | CTE mismatch, thermal cycling | Field returns, failure analysis | RMA, repair, redesign | Material selection, thermal design, solder joint design |
| Corrosion | Contamination, inadequate protection | Field returns, visual inspection | RMA, repair, redesign | Conformal coating, material selection, environmental design |

**Class 4: Business Failures (The Silent Killers)**

| Failure | Root Cause | Detection | Recovery | Prevention |
|---------|-----------|-----------|----------|------------|
| Cost overrun | Underestimated complexity, yield loss | Financial tracking | Negotiate, absorb, redesign | Accurate estimation, DFM review, yield modeling |
| Schedule slip | Unexpected issues, resource constraints | Project tracking | Crash schedule, reduce scope | Buffer time, risk management, realistic planning |
| Quality escape | Inadequate testing, design flaw | Field returns, customer complaints | Recall, redesign, process improvement | Comprehensive testing, FMEA, design review |
| Obsolescence | Component EOL, technology change | BOM monitoring | Redesign, last-time buy | Component lifecycle management, second-source strategy |
| Regulatory failure | Non-compliance with standards | Certification testing | Redesign, retest | Early compliance planning, pre-compliance testing |


## SUPERPOWER ACTIVATION (How to Become Unstoppable)
### The Infineon Power Electronics Layout App Notes Superpower

**What This Skill Gives You:**
- The ability to see problems before they become failures
- The confidence to make quantitative decisions, not guesses
- The discipline to document every decision with rationale
- The wisdom to know when to over-engineer and when to simplify
- The humility to ask for help when you don't know

**Activation Ritual:**
1. **Adopt the Mental Model:** Think like Infineon Power Electronics Layout App Notes — see the invisible, question the obvious
2. **Execute the Operational System:** Follow the phases, don't skip steps
3. **Embrace the Failure Universe:** Know what can go wrong, plan for it
4. **Document Everything:** If it's not documented, it didn't happen
5. **Validate Ruthlessly:** Trust but verify — with numbers, not feelings

**Integration with Other Skills:**
- Combine with Skill 077 (Saturn PCB Toolkit) for quantitative validation
- Combine with Skill 076 (IPC Standards) for formal compliance
- Combine with Skill 061 (EEVblog Forums) for peer validation
- Combine with Skill 081 (Rick Hartley GND Planes) for ground truth
- Combine with Skill 091 (Altium TechDocs) for tool implementation

**When to Escalate:**
- When the design exceeds your expertise (call an expert)
- When the failure cost exceeds the design budget (get approval)
- When the schedule doesn't allow for proper validation (negotiate or accept risk)
- When the requirements are unclear (demand clarification)
- When the manufacturing target is undefined (assume worst case)

**The Ultimate Question:**
"Would I bet my career, my company's reputation, and my customer's safety on this design?"
If the answer is not an unqualified YES, keep working.


## OUTPUT FORMAT
When this skill executes, produce:
1. **Mental State**: What perspective the agent adopted
2. **Decisions Made**: Specific choices with quantitative rationale
3. **Calculations Performed**: All math with inputs, formulas, and outputs
4. **Risks Identified**: What could fail and mitigation strategies
5. **Validation Results**: Pass/fail for each gate with evidence
6. **Next Actions**: What the agent will do next
7. **Knowledge Gaps**: What the agent doesn't know and needs from user

## DEPENDENCIES
- Skill 047 (TI Application Reports): For power supply layout
- Skill 076 (IPC Standards): For formal acceptance criteria
- Skill 061 (EEVblog Forums): For peer review validation

## ANTI-PATTERNS (What Destroys This Skill)
- NEVER make a design decision without quantitative justification
- NEVER skip validation because 'it looks fine'
- NEVER ignore manufacturing feedback from previous revisions
- NEVER design without understanding the failure cost
- NEVER skip documentation because 'everyone knows this'
- NEVER share vias between capacitors and IC power pins
- NEVER place decoupling capacitors more than 5 mm from power pins
