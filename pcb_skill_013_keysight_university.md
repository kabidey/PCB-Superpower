# SKILL: Keysight University

## Skill Metadata
- **ID**: 13
- **Category**: learning_platforms
- **Source**: Keysight University
- **URL**: https://www.keysight.com/find/keysight-university
- **Description**: Deep-dive webinars, engineering modules, and masterclasses dedicated to RF design and advanced signal integrity.
- **Soul**: The measurement truth - if you cannot measure it, you do not understand it.
- **Complexity**: Advanced
- **Confidence Threshold**: 0.85

## MENTAL MODEL (How to Think Like This Expert)
### The Keysight University Perspective

**Core Belief:** The measurement truth - if you cannot measure it, you do not understand it.

**How This Expert Sees the World:**
- Every PCB is a signal integrity analysis first, a collection of components second
- The invisible (RF design principles) matters more than the visible (traces and pads)
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
- When the design challenge maps to signal integrity analysis
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

**Core Technical Analysis (from Keysight University):**

**Signal Integrity Deep Dive:**

1. **Edge Rate Classification:**
   - T_r > 10 ns: Lumped element, no special treatment
   - 1 ns < T_r < 10 ns: Watch trace lengths, consider termination
   - T_r < 1 ns: Full transmission line treatment required
   - T_r < 100 ps: Everything is a transmission line, including vias

2. **Impedance Budget:**
   - Target Z0: 50Ω ± 10% (single-ended), 90Ω ± 10% (differential USB), 100Ω ± 10% (differential Ethernet)
   - Trace width calculation: Z0 = f(Er, h, w, t) — solve for w given target Z0
   - Example: Er=4.3, h=0.127mm, t=0.035mm, target Z0=50Ω
     → w ≈ 0.18mm (7 mils) for microstrip
     → w ≈ 0.09mm (3.5 mils) for stripline

3. **Length Matching Budget:**
   - DDR3: ±25 mils (0.635 mm) per byte lane
   - DDR4: ±10 mils (0.254 mm) per byte lane
   - DDR5: ±5 mils (0.127 mm) per byte lane
   - PCIe Gen3: ±5 mils (0.127 mm) per lane pair
   - PCIe Gen4/5: ±2 mils (0.051 mm) per lane pair
   - USB3: ±5 mils (0.127 mm) per SSTX/SSRX pair

4. **Via Stub Analysis:**
   - Stub length < λ/20 at highest frequency
   - λ = c / (f × √Er_eff) where c = 3×10⁸ m/s
   - Example: f = 5 GHz, Er_eff = 3.5
     λ = 3×10⁸ / (5×10⁹ × √3.5) = 0.032 m = 32 mm
     Max stub = 32/20 = 1.6 mm
   - If stub > max: use backdrill, blind via, or change layer assignment

5. **Crosstalk Budget:**
   - Aggressor-victim spacing: 3W for parallel runs > 1 inch
   - Aggressive high-speed: 5W spacing
   - NEXT < 5% of signal swing
   - FEXT < 5% of signal swing

**RF Design Deep Dive:**

1. **Wavelength & Electrical Length:**
   - λ = c / (f × √Er_eff)
   - Example: f = 2.4 GHz, Er_eff = 3.5
     λ = 3×10⁸ / (2.4×10⁹ × √3.5) = 0.0668 m = 66.8 mm
   - Electrically short: length < λ/10 = 6.68 mm
   - Electrically long: length > λ/10 → transmission line required

2. **Microstrip Design (50Ω):**
   - h = 0.127 mm, w ≈ 0.18 mm, t = 0.035 mm
   - Z0 ≈ 50Ω (verified with field solver)
   - Smooth curves, no sharp corners
   - Ground stitching vias around RF section

3. **Matching Network (L-section):**
   - For R_source = 50Ω, R_load = 100Ω:
     Q = √(R_load/R_source - 1) = 1
     X_series = Q × R_source = 50Ω (inductive)
     X_shunt = R_load / Q = 100Ω (capacitive)
   - At 2.4 GHz:
     L_series = 50 / (2π×2.4×10⁹) = 3.32 nH
     C_shunt = 1 / (2π×2.4×10⁹×100) = 0.663 pF

4. **RF Layout Rules:**
   - Route RF traces first, before digital
   - Maintain constant trace width
   - No layer changes for RF traces
   - Keep away from board edges (min 3× trace width)
   - Place ground stitching vias around RF traces (via fence)

### Phase 3: Quantitative Verification

**Verification Checklist (from Keysight University):**
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
### The Failure Modes of Keysight University

**Class 1: Design Errors (Your Fault)**

| Failure | Root Cause | Detection | Recovery | Prevention |
|---------|-----------|-----------|----------|------------|
| Impedance mismatch | Wrong trace width for stackup | TDR measurement, simulation | Adjust trace width, add termination | Calculate width from stackup before routing |
| Excessive reflections | Unterminated transmission line | Eye diagram, TDR | Add series/parallel termination | Identify critical lengths, plan termination |
| Crosstalk violation | Insufficient spacing | Near-end/far-end crosstalk measurement | Increase spacing, add guard trace | Apply 3W/5W rule during placement |
| Timing skew | Unequal trace lengths | TDR, oscilloscope | Add tuning structures | Plan length matching during routing |
| Via stub resonance | Long via stubs at high frequency | S-parameter measurement, simulation | Backdrill, use blind vias | Calculate max stub length from frequency |
| Ground bounce | High loop inductance, simultaneous switching | Oscilloscope, noise measurement | Add ground stitching vias, reduce loop area | Plan return path continuity |
| Power rail collapse | Insufficient decoupling, high PDN impedance | Oscilloscope, PDN measurement | Add capacitors, reduce loop inductance | Calculate PDN impedance target |

| Failure | Root Cause | Detection | Recovery | Prevention |
|---------|-----------|-----------|----------|------------|
| Schematic error | Wrong component, missing connection | ERC, functional test | Redesign, rework | Thorough ERC, peer review |
| Layout error | Wrong footprint, incorrect placement | DRC, visual inspection, functional test | Rework, redesign | Thorough DRC, 3D clearance check |
| Component unavailability | EOL, shortage, wrong package | BOM review, procurement | Find alternative, redesign | Check availability before design |
| Cost overrun | Unexpected manufacturing complexity | Quote review | Simplify design, change manufacturer | DFM review early |
| Schedule slip | Unexpected complexity, resource constraints | Project tracking | Crash schedule, reduce scope | Realistic estimation, buffer time |

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
### The Keysight University Superpower

**What This Skill Gives You:**
- The ability to see problems before they become failures
- The confidence to make quantitative decisions, not guesses
- The discipline to document every decision with rationale
- The wisdom to know when to over-engineer and when to simplify
- The humility to ask for help when you don't know

**Activation Ritual:**
1. **Adopt the Mental Model:** Think like Keysight University — see the invisible, question the obvious
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
- Skill 088 (W0QE RF Design): For RF matching networks
- Skill 076 (IPC Standards): For formal acceptance criteria
- Skill 061 (EEVblog Forums): For peer review validation

## ANTI-PATTERNS (What Destroys This Skill)
- NEVER make a design decision without quantitative justification
- NEVER skip validation because 'it looks fine'
- NEVER ignore manufacturing feedback from previous revisions
- NEVER design without understanding the failure cost
- NEVER skip documentation because 'everyone knows this'
- NEVER route RF traces with sharp corners or varying width
