# Sample Shortlist: Richmond-Brighouse Rental Search

> **Data privacy note:** This sample is based on a real rental search for a real user, driven by the anonymized requirement set in `LIVE_REQUIREMENTS.example.md`.
>
> In the actual workflow, the agent would deliver a full report similar to this one to the user. This public version intentionally removes or generalizes exact addresses, original listing URLs, landlord/contact information, active listing links, listing photos, and private user details. It also shows only a selected subset of candidates rather than the complete delivery.
>
> This file demonstrates the agent's output format, evidence discipline, and decision logic. It is **not** a public database of rental listings.

---

## 1. Search Context

The user wanted to find a whole-unit apartment / condo near Richmond-Brighouse Station. They preferred a quiet, newer building with convenient transit access. The agent was expected to prioritize listings that were clearly within budget, map-verified for walking distance, and low-risk based on external research.

---

## 2. Requirement Snapshot

### Hard Constraints

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

### Veto Conditions

Reject listings that clearly match any of the following:

- Detached house
- Basement suite
- Laneway house
- House unit / partial house rental
- Unit sharing the same property with the landlord, even if it has a separate entrance
- Not a whole-unit rental
- Aircraft-noise exposure

### Preferences

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

## 3. Run Summary

| Metric | Count |
|---|---:|
| Initial listings after listing-level deduplication | 170 |
| Candidates kept after pre-filtering | 123 |
| Accepted after detailed review and deduplication | 29 |
| Public sample candidates shown here | 10 |

This public sample shows only a selected anonymized subset of the final delivery. The full internal report contained more accepted and rejected listings.

---

## 4. Shortlist Overview

| Candidate | Tier | URL | Rent | Walk Time | Building Year | Key Positives | Main Risks / Confirmation Items |
|---|---|---|---:|---|---|---|---|
| A-001 | Strong match | Hidden | ~$2,950 | 1 min | 2022 | Very close to station, newer building, strong amenities | Lease length needs confirmation |
| A-002 | Strong match | Hidden | ~$2,700 | 9 min | 2015 | Newer concrete high-rise, A/C, parking | Possible road / transit noise needs review |
| A-003 | Strong value candidate | Hidden | ~$2,600 | 2 min | 2007 | Lower rent, A/C, furniture, very close to station | Possible central-location noise |
| B-001 | Qualified but needs confirmation | Hidden | ~$2,750 | 8 min | 2011 | Good location, newer building | Furniture and A/C unclear |
| B-002 | Qualified but needs confirmation | Hidden | ~$2,900 | 5 min | 2010 | Good location, move-in-ready signals | Building year needs second source; hidden costs unclear |
| B-003 | Qualified but needs confirmation | Hidden | ~$2,900 | 11 min | Unknown | Within distance threshold | Address too vague; building year unknown |
| B-004 | Qualified but needs building-reputation review | Hidden | ~$2,800 | 3 min | 2016 | Very close to station, newer building, good basic fit | External complaints mention maintenance, rental-unit concentration, and package theft |
| R-001 | Rejected | Hidden | ~$2,500 | 5 min | 1994 | Good price and distance | Fails building-age requirement |
| R-002 | Rejected | Hidden | ~$2,500 | 35 min | Not checked | Basic listing fields look compatible | Fails walking-distance requirement |
| R-003 | Rejected | Hidden | ~$2,200 | Not checked | Not checked | Lower rent | Fails bedroom-count requirement |
| R-004 | Rejected | Hidden | ~$2,600 | Not checked | Not checked | Private entrance stated | Fails whole-unit requirement |
| R-005 | Rejected / veto condition | Hidden | ~$2,800 | Within threshold | After 2000 | Good basic fit | Fails aircraft-noise veto condition |
| R-006 | Rejected | Hidden | ~$3,000 | Not checked | Not checked | Rent and unit type may fit | Fails move-in timing requirement |

Original listing URLs are hidden for compliance in this public sample.

---

## 5. Sample Candidate Details

### Candidate A-001 — Strong Match

**Status:** `Strong match / needs lease confirmation`

| Field | Result |
|---|---|
| Rent | Around 2,950 CAD/month |
| Location | Richmond / near target station |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | 1 min |
| Building year | 2022 |
| Furniture | Stated |
| A/C | Stated |
| Parking | Stated or strongly indicated |
| URL | Hidden for compliance |

**Why it is included:**

This candidate satisfies the core requirements: budget, bedroom count, whole-unit condo type, walking distance, and newer-building preference. It also has strong positive signals, including very short walking distance, newer building profile, and useful amenities.

**Signals and confirmation items:**

- Lease length needs confirmation because the listing asks for a one-year lease.
- Building year is based on building-level external evidence.
- No strong aircraft-noise, maintenance, water-damage, or building-management concern was found in the sample output.
- Hidden costs such as move-in fees or utility details should still be confirmed.

