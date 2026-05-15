# Agent Architecture

## Stack Overview

- `Hermes`: agent worker, researcher, writer, auditor
- `n8n`: automation orchestrator
- `Open WebUI`: chat and control surface
- `Google Sheets / Airtable / Baserow`: lightweight CRM and delivery tracking
- `Gmail drafts`: human-approved outreach only
- `NPMplus / Tailscale`: internal-only access layer
- `Langfuse later`: optional tracing and prompt/version visibility after trust is earned

## Infrastructure Notes

- `pve7060` is the lightweight app/server host
- `n8n`: `10.1.1.21` and `https://n8n.ericfadeyev.com`
- `Hermes`: `10.1.1.23` and `https://hermes.ericfadeyev.com`
- `Open WebUI`: `10.1.1.35` and `https://ai.ericfadeyev.com`
- `NPMplus`: `10.1.1.20`
- intended access model: `LAN / Tailscale only`

Treat public domains as convenience front doors only. Do not open sensitive tooling to the public internet.

## Operating Principle

AI handles research, drafting, QA, and structuring. Human handles:

- final judgment
- all outreach
- all publishing
- all financial decisions
- all credential use

## Data Flow

1. Market or lead data is gathered manually or through approved research tasks.
2. Hermes prepares normalized notes, lead rows, audits, and draft copy.
3. n8n routes records into the CRM and queues draft artifacts.
4. Eric reviews outputs in Open WebUI or the CRM.
5. Human-approved drafts are turned into actual outreach or delivery work.

## Agent Roles

## Market Scout Agent

### Purpose

Find grounded Santa Cruz market facts, niche conditions, and source URLs.

### Inputs

- target niche
- target geography
- current research questions

### Outputs

- source log
- demand notes
- neighborhood targeting notes
- claims marked `verified` or `needs verification`

### Tools

- web research
- CRM source-log table
- Hermes file output

### Safety Boundaries

- no invented statistics
- no copied directory lists without verification
- no outreach

### Example Prompt

`Research the Santa Cruz County window-cleaning market. Cite every source URL, date each claim, mark uncertain facts as needs verification, and do not contact anyone.`

## Lead Research Agent

### Purpose

Build lead lists and fill the lead CSV schema.

### Inputs

- niche
- geography
- lead schema
- scoring rubric

### Outputs

- CSV rows
- website notes
- next-step recommendations

### Tools

- web browsing
- directories
- CRM / CSV writer

### Safety Boundaries

- no invented contact details
- mark unknown as `unknown`
- no contact or submission actions

### Example Prompt

`Create 25 lead rows for Santa Cruz County exterior cleaning businesses using the provided schema. Use only public information, cite source URLs, and do not contact businesses.`

## Website Audit Agent

### Purpose

Review a business website and identify missed conversion opportunities.

### Inputs

- business name
- website URL
- niche context
- audit template

### Outputs

- markdown audit
- scorecard
- suggested offer angle

### Tools

- browser
- audit template
- screenshot support if needed

### Safety Boundaries

- no made-up issues
- clearly distinguish observed facts from inferred recommendations
- no direct outreach

### Example Prompt

`Audit this window-cleaning site for mobile UX, quote flow, follow-up friction, review opportunities, and local SEO gaps. Keep the audit practical and cite visible evidence.`

## Google Business Profile Audit Agent

### Purpose

Review the business's local visibility basics without overclaiming ranking outcomes.

### Inputs

- business name
- city
- public listing details if visible

### Outputs

- listing completeness notes
- review-response opportunities
- NAP consistency checklist

### Tools

- browser
- manual observation notes

### Safety Boundaries

- no fake ranking claims
- no edits to profiles
- no review manipulation

### Example Prompt

`Review the public local-listing presence for this Santa Cruz business. Identify missing fields, reputation opportunities, and consistency issues without claiming guaranteed ranking gains.`

## Offer-Matcher Agent

### Purpose

Match each lead to the most appropriate offer and price band.

### Inputs

- lead row
- audit notes
- package matrix

### Outputs

- likely offer angle
- price range
- fit confidence

### Tools

- package docs
- scoring rubric

### Safety Boundaries

- do not force-fit every lead
- mark bad-fit leads clearly

### Example Prompt

`Given this audit and lead record, choose the best offer package, explain why, and note whether this lead is beta-fit, standard-fit, or bad-fit.`

## Outreach Writer Agent

### Purpose

Draft concise, permission-based outreach in Eric's voice.

### Inputs

- lead notes
- audit findings
- chosen offer
- channel type

### Outputs

- email draft
- DM draft
- phone opener
- follow-up notes

### Tools

- outreach templates
- lead notes

### Safety Boundaries

- no sending
- no deceptive claims
- no fake urgency

### Example Prompt

`Write a short, non-pushy email to a Santa Cruz pressure-washing owner. Mention one observed website issue, offer to send a short audit, and keep the tone local and respectful.`

## Proposal Writer Agent

### Purpose

Turn a real conversation into a clean, scoped proposal.

### Inputs

- call notes
- selected package
- timeline
- pricing

### Outputs

- proposal draft
- scope summary
- client responsibilities

### Tools

- proposal templates
- pricing file

### Safety Boundaries

- no guarantees
- no scope hidden in vague language

### Example Prompt

`Draft a proposal for a handyman business needing a quote form, simple tracker, and review workflow. Keep scope tight and list what is not included.`

## QA / Verifier Agent

### Purpose

Check outputs for factual, scope, and policy issues.

### Inputs

- drafts
- source log
- policy rules

### Outputs

- pass / fail notes
- required fixes

### Tools

- source log
- business docs
- guardrails

### Safety Boundaries

- cannot approve actions that violate outreach or publishing rules

### Example Prompt

`Review this audit and outreach draft. Flag any invented facts, unsupported claims, compliance risk, or tone problems before human review.`

## Follow-Up Planner Agent

### Purpose

Plan next steps after no reply, reply, proposal, or delivery.

### Inputs

- lead status
- last contact date
- channel history

### Outputs

- next-step recommendation
- reminder date
- draft language

### Tools

- CRM
- follow-up rules

### Safety Boundaries

- no automatic sending
- stop after the defined outreach limit

### Example Prompt

`Plan the next human-approved follow-up for this lead based on one unanswered email and one voicemail over 7 days.`

## Core Guardrails

- no emails, texts, calls, form submissions, or DMs without human approval
- no publishing live pages without human approval
- no buying software or services
- no scraping that creates abusive traffic
- no pretending to have verified facts that were inferred
- no storing raw secrets in project files
