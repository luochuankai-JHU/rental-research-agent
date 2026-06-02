# RENTAL_PLAYBOOK.sample.md

> Purpose: This file records practical rental-market know-how, negotiation patterns, local heuristics, and risk signals used by the rental research agent.
>
> This is **not** a user requirement file. User-specific hard constraints, preferences, and veto conditions should live in `LIVE_REQUIREMENTS.md`.
>
> This playbook is used as execution guidance during screening, verification, comparison, and final reporting. It should help the agent avoid over-rejecting potentially good listings, surface risks that listings do not disclose, and produce a more useful human-reviewable shortlist.
>
> Public-scope note: This sample version intentionally omits specific building names, exact addresses, private contacts, and sensitive field observations for privacy, compliance, and commercial reasons.

---

## Core Execution Principles

### 1. Do not treat playbook heuristics as hard facts

The playbook contains market experience and useful patterns, but it should not override user requirements or evidence.

The agent must distinguish:

- **Hard requirement** — explicitly defined by the user or `LIVE_REQUIREMENTS.md`
- **Veto condition** — immediate rejection rule defined by the active requirements
- **Heuristic** — useful market experience, but not always true
- **Risk signal** — something worth surfacing to the user
- **Positive signal** — a feature that may improve ranking or comparison
- **Needs confirmation** — requires phone call, viewing, agent follow-up, or user decision
- **Verified fact** — supported by strong evidence

The agent should never present a heuristic, rumor, review, or weak signal as a confirmed fact.

---

### 2. Prefer “needs confirmation” over premature rejection when the issue may be negotiable

Some listing conditions are not as fixed as they appear. If a listing satisfies the user’s core housing needs but has a potentially negotiable issue, the agent should keep it as a candidate and mark it clearly.

Examples:

- lease length may be negotiable
- furniture may be negotiable
- move-in date may be flexible
- parking may be available for extra cost
- utilities may need clarification
- pet rules may require confirmation

Use `Qualified but needs confirmation` when the listing is otherwise strong but the issue requires follow-up.

---

### 3. Surface both risks and highlights

The agent should not only reject bad listings. It should also capture why a candidate may be attractive.

The final shortlist should include:

- hard-requirement fit
- confirmation items
- risk signals
- positive signals
- evidence status
- recommended next action

A good rental decision depends on trade-offs, not only pass/fail filtering.

---

## Playbook Rules

### 1. Lease length is not always fixed by the listing

Many rental listings state a minimum one-year lease. In practice, some landlords or agents may still accept a shorter lease after direct communication, especially if the unit has been listed for a while, the applicant is strong, or the landlord wants to fill the unit quickly.

**Execution rules:**

- Do not reject a listing early only because it says “one-year lease.”
- Keep it as a candidate if it satisfies the core housing requirements.
- Mark the lease issue clearly in the output.
- Recommend direct confirmation before final decision.

**Example output notes:**

- `Listing states one-year lease`
- `Need to confirm whether a six-month lease is negotiable`
- `Lease length is a confirmation item, not an automatic rejection`

**Recommended status:**  
`Qualified but needs confirmation`

---

### 2. Furniture status may be negotiable

If a listing does not mention furniture, it does not always mean furniture is impossible. Some landlords may be willing to provide basic furniture, leave existing furniture, or adjust the setup after negotiation.

This is especially relevant when the user only needs basic furniture rather than a fully furnished unit.

**Execution rules:**

- Do not use “furnished” as an early hard filter unless the user explicitly marks it as non-negotiable.
- Do not reject a listing just because furniture is not mentioned.
- Mark furniture as a confirmation item when the listing otherwise looks strong.
- If the user requires full furniture with no negotiation, follow `LIVE_REQUIREMENTS.md`.

**Example output notes:**

- `Furniture status not stated`
- `Need to confirm whether basic furniture can be negotiated`
- `Unfurnished / furniture unclear; user follow-up required`

**Recommended status:**  
`Qualified but needs confirmation`

---

### 3. Move-in date and stale-post risk matter

A listing may still be online but no longer realistic for the user’s move-in window.

Common risk patterns:

- The available date is much earlier than the user’s target move-in date.
- The available date is much later than the user’s target move-in date.
- The post date is too far before the user’s target move-in date.
- The same listing appears to be repeatedly reposted.
- The listing has inconsistent availability across platforms.

**Execution rules:**

- Use `LIVE_REQUIREMENTS.md` as the source of truth for active date thresholds.
- By default:
  - Reject listings with available dates more than 2 months earlier than the target move-in date.
  - Reject listings with available dates more than 2 weeks later than the target move-in date.
  - Reject listings posted more than 2 months before the target move-in date.