**Recommended next action:**  
Contact landlord / agent to confirm lease flexibility, current availability, and total monthly cost.

---

### Candidate A-002 — Strong Match

**Status:** `Strong match / minor noise-risk review`

| Field | Result |
|---|---|
| Rent | Around 2,700 CAD/month |
| Location | Richmond / central area |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | 9 min |
| Building year | 2015 |
| Furniture | Stated or indicated |
| A/C | Stated |
| Parking | Stated or indicated |
| URL | Hidden for compliance |

**Why it is included:**

This candidate satisfies the hard requirements and has strong preference matches: newer building, A/C, parking, and verified walking distance within the target threshold.

**Signals and confirmation items:**

- Unit may be near major roads or transit activity.
- Quietness should be checked during viewing.
- Unit-facing and floor-level information should be confirmed because walking distance and noise risk are judged separately.

**Recommended next action:**  
Ask about unit facing, floor, window direction, and whether there is noticeable road or transit noise.

---

### Candidate A-003 — Strong Value Candidate

**Status:** `Strong value candidate / needs noise review`

| Field | Result |
|---|---|
| Rent | Around 2,600 CAD/month |
| Location | Richmond / very close to target station |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | 2 min |
| Building year | 2007 |
| Furniture | Stated |
| A/C | Stated |
| Parking | Stated or indicated |
| URL | Hidden for compliance |

**Why it is included:**

This candidate is a strong value option because it is below the preferred rent level, very close to the target station, and has furniture and A/C stated.

**Signals and confirmation items:**

- Very central location may imply SkyTrain or traffic noise.
- Hidden monthly costs, parking inclusion, and move-in fees should be confirmed.
- Unit orientation should be checked if quiet surroundings are important.

**Recommended next action:**  
Confirm unit orientation, total monthly cost, parking inclusion, and visit during a realistic traffic/transit-noise period.

---

### Candidate B-001 — Qualified but Needs Confirmation

**Status:** `Qualified but needs confirmation`

| Field | Result |
|---|---|
| Rent | Around 2,750 CAD/month |
| Location | Richmond / near target station |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | 8 min |
| Building year | 2011 |
| Furniture | Unknown |
| A/C | Unknown |
| Parking | Stated or indicated |
| URL | Hidden for compliance |

**Why it is included:**

This candidate passes the core requirements and has a reasonable rent, good location, and verified building-age fit.

**Signals and confirmation items:**

- Furniture is not stated, but the playbook treats furniture as potentially negotiable.
- A/C is not stated.
- Lease length may require confirmation.
- Utilities and current availability should be confirmed.

**Recommended next action:**  
Contact landlord / agent to confirm furniture, A/C, lease length, utilities, and current availability.

---

### Candidate B-002 — Qualified but Needs Confirmation

**Status:** `Qualified but needs confirmation`

| Field | Result |
|---|---|
| Rent | Around 2,900 CAD/month |
| Location | Richmond / central area |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | 5 min |
| Building year | 2010, needs second-source confirmation |
| Furniture | Stated |
| A/C | Unknown |
| Parking | Stated or indicated |
| URL | Hidden for compliance |

**Why it is included:**

This candidate appears to satisfy the main requirements and has good walking distance, stated furniture, and move-in-ready signals.

**Signals and confirmation items:**

- Building year was found from only one source and should be confirmed with a stronger source.
- A/C is not stated.
- Duplicate or reposting signals may require current-availability confirmation.
- Hidden costs should be confirmed.
- External building reputation should be checked for recurring maintenance, water-damage, or management complaints before treating it as a finalist.

**Recommended next action:**  
Confirm building identity / year from a stronger source and ask whether the unit has A/C and is still available.

---

### Candidate B-003 — Qualified but Needs Confirmation

**Status:** `Qualified but needs confirmation`

| Field | Result |
|---|---|
| Rent | Around 2,900 CAD/month |
| Location | Richmond / approximate street-level location |
| Unit type | Likely whole-unit apartment |
| Walking distance | 11 min |
| Building year | Unknown |
| Furniture | Unknown |
| A/C | Unknown |
| Parking | Stated or indicated |
| URL | Hidden for compliance |

**Why it is included:**

This candidate passes the walking-distance and budget requirements, and the basic unit profile appears compatible.

**Signals and confirmation items:**

- Address is too vague to bind the listing to a specific building.
- Building year cannot be verified without exact address or building name.
- External building reputation, maintenance history, and water-damage signals cannot be checked until the building identity is resolved.
- Furniture and A/C require confirmation.
- Unit type should be confirmed before treating it as a finalist.

**Recommended next action:**  
Ask for exact address or building name before treating this as a serious finalist.

---

### Candidate B-004 — Qualified but Needs Building-Reputation Review

**Status:** `Qualified but needs confirmation / building-reputation risk review`

