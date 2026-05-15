# First 25 Leads Research Prompt

Paste into Hermes:

```text
You are helping build the first lead batch for Eric Fadeyev's Santa Cruz local service business project.

Task:
Research the first 25 leads in Santa Cruz County for the home-service / property-service cluster, prioritizing:
- window cleaning
- pressure washing / exterior cleaning
- gutter cleaning
- handyman / property maintenance
- solar panel cleaning

Hard requirements:
- do not contact anyone
- do not send emails
- do not submit forms
- do not publish anything
- use only public information
- cite source URLs
- do not invent data
- mark unknown fields as unknown
- prioritize businesses with weak quote/contact flows
- keep notes practical and concise

Use this exact CSV schema and column order:
business_name, category, city, website, phone_if_public, email_if_public, contact_page_if_public, google_rating_if_found, review_count_if_found, website_quality_notes, quote_flow_notes, review_opportunity, automation_opportunity, likely_offer_angle, score_1_to_5, confidence, source_url, next_step, status

Scoring guidance:
- 5 = strong fit, clear website/intake weakness, likely to pay
- 4 = good fit with minor unknowns
- 3 = possible fit
- 2 = weak fit
- 1 = bad fit

Geography priority:
1. Santa Cruz
2. Capitola / Soquel / Live Oak / Pleasure Point
3. Aptos
4. Scotts Valley
5. Felton / SLV if needed

Save the final CSV to:
/workspace/santa-cruz-agency/leads/santa_cruz_home_services_batch_001.csv

Also save a short markdown note to:
/workspace/santa-cruz-agency/logs/santa_cruz_home_services_batch_001_notes.md

The note should summarize:
1. how many leads were found in each category
2. the highest-scoring 5 leads
3. any claims or fields that still need verification
```
