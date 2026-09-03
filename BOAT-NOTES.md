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
To-do: **test float switches with BOTH helm switches AND the battery switch OFF** (lift by
hand; must run → auto circuit is independent, fused direct to the battery; if not, find the
inline fuse / rewire — manual says only "Aft Bilge 7 A / Fwd Bilge 7 A operates pump", nothing
about the float circuit; two pumps: mid bilge under the stairs, aft in the engine area); load-test both batteries (assume
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
- **REGAL FACTORY OWNER'S MANUAL FOUND 2026-09-02: "Manual - 2760, 292, 3060, 3260.pdf"** (141 pp,
  scanned/no text layer, 72 MB) in Regal's older-model archive (Canto). Also grabbed the
  successor-hull manual "2465, 2665, 2765, 2860, 3260" (216 pp, text). Files live in the session
  scratchpad (too big for git) — sent to Derek's phone. HOW TO RE-FETCH ANY REGAL MANUAL:
  `curl https://regalboats.canto.com/rest/share/protected/MG26S` → returns share id (/s/J4HTN);
  list: `rest/share/album/J4HTN/customview?type=document&size=1000&operator=and&time=1`
  (56 manuals, every model 1990s–2010s); download: `rest/share/album/J4HTN/rest/binary/
  document/<path-id>/download` (302 → signed CloudFront URL). 2760 id = ebps22k3f96vpbqiie55d7gs1j.

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
  **Held 2500 rpm smooth on muffs. ROOT CAUSE FOUND 2026-09-01: port IAC valve stuck open.**
  Diagnosis path: arrestor + PCV hoses back on → no change. Lever confirmed on its stop.
  **Throttle-body screws (deep dive 2026-09-02, GM Marine MEFI-3 manual L510004 + Merc parts):**
  the spring-loaded screw under the throttle lever is the throttle-shaft end nut with the return
  spring — NOT an adjuster. The real minimum-air stop screw is a Torx recessed inside the cast
  boss by the "TBI" letters, factory-sealed under a pressed steel cup plug (Merc "PLUG 806899") —
  the "little metal cover". GM: minimum air is factory-set and "should not be altered by turning
  the stop screw or bending the linkage." Idle spec: 600 rpm (Volvo book: in gear; Merc: neutral,
  "not adjustable"). TPS closed-throttle 0.3–0.9 V, typical 0.70–0.80 V on MEFI (not 0.5 V).
  Base timing 8° BTDC, ECM-controlled (needs base-timing mode to check). Nothing on the throttle
  body is an owner idle adjustment; idle problems are air-path problems.
  Unplugging the IAC changed nothing — CORRECT, a GM IAC is a stepper with no spring; unplugged
  it freezes in place (that test proves nothing). Thumb-over-the-IAC-hole also proves nothing
  on a TBI 220 (cavity is fed from above the plates; GM plugs the orifice with tool J-33047).
  Definitive test: pulled both IACs — port pintle retracted (open) vs starboard extended
  (closed) after the same key-off park; **swapped starboard's IAC onto port → idle normal.**
  Lesson: the IAC bypass CAN hold a warm 4.3 at ~2500 when fully open (earlier 1200–1500 claim
  was wrong). Port's valve: no part number left (etched number gone); connector cap molded
  "90384 / C3059 / H" = mold + date codes, C3059 ≈ day 305 of 1999 (inferred) → original valve.
  **IAC PART — deep dive 2026-09-02 (research complete; adversarial-verify pass did not run):**
  - Cap number "90384" = trailing digits of **GM 17090384** (GM molds the last 5 of the 8-digit
    number on the cap — verified on a GM 25527077 photo whose cap reads "77905"). 17090384 is in
    Delphi CV10027's OE list → flange family 17090384/17076228 → 17111788 → 17113099 → **GM 19333272
    (current)**. INFERRED-strong (two independent facts agree).
  - **The auto-store "4.3 TBI" valve is WRONG for this boat.** ACDelco 217-437 / GM 25527077 /
    SMP AC1 / Duralast AC102 is THREAD-IN (32 mm hex, square plug, 72 mm). Ours is a 2-screw
    FLANGE with O-ring (GM Marine MEFI manual fig 2-23; part in hand). VERIFIED. Earlier note
    suggesting 217-437 is retracted.
  - Auto-store FLANGE family that matches (INFERRED, three sources agree: cap number, SMP AC6 OE
    list naming Volvo 3855194, Delcoribo cross): **lookup = 1990–95 Chevy/GMC C2500/C3500 7.4L
    (454) TBI idle air control valve.** Numbers: Standard AC6 · Delphi CV10027 · ACDelco 217-408 ·
    Walker 215-1009 · Wells 2H1045 · Duralast AC105 · BWD 21758 · NAPA Echlin 2-1758. ~$25–45.
    Spec: oblong 4-pin plug, 2 holes 5.0 mm, 64.5 mm long, 22 mm port, **10 mm pintle**.
    TRAP: the same trucks also list a 12 mm-pintle flange valve (SMP AC27 / ACDelco 217-429 /
    Wells 2H1043 / Duralast AC116) — CALIPER THE PINTLE on our valve before buying. A competing
    catalog cross (SMP AC5 / 217-419 / Duralast AC107 / BWD 21755) also claims the Mercruiser
    number; cap number says AC6 family. GM says pintle shape/diameter is application-specific,
    so physical match at the counter with the dead valve in hand is mandatory. Phone stock first.
  - Marine numbers VERIFIED from Volvo EPC (marinepartseurope, catalog 7797477, "Throttle Body
    Repair Kits" for 4.3GiPEFS): **Volvo 3855194** ("Sensor", supersedes 3855185; ~$290 dealer).
    Aftermarket marine: Recmar REC3855194 $99.60 (Marine Parts Express), Sierra 18-7704 (Volvo
    cross, $190–250), Sierra 18-7632-1 (Mercruiser 805224A1 cross, ~$120 — same-looking valve,
    Sierra keeps the numbers separate). Mercruiser kit = valve + screw 805400 + O-ring 808547.
  - First-hand reports: marine techs on iboats buy the GM/Delphi valve after reading the number
    off the old part; cheap Chinese valves came with wrong-shape pintles (two reports) — avoid.
  - DO NOT soak a used IAC (GM manual). Wipe pintle/seat with carb cleaner only.
  Starboard currently has NO IAC installed — do not run it until one is back in. Idle-valve pintle max ~1.1" (28 mm) from
  flange before install. Battery switch OFF = full ECM reset (ECM feed is downstream of the
  switch). Starboard cold idle on muffs: ~900 rpm.
- **Starboard water leak on top of engine** (thermostat housing / manifold water inlet /
  riser joint — exact spot TBD): snug clamps or re-torque cold, new gasket if it still weeps.
  Fix-before-lake item.
- **Port water at prop hub not yet seen** (2026-09-01). Expect water at hub / relief slots
  within 15–30 s of start on muffs; nothing by 60 s = key off (impeller dies dry). Order:
  muff seal on port gills + hose wide open → pull impeller cover (vanes trailing, lubed,
  gasket sealing) → pump-outlet hose pulled at the thermostat housing, 5-second run.
  Port ran a while at 2500 with water unconfirmed — riser hand test is now mandatory.
- **Kohler 5E genset fires on starter fluid** (2026-09-01) → spark/compression/controller OK,
  problem is fuel (same tank, same water). Check: electric fuel pump runs during crank; drain
  the carb bowl; carb fuel-shutoff solenoid pulls in at 12 V; inline filter; anti-siphon valve
  at the tank fitting for the genset pickup. **RULE: genset has its own raw-water intake — muffs
  do not feed it. No run beyond a few seconds without a hose on its intake** (impeller + rubber
  exhaust mixer cook dry). Power test when it runs: ~120 V at its breaker, then hold under a
  real load (heat gun / shop vac).
  **Genset is LIQUID-COOLED, closed loop** (Kohler TP-5986 service manual, verified): Kawasaki
  FD501D 2-cyl water-cooled, 3600 rpm; heat exchanger + recovery tank (3.0 qt + 8 oz antifreeze),
  thermostat, rubber-impeller seawater pump on the generator end (impeller kit Kohler 359978),
  water-cooled exhaust manifold + mixer; seawater inlet hose 3/4" ID; shutdowns: exhaust temp
  215°F, coolant 232°F. Looks air-cooled because the FD501D has a fan/shroud. TO-DO: coolant
  level/condition + bleed, impeller kit, check siphon break in the seawater line.
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
**LOCATION (factory drawing 4-13, verified): BLOWER at the starboard aft corner of the engine
compartment, next to the waste pump-out fitting.** One blower shown. When replacing: measure the duct ID first (3" vs 4"), buy
ignition-protected (USCG/SAE J1171 on the label) inline blower, replace the duct if crushed/
cracked, intake end must sit low in the bilge but above bilge water; check the yellow feed
and ground for heat damage at the motor end; verify the helm fuse value matches the new motor.
Sister-boat listing (2001 2760, broker sheet) equipment list, INFERRED for ours: 30 A shore
inlet (→ expect L5-30 125 V), 6-gal water heater with heat exchanger (120 V element = shore
fault suspect), 2 bilge pumps, 2 batteries + 3-position switch.

## Fresh water + head (started 2026-09-02)

Spec sheet (2001 sister listing, inferred for ours): 27-gal water tank, pressure hot/cold,
6-gal water heater w/ heat exchanger, transom shower, **manual toilet** + holding tank, tank
monitor (waste + fresh). No dockside water inlet listed. Regal manual: deck fill with internal
vent (burps when full), 12 V pressure pump on a dash switch "fresh water pump" (5 A fuse),
pressure switch stops the pump. No changeover valve — if a CITY WATER hose-thread inlet exists
it has a check valve, pressurizes the taps directly, does NOT fill the tank; never leave the
boat on it unattended. Startup: switch on, open a tap to purge air. Runs-forever = empty tank /
open tap / suction air leak; won't run = fuse, switch, stuck pressure switch (tap it).
**Water heater: do NOT power the 120 V element until it is full AND the shore-ground test has
passed** (it sat swamped; it is a shore-fault suspect). Sanitize before drinking: ~1/2 cup
bleach in the full 27 gal, run every tap, sit 4 h, drain, refill, flush twice.
Head: manual hand-pump marine head, intake seacock under/behind it (closed on trailer), waste to
holding tank; trailer test = pitcher of water in bowl, pump to tank, pump dry. Expect a rebuild
kit (joker valve) after 2 years dry. Check holding-tank vent (dirt daubers) + pump-out deck
fitting; any overboard Y-valve stays locked — Lake Ouachita is no-discharge.
**FIELD FINDINGS 2026-09-02 (verified on the boat):** the only water fitting on deck is a
square chrome **CITY WATER INLET** (label on the ring) with a white cap + screen, starboard aft
next to GAS and WASTE key caps. NO fresh-water deck fill exists — boat was re-plumbed in PEX
at some point and the factory port-aft deck fill is gone. Tank monitor reads 3/4 but the pump
strainer bowl is DRY — gauge (float/reed) not trusted; extractor test on the tank line at the
strainer decides it (water = tank has water; air = gauge lying or pickup blocked). **Pump does
not move** when switched on (lights dip = inrush, no rotation) → meter 12 V at the red pair,
jumper the motor past the pressure switch; assume seized after 2 yr wet → replace with
Shurflo 4008/4028 (same footprint, 1/2" fittings). Future tank filling: with the city hose on,
watch the gauge/vent — if the level climbs, the inlet is teed to the tank side; if not, add a
deck fill. **BILGE: mid pump had water in it today and ran ONLY on the switch — float did not
fire.** Cockpit switches are 2-position rockers (manual only). Before launch: every float gets
its own fused feed direct from the battery post (or new Rule-A-Matic floats). This is very
likely how she sank.
**2760 AC/DC PANEL (manual 4-22, verified):** DC rockers ARE the breakers — MAIN 50 A, INST
PANEL 50, FWD CABIN LTS 15, MID CABIN LTS 10, STEREO 7.5, TV 10, REFRIG 15, **WATER PRESSURE
15**, MACERATOR 25, HEAD 25; three round panel fuses: SHOWER PUMP, CO DETECTOR, TANK MONITOR.
AC side: SHORE 30 A main + GENERATOR 40 A main, WATER HEATER 15, CONVERTER (charger) 10,
STOVE 20, OUTLETS 15, MICROWAVE 15, AIR CONDITIONER 10; polarity indicator on the panel.
Genset control on the panel: OFF/ON, START, STOP, BLOWER. No separate fuse for the water
pump at the panel (Shurflo asks for a 10 A inline — check the red wire near the pump). Lights
dipping when the switch is flipped = circuit complete, motor drawing inrush → the fuse is not
the problem, the motor is.
**HEAD CORRECTION 2026-09-02 (verified on the boat): the toilet is the MANUAL head** — wet/dry
bowl selector lever + hand pump, no vacuum generator anywhere. VacuFlush theory retracted.
Flush water comes from the TOILET RAW WATER SEACOCK (drawing 4-13, stbd aft engine area) —
no water on the trailer is normal. Trailer test: pitcher of water in bowl, lever wet, pump →
must go down to the holding tank; lever dry, pump bowl empty; stiff or creeping back = rebuild
kit (joker valve). Find + exercise that seacock before launch. Panel HEAD breaker (25 A) is
the electric-head option circuit — likely feeds nothing on this boat.
**BILGE = THE LOSS MECHANISM.** Mid bilge under the stairs fills with rain (path unknown — hose
test windshield frame, foredeck hatch, cabin door, cockpit sole one at a time with a watcher).
Regal cruisers of this era drain cockpit rain to the bilge; the bilge pumps ARE the drain, so
a float that does not fire = no drain → battery exhaustion → settled. Mid float did NOT fire
today with water in the bilge. PLAN (<$150): replace BOTH floats (Rule-A-Matic Plus / Johnson
Ultima), each on its own fused feed direct from the battery post, plus a high-water alarm
float + buzzer above them. Do not "clean" 25-year-old floats.
**RAIN PATH FOUND 2026-09-02: a factory drain port + tube runs from the companionway top
step / cockpit down into the mid bilge** — by design; the bilge pump is the drain. Before
plugging it: bucket test the cockpit. If the cockpit has its own transom scuppers, a plug in
the step drain is OK on the trailer only (pull it for use; standing water rots the sill). If
the cockpit drains ONLY through that port, never plug it (cockpit becomes a bathtub and
overflows into the cabin). Real fix = the float/alarm plan above + a cover when stored.
**FROM THE 2760 FACTORY MANUAL (ch. 6, verified, pdf pp.101–106):** system = fresh water tank,
deck fill + vent, monitor, pressure pump (35 psi), filter, **dockside water pressure regulator**,
water heater. "The dockside water inlet allows an outside water supply to be connected to the
inlet pressure valve by a hose... regulator allows only up to 35 psi... **This feature bypasses
the boat's fresh water tank, filter, and pump.**" NEVER leave the boat unattended on dockside
water. "**The fresh water tank deck fill is located on the port aft deck area.** Fresh water can
be added to the tank by using a hose." Overboard vent on deck burps when full; "some models use
a one piece fill/vent combo unit" (may not look like the FUEL/WASTE key caps). Layout drawing
6-6: WATER TANK forward under the cabin sole, FRESH WATER PUMP just aft of it (= under the
stairs, matches), WATER INLET + WATER VENT on the side deck amidships opposite the fuel fill,
WATER PRESSURE REGULATOR (dockside inlet) at the transom corner near the transom shower,
HOT WATER HEATER at the transom (**11 gal** per this manual, with engine heat-exchanger loop —
hot water while cruising; red reset button under the panel cover; drain valve at the rear),
HOLDING TANK aft with THRU-HULL VENT, MACERATOR under the mid-cabin floor, WASTE PUMP-OUT
fitting on deck. Sanitize: 0.13 oz bleach per gallon of system capacity (~3.5 oz for 27 gal),
4 h, drain, refill, flush. Water heater fill: tank full → pump on → open a hot tap until a
steady stream → only then the heater breaker on the AC side (and only after the ground test).
**UPDATE 2026-09-02 (field):** boat HAS a hose-thread DOCKSIDE inlet labeled WATER — on it, all
taps + water heater work. Panel switches: WATER PRESSURE / HEAD / MACERATOR → this is Regal's
**VacuFlush** setup, NOT a manual toilet. Water-pressure switch: lights dim (pump motor starts),
no pressure → **tank is empty** (dockside inlet does not fill it). Side deck has only FUEL and WASTE key caps + the
hose-thread WATER inlet. **The fresh-water deck fill is on the BOW** — Regal 2800 manual (sister
hull): "the deck fill marked 'water' located on the bow" / "the fill is located at the port front
bow" (inferred for the 2760). Dockside inlet has a check valve; it can never fill the tank. If
no bow fill is found, follow the 1.5" fill hose from the tank top (tank amidships under the
sole) to wherever it ends. Fill until it burps at the hull-side vent, open a tap to purge. VacuFlush (Regal
manual ch. 6): fresh-water switch ON (tank is the head's water source) → HEAD switch = vacuum
generator pump (runs ~2 min, then only after flushes) → lift foot pedal to add water → press
pedal to floor 3 s to flush (pop is normal). No water to the bowl even on dockside = shutoff
valve on the toilet supply line (under/behind toilet) or the pedal-operated water valve stuck
after 2 yr dry (work the pedal, else replace). MACERATOR = overboard discharge pump via its
own seacock, hold-to-run, seacock stays LOCKED CLOSED — pump-out station only on Ouachita.
**Fresh water pump FOUND under the companionway stairs: Shurflo 2088-423-244** (2.8 gpm,
45 psi, 7.5 A, 10 A fuse), clear inlet strainer on the tank suction (braided hose), blue tubing
on the pressure side, pressure switch under the pump. Drop-in modern replacement: Shurflo 4008
(~$80, same fittings). If it runs but won't deliver: strainer bowl/O-ring suction leak first,
then stuck check valves in the head (4 screws). Same compartment: green-corroded bronze
fitting low on the port side — if it is a seacock/through-hull, work it and confirm it seals
BEFORE LAUNCH; cream plastic unit with tan sanitation hose = likely the VacuFlush vacuum pump.
TO-DO: photo the pump, the toilet base/pedal, and the vacuum generator tank → confirm models.

## 2760 FACTORY DRAWINGS — machinery, seacocks, fuel (manual 4-13 / 5-4, verified)

**Under the companionway stairs (cluster on 4-13):** A/C WATER INTAKE seacock (= the green
corroded bronze fitting next to the Shurflo — work it, confirm it seals, or it is a sinking
risk), MID BILGE PUMP, WATER PUMP, SHOWER SUMP PUMP, SHOWER SUMP DISCHARGE thru-hull.
**Engine area:** A/C UNIT (port), BATTERY CHARGER (port), WATER HEATER (port aft), TRIM TAB
PUMP (center aft), BILGE PUMP (aft), **TOILET RAW WATER SEACOCK (stbd aft)** — a second
seacock to find and exercise; with the VacuFlush option it may be capped/unused but it is
still a hole in the hull. WASTE TANK + MACERATOR (stbd aft), **BLOWER = starboard aft corner
of the engine compartment** next to the waste pump-out fitting (answers the blower-location
question). FIRE EXTINGUISHER (Sea-Fire) on the engine-compartment forward bulkhead.
**Fuel (5-4):** 110-gal tank is **under the aft cabin berth** (not under the cockpit sole),
anti-siphon valve on the tank top, fuel tank vent, FUEL FILL/VENT COMBO at the starboard aft
deck, fuel sending unit on the tank, single "fuel to engine" line from the tank.
Seacock inventory before launch: A/C intake, toilet raw water, macerator discharge, plus the
engine intakes (through the drives) and the genset intake. Every one gets worked and checked.

## PROJECT: intelligent monitoring / security (Crystal Springs, spotty cell)

Uplink: **Starlink Mini** ($599, 12 V, 25–40 W, Roam plan from $50/mo, inland lakes covered,
works in motion <10 mph; big Flat HP dish + maritime plans are for offshore — not needed).
Marina Wi-Fi as free primary if the slip has it. Cellular boat monitors (Siren, Garmin OnDeck,
Boat Command) are out — no cell coverage. Controller: ESP32/ESPHome or a Pi (<1 W, 24/7),
Home Assistant on the dev box over Tailscale; controller owns a relay on the Starlink feed.
Sensors: high-water float above the bilge floats, current sense on each bilge pump (run
counts/duration), voltage on both banks, shore-power-present (AC relay coil), door + engine
hatch reeds, GPS geofence, engine-bay temp, cabin smoke/CO. Cameras: 1–2 PoE cams recording
locally, motion clips only. Alert rules: pump >N runs/hr, high-water, V <12.2, shore power
lost, hatch opened, boat moved >50 m. POWER BUDGET IS THE DESIGN: Starlink always-on ≈ 700
Wh/day vs ~400 Wh/day from 100 W solar → shore power at the slip = always-on mode (requires
the ground-fault fix + galvanic isolator FIRST); shore power lost → alert + duty-cycle mode
(dish on 10 min every 2 h + instantly on alarm; Mini boots ~2 min). Mechanical safety layer
(new floats, fused feeds, high-water alarm) comes first and does not depend on any of this.
**RESERVE BANK (decided direction 2026-09-02):** dedicated 12 V LiFePO4 in the mid-cabin
(30 Ah ≈ 380 Wh = ~10 h Starlink Mini continuous; 50–100 Ah if it also carries the bilge
pumps — 1,100 gph pump ≈ 3 A, a 100 Ah reserve runs it ~a day). Isolated from the house bank
by a one-way DC-DC charger (Victron Orion-Tr 12/12 class: charges only when house >~13 V,
boat loads can never drain it) + its own 100 W panel/MPPT. Controller lives on the reserve;
on house <12 V / shore lost / high-water: relay boots Starlink from the reserve, sends alert
(voltage, bilge state, GPS), waits for ack, shuts down, repeats on a phone-settable schedule.
Bilge floats moved to the reserve = pumps outlive the batteries the fridge/stereo eat.
Layering: house runs the boat; reserve runs pumps + brain + radio; solar keeps the reserve;
shore keeps everything when plugged in and healthy.

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
