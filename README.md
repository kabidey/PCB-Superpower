# PCB Design Bulletproof Agentic Skills (v4.0)

## What Makes These Bulletproof

Each skill is a **complete operational system** — not just a reference, not just a procedure, but a **mental model** that your agent can inhabit.

### The Four Pillars of Every Skill

1. **MENTAL MODEL** — How to think like the expert
   - Core belief system
   - Decision framework (First Principles → Quantitative Rigor → Manufacturing Reality → Economic Truth → Testability Mandate)
   - Cognitive biases to avoid
   - When to activate

2. **OPERATIONAL SYSTEM** — How to execute like the expert
   - Contextual intelligence gathering (8 critical questions before any action)
   - Domain-specific deep analysis with real formulas
   - Quantitative verification checklist
   - Decision documentation requirements

3. **FAILURE UNIVERSE** — What can go wrong & how to survive
   - Class 1: Design Errors (Your Fault)
   - Class 2: Manufacturing Errors (Their Fault, Your Problem)
   - Class 3: Field Failures (Everyone's Nightmare)
   - Class 4: Business Failures (The Silent Killers)

4. **SUPERPOWER ACTIVATION** — How to become unstoppable
   - What this skill gives you
   - Activation ritual
   - Integration with other skills
   - When to escalate
   - The ultimate question

### Real Formulas Included

**Impedance Control:**
- Microstrip: Z₀ = (87/√(Er+1.41)) × ln(5.98h/(0.8w+t))
- Stripline: Z₀ = (60/√Er) × ln(4h/(0.67π(0.8w+t)))
- Differential: Zdiff = 2×Z₀×(1-0.48×e^(-0.96×s/h))

**Signal Integrity:**
- Reflection: ρ = (ZL-Z₀)/(ZL+Z₀), RL = -20×log₁₀(|ρ|)
- Critical length: Lcrit = Tr/(2×Tpd) where Tpd ≈ 150 ps/inch for FR-4
- Crosstalk: VNEXT/Vdrive = (1/4)×(Lm/Lself + Cm/Cself)×(Td/Tr)

**Power Delivery:**
- PDN target: Ztarget = Vripple/(0.5×Itransient)
- Capacitor SRF: fSRF = 1/(2π√(LESL×C))
- Plane capacitance: Cplane = (Er×ε₀×A)/d

**Thermal Management:**
- θJA = θJC + θCS + θSA
- ΔT = P × θJA
- Heatsink: θSArequired = (Tjunctionmax - Tambient)/P - θJC - θCS

**Manufacturing (IPC-2152):**
- I = k×ΔT^b×A^c where k=0.048, b=0.44, c=0.725
- Aspect ratio: AR = thickness/drill < 10:1
- Copper balance: |coverage_top - coverage_bottom|/average < 15%

**EMC/Shielding:**
- Shielding: S = A + R + B (dB)
- Slot leakage: S = 20×log₁₀(λ/(2×l))
- Ground bounce: VGB = Lloop × di/dt

**RF Design:**
- Wavelength: λ = c/(f×√Er_eff)
- Matching: Q = √(Rload/Rsource - 1)
- Electrically short: length < λ/10

## Complete Skill Registry

| ID | Skill Name | Category | File |
|----|-----------|----------|------|
| 1 | Altium Academy | Learning | `pcb_skill_001_altium_academy.md` |
| 2 | FEDEVEL Academy | Learning | `pcb_skill_002_fedevel_academy.md` |
| 3 | Robert Feranec (YouTube) | Learning | `pcb_skill_003_robert_feranec_youtube.md` |
| 4 | Contextual Electronics | Learning | `pcb_skill_004_contextual_electronics.md` |
| 5 | EEVblog (YouTube) | Learning | `pcb_skill_005_eevblog_youtube.md` |
| 6 | KiCad Academy | Learning | `pcb_skill_006_kicad_academy.md` |
| 7 | Coursera (Circuits & Systems) | Learning | `pcb_skill_007_coursera_circuits_systems.md` |
| 8 | edX (MIT/Berkeley Engineering) | Learning | `pcb_skill_008_edx_mitberkeley_engineering.md` |
| 9 | Udemy PCB Design Masterclasses | Learning | `pcb_skill_009_udemy_pcb_design_masterclasses.md` |
| 10 | PhilsLab (YouTube) | Learning | `pcb_skill_010_philslab_youtube.md` |
| 11 | DesignSpark Learning | Learning | `pcb_skill_011_designspark_learning.md` |
| 12 | Hackaday U | Learning | `pcb_skill_012_hackaday_u.md` |
| 13 | Keysight University | Learning | `pcb_skill_013_keysight_university.md` |
| 14 | Ansys Innovation Courses | Learning | `pcb_skill_014_ansys_innovation_courses.md` |
| 15 | Texas Instruments Precision Labs | Learning | `pcb_skill_015_texas_instruments_precision_labs.md` |
| 16 | Signal Integrity Journal | Signal Integrity | `pcb_skill_016_signal_integrity_journal.md` |
| 17 | Bogatin’s Practical Readout | Signal Integrity | `pcb_skill_017_bogatins_practical_readout.md` |
| 18 | In-Circuit Design (ICD) | Signal Integrity | `pcb_skill_018_in_circuit_design_icd.md` |
| 19 | Speeding Edge | Signal Integrity | `pcb_skill_019_speeding_edge.md` |
| 20 | Polar Instruments | Signal Integrity | `pcb_skill_020_polar_instruments.md` |
| 21 | BeTheSignal.com | Signal Integrity | `pcb_skill_021_bethesignalcom.md` |
| 22 | EDN Network Design Center | Signal Integrity | `pcb_skill_022_edn_network_design_center.md` |
| 23 | EEWeb Signal Integrity | Signal Integrity | `pcb_skill_023_eeweb_signal_integrity.md` |
| 24 | Intel High-Speed PCB Layout Guidelines | Signal Integrity | `pcb_skill_024_intel_high_speed_pcb_layout_guidelines.md` |
| 25 | AMD/Xilinx PCB Design Guides | Signal Integrity | `pcb_skill_025_amdxilinx_pcb_design_guides.md` |
| 26 | Samtec Microelectronics Insights | Signal Integrity | `pcb_skill_026_samtec_microelectronics_insights.md` |
| 27 | Microwave Journal | Signal Integrity | `pcb_skill_027_microwave_journal.md` |
| 28 | Sierra Circuits High-Speed Design Blog | Signal Integrity | `pcb_skill_028_sierra_circuits_high_speed_design_blog.md` |
| 29 | Teledyne LeCroy Signal Integrity Academy | Signal Integrity | `pcb_skill_029_teledyne_lecroy_signal_integrity_academy.md` |
| 30 | Signal Integrity Quarterly | Signal Integrity | `pcb_skill_030_signal_integrity_quarterly.md` |
| 31 | JLCPCB Capabilities & DFM Guides | Manufacturing | `pcb_skill_031_jlcpcb_capabilities_dfm_guides.md` |
| 32 | PCBWay Community & Tech Blog | Manufacturing | `pcb_skill_032_pcbway_community_tech_blog.md` |
| 33 | Eurocircuits PCB Design Guidelines | Manufacturing | `pcb_skill_033_eurocircuits_pcb_design_guidelines.md` |
| 34 | Advanced Circuits (4PCB) Layout Tips | Manufacturing | `pcb_skill_034_advanced_circuits_4pcb_layout_tips.md` |
| 35 | Sierra Circuits Guide Center | Manufacturing | `pcb_skill_035_sierra_circuits_guide_center.md` |
| 36 | OshPark Docs | Manufacturing | `pcb_skill_036_oshpark_docs.md` |
| 37 | San Francisco Circuits Learning Center | Manufacturing | `pcb_skill_037_san_francisco_circuits_learning_center.md` |
| 38 | Sunstone Circuits Design Tips | Manufacturing | `pcb_skill_038_sunstone_circuits_design_tips.md` |
| 39 | Multi-Circuit Boards Technical Guide | Manufacturing | `pcb_skill_039_multi_circuit_boards_technical_guide.md` |
| 40 | Epec Engineered Components Blog | Manufacturing | `pcb_skill_040_epec_engineered_components_blog.md` |
| 41 | RayPCB Layout Blog | Manufacturing | `pcb_skill_041_raypcb_layout_blog.md` |
| 42 | PCB Cart Design Resource | Manufacturing | `pcb_skill_042_pcb_cart_design_resource.md` |
| 43 | Mill-Max Application Notes | Manufacturing | `pcb_skill_043_mill_max_application_notes.md` |
| 44 | Bittele Electronics Manufacturing Guide | Manufacturing | `pcb_skill_044_bittele_electronics_manufacturing_guide.md` |
| 45 | Proto-Express Design Guides | Manufacturing | `pcb_skill_045_proto_express_design_guides.md` |
| 46 | Analog Devices Technical Library | Silicon Vendor | `pcb_skill_046_analog_devices_technical_library.md` |
| 47 | TI Application Reports | Silicon Vendor | `pcb_skill_047_ti_application_reports.md` |
| 48 | STMicroelectronics Hardware Development Guides | Silicon Vendor | `pcb_skill_048_stmicroelectronics_hardware_development_.md` |
| 49 | NXP Hardware Design Checklists | Silicon Vendor | `pcb_skill_049_nxp_hardware_design_checklists.md` |
| 50 | Microchip WebSeminars | Silicon Vendor | `pcb_skill_050_microchip_webseminars.md` |
| 51 | Infineon Power Electronics Layout App Notes | Silicon Vendor | `pcb_skill_051_infineon_power_electronics_layout_app_no.md` |
| 52 | Murata Chip Capacitor Guides | Silicon Vendor | `pcb_skill_052_murata_chip_capacitor_guides.md` |
| 53 | onsemi Design Resources | Silicon Vendor | `pcb_skill_053_onsemi_design_resources.md` |
| 54 | Maxim Integrated (Analog Devices) Tutorials | Silicon Vendor | `pcb_skill_054_maxim_integrated_analog_devices_tutorial.md` |
| 55 | Renesas Hardware Layout Application Notes | Silicon Vendor | `pcb_skill_055_renesas_hardware_layout_application_note.md` |
| 56 | Skyworks RF Layout Application Notes | Silicon Vendor | `pcb_skill_056_skyworks_rf_layout_application_notes.md` |
| 57 | Nordic Semiconductor Infocenter | Silicon Vendor | `pcb_skill_057_nordic_semiconductor_infocenter.md` |
| 58 | Würth Elektronik Component Selection & Layout | Silicon Vendor | `pcb_skill_058_würth_elektronik_component_selection_lay.md` |
| 59 | Littelfuse ESD Protection Layout Guide | Silicon Vendor | `pcb_skill_059_littelfuse_esd_protection_layout_guide.md` |
| 60 | Silicon Labs Hardware Design Layouts | Silicon Vendor | `pcb_skill_060_silicon_labs_hardware_design_layouts.md` |
| 61 | EEVblog Electronics Community Forums | Community | `pcb_skill_061_eevblog_electronics_community_forums.md` |
| 62 | Reddit r/PrintedCircuitBoard | Community | `pcb_skill_062_reddit_rprintedcircuitboard.md` |
| 63 | Altium Forums | Community | `pcb_skill_063_altium_forums.md` |
| 64 | KiCad User Forum | Community | `pcb_skill_064_kicad_user_forum.md` |
| 65 | EDABoard.com | Community | `pcb_skill_065_edaboardcom.md` |
| 66 | Hackaday PCB Category | Community | `pcb_skill_066_hackaday_pcb_category.md` |
| 67 | Dangerous Prototypes | Community | `pcb_skill_067_dangerous_prototypes.md` |
| 68 | Dave Tweed’s Stack Exchange Contributor Profile | Community | `pcb_skill_068_dave_tweeds_stack_exchange_contributor_p.md` |
| 69 | Electronics Point | Community | `pcb_skill_069_electronics_point.md` |
| 70 | Element14 Community | Community | `pcb_skill_070_element14_community.md` |
| 71 | All About Circuits Forum | Community | `pcb_skill_071_all_about_circuits_forum.md` |
| 72 | EEWeb Community | Community | `pcb_skill_072_eeweb_community.md` |
| 73 | GitHub Open Source Hardware (Search Engine) | Community | `pcb_skill_073_github_open_source_hardware_search_engin.md` |
| 74 | Maker Pro Projects | Community | `pcb_skill_074_maker_pro_projects.md` |
| 75 | EngineerZone (Analog Devices) | Community | `pcb_skill_075_engineerzone_analog_devices.md` |
| 76 | IPC (Association Connecting Electronics Industries) | Standards | `pcb_skill_076_ipc_association_connecting_electronics_i.md` |
| 77 | Saturn PCB Design (Toolkit Download) | Standards | `pcb_skill_077_saturn_pcb_design_toolkit_download.md` |
| 78 | IPC-7351 Standard land Pattern Calculator | Standards | `pcb_skill_078_ipc_7351_standard_land_pattern_calculato.md` |
| 79 | Mantaro Trace Width Calculator | Standards | `pcb_skill_079_mantaro_trace_width_calculator.md` |
| 80 | Chemtech PCB Materials Guide | Standards | `pcb_skill_080_chemtech_pcb_materials_guide.md` |
| 81 | Rick Hartley’s "GND Planes" Architecture (YouTube) | Standards | `pcb_skill_081_rick_hartleys_gnd_planes_architecture_yo.md` |
| 82 | High Speed Digital Design: A Handbook of Black Magic | Standards | `pcb_skill_082_high_speed_digital_design_a_handbook_of_.md` |
| 83 | EMC for Product Designers | Standards | `pcb_skill_083_emc_for_product_designers.md` |
| 84 | Right the First Time | Standards | `pcb_skill_084_right_the_first_time.md` |
| 85 | Signal and Power Integrity - Simplified | Standards | `pcb_skill_085_signal_and_power_integrity_simplified.md` |
| 86 | Signal Integrity Issues and Printed Circuit Board Design | Standards | `pcb_skill_086_signal_integrity_issues_and_printed_circ.md` |
| 87 | PCB Toolkit by Mis (Web Apps) | Standards | `pcb_skill_087_pcb_toolkit_by_mis_web_apps.md` |
| 88 | W0QE RF Design (Technical Articles) | Standards | `pcb_skill_088_w0qe_rf_design_technical_articles.md` |
| 89 | Microwave 101 | Standards | `pcb_skill_089_microwave_101.md` |
| 90 | Henry Ott Consultants Technical Papers | Standards | `pcb_skill_090_henry_ott_consultants_technical_papers.md` |
| 91 | Altium TechDocs | EDA | `pcb_skill_091_altium_techdocs.md` |
| 92 | KiCad Documentation | EDA | `pcb_skill_092_kicad_documentation.md` |
| 93 | Autodesk Fusion 360 / Eagle Electronics Support | EDA | `pcb_skill_093_autodesk_fusion_360_eagle_electronics_su.md` |
| 94 | Cadence OrCAD/Allegro Information Hub | EDA | `pcb_skill_094_cadence_orcadallegro_information_hub.md` |
| 95 | Siemens EDA (PADS Hub) | EDA | `pcb_skill_095_siemens_eda_pads_hub.md` |
| 96 | DigiKey Scheme-it Portal | EDA | `pcb_skill_096_digikey_scheme_it_portal.md` |
| 97 | SnapEDA Blog | EDA | `pcb_skill_097_snapeda_blog.md` |
| 98 | Ultra Librarian Education Center | EDA | `pcb_skill_098_ultra_librarian_education_center.md` |
| 99 | Texas Instruments WEBENCH Design Center | EDA | `pcb_skill_099_texas_instruments_webench_design_center.md` |
| 100 | Cadence Sigrity System Analysis | EDA | `pcb_skill_100_cadence_sigrity_system_analysis.md` |

## Version
- **Generated**: 2026-06-24
- **Version**: 4.0 (Bulletproof)
- **Total Skills**: 100
- **Format**: Markdown with mental models, operational systems, failure universes, and superpowers
