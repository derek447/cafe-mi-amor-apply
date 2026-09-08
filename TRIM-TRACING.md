# Trim Circuit Tracing Guide

**2000 Regal 2760 Commodore — twin Volvo Penta 4.3Gi / SX-M — twin trim pumps**
Symptom: motors proven good on direct 12V; key on, helm switch pressed, **0V at every relay socket pin (coil AND contact side), both engines**, fuses look good, no corrosion. Both starters recently replaced.

**Bottom line up front:** one broken wire per engine explains everything, and it's almost certainly at the new starters' battery studs. Expected fix: reattach two ring terminals, $0 in parts. Do the eyeball check before anything else.

---

## 1. THE MAP — where trim 12V comes from and where it goes

### Power origin (the load-bearing fact)

**VERIFIED (multi-source):** On 1990s–2004 non-EVC Volvo Penta gas sterndrives, the trim pump's *entire* electrical supply — relay contacts AND helm-switch feed — originates at the **starter solenoid's main battery-positive stud**. A red ~10 AWG wire leaves that stud, passes through **either**:

- a **55A sealed fuse block** (white plastic, 2 studs, Volvo PN 3819905 → 853502/856355), often bolted right at the solenoid stud — "the whole block IS the fuse," cannot be verified visually, replaced whole
  — iboats moderator Don S: https://forums.iboats.com/threads/trim-stopped-working-volvo-penta.55423/
- **or** a **50A red push-button manual-reset breaker** (Volvo 3854164 = Sierra 18-69550 = Merc 88-11178A01), mounted on the engine — documented on the starboard exhaust riser or top of engine
  — https://www.boatered.com/threads/tilt-trim-on-volvo-penta-outdrive-is-mad-at-me.38292/
  — https://forums.iboats.com/threads/tilt-trim-system.743069/ (moderator: "It comes from the starter post to a fuse or breaker")

**INFERRED:** which of the two (or both in series) your specific 2000 4.3Gi units use. Both arrangements existed 1996–2003 and Regal may have done its own thing. **The boat is the primary source — follow the heavy red wire backward from each pump.** Twin engines = one complete independent feed per pump.

### Full circuit path

**VERIFIED (circuit topology, multi-source):**

```
Battery → starter B+ stud → 55A fuse block OR 50A breaker
  → heavy RED (~10 ga) → trim pump
      ├→ spliced to BOTH relays' supply terminals (contact side)
      └→ 10A blade fuse ON the pump (Volvo 967545)
           → red / red-purple wire → HELM trim switch
               → BLUE/WHITE (UP signal) & GREEN/WHITE (DOWN signal)
                   → relay coils → relays flip → motor
```

**VERIFIED — the ignition key is NOT in this circuit.** Trim should work with the key OFF on this era. "Power to the trim switch at all times" — https://www.marineengine.com/boat-forum/threads/5-7-volvo-penta-dp-trim-not-working.417597/ ; "10A fuse on the trim pump supplies power to the trim button on your control only" — https://forums.iboats.com/threads/volvo-penta-power-trim-unit-problem.545788/ . (Only later EVC/DPH needs key-on — not your boat.) Your key-on test result is a red herring either way.

**KEY DIAGNOSTIC IMPLICATION (VERIFIED logic):** because the helm switch is fed from the pump's 10A fuse off the *same* main red feed, **one break upstream of the pump produces exactly your symptom** — 0V on every relay pin, coil and contact side, no clicks. Nothing about this symptom implicates relays, switches, or grounds yet. Both engines dead simultaneously right after both starters were swapped = the same wire missed twice.

### Wire colors (OMC/Volvo SX standard)

**VERIFIED** — https://maxrules.com/fixomcwiringcodes.php + multiple forum confirmations:

| Wire | Function |
|---|---|
| RED (heavy) | unfused battery feed, starter stud → fuse/breaker → pump |
| RED / RED-PURPLE (small) | pump 10A fuse → helm switch supply |
| LT BLUE/WHITE | UP signal, switch → relay coil |
| LT GREEN/WHITE | DOWN signal, switch → relay coil |
| BLUE / GREEN | motor UP / DOWN leads (early harness colors) |
| BLACK | ground |

