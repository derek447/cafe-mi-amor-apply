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
sulfated) — **2026-09-03 field data: switch on "1" all day → lights went dim; flipping to BOTH
brightened them.** Confirms banks are separate, switch works, battery 2 currently healthier.
Battery 1 (house — carries the bilge pumps) sagged after one light day: full overnight charge,
rest 1 h disconnected, then meter — ≥12.6 V healthy, low-12s after a real charge = replace.
Do NOT park on BOTH (a low bank drags the good one down; BOTH is for running/emergencies); decide shore-power vs proper solar (50–100W + MPPT) for where she'll live; backup
pump gets own thru-hull/hose/float/fuse — NO shared discharge, NO check valve.
## Standing context (for future sessions — read this, don't guess)

- **Aria** = Derek's AI companion, running as `aria-service` on Railway in
  `derek447/sclass-platform` (attach that repo via add_repo when Aria/dev context is needed).
  Agentic loop, self-directed wakeups, voice server, and real SMS conversations with Derek.
- **Aria's tablet** = phone-bridge device `TB336ZA` (Lenovo tablet; replaced a Pixel).
  Runs the bridge Android app (`tipper-bridge/`), outbound WebSocket to Railway, self-heals,
  OTA via Redis. Aria drives it fully: screenshot/tap/swipe/type/launch/SMS/battery.
- **Aria's texting** = outbound SMS through that tablet (`send_sms` bridge action), Telnyx
  fallback only, NO Twilio. Redis retry queue drains on bridge reconnect; dedupe + quiet hours.
- **BOAT INTEGRATION PLAN:** boat monitoring should NOT build its own alerting — ESP32/HA
  events POST to aria-service's alert-router and ARIA TEXTS DEREK. The bridge app's
  outbound-WS pattern is also the right shape for Starlink CGNAT (no inbound ports); the
  cockpit rugged tablet can run the same bridge APK as a SECOND bridge device long-term.
  Borrowing the TB336ZA for boat prototyping = Aria's SMS body goes offline (queue+Telnyx
  cover it) — OK for a weekend, not permanent.

