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
**Power:** Twin Volvo Penta 4.3Gi — Gen-I 262 CID V6 (NOT the later Gen-III Vortec), serpentine belt, SX sterndrives.
Both engines rotate clockwise viewed from the front; counter-rotation happens in the drive (LH prop on port).

## Artifacts (claude.ai/code)

- Turning the 4.3Gi (field card): https://claude.ai/code/artifact/c1a71f75-9192-4086-ab0b-21939bdd6b4c
- Mi Amor Manual Library: https://claude.ai/code/artifact/af534e50-c8bd-4033-be32-6d217c2bd637
- Two Loose Screws — the $2,000 boat: https://claude.ai/code/artifact/884f3ced-ef6a-4903-962c-fb5b1d1e8fb3
- Field check: https://claude.ai/code/artifact/7c72b538-c759-4f77-a93e-0a05d5e1d97f
- Copart auction record: https://claude.ai/code/artifact/d4602e24-579e-481c-b065-d0f6ba0120af
- Bimini/camper tops session (2026-08-28): 4 canvas shops + strategy, ~$3–4k factory fit
- Kohler 5E genset: oil refill + fuel sender gasket diagnosis (session 2026-08-27)

## Progress log

- 2026-08 early: hand-turned engines (plugs out), read starter water lines, freed rotation
- 2026-08-26: "Turning the 4.3Gi" field card (crank balancer access, ring-gear pry method)
- 2026-08-29: **both new starters installed; LEFT (port) engine turns over on the key.**
  Manifolds + risers/tops + impeller reinstall in progress.
- 2026-08-29 oil check: **LEFT pan dry — no water. RIGHT pan has some water.**
  One-wet/one-dry contradicts submersion (both pans would be wet) → working theory:
  right engine took water through the exhaust path (bad riser gasket/rotted manifold
  passage → cylinder → rings → pan), and that may BE the original insurance "water loss."
  Verify: inspect right side's old riser gaskets/manifold water passages for the breach;
  check freeze plugs/block sides both engines while exposed. After oil change + first run:
  re-check dipstick — clean = legacy ingress (fixed); water returning = head gasket/crack,
  compression test next.

## Compression test — 2026-08-30 — PORT (left) engine, the clean-oil one

Cold, plugs out, cranking, Pittsburgh 62622 gauge. Owner's numbering: left-front = 1, down the bank.
**Left bank: 135 · 152 · 152 — Right bank: 152 · 137 · 145** (psi)
Verdict: PASS — no dead holes, no adjacent-pair pattern, spread ~11%.
Fresh-smelling fuel misted from plug holes during cranking (injectors firing — fuel pump
fuse was not pulled): possible fuel wash means the 135/137 may read low. Retest the
low holes after first heat cycles; expect them to climb toward 150.

## Exhaust reassembly — 4.3Gi torque specs

No specs came with the gasket sets. Community/service consensus for Volvo Penta 4.3 GL/Gi:

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
