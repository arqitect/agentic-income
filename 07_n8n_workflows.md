# n8n Workflow Plan

Do not assume external credentials already exist. Build these as workflow designs first, then connect tools only after a manual process has already proven useful.

## Pre-Revenue Automation Rule

Before the first paid beta client, only build or use:

- manual lead intake to CRM
- internal follow-up reminders

Do not spend pre-revenue time wiring:

- client onboarding automations
- review request workflows
- audit-generation pipelines
- proposal pipelines

Those can stay on paper until a client has paid and the manual version has already worked once.

## Common Rules

- every workflow must log who approved the next action
- every client-facing artifact must pause for human review
- failures should create a retry task, not silent loss
- use placeholders for Gmail, Sheets, Airtable, and webhook credentials until configured

## Manual Lead Intake To CRM

### Trigger

- manual form submission
- manual spreadsheet row
- manual webhook from a local form

### Nodes

- Manual Trigger or Webhook
- Set / Normalize Fields
- IF required fields present
- Append to Google Sheets / Airtable / Baserow
- Create internal review task

### Data Fields

- business name
- category
- city
- source URL
- website
- contact details if public
- lead score
- status

### Human Approval Step

- human confirms the lead is worth researching further

### Failure Handling

- if required fields are missing, route to `needs cleanup`
- if duplicate business found, flag instead of overwriting

### What To Log

- create timestamp
- source
- duplicate check result
- user who added the lead

### Future Upgrade Ideas

- QR code or phone shortcut for adding walk-in leads

## Lead Scoring Workflow

### Trigger

- new lead added

### Nodes

- Fetch lead row
- Rule-based score calculation
- Optional LLM summarizer
- Update CRM

### Data Fields

- website quality
- quote-flow quality
- review opportunity
- automation opportunity
- fit confidence

### Human Approval Step

- human can override the score before audit generation

### Failure Handling

- if score fields are incomplete, mark `manual review needed`

### What To Log

- original score
- adjusted score
- scorer

### Future Upgrade Ideas

- niche-specific scoring profiles

## Website Audit Generation Workflow

### Trigger

- lead status changed to `audit requested`

### Nodes

- Fetch lead record
- Fetch audit template
- LLM draft node
- QA node
- Save markdown to audits folder
- Notify human reviewer

### Data Fields

- business name
- website URL
- niche
- city
- observed issues
- recommended offer

### Human Approval Step

- human must approve the audit before it is referenced in outreach

### Failure Handling

- if the website is unavailable, save audit as partial and flag `manual browser check`

### What To Log

- audit file path
- draft timestamp
- QA result

### Future Upgrade Ideas

- screenshot capture
- scorecard auto-fill

## Outreach Draft Creation Workflow

### Trigger

- lead status changed to `approved for outreach draft`

### Nodes

- Fetch lead + audit
- Offer-Matcher logic
- LLM draft node
- QA node
- Save draft to CRM and file
- Create approval task

### Data Fields

- channel
- offer angle
- local observation
- CTA
- stop-after count

### Human Approval Step

- human must approve every draft before use

### Failure Handling

- if no clear offer angle exists, route back to manual review

### What To Log

- draft version
- reviewer
- disposition

### Future Upgrade Ideas

- per-channel style presets

## Follow-Up Reminder Workflow

### Trigger

- lead contacted date entered
- proposal sent date entered

### Nodes

- Wait / date compare
- IF reply exists
- Create reminder task
- Update next-step field

### Data Fields

- last contact date
- follow-up stage
- next reminder date
- stop flag

### Human Approval Step

- reminder only; no sending

### Failure Handling

- if dates are missing, route to admin review

### What To Log

- reminder created
- reminder completed
- follow-up stopped reason

### Future Upgrade Ideas

- calendar event creation

## Proposal Generation Workflow

### Trigger

- lead status changed to `proposal needed`

### Nodes

- Fetch call notes
- Fetch package template
- LLM draft
- QA check
- Save proposal draft
- Human review task

### Data Fields

- scope
- timeline
- price
- client responsibilities
- exclusions

### Human Approval Step

- required before sending

### Failure Handling

- if scope or price missing, block output

### What To Log

- proposal version
- approval status
- sent date

### Future Upgrade Ideas

- PDF export

## Weekly Lead Batch Workflow

### Trigger

- manual run once per week

### Nodes

- prompt assembly
- Hermes task creation
- CSV validation
- append to CRM
- shortlist scoring

### Data Fields

- niche
- geography
- batch ID
- source URLs

### Human Approval Step

- approve the prompt before the run
- approve final shortlist before audits

### Failure Handling

- reject rows missing source URLs

### What To Log

- batch ID
- records added
- rejected rows

### Future Upgrade Ideas

- rotating niche queues

## Client Onboarding Workflow

### Trigger

- deal status changed to `won`

### Nodes

- create client record
- generate onboarding email draft
- create task checklist
- create project folders
- create delivery milestone rows

### Data Fields

- client name
- main contact
- package
- start date
- payment status

### Human Approval Step

- approve onboarding email draft
- confirm payment received before delivery starts

### Failure Handling

- if payment not confirmed, route to pending

### What To Log

- project ID
- onboarding sent
- assets received

### Future Upgrade Ideas

- e-sign integration later

## Review Request Workflow

### Trigger

- job completion row marked complete

### Nodes

- fetch review links
- choose email or SMS template
- create draft message
- queue manual reminder

### Data Fields

- customer first name
- job type
- completion date
- review link

### Human Approval Step

- human sends or confirms sending
- default to manual email first; do not auto-send SMS in version 1

### Failure Handling

- if review link missing, create fix task
- if customer consent status for SMS is unclear, block SMS use and route to manual email only

### What To Log

- draft created
- sent yes/no
- review received if tracked

### Future Upgrade Ideas

- sentiment tagging on responses
