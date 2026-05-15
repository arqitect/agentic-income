# Hermes Project Setup

## Workspace Path

Primary workspace:

`/workspace/santa-cruz-agency`

Likely host path:

`/opt/hermes/projects/santa-cruz-agency`

## Recommended Folder Structure In Hermes

- `/workspace/santa-cruz-agency/docs`
- `/workspace/santa-cruz-agency/leads`
- `/workspace/santa-cruz-agency/audits`
- `/workspace/santa-cruz-agency/proposals`
- `/workspace/santa-cruz-agency/outreach_drafts`
- `/workspace/santa-cruz-agency/logs`
- `/workspace/santa-cruz-agency/templates`

## Files Hermes Should Read First

Copy or make available these files from this repo:

- `00_executive_summary.md`
- `03_recommended_business_model.md`
- `05_operations_plan.md`
- `06_agent_architecture.md`
- `09_lead_generation_system.md`
- `10_sales_outreach.md`
- `11_website_audit_template.md`
- `12_proposal_templates.md`
- `14_legal_compliance_risk.md`
- `25_decision_log.md`

## Hermes System Instructions

Use a system prompt like this:

```text
You are Hermes operating inside Eric Fadeyev's Santa Cruz local business project.

Primary job:
- research markets
- build lead lists
- draft audits
- draft outreach for human review
- draft proposals
- verify outputs against source URLs and project rules

Hard rules:
- never send emails
- never submit forms
- never message businesses
- never publish pages
- never buy anything
- never contact clients or leads
- never invent business facts, contact data, or statistics
- always cite source URLs when claiming local facts
- mark uncertain information as unknown or needs verification
- respect the lead CSV schema exactly when requested
- write drafts for human approval only
```

## Safe Operating Rules

- treat all external actions as forbidden unless Eric explicitly approves
- default to saving drafts, not acting
- when uncertain, output `needs human review`
- use hosted frontier models for serious synthesis or proposal work
- do not rely on weaker local models for final client-facing quality without review
- before the first paid beta, prioritize research, audits, and drafts over building new automation layers

## First Task Prompt

```text
Read the core project docs first. Then produce a short execution memo with:
1. the recommended first niche
2. the first offer to sell
3. the first 25-lead research plan
4. the top 5 facts that must be verified before outreach

Do not contact anyone. Save the memo to /workspace/santa-cruz-agency/logs/first_execution_memo.md
```

## Lead Batch Prompt

```text
Use the lead-generation rules in the project docs to research 25 Santa Cruz County leads in the exterior cleaning / property-maintenance cluster.

Requirements:
- do not contact anyone
- use only public information
- cite source URLs
- do not invent data
- mark unknown fields as unknown
- follow the required CSV schema exactly

Save the file to:
/workspace/santa-cruz-agency/leads/santa_cruz_home_services_batch_001.csv
```

## Audit Prompt

```text
Using the approved lead CSV, select one target lead and create a practical website audit.

Requirements:
- use observed evidence only
- separate observations from recommendations
- recommend only one best-fit offer
- no outreach, no contact

Save the markdown file to:
/workspace/santa-cruz-agency/audits/<business_slug>_audit.md
```

## Proposal Prompt

```text
Using the call notes and selected package, draft a scoped proposal.

Requirements:
- no guarantees
- clear timeline
- clear deliverables
- clear client responsibilities
- clear exclusions

Save the markdown file to:
/workspace/santa-cruz-agency/proposals/<business_slug>_proposal.md
```

## Follow-Up Prompt

```text
Review the CRM status and suggest the next human-approved follow-up step for each active lead.

Requirements:
- no sending
- no contacting
- stop follow-up if the project rules say to stop

Save the output to:
/workspace/santa-cruz-agency/logs/follow_up_plan_<date>.md
```

## Cron Jobs To Avoid Initially

- all cron jobs before the first paid beta client
- autonomous daily outreach drafting without review
- continuous website crawling
- any job that sends email, SMS, or messages
- auto-publishing content jobs
- high-frequency jobs that generate API cost without clear use

## Good Cron Jobs To Add Later

Only after manual trust is established:

- weekly lead-batch reminder
- weekly KPI review memo
- weekly stale-lead follow-up plan
- monthly source-reverification checklist

## How To Keep Hermes From Sending Or Publishing

- do not configure direct outbound email tools in Hermes
- do not give Hermes access to browser actions that can submit forms without review
- route all outreach through draft files or Gmail drafts
- require a human approval field in the CRM before any downstream workflow can continue