- If timing is not an automatic rejection but still looks risky, keep the listing only with a clear time-risk note.

**Example output notes:**

- `Potential stale listing`
- `Available date may not match target move-in window`
- `Need to confirm actual availability`
- `Post date suggests listing may no longer be active`

---

### 4. “Private entrance” does not always mean independent whole-unit living

Some basement suites, laneway homes, or lower floors of detached houses may advertise a “private entrance.” However, they may still share the same property, utilities, yard, laundry, or daily living environment with the landlord or other occupants.

**Execution rules:**

- If the user requires a whole-unit apartment or condo, basement suites, laneway homes, and partial-house units should be rejected.
- Do not treat “private entrance” as equivalent to independent whole-unit living.
- If the unit type is unclear, mark it as `needs confirmation` instead of assuming it qualifies.

**Recommended rejection reasons:**

- `Fails whole-unit requirement`
- `Likely basement / laneway / partial-house unit`
- `Private entrance does not satisfy whole-unit requirement`

---

### 5. Walking distance and noise risk must be judged separately

Being close to transit is usually a positive signal, but it can also create noise risk.

Examples:

- A unit near a subway or SkyTrain station may be convenient, but a unit directly facing tracks may have noise issues.
- A unit near a major road may satisfy the walking-distance requirement but still be less desirable for quiet living.
- A short walking distance does not automatically mean a good living environment.

**Execution rules:**

- Verify walking distance separately from noise risk.
- Do not treat “close to transit” as automatically positive.
- Mark whether the unit is:
  - near major roads
  - near subway / SkyTrain tracks
  - facing a major traffic corridor
  - next to bus loops, loading zones, or commercial traffic
- If the user values quiet surroundings, include these risks in the final comparison.

**Example output notes:**

- `Walking distance passes, but possible traffic noise risk`
- `Close to transit; noise exposure needs confirmation`
- `Map check required for actual walking time`
- `Listing claim says close to station; walking time must be verified`

---

### 6. Richmond searches require aircraft-noise consideration

For Richmond-area searches, quietness should include possible aircraft-noise exposure due to proximity to Vancouver International Airport.

This does not mean Richmond is always noisy. It means the agent should treat aircraft noise as a local factor when the user cares about a quiet environment.

**Execution rules:**

- For Richmond listings, check possible aircraft-noise exposure when quietness matters.
- Use public airport-noise references where available, such as:
  - YVR noise-management materials
  - aircraft track tools
  - aircraft-noise-sensitive development maps
- Consider flight-path proximity as a risk signal, not a hard rejection unless the user explicitly says so.
- As a simplified local heuristic, areas south of Westminster Highway may have lower aircraft-noise impact than areas closer to common flight paths, but this should be treated as a heuristic rather than a confirmed rule.

**Example output notes:**

- `Richmond aircraft-noise exposure should be checked`
- `Possible aircraft-noise risk based on location`
- `No strong aircraft-noise concern found in initial check`
- `Quietness requires user confirmation or viewing`

---

### 7. External reviews may reveal risks that listings do not disclose

Rental listings are marketing materials. They usually do not mention recurring negative signals such as poor maintenance, noise complaints, water-damage history, building-management issues, or repeated resident complaints.

**Execution rules:**

- Search external sources when the building identity can be resolved.
- Record negative signals separately from listing facts.
- Do not present external complaints as confirmed facts unless supported by strong evidence.
- Prefer evidence labels such as:
  - `confirmed`
  - `likely`
  - `reported by external reviews`
  - `unconfirmed`
  - `not found`
- Surface relevant risks in the final shortlist.

**Example risk notes:**

- `External reviews mention maintenance concerns`
- `External reviews mention noise complaints`
- `External reviews mention water-damage or leak-related issues`
- `Building-management complaints found online`
- `No major negative signals found in public search`

---

### 8. Maintenance and water-damage history should be treated as high-priority risk signals

Some buildings may appear attractive because of location, amenities, or price, but external research or field observations may reveal recurring maintenance issues or water-related incidents.

Specific building names are intentionally omitted from this public sample for privacy, compliance, and commercial reasons.

**Execution rules:**

- Treat recurring maintenance complaints as risk signals.
- Treat water leaks, pipe bursts, mold, or water-damage complaints as high-priority risk signals.
- Confirm through multiple sources where possible.
- If only anecdotal evidence is available, mark it as `reported risk` or `needs confirmation`.
- Do not reject solely based on weak evidence unless the user marks this risk as a hard veto.
- Surface the risk clearly so the user can decide whether to investigate further.

**Example output notes:**

