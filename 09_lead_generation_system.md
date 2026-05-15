# Lead Generation System

## Goal

Build a repeatable, low-cost lead engine for Santa Cruz County that finds small businesses with:

- visible conversion problems
- enough job value to pay for a setup
- realistic decision speed

## Anti-Overbuild Rule

Do not build the first `100` leads before contacting anyone. Build `25`, score them, create `5` audits, start outreach, and only then decide whether a second batch is worth the time.

## Lead Sources

### High-priority sources

- Santa Cruz Chamber directory
- Downtown Santa Cruz directory
- Scotts Valley Chamber directory
- Capitola-Soquel Chamber
- Aptos Chamber / service directory
- City of Santa Cruz business-license database
- Santa Cruz County FBN search
- Visit Santa Cruz County hotel finder and destination pages
- Google Maps searches

### Secondary sources

- Yelp
- Instagram business profiles
- business websites
- local directories and neighborhood pages

## Manual Research Method

1. Pick one niche and one geography cluster.
2. Search Google Maps and local directories.
3. Open the business website.
4. Check for:
   - missing quote form
   - phone-only or email-only contact
   - weak mobile UX
   - no clear service area
   - weak calls to action
   - low or stale review activity
5. Record public details only.
6. Add one sentence for the best likely offer angle.
7. Score the lead `1 to 5`.

## Search Queries

- `"pressure washing" "Santa Cruz" "free estimate"`
- `"window cleaning" "Capitola" "contact us"`
- `"gutter cleaning" "Aptos" site:.com`
- `"solar panel cleaning" "Scotts Valley"`
- `"handyman" "Soquel" "request a quote"`
- `"property management" "Santa Cruz" maintenance request`
- `"vacation rental cleaning" "Santa Cruz"`
- `"landscaping" "Live Oak" "estimate"`

## CSV Schema

Required columns:

`business_name, category, city, website, phone_if_public, email_if_public, contact_page_if_public, google_rating_if_found, review_count_if_found, website_quality_notes, quote_flow_notes, review_opportunity, automation_opportunity, likely_offer_angle, score_1_to_5, confidence, source_url, next_step, status`

## Lead Qualification Rubric

### Score 5

- clear local fit
- real website
- obvious intake weakness
- owner likely reachable
- setup could plausibly pay for itself from one or two extra jobs

### Score 4

- good fit with one missing data point
- likely worth outreach and maybe an audit

### Score 3

- interesting but not urgent
- weak evidence of budget or pain

### Score 2

- possible fit, but unclear offer angle

### Score 1

- bad fit, weak budget, or no visible operational leverage

## What Makes A Business High-Potential

- outdated site but active business
- call-to-action buried or unclear
- no visible quote form
- poor mobile layout
- decent review volume but no clear follow-up system
- owner-operated category with fast decision-making
- multiple service pages needed by city or service
- obvious operational pain from intake fragmentation

## How To Detect Bad-Fit Leads

- no website and no evidence of wanting more digital business
- franchise or corporate chain
- category with tiny average job value
- committee-driven organization
- regulated complexity outside Eric's current scope
- business already has polished systems and strong follow-up

## First 100-Lead Plan

### Batch 1: 25 leads

- window cleaning
- pressure washing
- gutter cleaning

### Batch 2: 25 leads

- handyman
- property maintenance
- solar panel cleaning

### Batch 3: 25 leads

- landscaping maintenance
- vacation rental cleaning
- property management support

### Batch 4: 25 leads

- ADU/remodel contractors
- small hotels/motels
- wellness or other backup categories

Only move beyond Batch 1 after actual outreach feedback comes in.

## First 25-Lead Batch Plan

Target mix:

- 8 window cleaning
- 7 pressure washing / exterior cleaning
- 4 gutter cleaning
- 3 handyman / property maintenance
- 3 solar panel cleaning

Geography order:

1. Santa Cruz
2. Capitola / Soquel / Live Oak / Pleasure Point
3. Aptos
4. Scotts Valley
5. Felton / SLV if needed to complete the batch

## How To Pick Top 5 For Audits

Choose businesses with:

- score `4` or `5`
- clear website issues
- public phone or contact path
- enough reviews or business maturity to show they are active
- a specific, concrete offer angle

Avoid choosing all 5 from one city unless the niche density demands it.

## Suggested Lead Status Values

- `new`
- `researched`
- `qualified`
- `audit candidate`
- `audit complete`
- `outreach draft ready`
- `contacted`
- `replied`
- `proposal sent`
- `won`
- `lost`
- `bad fit`

## Notes On Ethics And Data Quality

- record only public business contact data
- do not copy directory content blindly
- verify the website and contact path yourself
- mark unknowns as `unknown`
- preserve source URLs for every lead row
