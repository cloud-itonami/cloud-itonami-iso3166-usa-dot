# Business Model: Independent DOT Transportation-Procurement Compliance Service — United States

## Classification

- Repository: `cloud-itonami-iso3166-usa-dot`
- ISO 3166 (agency-level): `USA-DOT`, parent `USA`
- Ooyake cross-reference: `gov.usa.dot` (Department of Transportation)
- Activity: DOT/FAA/FTA procurement registration and Buy America transportation rules

## Customer

- an operator already using `cloud-itonami-iso3166-usa` whose contract
  touches Department of Transportation rules or buying channels
- a foreign SME entering a Department of Transportation-specific public program for the first time

## Offer

- walkthrough and evidence checklist for: DOT/FAA/FTA procurement registration and Buy America transportation rules
- ongoing regulatory-change monitoring for this body's public sources
- compliance-audit export package

## Trust Controls

- `:filing/submit` never auto-commits at any phase
- fabricated regulatory claims are HARD holds
- not legal advice — cite https://www.transportation.gov/

## Boundary

- **`cloud-itonami-iso3166-usa`**: country coordinator (general U.S. market entry)
- **`com-etzhayyim-ooyake`**: read-only civic atlas (never acts as the body)