Your observed **green/white + purple/white at the motor**: doesn't match the classic chart. Likely UV-faded lt-blue/white reading as purple/white, or a later/replacement motor (**INFERRED**). Irrelevant to this fault — motors are proven good, and swapped polarity just reverses up/down.

---

## 2. THE STARTER-STUD HYPOTHESIS — confirmed?

**CONFIRMED as the standard topology, with direct precedent for your exact failure.**

- **VERIFIED:** trim feed lives on the starter solenoid main stud on these installs (sources above, thread 55423 + 743069).
- **VERIFIED:** correct dress on the solenoid's big stud is **battery cable + orange wire (alternator) + one or two red wires** — one red feeds the engine fuse block/breaker, the other red (often with the flat 55A fuse block attached) feeds the trim. A new starter showing only battery cable + orange = feeds not transferred. — https://www.justanswer.com/boat/3ymtp-installed-starter-2006-volvo-penta-4-3-engine.html
- **VERIFIED precedent — trim death immediately after starter work, twice documented:**
  - 2000 Glastron 3.0: trim died right after starter replacement; fix = dead 50A breaker in the feed (confirmed by jumpering it). https://forums.iboats.com/threads/volvo-penta-power-trim-unit-problem.545788/
  - 2000 Bayliner: trim dead after starter + battery cable job; diagnosis = red/orange fused wires at the starter stud not properly reconnected. https://www.marineengine.com/boat-forum/threads/power-trim-not-working.380615/
- **VERIFIED — breakers lie statically:** 1998 5.7Gi, 50A riser breaker with hairline crack read **13V unloaded but collapsed to 0.43V with the button pressed**. Test under load, not static. https://www.boatered.com/threads/tilt-trim-on-volvo-penta-outdrive-is-mad-at-me.38292/
- **INFERRED (your boat specifically):** that Regal routed it factory-standard. Multi-source consensus, but nobody has photographed *your* engine bays — which is why the trace below starts at the pump and walks forward.

---

## 3. THE TRACE — ordered, most-likely first

⚠️ **Gasoline boat: disconnect batteries before putting a wrench near any starter stud.** One iboats poster blew his 55A trim fuse with an accidental wrench spark on that exact stud. Blower on, no sparks near the bilge.

Per engine. Steps 1–2 are eyeball-only, no meter, no parts, ~10 minutes.