- `Reported maintenance risk`
- `Reported water-damage concern`
- `Leak-related complaints found in external search`
- `Risk requires user confirmation before signing`

---

### 9. Neighborhood safety and livability signals should be checked carefully

Neighborhood quality is not fully captured by rental listings. A unit may look attractive by price, size, or transit access, but the surrounding area may still affect the living experience.

Safety-related claims should be handled carefully. The agent should avoid broad stereotypes and should prefer specific, evidence-backed observations.

**Signals to check:**

- recurring public complaints about safety or disorder
- poor street lighting or isolated walking routes
- proximity to very busy nightlife areas
- repeated mentions of break-ins, package theft, or vehicle theft in public reviews/forums
- whether the walking route to transit feels practical, especially at night
- nearby construction, industrial activity, or heavy truck routes

**Execution rules:**

- Do not label an area as “unsafe” without strong evidence.
- Treat safety-related information as a risk signal, not a confirmed conclusion, unless supported by reliable sources.
- Prefer specific observations over broad neighborhood stereotypes.
- If evidence is weak or mixed, mark the field as `needs confirmation`.
- Surface the concern in the final shortlist so the user can decide whether to visit, ask locals, or inspect the route in person.

**Example output notes:**

- `Potential safety concern based on external reviews`
- `Walking route to transit may require user confirmation`
- `Area has mixed external signals; recommend in-person check`
- `No major public safety concern found in initial search`

---

### 10. Hidden monthly costs should be checked

Base rent is not the full cost of living in a unit. Some listings look cheaper than comparable units but become less attractive after utilities, parking, internet, furniture, or move-in fees.

**Signals to check:**

- whether utilities are included
- whether parking is included or extra
- whether internet is included
- move-in / move-out fees
- furniture cost if the unit is unfurnished
- heating type and possible winter cost
- storage locker cost
- strata move-in deposits or elevator booking fees

**Execution rules:**

- Record hidden costs separately from base rent.
- Do not rank a listing only by rent if major recurring costs are unknown.
- Mark unclear cost items as `needs confirmation`.
- If a lower-rent unit has many unknown costs, surface that uncertainty.

**Example output notes:**

- `Base rent is attractive, but utilities are unclear`
- `Parking cost needs confirmation`
- `Move-in fees may apply`
- `Total monthly cost requires follow-up`

---

### 11. Unit-level factors can change the living experience

Even in the same building, unit-level details can significantly affect quality of life.

**Signals to check:**

- low floor vs. high floor
- facing major road, subway / SkyTrain, alley, construction site, or garbage area
- sunlight and direction
- balcony usability
- view obstruction
- elevator proximity
- garbage chute proximity
- noise from amenities, loading docks, or commercial units
- privacy from neighboring buildings

**Execution rules:**

- Treat these as comparison signals unless the user marks them as hard constraints.
- If the listing does not disclose floor, facing, or exposure, mark as `needs confirmation`.
- Do not assume two units in the same building have the same living quality.

**Example output notes:**

- `Unit facing not disclosed`
- `Possible road-facing noise risk`
- `Floor and sunlight require confirmation`
- `Same building, but unit-level quality unknown`

---

### 12. Building management and strata rules matter

A building may satisfy location and price requirements but still create friction through strict strata rules, poor management, or inconvenient move-in procedures.

**Signals to check:**

- move-in booking requirements
- elevator booking fees
- move-in deposits
- pet restrictions
- smoking restrictions
- BBQ restrictions
- visitor parking rules
- package room or parcel theft complaints
- recurring complaints about building management
- amenity access rules

**Execution rules:**

- Record building-rule issues as risk or confirmation notes.
- Do not assume amenities are usable without checking access rules.
- If strata rules affect the user’s requirements, mark them clearly.

**Example output notes:**

- `Move-in fee / elevator booking may apply`
- `Visitor parking rules need confirmation`
- `Amenity access unclear`
- `Building-management reviews are mixed`

---

### 13. Listing reliability should be assessed

Some listings may be stale, duplicated, misleading, incomplete, or potentially risky.

**Signals to check:**

- unusually low rent compared with similar units
- missing address or vague location
- reused photos
- inconsistent bedroom / unit-type descriptions
- contact method looks suspicious
- listing reposted repeatedly
- price or availability changes across platforms
- listing text appears copied or machine-translated
- photos do not match the described unit type

**Execution rules:**

- Flag suspicious listings instead of treating them as normal candidates.
- Do not recommend a listing as clearly qualified if basic authenticity signals are weak.
- Use `needs confirmation` when the listing may be valid but reliability is uncertain.
- If scam risk appears high, reject or warn clearly depending on evidence strength.

**Example output notes:**

