# Two Loose Screws — boat project notes

**Boat:** 2000 Regal 2760 Commodore · HIN RGMRC083C000 · $2,000 Copart auction.
**Loss story (per insurance record):** during a bad Arkansas storm the bilge flooded, the bilge
pump shorted, and the boat "sank" — but physical evidence says it never fully went under.
Best fit: **settled stern-low / partially swamped** (freshwater). Water backed up the exhaust
into the RIGHT engine via an open exhaust valve (→ water found in right pan; left pan dry).
Old manifolds/risers inspected 2026-08-29: not rotted — ingress was backflow, not a breach.
Consequences: inspect everything below the stern-low waterline (trim pumps, low connectors,
transom electrics, drive tops/bellows); **replace bilge pump(s) + float switches + wiring before
she floats** (the shorted pump is why the boat was lost) — add second pump + high-water alarm.
2026-09-06 refinement: found a **shattered ~25W cheap solar panel** aboard → boat likely was NOT
on shore power; storm scenario is probably **battery exhaustion** (days of rain, no solar, pump
cycling until the battery died), not a literal pump short — pumps run fine on manual switch today.
To-do: test float switches (lift by hand, helm switch off); load-test both batteries (assume
sulfated); decide shore-power vs proper solar (50–100W + MPPT) for where she'll live; backup
pump gets own thru-hull/hose/float/fuse — NO shared discharge, NO check valve.
**Power — ENGINES ARE NOT TWINS (discovered 2026-09-01):**
- **PORT: original Volvo Penta 4.3Gi**, Gen-I 262 V6, 349.7 hrs (its tach works). Compression
  tested 2026-08-30: 135-152 PASS.
