# KPI Dashboard

## Core KPIs

| KPI | Definition | Why It Matters | Tracking Cadence |
| --- | --- | --- | --- |
| leads found | raw leads added to CRM | top-of-funnel health | weekly |
| leads qualified | leads scored as real fit | quality of research | weekly |
| audits created | completed audits | output toward conversations | weekly |
| messages sent | human-approved outreach attempts | activity level | weekly |
| replies | any response from lead | message resonance | weekly |
| calls booked | discovery calls scheduled | sales progress | weekly |
| proposals sent | proposals delivered | pipeline maturity | weekly |
| closed clients | won deals | direct business result | weekly / monthly |
| revenue | cash actually collected | real performance | weekly / monthly |
| fulfillment time | hours spent delivering | margin and scope control | per project |
| retention | active support clients retained | recurring stability | monthly |
| cost per lead | lead-gen cost divided by leads found | efficiency | monthly |
| API cost | direct model/tool spend | keeps stack grounded | weekly / monthly |
| effective hourly rate | collected revenue divided by hours worked | real-world sustainability | monthly |
| pre-revenue automation hours | hours spent building workflows before first paid beta | catches overbuilding early | weekly until first client |

## Suggested Dashboard Tabs

- `Leads`
- `Outreach`
- `Sales Pipeline`
- `Clients`
- `Delivery`
- `Finance`
- `Source Log`

## Google Sheet / Airtable-Style Schema

| Table | Key Fields |
| --- | --- |
| Leads | lead_id, business_name, niche, city, source_url, score_1_to_5, status, next_step |
| Outreach | outreach_id, lead_id, channel, date_sent, template_used, result, next_follow_up_date |
| Sales Pipeline | opportunity_id, lead_id, offer, estimated_value, stage, proposal_date, outcome |
| Clients | client_id, client_name, package, start_date, monthly_support, status |
| Delivery | task_id, client_id, deliverable, owner, due_date, completion_date, hours_spent |
| Finance | entry_id, client_id, type, amount, due_date, paid_date, notes |

## Simple Weekly Targets For The First 30 Days

- `25` new leads researched
- `5` audits created
- `10 to 20` outreach attempts
- `2 to 4` replies
- `1 to 3` calls
- `1` proposal
- `1` paid beta target by day 14 to 30

## Interpretation Rules

- low replies with strong audits means improve outreach copy or channel choice
- many replies but few proposals means discovery handling needs work
- proposals with no closes means pricing, niche, or trust may be off
- low effective hourly rate means narrow scope or raise price
