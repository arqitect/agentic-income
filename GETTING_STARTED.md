# Getting Started (Post-Migration)

This guide turns the repository into a single linear operating workflow.

## 1) Set up your working docs and data files (Day 1)

1. Read the strategy spine in this order:
   - `00_executive_summary.md`
   - `03_recommended_business_model.md`
   - `15_execution_roadmap.md`
2. Create your local working copies of CSV files in `22_data/`.
3. Confirm your operating constraints in `14_legal_compliance_risk.md` before outreach.

## 2) Build your first lead batch (25 leads)

1. Follow `09_lead_generation_system.md`.
2. Use `18_first_25_leads_research_prompt.md` and `23_prompts/lead_scout_agent.md`.
3. Store leads using the exact header from `22_data/leads_schema.csv`.

## 3) Produce first 5 audits

1. Use `11_website_audit_template.md`.
2. Optionally use `19_top_5_audits_prompt.md` + `23_prompts/website_auditor_agent.md`.
3. Ensure each audit includes evidence, one best-fit recommendation, and no guarantee language.

## 4) Start outreach (human-approved only)

1. Use `10_sales_outreach.md` for channel and compliance rules.
2. Draft from `21_assets_and_templates/` and `23_prompts/outreach_writer_agent.md`.
3. Track each attempt in `22_data/outreach_tracker_schema.csv` format.

## 5) Close and deliver first paid beta

1. Scope via `12_proposal_templates.md` and `21_assets_and_templates/simple_contract_scope.md`.
2. Deliver with `20_client_delivery_sops.md`.
3. Track pipeline stage in `22_data/client_pipeline_schema.csv`.

## 6) Run weekly review loop

1. Update `17_kpi_dashboard.md` metrics.
2. Run `23_prompts/weekly_review_agent.md`.
3. Log decisions in `25_decision_log.md` and follow `26_master_next_steps.md`.

## Validation checklist

- No automated outreach is sent.
- Every external claim includes source URLs.
- Unknown fields are marked `unknown`.
- Proposals contain clear scope, exclusions, and timeline.
