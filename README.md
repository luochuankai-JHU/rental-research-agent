# Rental Research Agent

An LLM agent system that collects and evaluates rental listings, verifies key claims, and produces evidence-backed shortlists.

Most public rental websites are still built around coarse filters: price, bedroom count, property type, and broad location. But real housing decisions often depend on more specific requirements — quiet surroundings, a 10-minute walk to a specific subway station, a newly built home, or few negative reviews online.

Checking these criteria usually requires renters to open listings one by one, read through noisy descriptions, cross-check maps, search for external information, and make judgment calls manually. For rental beginners, the process is even harder because many market-specific heuristics are rarely taught explicitly and are often learned only after running into problems.

I built this project with OpenClaw to automate that research workflow. The agent collects listings from rental platforms, translates natural-language user preferences into executable screening rules, verifies critical claims with external evidence, combines online research with feedback from experienced local rental agents, and produces a structured shortlist with reasons, uncertainty labels, and source traces.

In a real Vancouver rental search, the system helped me find a better unit than the one I was about to sign, while saving roughly **2,400 dollars per year** in rent. The system has also been refined with feedback from experienced rental agents and piloted with a small group of trial users.

> **Note on scope:** This repository is a technical showcase of a working product prototype. It documents the architecture, methodology, and real results of a system I built and ran on live rental data. For commercialization reasons, the core implementation, including scrapers, prompts, and the filtering engine, is not open-sourced at this stage.

---

## Public Artifacts

This public repository includes anonymized examples of the system inputs, playbook, architecture, and output format:

- [`LIVE_REQUIREMENTS.example.md`](examples/LIVE_REQUIREMENTS.example.md) — anonymized user requirement file used to drive the agent workflow
- [`RENTAL_PLAYBOOK.sample.md`](examples/RENTAL_PLAYBOOK.sample.md) — public sample of rental-market heuristics, negotiation patterns, and risk signals
- [`sample-shortlist-anonymized.md`](docs/sample-shortlist-anonymized.md) — anonymized sample delivery output showing shortlist structure, rejection reasons, and confirmation items
- [`architecture.svg`](docs/architecture.svg) — system architecture diagram

---

## The Problem

The challenge is not a lack of rental listings. It is that renters still have to manually inspect listings one by one, screen them against customized requirements, and search elsewhere for missing information.

Rental websites usually provide only coarse filters such as price, bedroom count, property type, and broad location. They do not support many real decision criteria, such as quiet surroundings, walking time to a specific subway station, whether the building is newly built, or whether the building has recurring negative reviews.

The hard part is therefore not simply collecting listings. It is automating the manual research process: translating customized user requirements into executable screening rules, extracting useful facts from noisy listing pages, filling in missing information through external research, verifying important claims, and producing a shortlist that a person can review and act on.

---

## What It Does

Given a natural-language rental requirement, the agent combines the user's preferences with a rental-market playbook and turns them into executable screening criteria. It then runs a multi-stage research pipeline and returns an auditable shortlist instead of a black-box recommendation.

Each candidate is classified into one of three tiers:

- **Clearly qualified** — satisfies the hard requirements with sufficient evidence
- **Qualified but needs confirmation** — likely matches, but some important fields require human confirmation
- **Rejected** — fails one or more requirements, with explicit rejection reasons

For a public anonymized example of the final delivery format, see [`sample-shortlist-anonymized.md`](docs/sample-shortlist-anonymized.md).

---

## Architecture

![System architecture](docs/architecture.svg)

The system is organized as an OpenClaw agent workspace rather than a single scraper script. Its design separates **requirements**, **domain knowledge**, **tool capabilities**, and **execution artifacts**, so the agent can reason, act, review, and produce traceable outputs in a controlled workflow.

### Agent workflow

A single project-manager-level agent (`proj-rent-self-mgr`) owns the end-to-end process. It operates with explicit boundaries and follows an enforced loop of **plan → self-review → execute → wrap-up**, instead of directly calling tools or making unverified decisions.

### Configuration and execution artifacts

| File / Artifact | Role |
|---|---|
| [`LIVE_REQUIREMENTS.example.md`](examples/LIVE_REQUIREMENTS.example.md) | Anonymized active user requirements — area, budget, unit type, hard constraints, veto conditions, and preferences |
| [`RENTAL_PLAYBOOK.sample.md`](examples/RENTAL_PLAYBOOK.sample.md) | Rental-market heuristics and domain knowledge, including negotiation patterns, local risk signals, and execution reminders |
| `AGENTS.md` | The agent's operating discipline, including workflow rules, candidate-queue maintenance, worklog requirements, and final delivery format |
| `TOOLS.md` | Tool boundaries and routing rules, such as which capability handles listing parsing, map checks, or building-year lookup |
| `skills/` | Modular capabilities used by the agent for listing extraction, map verification, building-year research, evidence collection, and result formatting |
| Candidate queue artifact | Intermediate list of listings that survive pre-filtering and must be reviewed in detail |
| Worklog artifact | Append-only review log that records decisions immediately after each listing is evaluated |
| [`sample-shortlist-anonymized.md`](docs/sample-shortlist-anonymized.md) | Public anonymized sample of the final shortlist and rejection output |

---

## Methodology

The system is designed around five principles: explicit rule decomposition, rental-market playbook reasoning, staged verification, evidence-aware outputs, and auditable execution.

### 1. Human preferences → layered, executable rules

Natural-language rental requirements are decomposed into separate rule layers, so the agent does not confuse a “nice to have” with a hard requirement.

