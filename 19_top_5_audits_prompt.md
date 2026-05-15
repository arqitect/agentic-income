# Top 5 Audits Prompt

Paste into Hermes:

```text
Use the lead CSV at:
/workspace/santa-cruz-agency/leads/santa_cruz_home_services_batch_001.csv

Task:
1. select the top 5 leads based on fit, clear website/contact-flow weakness, and practical sales potential
2. create one markdown audit per lead

Rules:
- do not contact anyone
- do not send anything
- do not submit forms
- use observed evidence from public pages
- if something cannot be confirmed, mark it as needs verification
- recommend only one best-fit offer per lead

Audit requirements for each file:
- business overview
- what they do well
- missed conversion opportunities
- quote/contact flow issues
- mobile issues
- review/reputation opportunities
- local SEO opportunities
- suggested quick wins
- recommended offer
- draft outreach note
- scorecard

Save all audit files to:
/workspace/santa-cruz-agency/audits

Use filenames like:
<business_slug>_audit.md

Also create an index file at:
/workspace/santa-cruz-agency/audits/top_5_audits_index.md

The index should list:
- selected businesses
- why each was selected
- the recommended offer for each
- any data that still needs human verification
```
