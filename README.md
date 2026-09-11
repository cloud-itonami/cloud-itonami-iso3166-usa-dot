# cloud-itonami-iso3166-usa-dot

Open ISO 3166 **agency-level** Blueprint for **USA-DOT**: Department of Transportation
(parent country: **USA**).

This leaf designs a forkable OSS business for an independent operator
navigating **Department of Transportation**-specific public-procurement / regulatory compliance,
composing with the country coordinator `cloud-itonami-iso3166-usa`.

## The catalog

`src/statute/facts.cljk` holds **61 verified regulatory anchors** across
**6 CFR titles**, plus **3 checked negatives** — things a competent reader
expects to find and which are not there. **15 quoted spans** of live section
text are pinned byte-exactly, so the notes are falsifiable and not just the
citations.

Every anchor's heading was confirmed against the official eCFR versioner API,
and `tools/verify_citations.cljk` re-fetches all of it and fails if anything
drifted:

```bash
kbb --backend sci tools/verify_citations.cljk     # exit 0 verified / 1 drifted / 2 could-not-answer
kbb -M:test                     # offline shape invariants
```

The live gate refuses to report a pass it did not earn: a network failure, an
undeclared endpoint, a control pattern that stopped matching, or a catalog that
shrank below its floors all exit **2**, which is neither a pass nor a drift.

### What the entries are organised by

Each anchor declares a `:statute/hat` — which role DOT is playing. Conflating
these is the failure the catalog exists to prevent.

| hat | what it means |
|---|---|
| `:acquirer` | DOT buying for itself, under the FAR as supplemented by the TAR (48 CFR chapter 12) |
| `:grantor` | DOT awarding financial assistance, where the procurement being regulated belongs to the recipient |
| `:regulator` | DOT writing operating rules, including conditions attached to assisted projects |
| `:excluded` | inside DOT, outside the acquisition regulation that bears its name |
| `:not-dot` | in a transportation CFR title, owned by another department or by nobody |
| `:far-baseline` | 48 CFR chapter 1 — what governs before any supplement |
| `:grants-baseline` | 2 CFR subtitle A — OMB's government-wide grants rules |

## What the catalog found

**DOT is not one buyer under one rulebook.** The four findings below are each
recorded as data — a quoted span or a checked negative — rather than as prose,
so that a reorganisation of the CFR cannot leave a stale claim here looking
verified.

1. **The FAR, the TAR and the TAM do not apply to the FAA.** 48 CFR 1201.104(d)
   says so in those words, citing 49 U.S.C. 40110(d), and the FAA is named
   nowhere in title 48. It buys under its own Acquisition Management System,
   which is not CFR text at all. The Maritime Administration is separately
   permitted by 1201.104(c) to depart from both.

2. **`Buy America` and `Buy American` are different regimes, and the FAR
   contains only the second.** Scanning every node label in title 48 for
   `Buy America` as a whole word returns nothing; `Buy American` returns dozens.
   Buy American (48 CFR part 25) governs the United States buying for itself
   through a price preference a foreign offer can overcome. Buy America
   (49 CFR 661, 23 CFR 635.410) governs a *grantee* spending federal
   assistance — 49 CFR 661.1 says `federally assisted procurements` — and FTA's
   661.5 admits no price comparison at all.

3. **`Buy America` is not even one rule inside DOT.** FHWA allows a de minimis
   (0.1 percent or $2,500, whichever is greater) and a 25 percent alternate-bid
   path at 23 CFR 635.410(b); FTA's 49 CFR 661.5 allows neither. A third
   regime, the Build America, Buy America preference at 2 CFR part 184, sits on
   top of both and flows down to subawards.

4. **DOT never supplemented FAR part 25.** There is no part 1225 anywhere in
   48 CFR chapter 12 — the numbering runs 1224 straight to 1227. The
   department's entire domestic-preference apparatus lives on the grants side,
   where the buyer is someone else.

Two further hazards are carried by entries rather than negatives, because in
both cases the evidence is a heading that exists:

- **A CFR title is a subject, not an owner.** In title 49, chapters IV and XII
  are the Coast Guard and TSA — *Department of Homeland Security* — while VII is
  Amtrak, VIII the NTSB and X the Surface Transportation Board. Title 46 repeats
  the pattern. Their own labels say so.
- **Part numbers are not addresses here.** 49 CFR 661 is FTA's Buy America rule;
  23 CFR 661 is the Tribal Transportation Facility Bridge Program. 48 CFR 1201
  is the TAR's regulations-system part; 2 CFR 1201 is DOT's adoption of the
  uniform grant requirements. Both collisions are inside this one department.

### Where this contradicts the blueprint

Recorded rather than smoothed over, because a compliance catalog that quietly
agrees with its own marketing is worth nothing:

- `blueprint.edn` names this leaf a **Transportation-Procurement Compliance
  Service**. The catalog shows that most of what a DOT-funded client actually
  faces is *not* procurement law: it is grant law binding the recipient's own
  purchasing. The name is left unchanged pending an owner decision, because
  fleet consumers key on `:itonami.blueprint/name`.
- This README previously promised **"DOT/FAA/FTA procurement registration"**.
  Two of those three are wrong. There is no FAA procurement regime to register
  under in the CFR (finding 1), and *registration* is government-wide SAM
  (2 CFR part 25), not a DOT procedure. The FTA half stands.

## What this is NOT

- **Not Department of Transportation.** Commercial compliance navigation only.
- **Not legal advice.** Cite official sources; route licensed work to counsel.
- **Not a substitute for the country coordinator.** Government-wide U.S. federal
  law lives in `cloud-itonami-iso3166-usa`; this leaf carries the DOT-specific
  layer and the two baselines it departs from.

## Official surface

- https://www.transportation.gov/

## Capability layer

Resolves via `kotoba-lang/iso3166` (`USA-DOT`, parent `USA`).

## License

AGPL-3.0-or-later.