- **STARBOARD: Marine Power barcode sticker found on valve cover — repower POSSIBLE, NOT CONFIRMED.**
  Engines look identical (but repowers transfer dress parts, so looks don't settle it).
  VERIFY: (1) Volvo serial plate low on stbd flywheel housing near starter — present+era-correct
  = original engine, sticker was a part/service; absent = repower. (2) Block casting date on
  block side. (3) Photograph the barcode sticker — decode model/date from its text.
  Stbd tach dead + Carter fuel pump + hours unknown either way.
  **PARTS RULE: verify starboard's consumables (oil filter thread! plugs!) against ITS OWN old
  parts/tag — do NOT assume it matches port.** Internal parts order by Marine Power spec.
- Working theory (inferred): repower was recent at time of loss — fits fresh 7/8 fuel tank,
  clean-smelling fuel, mid-service disconnections. Boat may carry a nearly-new engine.
Both engines rotate clockwise viewed from the front; counter-rotation happens in the drive (LH prop on port).
SX drives, serpentine belts.

## Artifacts (claude.ai/code)

- Turning the 4.3Gi (field card): https://claude.ai/code/artifact/c1a71f75-9192-4086-ab0b-21939bdd6b4c
- Mi Amor Manual Library: https://claude.ai/code/artifact/af534e50-c8bd-4033-be32-6d217c2bd637
- Two Loose Screws — the $2,000 boat: https://claude.ai/code/artifact/884f3ced-ef6a-4903-962c-fb5b1d1e8fb3
- Field check: https://claude.ai/code/artifact/7c72b538-c759-4f77-a93e-0a05d5e1d97f
- Copart auction record: https://claude.ai/code/artifact/d4602e24-579e-481c-b065-d0f6ba0120af
- Bimini/camper tops session (2026-08-28): 4 canvas shops + strategy, ~$3–4k factory fit
- Kohler 5E genset: oil refill + fuel sender gasket diagnosis (session 2026-08-27)

**Hour meter (tach LCD), read 2026-08-31: 349.7 hrs** — ~14 hrs/yr over 24 seasons: a low-use,
well-kept boat. Baseline for all hours-based maintenance going forward. (Cross-check the second
tach's meter when convenient; matching totals = trustworthy.)
**STARBOARD tach came alive 2026-09-01 — hour meter 360.0 hrs.** Ten hours off port's 349.7:
both engines have lived the same life on this boat (does not settle the repower question on
its own, but it is what an original pair looks like).
**Kohler 5E genset hour meter: 92.0 hrs** (read 2026-08-31) — corroborates the ~14 hr/yr
low-use story from an independent meter; genset baseline for service intervals.
Dash note: both Faria TRIM gauges peg "UP" regardless of actual drive position → open sender
circuit(s), fix-later. Trim pump relay clicks, motor silent → suspect stuck brushes/corroded
motor or relay contacts (transom sat low); hammer-tap test pending.

## Progress log

- 2026-08 early: hand-turned engines (plugs out), read starter water lines, freed rotation
- 2026-08-26: "Turning the 4.3Gi" field card (crank balancer access, ring-gear pry method)
- 2026-08-29: **both new starters installed; LEFT (port) engine turns over on the key.**
  Manifolds + risers/tops + impeller reinstall in progress.
- 2026-08-29 oil check (initial read): left pan looked dry, right had some water.
- 2026-09-06 oil extraction, BOTH engines (~10 qt total): **each pan had ~1/2 to 1 cup of
  water — symmetric.** Verdict: normal 2-year condensation, NOT exhaust-path ingress;
  the earlier "right engine drank" theory is retired. Old manifolds/risers inspected: not
  rotted (metal/graphite gaskets scraped clean, faces dressed flat).
  After first run + heat cycles: check dipsticks for new water (expect none), second oil
  change to finish the flush.

## FIRST ENGINE START — 2026-09-01 (on muffs, drives fully down, hatch open, blower on)

- **STARBOARD started almost immediately on the first key.** Water flow at prop hub / idle relief
  slots NOT yet confirmed — confirm before any more running (impeller rule: never run dry).
- **PORT: no start on its own fuel; starts and runs on ether** → spark + compression good, problem
  is fuel delivery. Throttle body very dirty. Injectors went from dripping varnished gas to
  misting stale gas, engine tried to hold ~2000 rpm then died. **Water found in port's fuel/water
  separator.** Working theory (inferred, fits the facts): boat sits at an angle; port pickup is on
  the low side of the tank and draws the water layer; starboard's pickup sits in clean gas.
- Action: pump the tank until jar samples show no water/phase layer. Tank hose was disconnected
  at the port fuel module (the hose that runs to the tank, next to the separator), run out the
  transom drain hole, **siphon into cans on the ground** (no pump, no sparks, gravity head from
  the cockpit-sole tank to ground level). Prime with the extractor / a primer bulb — never by
  mouth. If it will not flow: that is the tank's anti-siphon valve doing its job, not a clog
  (needs pump suction; pull the valve at the tank fitting only for the flush, then refit).
  If it siphons freely on its own: note it — there may be NO anti-siphon valve (required on a
  gas boat; add one). Fallback = pull the WEMA sender (top of tank) and drop a tube to the tank
  floor on the low corner — reaches below the pickup.
- Port fuel module (casting 170-2624 FM 1) hose map — INFERRED from Gi module design, verify
  by tracing each hose: tank supply IN + return TO tank (both head toward the tank), pressure
  feed TO throttle body + regulator return FROM throttle body (both head to the engine top).
  Fuel cooler water hoses (black) are separate if present.
- **PORT RUNNING 2026-09-01** after siphoning water/stale fuel from the tank. Idle high — no
  idle screw on MEFI; do NOT touch the throttle stop. Order: warm up, lever on its stop, IAC
  relearn (batteries were off), clean IAC + throttle bores, vacuum leak, TPS ~0.5 V at idle.
  Normal warm: 600–700 rpm, temp 160–180°F (160°F thermostat), riser elbows hand-holdable.
  **Held 2500 rpm smooth on muffs** — that is NOT an IAC/relearn problem (IAC bypass tops out
  ~1200–1500): throttle plates are open (cable holding lever off the stop, binnacle in
  throttle-only mode) or a big intake air leak. Battery switch OFF = full ECM reset (ECM feed
  is downstream of the switch); no cable pull needed. Too fast for muffs — key off and find it.
- **Starboard water leak on top of engine** (thermostat housing / manifold water inlet /
  riser joint — exact spot TBD): snug clamps or re-torque cold, new gasket if it still weeps.
  Fix-before-lake item.
- Still to do before port runs on its own: new separator (Quicksilver 8M0154772) on arrival,
  fill it with clean gas, several key-on prime cycles, flame arrestor ON before running,
  lever at idle (neutral throttle release = round button at the lever pivot hub).
- Port oil reads slightly over the full mark before first run — re-check after the first run
  (new dry filter takes some), pump a bit out only if still over.

## Bilge blower — burning-wire smell when running (2026-09-01) → REPLACE, do not run

Blower works but smells of hot insulation = motor windings/bearing cooking. In a gasoline
compartment that is an ignition source in its own right. **Do not use it until replaced.**
Blower ventilation is required by regs (USCG 33 CFR 183.610) — no blower = no lake.
Location research (2026-09-01): Regal does not print the blower location in any 2760-era
manual we can reach (Commodore 272/276/300/400 manual, 2000, 2300/2500/2550, 2700/2750,
General Vessel manual all checked; Regal's older-model library is a JS app we cannot read;
the 2860 successor manual on issuu is gone). What Regal DOES say, consistently: fresh air
enters through the hull/deck vent shrouds; **a powered blower attached to duct work whose
intake sits in the lower one-third of the bilge evacuates air to the atmosphere**; "check the
ventilation ducts and black bilge hose"; blower switch at the helm, fuse marked Blower on the
DC panel; ABYC/Regal blower wire = **yellow 12 AWG** (yellow/black is stereo memory).
FIND IT: run the switch and follow the sound, or follow the flex duct from the hull-side/
transom cowl vents inboard — the motor sits at the vent end, high on the compartment side.
Twin-engine 2760 likely has two. When replacing: measure the duct ID first (3" vs 4"), buy
ignition-protected (USCG/SAE J1171 on the label) inline blower, replace the duct if crushed/
cracked, intake end must sit low in the bilge but above bilge water; check the yellow feed
and ground for heat damage at the motor end; verify the helm fuse value matches the new motor.
Sister-boat listing (2001 2760, broker sheet) equipment list, INFERRED for ours: 30 A shore
inlet (→ expect L5-30 125 V), 6-gal water heater with heat exchanger (120 V element = shore
fault suspect), 2 bilge pumps, 2 batteries + 3-position switch.

## ⚠ SHORE POWER FAULT — HARD GATE (found 2026-09-01)

**Derek feels AC "juice" on the outdrive when the boat is on shore power (on the trailer).**
That is a leak to the AC safety ground PLUS an open/poor ground path back to the outlet.
In the water this is electric-shock-drowning territory for anyone swimming near the boat.
**GATE: no dock shore power at Crystal Springs until the tests below pass.** Galvanic isolator
does NOT address this. Deferred until engines are running; meanwhile: unplug before wrenching
(drive, block, manifolds are all bonded and live).
Observation: tingle on the OUTDRIVE, none on the ENGINE. Most likely reading: same voltage on
both, different reference — engine is touched from inside the boat (standing on fiberglass,
no circuit), drive is touched from the dirt (earth-referenced). Alternate: drive lost its bond
to the transom shield/engine. Separate them: AC volts earth→block vs earth→drive while plugged
in; then ohms drive→block unplugged (want <1 Ω, else fix the bonding strap first).
Prime suspect: the L6-30 → household adapter. L6-30 = 250 V, two hots + ground, NO neutral;
a 2760 with a single 30 A inlet should be L5-30 (125 V, H-N-G). READ THE INLET STAMP. If it is
truly L6-30 fed from a 120 V cord, the adapter is arbitrarily assigning hot/neutral to a
two-hot panel. Second suspects (swamped stern-low): Xantrex charger leaking to case, water
heater element, any AC box that went under, genset transfer switch bonding N-G on shore.
Test sequence (boat on trailer): (1) 3-light tester on outlet, then every cord/adapter end —
open ground / reversed polarity. (2) Plugged in, AC volts drive→screwdriver in wet dirt and
drive→outlet ground pin; record. (3) Cord off the wall, still in the boat: ohms wall-end ground
pin→engine block, want <1 Ω. (4) Same, main breaker on: ohms hot→ground and neutral→ground at
wall end, both must be open; kill branch breakers one at a time to name the leaking circuit.
(5) Clamp H+N together at the cord under power: any reading = leakage, marine limit 30 mA.
A GFCI not tripping is NOT a pass (open ground → leak has no path until a person is one).
Later, with the fix: galvanic isolator (ABYC A-28) in the green wire for dock life, and
consider an ELCI breaker at the inlet.

## Trim system — RESTORED 2026-08-31 (both drives, $0 parts)

Symptom: both pumps dead from helm; motors proven good on direct 12V. Root causes found:
- **Engine 1: main round 9-pin engine harness connector** making partial contact (same connector
  that caused the earlier no-crank). Fixed by reseat. TO-DO: pin-height check, contact cleaner,
  dielectric grease, firm seat.
- **Engine 2: 55A trim breaker stuck** — no power at OUT side; percussion (channellocks) freed it.
  **TO-DO (priority): REPLACE this breaker** (~$20, Sierra 18-69550 family / match stamping) —
  a breaker that needed hammering will stick again. Channellocks stay aboard until swapped.
Also found: trim sender bullet connectors unplugged at BOTH drives (explains gauges pegged UP) —
replug; several factory-capped unused circuits (bail-clip caps = ignore). Manual drive control
any time: jumper battery direct to pump motor wires (grn/wht + ppl/wht, swap polarity to reverse).
Full research + wiring map: TRIM-TRACING.md.

## Compression test — 2026-08-30 — PORT (left) engine, the clean-oil one

Cold, plugs out, cranking, Pittsburgh 62622 gauge. Owner's numbering: left-front = 1, down the bank.
**Left bank: 135 · 152 · 152 — Right bank: 152 · 137 · 145** (psi)
Verdict: PASS — no dead holes, no adjacent-pair pattern, spread ~11%.
Fresh-smelling fuel misted from plug holes during cranking (injectors firing — fuel pump
fuse was not pulled): possible fuel wash means the 135/137 may read low. Retest the
low holes after first heat cycles; expect them to climb toward 150.

## Exhaust reassembly — 4.3Gi torque specs

No specs came with the gasket sets. Community/service consensus for Volvo Penta 4.3 GL/Gi:

**OIL FILTER — CORRECTED 2026-08-31 (do not trust old notes/retail cross-listings):**
The filter ON these engines is **Volvo 841750** — thread **M18x1.5 metric**, gasket 2.734" OD,
can 2.99"x4.92". Correct crosses: **AC Delco PF52 / Fram PH3980 / STP S3980 / Super Tech ST3980 /
Wix 51036 / NAPA 1036 / Sierra 18-7879**. The 3850559 / Wix 51061 / STP S5 / PH30 family is
13/16"-16 imperial thread and DOES NOT FIT — earlier notes recommending it were wrong.
Rule learned (3x today): the label on the old part outranks every cross-reference database.

- **Manifold → cylinder head (graphite gasket, DRY, no sealant):**
  20–26 ft·lb. Start at center bolts, work outward. Two passes (snug ~15, final ~25).
- **Riser/elbow → manifold (metallic water-passage gasket, DRY):**
  even cross pattern in steps to ~25 ft·lb (OEM metal gasket). Long bolts relax —
  wait a few minutes after final torque and re-check. Aftermarket paper (Barr) gaskets
  spec higher (36–38 ft·lb) — follow the gasket maker if the packaging states a number.
- **RE-TORQUE everything after the first run + full cool-down.** Graphite relaxes on first heat cycle.
- Flood boat: inspect manifold/riser mating faces with a straightedge, wire-brush old residue,
  and eyeball water passages for rust-through before final assembly.

## Impeller (crank-driven sea water pump, front of engine, black hoses)

- Lube impeller with glycerin/dish soap only — no petroleum grease.
- Vanes all bent the same way, trailing relative to rotation (CW from front); housing screws snug only.
- Never run the pump dry — hand rotation is fine.