For example, one trial user wanted to find a quiet unit in Richmond. The agent did not treat “quiet” as a simple keyword. Based on its own research and the rental-market playbook, it translated that preference into concrete local signals to investigate: potential aircraft noise due to Richmond’s proximity to Vancouver International Airport, noise from nearby SkyTrain tracks, and traffic noise from units facing or directly adjacent to major roads. These signals were then checked through maps, listing context, and external evidence where available.

- **Hard constraints** — must be satisfied, such as budget, bedroom count, whole-unit requirement, and maximum walking time
- **Veto conditions** — trigger immediate rejection, such as basement / laneway units, unsuitable move-in dates, or clearly stale posts
- **Preferences** — recorded and used for ranking or comparison, but not used to reject, such as furniture, A/C, parking, lower rent, or building amenities
- **To-be-confirmed fields** — never guessed when evidence is insufficient, such as unstated furniture status, negotiable lease length, unclear building age, or missing neighborhood signals

### 2. Rental-market playbook for practical judgment

The rental-market playbook captures practical market know-how — the kind of local heuristics, negotiation patterns, and risk signals that experienced renters and rental agents learn over time.

For example, a listing that asks for a one-year lease may still be worth confirming for users seeking a six-month lease, instead of being rejected immediately. At the same time, external reviews may reveal recurring complaints about poor maintenance, a high proportion of rental units, noise, or water-damage issues. These signals are recorded as risk factors so users can notice potential problems before making a decision.

The playbook is continuously updated with feedback from experienced rental agents, trial users, external research, and field observations.

### 3. Multi-stage pipeline, not one large pass

Instead of scraping everything and applying all checks at once, the workflow is staged so that cheap, conservative filtering happens first and expensive verification only runs on surviving candidates.

1. **Listing pre-filter** — uses the rental platform's own coarse filters, such as area, rent, bedroom count, and property type, to reduce the search space and avoid wasting tokens on clearly irrelevant listings. Missing information is not treated as failure.
2. **Candidate queue** — writes surviving URLs to an intermediate queue before detail review, so candidates are not lost to context drift.
3. **Detail-page extraction** — extracts structured fields from each listing and applies hard rules.
4. **Map verification** — checks actual walking time instead of trusting phrases like “near SkyTrain.”
5. **External research** — resolves building age, building identity, neighborhood quality, online reviews, positive/negative signals, and listing highlights from external sources where possible. This includes both risk signals, such as noise or poor maintenance reviews, and positive signals, such as amenities, building features, and surrounding environment.
6. **Deduplication and stratification** — merges duplicate listings and sorts results into clearly qualified, needs-confirmation, and rejected groups.

### 4. Evidence first: fact vs. inference vs. unknown

The system treats evidence quality as part of the output, not an implementation detail. Each important field is labeled according to what the agent actually knows:

- **Stated fact** — directly shown in the listing or an external source
- **Verified fact** — checked against a stronger source, such as maps, building records, or multiple independent references
- **Inference** — likely but not directly confirmed
- **Unknown / to confirm** — insufficient evidence, requiring human follow-up

This prevents the agent from presenting assumptions as facts, especially when dealing with noisy listing pages, marketing language, or incomplete external information.

### 5. Auditable execution

The agent is required to maintain intermediate execution artifacts instead of only producing a final answer.

- A **candidate queue** defines the exact set of listings that survived pre-filtering and need detail review.
- A **worklog** records each listing review immediately after it happens, including keep/reject decisions and reasons.
- The final shortlist is generated from these artifacts, making the process easier to inspect, reproduce, and extend.

This turns the agent from an opaque “LLM answer generator” into a traceable research workflow.

---

## Results

I first built and ran the system for my own Vancouver rental search. Starting from over 200 initial rental listings, the agent narrowed the pool down to around 20 strong matches that satisfied my core requirements and were worth serious consideration.

The most meaningful result was that the agent surfaced a stronger option than the unit I had found through my own manual search and was about to sign. In other words, it did not just organize listings — it helped discover a better decision candidate that my manual process had not found.

The final choice saved about **2,400 dollars per year** in rent while offering stronger overall living value, including better building amenities, a swimming pool, a sky garden, and a better surrounding environment.

The system has also been piloted with a small group of trial users and refined with feedback from experienced rental agents.

---

## Technical Highlights

- **Research workflow, not keyword filtering** — the system treats rental search as a staged research process with filtering, extraction, verification, intermediate state, and final delivery.
- **Domain-aware requirement translation** — vague requirements such as “quiet environment” or “short-term lease preferred” are translated into concrete signals, checks, and confirmation steps rather than treated as simple keywords.
- **Fact / inference / unknown discipline** — the agent separates stated facts, verified facts, inferred signals, and to-confirm fields instead of presenting all outputs as equally certain.
- **Robust noisy-web extraction** — the workflow is designed around real listing-page issues such as missing fields, marketing language, pagination gaps, duplicate posts, and irrelevant page content.
- **External verification** — high-impact claims such as walking distance, building age, building identity, and neighborhood quality are checked against external evidence where possible.
- **Auditable agent execution** — candidate queue → worklog → shortlist makes the process inspectable, reproducible, and easier for a human to trust.

---

## Status & Contact

This is a working product prototype that has processed live rental data and produced real decision outcomes. The public repository focuses on the system architecture, methodology, and results; the core implementation is not open-sourced at this stage for commercialization reasons.

**I'm open to LLM / agent engineering opportunities.** If you're hiring in this space or want to discuss how the system was built, I'm happy to walk through the design, workflow, and implementation details.

- LinkedIn: https://www.linkedin.com/in/chuankailuo/
- Email: luochuankai1997@outlook.com