| Field | Result |
|---|---|
| Rent | Around 2,800 CAD/month |
| Location | Richmond / near target station |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | 3 min |
| Building year | 2016 |
| Furniture | Stated or indicated |
| A/C | Stated or indicated |
| Parking | Stated or indicated |
| URL | Hidden for compliance |

**Why it is included:**

This candidate appears to satisfy the main requirements: budget, bedroom count, whole-unit condo type, walking distance, and building age. It also has strong location value because it is very close to the target station.

**Signals and confirmation items:**

- External online discussions mention a high proportion of rental units in the building.
- Some external comments associate the building with maintenance concerns.
- Package theft / missing parcel complaints were also found in external sources.
- These are treated as reported risk signals, not confirmed facts.
- The user should verify the building condition, package-management setup, and overall living experience before treating it as a finalist.

**Recommended next action:**  
Ask the agent / landlord about building management, parcel delivery security, elevator / common-area maintenance, and whether there have been recurring resident complaints.

---

## 6. Rejected Examples

### Candidate R-001 — Rejected for Building Age

**Status:** `Rejected`

| Field | Result |
|---|---|
| Rent | Around 2,500 CAD/month |
| Location | Richmond / near target station |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | 5 min |
| Building year | 1994 |
| URL | Hidden for compliance |

**Rejection reason:**

The active requirement asks for buildings built after 2000. This candidate may have good rent and distance, but it fails the building-age requirement.

**Notes:**

- Good price and location do not override a hard requirement.
- If the user later relaxes the building-age requirement, this candidate could be reconsidered.

---

### Candidate R-002 — Rejected for Walking Distance

**Status:** `Rejected`

| Field | Result |
|---|---|
| Rent | Around 2,500 CAD/month |
| Unit type | 2-bedroom apartment |
| Walking distance | 35 min |
| Building year | Not checked |
| URL | Hidden for compliance |

**Rejection reason:**

The listing failed the walking-distance hard requirement. Since map verification showed that it was far beyond the target threshold, downstream checks such as building-year research were not executed.

**Notes:**

- Walking distance is checked with map-based verification rather than trusted from listing text.
- Expensive verification is skipped after a hard-rule failure is confirmed.

---

### Candidate R-003 — Rejected for Bedroom Count

**Status:** `Rejected`

| Field | Result |
|---|---|
| Rent | Around 2,200 CAD/month |
| Unit type | 1-bedroom apartment |
| Walking distance | Not checked |
| Building year | Not checked |
| URL | Hidden for compliance |

**Rejection reason:**

The user required a 2-bedroom unit. This listing was rejected before map verification or external research.

**Notes:**

- Bedroom count is a hard requirement.
- The agent does not spend tokens on expensive downstream checks once an early hard failure is confirmed.

---

### Candidate R-004 — Rejected for Unit Type

**Status:** `Rejected`

| Field | Result |
|---|---|
| Rent | Around 2,600 CAD/month |
| Unit type | Basement / partial-house rental |
| Private entrance | Stated |
| Walking distance | Not checked |
| Building year | Not checked |
| URL | Hidden for compliance |

**Rejection reason:**

The user required a whole-unit condo / apartment. A private entrance does not satisfy the whole-unit requirement if the listing is still a basement, laneway, or partial-house rental.

**Notes:**

- “Private entrance” is not treated as equivalent to independent whole-unit living.
- Basement, laneway, and partial-house rentals are rejected under the active requirements.

---

### Candidate R-005 — Rejected for Aircraft-Noise Exposure

**Status:** `Rejected / veto condition`

| Field | Result |
|---|---|
| Rent | Around 2,800 CAD/month |
| Unit type | Whole-unit 2-bedroom condo |
| Walking distance | Within threshold |
| Building year | After 2000 |
| Aircraft-noise exposure | High risk based on location check |
| URL | Hidden for compliance |

**Rejection reason:**

The active requirements list aircraft-noise exposure as a veto condition. Because this candidate showed strong aircraft-noise risk under the Richmond/YVR quietness check, it was not promoted to the shortlist.

**Notes:**

- Richmond aircraft-noise exposure is checked when quietness matters.
- Aircraft-noise is usually a risk signal, but in this requirement set it is a veto condition.

---

### Candidate R-006 — Rejected for Move-in Timing

**Status:** `Rejected`

| Field | Result |
|---|---|
| Rent | Around 3,000 CAD/month |
| Unit type | 2-bedroom apartment |
| Availability | Too early or too late for the target move-in window |
| Walking distance | Not checked |
| Building year | Not checked |
| URL | Hidden for compliance |

**Rejection reason:**

The listing failed the active move-in timing rule. It was rejected before expensive verification because the available date was outside the acceptable window.

**Notes:**

- Move-in date and stale-post risk are handled before expensive checks.
- Listings outside the move-in window are not promoted just because other fields look attractive.

---

This public sample only shows a selected, anonymized subset of the full delivery.