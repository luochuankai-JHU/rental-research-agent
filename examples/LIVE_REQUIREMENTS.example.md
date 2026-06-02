# LIVE_REQUIREMENTS.example.md

> Example only. This file represents an anonymized rental-search requirement set used to drive the agent workflow.

## Search Goal

Find a whole-unit apartment / condo near Richmond-Brighouse Station

The user prefers a quiet, newer building with convenient transit access. The agent should prioritize listings that are clearly within budget, map-verified for walking distance, and low-risk based on external research.

---

## Hard Constraints

These conditions must be satisfied unless explicitly marked as `needs confirmation`.

| Dimension | Requirement |
|---|---|
| Location | Near Richmond-Brighouse Station |
| Budget | ≤ 3,000 CAD / month |
| Bedroom count | 2 bedrooms |
| Move-in date | Available around 2026-06-01 |
| Unit type | Whole-unit condo / apartment only |
| Walking distance | ≤ 15 minutes walking to Richmond-Brighouse Station |
| Building age | Built after 2000 |

---

## Veto Conditions

Reject listings that clearly match any of the following:

- Detached house
- Basement suite
- Laneway house
- House unit / partial house rental
- Unit sharing the same property with the landlord, even if it has a separate entrance
- Not a whole-unit rental
- Aircraft-noise exposure

---

## Preferences

These are preferred but should not be used as immediate rejection reasons.

| Preference | Notes |
|---|---|
| Rent ≤ 2,800 CAD / month | Strong positive signal |
| Furnished | Preferred, but furniture may be negotiable |
| Air conditioning | Preferred |
| Parking | Preferred |
| Quiet surroundings | Evaluate using local noise signals and external evidence |
| Good building condition | Prefer buildings with fewer negative maintenance or management complaints |
| Amenities | Positive signal, such as gym, pool, garden, lounge, or other useful facilities |

---

## Research / Verification Required

The agent should not rely only on the listing text for the following fields:

| Field | Verification approach |
|---|---|
| Walking distance | Verify with map-based walking time to Richmond-Brighouse Station |
| Building age | Search external sources for building year / project identity |
| Aircraft noise | Check whether the location is likely affected by Richmond / YVR flight-path noise |
| Traffic noise | Check proximity to major roads and whether the unit appears to face them |
| SkyTrain noise | Check proximity to tracks and station infrastructure |
| Building reputation | Search for recurring complaints about maintenance, noise, water-damage issues, or management problems |
| Unit type | Confirm whether it is truly a whole-unit condo / apartment, not a basement, laneway, or partial house rental |