- `Listing reliability concern`
- `Address unclear`
- `Photos / description may be inconsistent`
- `Price looks unusually low; verify before contacting`
- `Potential duplicate or stale listing`

---

### 14. Nearby construction and future disruption should be checked

A unit may look good now but become less attractive if there is nearby construction or planned development.

**Signals to check:**

- nearby active construction
- planned towers or roadwork
- noise / dust risk
- blocked views in the future
- construction-related traffic changes
- nearby demolition or redevelopment signs
- large empty lots or development notices nearby

**Execution rules:**

- Record construction as a risk signal.
- If evidence is unclear, mark as `needs confirmation`.
- Do not reject only because of possible construction unless the user explicitly cares about quietness or long-term stability.

**Example output notes:**

- `Nearby construction risk`
- `Possible future development nearby`
- `Construction impact requires confirmation`
- `No obvious construction concern found in initial search`

---

### 15. Daily convenience should be captured as a positive signal

Some factors do not determine pass/fail but strongly affect livability.

**Signals to check:**

- nearby grocery stores
- pharmacy
- gym / community center
- parks
- restaurants
- schools or daycare if relevant
- distance to workplace / campus
- access to major roads
- nearby medical clinics
- walkability for daily errands

**Execution rules:**

- Record these as positive comparison signals.
- Use them to distinguish otherwise similar candidates.
- Do not use convenience signals to override hard constraints.

**Example output notes:**

- `Good daily convenience`
- `Strong nearby amenities`
- `Good transit and grocery access`
- `Positive surrounding environment`

---

### 16. Positive building features should be recorded

The agent should capture listing highlights and external positive signals, not only risks.

Examples:

- swimming pool
- gym
- sky garden
- concierge
- newer building
- better surrounding environment
- convenient transit access
- strong nearby amenities
- lower rent compared with similar candidates
- good building reputation
- quiet orientation
- good floor plan

**Execution rules:**

- Record positive signals during detail review and external research.
- Use positive signals for comparison and ranking.
- Positive signals do not override hard failures.
- If a listing has strong positives but also unresolved risks, mark the trade-off clearly.

**Example output notes:**

- `Strong building amenities`
- `Better surrounding environment`
- `Good value relative to comparable units`
- `Positive lifestyle features`
- `Strong candidate if confirmation items pass`

---

## Sensitive Building Notes

### Buildings with reported maintenance concerns

Some buildings may appear attractive on paper because of location, amenities, or transit access, but experienced rental agents, public sources, forums, or field observations may indicate recurring maintenance concerns.

Specific building names are intentionally omitted from this public sample for privacy, compliance, and commercial reasons.

**Execution rules:**

- Do not disclose sensitive building-specific notes in public output.
- In private runs, record the concern as a risk signal with evidence status.
- If the evidence is weak or anecdotal, mark it as `reported risk` or `needs confirmation`.
- Do not present sensitive observations as confirmed facts unless evidence is strong.

---

### Buildings with reported water-leak or pipe-burst history

Some buildings may have public or field-reported history of water leaks, pipe bursts, mold, or water-damage complaints.

Specific building names are intentionally omitted from this public sample for privacy, compliance, and commercial reasons.

**Execution rules:**

- Treat water-damage history as a high-priority risk signal.
- Confirm through multiple sources where possible.
- If only anecdotal evidence is available, mark it as a risk note rather than a verified fact.
- Surface the risk clearly in the final shortlist so the user can decide whether to investigate further.

---

## Final Output Guidance

When applying this playbook, the agent should include the following fields where relevant:

| Field | Meaning |
|---|---|
| `status` | clearly qualified / needs confirmation / rejected |
| `hard_requirement_fit` | whether the listing satisfies active hard requirements |
| `veto_reason` | why the listing fails, if rejected |
| `confirmation_items` | issues requiring phone call, viewing, or user follow-up |
| `risk_signals` | external or inferred risks to surface |
| `positive_signals` | amenities, value, location, or lifestyle highlights |
| `evidence_status` | confirmed / likely / inferred / reported / unknown |
| `recommended_next_action` | contact, confirm, view, reject, or compare |

The final output should be useful for a human decision-maker, not just technically correct.

---

## Evidence Discipline

The playbook should guide the agent, but it should not cause unsupported conclusions.

When using playbook knowledge, the agent must distinguish:

- **Confirmed fact** — supported by strong evidence
- **Reported signal** — mentioned in reviews, forums, or field notes
- **Heuristic** — useful pattern but not always true
- **Inference** — likely conclusion based on partial evidence
- **Unknown** — insufficient evidence
- **Needs confirmation** — requires direct follow-up

The agent should never present a heuristic, review, or anecdotal note as a confirmed fact.