1. **Eyeball the new starter's B+ stud.** Expected: battery cable + orange + red wire(s). Missing reds, a dangling ring terminal, or an unattached white 2-stud fuse block hanging near the starter = **found it.** (Most likely fault — the wire was never transferred.)
2. **Eyeball around/behind the starter and the old starters if you still have them.** A red wire zip-tied out of the way, or still bolted to an old starter in a box, is the same finding.
3. **Find the protection device.** Follow the heavy red from the pump forward to a white 2-stud fuse block or a red-button 50A breaker (check starboard riser / top of engine / pump bracket). **If breaker: press the red button** — it's manual-reset and could simply have tripped during the job.
4. **Meter the fuse/breaker — both sides, UNDER LOAD.** Batteries reconnected, meter on the output stud to ground, have someone press trim. 12V in / 0V out = dead device. 12–13V static that collapses when the button is pressed = the cracked-breaker failure mode. 0V on the *input* side = the feed upstream (back to step 1's stud). The 55A block cannot be judged visually — meter across it or replace it.
5. **Meter the heavy red at the pump relay sockets under load.** 12V arriving here says the feed is fine and contradicts everything above — then check the pump's 10A fuse with a meter (not eyes) and the red/red-purple switch-feed wire.
6. **Only if 1–5 all pass** (unlikely given your symptom): helm-switch supply and signal wires. Red at the switch should be hot at all times; blue/white shows ~13V pressing UP, green/white pressing DOWN. Known failure: switch-feed wire chafed inside the throttle handle — https://forums.iboats.com/threads/10-amp-fuse-on-volvo-penta-powertrim-motor.323520/
7. **Grounds last.** Your symptom (0V everywhere) is a supply fault, not a ground fault — a bad ground would still show voltage somewhere.

Closest documented symptom-twin (motor good direct, new relays, 0V, no corrosion; fixed via the main feed / red-button breaker): https://forums.iboats.com/threads/power-trim-motor-getting-no-power-not-operating-no-clicking.603697/

**Phone-confirm shelf stock before driving anywhere** — but expect the fix to be re-landing ring terminals, not parts.

---

## 4. RELAY REFERENCE (for later — relays are NOT your current suspect)

**VERIFIED part numbers:**

| Item | Volvo PN | Cross | Notes |
|---|---|---|---|
| Trim relay (x2 per pump) | **3858809** (↔ 3858081) | **Sierra 18-5700** (~$26) | Square Bosch/DIN 5-pin SPDT cube, 20/40A, resistor-suppressed coil, SX-M 1998–2005. https://www.go2marine.com/products/trim-relay-replaces-3858081-3858809 |
| ⚠️ Wrong relay | 872300/876040/1324492 | Sierra 18-6266, Arco R040 | Older **cylindrical** family — do not order for a square-relay pump. Verify by shape; relay in hand outranks the catalog. |
| 50A breaker | 3854164 | Sierra 18-69550, Merc 88-11178A01 | Red push-button, trip-free, marine rated |
| 55A fuse block | 3819905 (→853502/856355) | — | Sealed, replace whole |
| 10A pump fuse | 967545 | standard blade | On pump, feeds helm switch |
| Pre-wired relay/fuse harness | 3857345 | — | ~$200; or re-terminate with ~$1.50 VF4 sockets (Mouser/DigiKey). https://forums.iboats.com/threads/volvo-penta-trim-relay-issue.779594/ |

**Pinout (VERIFIED** — https://forums.iboats.com/threads/tilt-trim-relay-wiring-need-help.196867/ **):**

- **87** = +12V, jumpered to BOTH relays from the heavy red feed
- **87a** = ground on BOTH relays (normally closed)
- **30** = common → one motor wire per relay
- **85/86** = coil: one side to helm signal wire (UP on one relay, DOWN on the other), one to ground. OEM resistor-type coil is polarity-insensitive.

*(Note: one JustAnswer/iboats source describes it as 30 = feed / 87 = motor instead. The 87-feed/30-motor version above is the one whose mechanism checks out and has two independent sources — but if you ever rewire, buzz out the socket in hand.)*

**How reversing works (VERIFIED):** not cross-wired coils — at rest both motor wires are grounded through each relay's 30→87a NC contact (also dynamic braking). Press UP: that relay's 30 flips to +12V, return current flows back through the *other* relay's still-closed 30→87a to ground. So: one dead relay or lost 87a ground = one direction dead; lost 87 supply = both directions dead; **lost main feed = everything dead including coils — your symptom.**

**SAFETY (hard rule):** generic automotive relays (JD1914/Tyco 330-070 footprint) plug right in but are **not SAE J1171 ignition-protected** — in a gasoline engine bay that's a fire/insurance problem. Marine-rated only for anything living in the compartment. Diode-suppressed automotive relays are also coil-polarity-sensitive where OEM isn't.

**Factory drawings, if wanted:** trim/tilt schematic is at the **end of the SX drive workshop manual** (not the engine manual); era-correct 4.3Gi engine diagram (43GiPBYCCE, `43giBYr.pdf`) is attached in https://forums.iboats.com/threads/volvo-penta-4-3gi-cable-wiring-diagram.581821/ . The SX-A manual on ManualsLib is 2007+ — wrong generation for a 2000 SX-M.

---

# Trim Hunt — Round 2

**Headline:** The "missing" protection isn't missing — it's a **50A red-button breaker hidden under a black snap-on plastic cover** on each engine's circuit-breaker bracket (VERIFIED from Volvo's own parts catalog). The 55A white fuse block is MerCruiser rigging — it does not exist on your package. Stop looking for it. But two hidden per-engine breakers don't kill both pumps on the same day — the both-at-once pattern points at one shared Regal boat-side feed, and the best forum match found exactly that: a blown boat-rigged fuse **at the battery bank**.

---

## 1. WHERE THE DEVICE IS on this boat (ranked)

**1. On each engine, under the black cover on the circuit-breaker bracket — VERIFIED (Volvo EPC).**
Volvo P/N 3854164 breaker, factory-annotated "50A, trim pump," mounts on bracket 3856186 (MY2000 WTR engines) under snap-on cover 3856764 — the same bracket where the **gray 10-pin engine cable** lands and the starter slave relay sits. It's a *cluster* of round breakers under one cover (50A trim, 20A + 6A fuel pump, 12.5A ECA), not a lone device. This is why you've looked straight past it. Follow the 10-pin cable to its bracket on each engine.
- EPC "Engine Harness Bracket" (annotated 50A trim pump): https://www.volvopenta.com/shop/0/part-sections/54142992
- Your MY2000 bracket/cover section: https://www.volvopenta.com/shop/0/part-sections/54142968

**2. In/at the white box behind the mid-cabin berth (battery switches) — INFERRED, leading suspect for the shared kill.**
White box = battery switch enclosure, VERIFIED for this hull family (2860 owner: https://forums.ybw.com/threads/regal-2860-electrics.153443/). Regal of this era does NOT route engine/trim power through helm or cabin panels (VERIFIED, same-gen 3760 manual p.84: https://www.manualslib.com/manual/849255/Regal-3760.html?page=84) and uses scattered inline fuses, not a central panel (http://www.regalownersforum.com/forum/viewtopic.php?f=5&t=2245). If both pump feeds share a stud, switch output, or paired inline holders here, that's your single point.

**3. Right at the battery positives — INFERRED, backed by the best case match.**
Twin-VP boat, both trims dead at once, all per-engine fuses/breakers good, culprit was a blown **40A boat-rigged fuse by the battery bank**: https://www.justanswer.com/boat/6lu3x-twin-2004-5-0-volvo-penta-gxi-sx-drives-trim-stopped.html — look for a stacked small-gauge red lead with an inline holder on a battery post.

**Not** at the helm breaker panel (verified excluded), **not** a white block on the starter (that's the MerCruiser/older-VP setup — negative finding, verified from the full Volvo catalog for your engines).

## 2. SINGLE-POINT CANDIDATES that kill both pumps (ranked)

1. **Shared Regal feed at battery/switch end** (white box stud, switch output, or paired inline fuse holders). Test: meter it where the pump red wires terminate.
2. **Battery switch position/failure** — a failed common post or loose output lug drops trim while starters crank from their own lugs. Test: 60 seconds — cycle/wiggle each switch, retest trim.
3. **Both 50A breakers tripped** (possible if one shared helm-harness chafe short trips both — precedent: 1997 Regal 2200 wires pinched in throttle control: https://forums.iboats.com/threads/volvo-power-trim-suddenly-stops-working.667775/). Test: pop each cover, press red button, meter both studs. If both were tripped, hunt the chafe in the trim switch pod before calling it fixed.
4. **Shared ground** — LOW priority: no forum case produced zero-volts-everywhere from ground; ground faults click relays instead.

## 3. NEXT THREE MEASUREMENTS (in order, solo, meter, no key)

1. **Pop the breaker-bracket cover on one engine** (follow the gray 10-pin cable to its bracket). Press the red button on the 50A breaker, then meter both studs to ground. Feed stud hot = starter-to-breaker is live; load stud dead with button pressed = bad breaker (~$15-25 aftermarket, Sierra 18-69550, before any $192 genuine buy). **Both studs dead = feed is upstream → go to step 2.**
2. **Hand-trace the fat red wire aft from each trim pump to its termination.** No tools. Where it lands IS the feed point, and the fuse/holder lives within inches of that termination. If both reds converge — that junction is almost certainly your fault.
3. **Open the white box + check battery posts.** Meter the backs of the switches (in vs. out studs, each position), every inline holder, and each battery positive for a stacked red lead. Cycle the switches and retest trim before condemning anything.

**Buy nothing until one of these three condemns a specific part.** If it comes to parts: 50A breaker 3854164 (cross 88-11178A01 / Sierra 18-69550), 10A control fuse 967545 ($6.80), relays 3858809 ($46.60 ea) — all in stock genuine.