**CHARGING CRISIS 2026-09-03:** batteries read 9.0 V and 10.3 V after a night "on charge";
Xantrex Truecharge2 20A shows Charging + <5% output, no Fault, but its own output lead meters
**6 V** — charger not delivering. Timeline: worked yesterday → bilge rinsed with soapy water
today → 6 V now. Prime suspect: water in the charger/connections (it lives low, also went
under in the sinking). RECOVERY: (1) shore power UNPLUGGED, charger drying 1–2 days —
**RULE: never wash the bilge with shore power connected, especially with the ground fault
open**; (2) garage charger on each battery individually overnight (9 V is actively killing
them); (3) test dried Xantrex in isolation, leads off: 13–14.4 V at studs = lives, 6 V = dead
→ ProMariner ProSport 20 / new Truecharge ($150–300); (4) battery verdicts by 1-h rest test
after a REAL charge: ≥12.6 = load test, low-12s = replace (the 9 V one is on death row).
NO CRANKING either engine until real voltage is back (low-V cranking cooks starters + MEFI).
**ROOT CAUSE FOUND 2026-09-03: 15 A push-button breakers at the battery switch (Xantrex
output circuits) were TRIPPED.** Charger charged into an open all night (<5% = no load; "6 V"
= floating disconnected output); fridge ran the banks down to 9/10.3 V. Rinse theory retracted;
charger likely fine. Note the design flaw: 20 A charger behind 15 A breakers → dead-flat banks
pull max bulk current → breaker pops. Recovery: reset, verify 13+ V at battery posts, expect
re-trips while banks are <12 V (lift the low bank with the garage charger/truck jumpers first),
feel the breakers — warm at 15 A = aging, replace with the trim breaker order. Fridge OFF
until both banks are back in the 12s (it dug this hole). Rest-test verdicts tomorrow.
**Breakers reset → CHARGING CONFIRMED (same day).** Watch for re-trips during bulk; output %
should fall as banks fill.
**Head unit (Kenwood) CONFIRMED DEAD 2026-09-03** — power verified at fuse/harness (yellow +
red hot, ground good), no life. Swamp casualty. Boat-side stereo wiring proven good = the
interface for the A/V build. Options: go straight to the amp-first build (per AV-BUILD-STUDY),
or ~$25 interim Bluetooth receiver/amp board on the existing speakers + STEREO circuit.
Salvage the Kenwood harness pigtail before tossing the unit.
**Direction chosen: no replacement head unit — the aft-bulkhead touchscreen becomes the head
unit.** Pi 5/CM4 on real Linux: HA kiosk = monitoring panel, Music Assistant/Mopidy + USB DAC
→ amps (amp-first per the study), camera recording + Tailscale on the same box, ESP32 feeds it.
Spend the money on a high-brightness/marine 10" touchscreen (sunlight). Android head units =
lockable junk; Victron Cerbo GX noted as the off-the-shelf Linux monitoring alternative.
**TWO-PANEL PLAN (2026-09-03): cabin station = hub/server** at the old TV/stereo spot where ALL
speaker harnesses + the stereo circuit terminate — Pi server + amp stack live there; screen =
any TV/monitor (indoor, doubles as TV via Starlink). **Cockpit station = thin client**: small
Pi/tablet + the high-brightness touchscreen, HA dashboard + music control over Wi-Fi (no long
HDMI). Zones: cockpit and cabin speakers on separate amp channels → per-zone volume in Music
Assistant. While the TV station is open: confirm amp-stack space/airflow + drop a pull string
to the cockpit for future power + sub feed runs.
**Hardware pricing verified 2026-09-03:** Pi 5 8GB now $175 board-only (2026 memory crunch —
Raspberry Pi announced memory-driven price rises) → server pick changed to **N100 mini PC
16GB/500GB (Beelink S12 Pro/EQ13, $129 used–$190 new, 12 V barrel input — feed via regulated
12-12 buck)**; HAOS native on x86, Frigate runs better. Cabin wall screen: batteryless only
(mounted tablets cook their lithium at 100% in cabin heat — the $387 MESWAO 16" was declined).
**Cockpit screen tiers (prices read off pages 2026-09-03):** Xenarc marine IP67 1200-nit
10.1" — 1022TSH $659 / 1029CNH $819 / 1029GNH $899, 9–36 V DC, USB touch, VESA (the proper
one); rugged Android tablet on RAM mount — Ulefone Armor Pad 3 Pro/4 Ultra ~$250–350, IP68
but ~500–600 nit (shade-readable, removable = theft/heat/roaming controller solved);
VSDISPLAY 10.1" 1000-nit ~<$200 (bright but only splash-resistant — protected cutout only).
DECISION LEAN: rugged tablet first season, Xenarc as the upgrade path.
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
  **Bimini measurement 2026-09-04: 90" between mounting points** — boundary of the 85–90
  bracket; buy an adjustable-range (88–96 style) 4-bow frame, ~8 ft coverage, ≥54" height
  (Derek 6'2" — check standing headroom at helm). Still need: height + length/strap landing
  measurements, and mount style (deck-hinge vs rail clamp). Aftermarket 4-bow ≈ $250–450.
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
- **✅ PORT WATER FLOW CONFIRMED — 2026-09-05, on muffs.** Water exiting the back of the
  outdrive at the **bottom of the lower (exhaust) bellows** area, ONLY while the engine runs.
  Diagnosis: benign exhaust/cooling discharge — on muffs at idle there isn't enough exhaust
  pressure to push all the spent cooling water out the prop hub, so it dribbles out around
  the exhaust boot / relief slots. The static-vs-running test rules out the dangerous case:
  a torn **U-joint bellows (the TOP boot)** leaks whenever water is present, engine or not;
  this only weeps while running. Worst case here = tired exhaust bellows seeping at a clamp —
  a little transom burble in the water, NOT a sinker; replace whenever the drive comes off,
  not a launch blocker. **Both engines now proven pumping** — engine-side water gates closed.
  - **Port exhaust bellows has visible cracks in the bottom** (2026-09-05, inspected). SAFE:
    the exhaust bellows is entirely OUTSIDE the hull — it connects the Y-pipe outlet on the
    transom shield to the drive, underwater; a crack connects lake water to the exhaust
    stream only. No path to the bilge (the watertight boundary is the transom shield +
    U-joint bellows). Water can't reach the engine either — the Y-pipe rises above the
    waterline inside the boat (standard anti-reversion geometry). While running, exhaust
    side is positive pressure → flow pushes OUT through cracks, nothing drawn in. Symptom
    of a torn one = louder/burblier idle at the transom (Alpha owners cut them off on
    purpose). Replace when the drive comes off for gimbal/U-joint service — not before.
  - STILL REQUIRED before launch: trim both drives full up, flashlight every bellows with
    the pleats stretched open (**top U-joint boot on both sides especially** — that's the
    hull-integrity one; cracks hide in the pleat valleys). ~2 min per drive. Port's bottom
    boot is now inspected and cleared.
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
**Found behind the toilet 2026-09-04: a fused 12 V power drop (corroded inline fuse barrel,
connected to nothing)** — almost certainly the electric-head feed for the panel's HEAD 25 A
breaker. Neighboring hose is Shields Series 148 vacuum-rated sanitation hose → boat was
plumbed/wired for a powered (VacuFlush-style) head, later swapped to the manual toilet
(inferred; fits the HEAD+MACERATOR switches). CONFIRMED live on the HEAD breaker 2026-09-04 (big red + black pair,
heavy gauge = sized for a 10–25 A electric head/vacuum pump). Capped-and-labeled "HEAD PWR",
breaker off — ready-made 25 A fused feed for a future head fan / tank sensor / electric head.
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
Shurflo 4008/4028 (same footprint, 1/2" fittings). **2026-09-03 extractor test: PULLED WATER
from the suction hose at the pump** → tank has water (gauge honest), pickup + line clear;
fault is the pump or its power. NOTE: the "pump won't move" test happened during the 9–10 V
battery crisis — RETEST at full voltage (prime the strainer bowl first) before buying. Future tank filling: with the city hose on,
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

## Depth/sonar gear inventory + cable hunt — 2026-09-05

Three sonar-era layers aboard:
- **In-dash Humminbird depth gauge** (factory ~2000, fed by 20A helm fuse) — dead until its
  transducer story is sorted.
- **Garmin GSD 22** network sounder module (mid-2000s) — useless without a Garmin plotter.
  **SELL IT.** Cable pile found in cabin (2026-09-05) confirms its kit: threaded screw-collar
  Garmin connectors incl. a large multi-pin, cable printed **AIRMAR TRANSDUCER CABLE #C32 /
  C1225**, GARMIN-labeled leads. **UPDATE 2026-09-05: the Airmar C32 cable is CUT** — GSD 22
  transducer feed is scrap. Module still sells (list as "no transducer cable"). Check whether
  the in-hull puck's own tail is the cut piece: cut = puck is scrap too (no splicing
  transducer cable); intact connector = keep it in the sell lot. The loose **Airmar in-hull puck** in the mid bilge very
  likely belongs to this Garmin system (Garmin pucks are Airmar-made). Sell GSD 22 + cables
  + puck as a complete lot — worth more together; funds the Helix rigging.
- **Humminbird Helix 5** (2015+) found aboard, **no mount/cables located**. Cable-pile search
  2026-09-05: NO Humminbird-style ends found. Also found a set of **3 cut-off cables** +
  old sealant residue = previous owner de-rigged something and snipped.
- NEXT CHECK (cheap, before buying anything): **trace the transom wedge transducer's cable
  forward.** If it ends in a slim black threaded barrel that matches nothing in the Garmin
  pile → likely a Humminbird XNT that pairs with the Helix → buy only gimbal mount (~$20)
  + PC-10 power cable (~$25). If the wedge's tail is one of the 3 CUT cables → wedge is
  scrap → Helix also needs XNT 9 20 T (~$100). ID by connector: Garmin old-style = fat
  knurled screw collar; Humminbird Helix = slimmer barrel, fewer pins. Count pins if unsure.
- Airmar in-hull puck was loose (stuck-then-freed from hull) — whoever keeps it must re-bed
  in epoxy/silicone with zero bubbles or it reads nothing.
- Pitot speedo pickup on transom: clogged tip = dead speedo (poke wire, compressed air).

## Transom drain plug — 2026-09-05

- Garboard drain plug goes in from the **OUTSIDE** of the transom — that's where the threads
  face. One plug, one location; there is no inside plug.
- Washer-style plug: hand-tight + 1/4 turn with wrench. Bare NPT thread: 2 wraps teflon,
  snug (soft brass — don't gorilla).
- Dry-fit BEFORE ramp day (threads clean, plug bottoms out). Plug lives with the winch
  handle / boat keys. Ritual: plug in before the trailer touches water, said out loud.

## Navigation architecture decision — 2026-09-05 (build, don't buy an MFD)

A prebuilt MFD bundles 4 jobs; only sonar is hard to DIY. Our stack (mostly already planned/owned):
1. **Charts/GPS** = cockpit rugged tablet + Navionics or Aqua Map (~$25/yr, verify at buy).
   Better + more current Ouachita charts than most plotters; tablet has real GPS chip.
2. **Sonar** = Helix 5 (owned). Never DIY sonar — proprietary DSP. $45–145 to rig pending
   transom-wedge cable trace.
3. **Engine/systems** = ESP32 + Signal K/HA on the N100 (the monitoring project). MEFI-3 has
   no cheap NMEA2000 path — tap the existing analog SENDERS in parallel (high-impedance ADC
   on sender wires; doesn't disturb gauges). Add USB GPS puck (VK-162 class, ~$20) to N100
   so the hub has position/tracks/anchor watch natively.
4. **Glass** = the two planned panels.
DIY delta over existing plan ≈ $50–170 vs $2,000+ MFD + transducer + N2K network. BUILD.

**ANALOG GAUGES STAY — hard rule.** Oil pressure + water temp are engine-saving instruments
with zero boot time and no dependencies (same philosophy as bilge floats never through ESP32).
They're also free parallel sensors for the ESP32 layer. Dead units (depth gauge, pitot speedo)
get individually fixed/blanked, not torn out. Factory cluster also = resale value.
Layered stack: gauges (always works) → Helix (sonar) → tablet (charts) → N100+ESP32 (brains).

## Sonar-into-panels — verified options 2026-09-05 (replaces rigging the Helix 5)

Decision: don't rig the cable-less Helix — sell it ($50-80 parts value, INFERRED) + the GSD 22
lot to fund something that feeds the panels. Verified paths:
- **Tier 1: Vexilar SP300 SonarPhone T-Box, $121-174** (NVN Marine $121 / Sportsman's Guide /
  Amazon — page-verified 2026-09-05). Black box + transom transducer, own WiFi hotspot,
  streams live sonar to free Android app = cockpit tablet IS the fish finder. Dual-beam
  200 kHz, 240 ft. Caveat: basic 2D sonar, dated app — depth/structure, not imaging.
- **Tier 2: Lowrance Elite FS 7** — Lowrance app MIRRORS + remote-controls full sonar on a
  tablet (verified, lowrance.com/lowrance-app), AND has NMEA 2000 → depth/temp into
  Signal K/HA via cheap gateway. Tackle Warehouse verified: $749 no-ducer / $849 HDI /
  $949 AI 3-in-1, **15% Labor Day sitewide thru 9/9** (HDI ≈ $722). Used FS 7 $400-500
  (INFERRED — check listings). Its own screen = sunlight backup glass at helm.
- **TRAP (verified): Lowrance Eagle series does NOT network/mirror** — deliberately
  standalone. Do not buy Eagle for this plan.
- Used older Lowrance (Ti/Ti2 era): VERIFY current-Lowrance-app support before buying —
  they shipped on the retired GoFree/Link app. FS series is safe.
Recommendation: SP300 to prove the concept cheap this season, or Elite FS 7 HDI in the
Labor Day window if fishing seriously — one box does imagery-to-tablet + depth-to-SignalK.

## FINAL sonar/GPS decision — 2026-09-05 (priorities: depth + GPS charts + custom stack)

Elite FS 7 OFF the list (imaging not a priority). The ~$150 answer:
- **Vexilar SP300 T-Box ($121, page-verified)** integrates DIRECTLY into the Navionics
  Boating app: split-screen sonar + chart, live depth on chart, and SonarChart Live builds
  our own HD bathymetry of Ouachita as we drive (Panbo/PassageMaker/SportFishing confirm).
  Hookup: tablet joins T-Box WiFi → open Navionics → sonar appears. Charts downloaded
  offline (T-Box WiFi has no internet — fine on the lake).
- **⚠ VERIFY BEFORE ORDERING:** integration dates to 2014-16; Garmin owns Navionics since
  2017. Check the CURRENT Boating app still supports SonarPhone (install free app, look for
  Sonar/SonarPhone in settings). If dropped: SP300's own app still works; depth-on-chart
  plan B = Airmar DST810 smart transducer into Signal K ($399 verified, oceanrope/airmar.com;
  needs thru-hull hole + N2K gateway — "later, if ever" upgrade).
- SP300 data stays in tablet apps (no native Signal K/HA feed). Anchor watch via tablet;
  HA-grade depth logging = someday-DST810 problem.
- Sell Helix 5 + GSD 22 lot → sonar side of the build ≈ net-free.
- **Rejected 2026-09-05: BoatEye360 "External Monitor V2"** ($299, 10", IP68) — NOT a
  touchscreen ("touch screen buttons only"), no brightness spec published, no OS/GPS, vendor
  supports only their own cameras. Dumb HDMI display = wrong shape for the cockpit slot
  (would drag the N100 to the helm). Cockpit panel must BE a computer → rugged Android
  tablet stands as the pick.
- **Cockpit tablet shortlist (2026-09-05):** Oukitel RT6 (10.1" FHD+, 400 nits VERIFIED,
  20Ah battery, IP68/69K, GPS; sold out Geekbuying, Amazon listing live) vs Ulefone Armor
  Pad 3 Pro (10.36" 2K, huge battery; ~$265 import, Notebookcheck-verified). Budget 8":
  Armor Pad Pro. Premium: Armor Pad 4 Ultra (Android 15, Corning, ~$400-500 INFERRED).
  RULES: buy the 4G/LTE variant (that's where the real GPS chip is); brightness is the
  weak spot at 400-550 nits (bimini fine, direct sun meh — Xenarc 1200-nit is the someday
  fix); check Amazon reviews for "GPS"/"brightness" on the exact model year — these brands
  revise silently. Exact cart price: check phone (Amazon blocks remote pulls).
- **Prototype on Aria's Lenovo (2026-09-05):** stack is hardware-agnostic — build now, $0.
  Android tablet path: install free Navionics Boating app → CHECK settings for
  Sonar/SonarPhone support (= the SP300 pre-order gate); HA companion app; take it on the
  water in a dry bag as cockpit panel v0.5 (real-sun readability test tells us the nits
  we actually need). Laptop path: HAOS in VirtualBox/Docker = dev bench for dashboards,
  Music Assistant, ESPHome; migrate to N100 later via HA snapshot restore (~10 min).

## BOAT HELM = ARIA'S THIRD PLACE — architecture locked 2026-09-06

Companion (`aria-dev` / @starlight/companion) ALREADY has a full Home Assistant integration
(`src/companion/integrations/home-assistant.ts`: REST+WS, entity discovery, states, history,
service calls, realtime subscriptions). The helm is an integration, not a build:
1. **N100 cabin hub:** HAOS + ESPHome + Music Assistant (+Frigate later) + **Tailscale**
   (outbound-only — Starlink CGNAT solved, same pattern as the phone bridge).
2. **Companion → boat HA** via long-lived token: Aria reads every sensor, drives every
   switch, has getHistory() for trends.
3. **ESP32 sensors** (per monitoring section) surface as HA entities → companion
   auto-discovers. Bilge floats stay HARDWIRED; ESP32 watches only.
4. **Alerting:** HA automation → webhook → aria-service alert-router → Aria SMS via
   TB336ZA (existing retry queue + dedupe). TASK in sclass-platform: authed inbound
   boat-events route on the alert-router (~small addition). Reserve-bank phone-home
   stays as the independent last-resort layer.
5. **Rugged tablet at helm:** Navionics + SP300 + HA dashboard + **bridge APK as second
   phone-bridge device** (Aria can see/drive the helm remotely). CHECK: PhoneBridgeManager
   multi-device — connections carry a `device` string (anticipated?); confirm 2 concurrent
   or patch.
Build order: TB336ZA aboard this weekend (Navionics + SonarPhone check) → N100+HAOS+
Tailscale+companion token → ESP32 nodes → alert-router route → rugged tablet as bridge #2.
- **Widescreen rugged tablets (asked 2026-09-06): don't exist** — rugged market is all
  16:10/squarer. Closest: 11" landscape = Ulefone Armor Pad 5 Ultra (TechRadar best-overall,
  IP68/69K) or ORCATAB WT1 Pro (2026: 11" 2K 120Hz, 450 nits stated, Android 15, 20Ah, 5G).
  True ultrawide = automotive 32:9 strip displays (NOT IP-rated, no GPS) — viable later as
  N100-driven GAUGE strip under the helm brow only; verify brightness before buying.
  Xenarc 1022TSH ($659, IP67, 1200 nits, 16:10) remains the marine-monitor path.
- **Dell Latitude 7220 Rugged Extreme (eBay find 2026-09-06):** 11.6" FHD **1000-nit
  sunlight-viewable** (VERIFIED, Dell PR), IP65, MIL-STD-810G/H, glove touch, hot-swap
  batteries, i5-8365U/16GB/256GB. Seller's 7 units @ $259.99 are **Active Directory +
  Absolute locked = pass** (works until first reset; Absolute = remote-brick risk; that's
  unlocked pricing for locked goods). BUT unlocked 7220/7212s run $300-500 on eBay and are
  the 1000-nit helm option — caveat: x86 not Android → OpenCPN/Linux + Signal K instead of
  Navionics/SonarPhone apps; GPS was a config OPTION (verify per unit; $20 USB puck fixes).
  Locks explained: AD/Autopilot = cloud-side enrollment survives wipes; Absolute =
  BIOS-embedded agent, re-injects into Windows forever, inert under Linux.
- **UNLOCKED 7220 @ $299 (2026-09-06): BUY SIGNAL** — pending seller confirmation of:
  (1) clean Windows install, personal-account setup, NO org enrollment screen (if same
  seller as the locked lot, confirm THIS unit differs in writing); (2) Absolute =
  Disabled/Not Activated in BIOS (make them check the BIOS page); (3) GPS/WWAN module
  populated (Device Manager screenshot; absent = $20 USB puck); (4) battery count +
  health (dual hot-swap slots, spares $50-80); (5) charger included (12V vehicle
  adapters exist for boat power).
  **Helm plan v2 (x86 variant):** Dell = main helm glass, Linux/Win11 + OpenCPN charts +
  Signal K/HA dashboard @ 1000 nits. Aria presence via companion DESKTOP module
  (aria-dev/src/companion/desktop) + Tailscale (bridge APK is Android-only). Android-only
  apps (Navionics/SonarPhone) run on a second small screen: TB336ZA or cheap Android
  beside the Dell = two-screen helm, one brain.
- **Getac F110 flood on eBay (2026-09-06) — triage rule = GENERATION:** G1/G2 skip;
  G3/G4 (6th/7th-gen i5) = Linux-only helm, only if sub-$150; **G5 (i5-8265U, 8th-gen) =
  sweet spot**, Win11-eligible, same class as Dell 7220; G6/11th-12th gen = 1000-nit,
  pricier. All gens have LumiBond sunlight screens (~800-1000 nits). Listing survives only
  if: no AD enrollment + Absolute disabled + **BIOS not password-locked (common on fleet
  Getacs)** in writing; GPS module confirmed; battery+charger; screen photographed ON
  (cop-unit burn-in). Getac bonus: many configs have real RS-232 = native NMEA 0183.
  Benchmark: the $299 unlocked Dell 7220; clean F110 G5 under ~$250 beats it.
- **VERDICT x86 vs Android helm (2026-09-06): ANDROID WINS for this boat.** Two decisive
  facts: (1) Lake Ouachita chart data lives in Navionics (Android/iOS only) — OpenCPN's
  free sources are coastal-focused and weak on inland Corps lakes; (2) SonarPhone is
  Android-only, so x86 needs an Android sidekick anyway = two devices. Plus: built-in GPS,
  5-10W vs 15-25W draw, battery=UPS, bridge APK proven. x86's one real win = 1000-nit
  direct sun; fixes first: mount in bimini shade line; a 1000-nit Dell/Getac is the V2
  SECOND screen (custom dashboard), never the primary. Buy list unchanged: rugged Android
  tablet + SP300 + Navionics (~$400 all-in).

## Launch deferred past 2026-09-06 weekend — insurance is gate #1

- **Try binding NOW anyway (15 min, free):** Progressive and GEICO/BoatUS both quote AND
  purchase fully online (VERIFIED) — no agent hours; weekend bind is likely possible
  (INFERRED — the quote flow answers definitively). Liability-only for the $2k boat.
  **Answer salvage/prior-damage questions HONESTLY** — a policy bound on wrong answers
  evaporates at claim time; liability-only usually needs no survey. If Progressive
  declines on salvage history → GEICO/BoatUS → Monday: independent agent (Markel,
  Foremost, National General). AR requires liability >50 HP; we have 410.
- **Silver lining of the slip:** order tonight so parts beat the new launch date —
  IAC (Sierra 18-7704 or Recmar REC3855194), starboard impeller kit, bilge floats
  (Rule-A-Matic Plus / Johnson Ultima ×2) + high-water alarm. Launch #1 happens with
  real parts: proper floats wired, real winch found, pump wet-tested + system sanitized
  unhurried, trim-up bellows inspection done in daylight, no stopgaps.

## Custom dash research — 2026-09-06 (2760 split-pod helm)

No documented full glass-dash 2760 build exists online — but the dash was DESIGNED for this:
- **VERIFIED (Regal factory + owners forum):** this era's helm = flat dash panels on
  aluminum backing plates in the fiberglass pods; panels unscrew individually. Commodore
  owner precedent: traced panels → local plastics shop → all 3 in black StarBoard/acrylic,
  cut/drilled/finished, ~$250.
- **Design that fits the split pods:** gauge pod stays analog (layer 0; blank/repurpose the
  dead Humminbird hole); largest panel gets flush tablet cutout — MEASURE POD DEPTH FIRST
  (~1"+ needed; too shallow = RAM mount on dash top, panel gets switches instead); switch
  panel = custom backlit rockers for monitoring/AV controls.
- **Vendors:** New Wire Marine (custom backlit dash/switch panels, E-Panel Builder,
  reproduces originals) and Boat Outfitters (acrylic/StarBoard, print-and-test-fit step).
  Process: unscrew factory panel → ship/trace as template → CNC panel back → transfer
  hardware. Keep originals boxed for resale.
- iboats trick: reverse-printed Lexan film laminated on black acrylic = full custom
  legends/graphics.
- **Whole-dash recuts ARE done** (THT: "chop console front, glass in new flat section";
  pro shops cut old recess + glass new face during electronics packages) — but nearly all
  on flat center consoles. 2760's wraparound multi-pod dash = compound curves; full recut
  = real glasswork (cut/fill valleys/fair/gelcoat), winter project, permanent, resale
  stakes. Verdict: earns its cost ONLY if dash core turns up soft/rotten someday.
- **DEREK HAS A CNC CUTTER → middle tier:** CNC new pod faces in 1/4" cast acrylic matte
  black or Dibond (acrylic: single-flute upcut, high feed, no melting; StarBoard machines
  easy but flexes/no gloss). Machine a flush REBATE pocket so tablet sits recessed with a
  lip; switch cutouts + engraved backlit legends; CNC mounting frames/cradle behind the
  face onto the factory aluminum backing plates. Pods close together → CNC stepped bridge
  piece spanning them = wide visual surface, zero fiberglass cut, reversible.
- **Grey dash over cream boat = normal/deliberate** (anti-glare: dark dash tops don't
  reflect into the windshield at sightline; industry standard, Regal two-toned Commodores).
  30-sec test: polish a hidden spot — cuts to glossy cream = just oxidation (whole dash
  would polish back); stays grey under gloss = factory. Also check for overspray/tape
  lines = PO repaint. Factory grey is good for the CNC panel plan — matte black on grey
  reads factory glass-cockpit.
- **Dash grey CONFIRMED factory** (2026-09-06): ends exactly at dash part boundaries =
  molded-in grey gelcoat, anti-glare package. Keep.
- **Tinted panel folded down on dash = windshield center WALK-THROUGH closure**, not a
  dash cover: lift + latch across the gap to complete the windshield for running (down =
  bow access). CHECK: side latch hardware grabs (loose panel underway = flying acrylic),
  hinge screws snug, gasket/trim intact. Hazy = Novus plastic polish; reseal near it
  plastic-safe silicone ONLY (PU crazes acrylic). Run latched up at speed.
- **Tinted panel IDENTIFIED (2026-09-06, ref photos): factory smoked-acrylic ELECTRONICS
  COVER** for the recessed mid-dash bay (flat shelf between top gauge pod and lower gauge
  row) — Regal's helm electronics bay, where factory chartplotter/depth package mounted;
  cover hinges/lifts off, protects from sun/spray/theft-eyes when parked. Boats without
  the package = tinted lid over empty shelf. **THAT RECESS = THE TABLET BAY, pre-built:**
  CNC a bezel panel dropping the Android tablet into the factory bay, wire pass-through
  behind, original smoked lid still closes over it. Zero new holes; looks factory.
  MEASURE next visit: recess W×H×depth + hinge points intact.

## Learn fiberglass — on-ramp (2026-09-06)

Epoxy first (forgiving, no stink, sticks to old polyester), gelcoat/polyester later (cosmetic).
Kit ~$150: TotalBoat/West epoxy WITH PUMPS (bad ratio = #1 beginner failure), 6oz cloth +
1708 biax, colloidal silica + fairing filler, chip brushes/cups/squeegees, nitrile gloves
BY THE BOX (epoxy skin sensitization is permanent — gloves every time), organic-vapor
respirator for resin, P100 for sanding (bottom-paint rule stands).
Curriculum on this boat, in order: (1) re-bed Airmar puck (pure pour, learn mixing/bubbles);
(2) seal cut edges of dash panel cutouts (wet-out); (3) glass backing block for 2nd bilge
pump/high-water switch (first cloth layup, hidden); (4) topside gelcoat chip repairs;
(5) someday dash recut/transom work.
Resources: Boatworks Today (Andy Miller, YouTube) + West System "Fiberglass Boat Repair &
Maintenance" free PDF.
- **Angled internal pockets for screens (design locked-in 2026-09-06):** recessed angled
  pocket = factory glass-helm look. Engineering rules for the cut files: screen tilt only
  10-20° back from vertical (screen must "see" dark torso/dash at mirror angle, NOT sky —
  cardboard mockup from the helm seat before cutting); HEAT = killer spec (open pocket
  back into dash void + vent slots top/bottom of bezel; smoked lid = parked/shade only,
  lithium + oven = swollen battery); weep slot at pocket low corner; USB-C entry from
  below w/ drip loop; machined retention lip + thumb-latch/magnet quick-release (tablet
  goes home = anti-theft). Build: (a) CNC layered acrylic/HDPE wedge stack + bezel = do
  NOW for electronics-bay tablet; (b) CNC foam plug → glass over → fair → paint factory
  grey = the molded look, first real layup, LATER for second screen.
  NEED from boat: recess W×H×D + seated eye height above dash → pocket angle geometry.
- **Off-the-shelf angled tablet pockets: DON'T EXIST** (verified — market is clamp/rail
  mounts; THT confirms flush/recessed = custom audio-shop fab). Donor shortcuts: molded
  glove-box/storage pockets (Attwood/T-H Marine ~$20-40) as pocket shells + CNC bezel;
  MFD flush-mount wedges as geometry reference. Flat shelf physics: drop-in pocket must
  hold screen STEEP (60-75° from horizontal, lectern-slot style) or it faces the ceiling —
  deeper than any storage pocket → CNC wedge box under shelf cutout + bezel + smoked lid
  closes over. Cardboard mockup from helm seat doubly critical at steep angles (sky glare
  lives or dies by degrees).

## Trim tabs — troubleshooting queue (2026-09-06)

Dash rockers by throttle = TRIM TAB switches (bow up/down labeling; drive trim is on the
throttle handle). Likely Bennett hydraulic. Switches physically loose. HPU + wiring live
low in the stern = swamp-zone suspects. Order of attack:
1. Transom check: two stainless plates w/ rams at hull trailing edge = tabs exist
   (no plates = orphan switches like the HEAD PWR feed; done).
2. Fix looseness first (mounting nut / plate screws) + reseat spade terminals — loose
   spade = #1 "works sometimes" cause.
3. Listen test: key on, hold rocker, ear aft — pump hums = hydraulic problem;
   silence = electrical.
4. Meter switch: no 12V feed → find tab fuse/breaker (manual DC pages); feed OK but no
   output on press → dead rocker (~$15, Bennett sells exact).
5. Pump runs, no movement → HPU reservoir (Bennett = Dexron ATF), level, air, oily
   traces on lines, ram condition. Swamped 2 yrs = rusted pump motor plausible.
NOT a launch gate — drive trim covers it. Fix loose switch (10 min), hydraulics at
curiosity pace behind floats + insurance.
- **UPDATE: tab rockers feel like loose CAPS, no click** — Carling Contura-style two-piece
  (snap cap + switch body behind panel). Pull plate (2 screws) → either (a) bodies dangling
  w/ wires (snap back in / replace $10-15 ea if lock ears broke), (b) caps only, NO bodies/
  wires = system de-rigged, orphan like HEAD PWR feed, or (c) bodies dead inside. TRANSOM
  LOOK NOW FIRST: no tab plates + no wires = no tab system exists, case closed $0.
- **Trim tabs CONFIRMED on transom (2026-09-06)** → system real, loose caps = the fault
  line. Next: photo a ram (slim + fluid line = Bennett hydraulic w/ bilge pump box; fat +
  wire pair = Lenco electric); check ram shafts for pitting/frozen (2 wet years); pull
  switch plate → bodies w/ wires = snap in / ~$15 ea; nothing = trace de-wired harness.
  Then key-on listen test. Restore job, likely ~$30, curiosity pace.
- **Tab photo IDs system as BENNETT-STYLE HYDRAULIC** (slim rod + compact ram, not fat
  Lenco barrel; confirm: fluid line at ram top = hydraulic final). Tab fully drooped =
  normal dormant hydraulic (pressure bleeds off; electric would hold position — another
  Bennett point). Restore: switch bodies behind plate → find HPU in aft bilge (swamp-zone;
  check reservoir level + milky fluid = water) → key-on listen + watch tab; 2-yr Bennett
  often just needs fluid + purge cycles. ALSO: check tab hinge/ram-mount screws into
  transom — bedded holes at waterline, drooped tab tugging old bedding = classic slow-leak
  path; re-bed if weep stains. Watch drooped tabs on trailer bunks.
