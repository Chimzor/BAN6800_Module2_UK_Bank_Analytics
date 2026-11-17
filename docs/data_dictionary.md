# Preliminary Data Dictionary

The dictionary separates the supplied P6 customer profile fields from future core-banking and CRM fields. Final names and types must be confirmed during Sprint 0 data-access review.

| Field | Source | Proposed type | Sensitivity | Planned use | Control or limitation |
|---|---|---:|---|---|---|
| customer_id | P6 profile | String | Indirect identifier | Record linkage | Replace with salted hash at ingestion |
| name | P6 profile | String | Direct identifier | None | Exclude before analytics processing |
| surname | P6 profile | String | Direct identifier | None | Exclude before analytics processing |
| gender | P6 profile | Category | Protected characteristic | Fairness monitoring only | Do not use to determine offers |
| age | P6 profile | Integer | Protected characteristic | Segmentation review and fairness audit | Test for disparate outcomes |
| region | P6 profile | Category | Potential geographic proxy | Segmentation and fairness audit | Enforce minimum group size; review Northern Ireland sample |
| job_classification | P6 profile | Category | Potential socioeconomic proxy | Candidate segmentation feature | Validate before using as an income proxy |
| date_joined | P6 profile | Date | Customer history | Derive tenure | Validate date range and missingness |
| balance | P6 profile | Decimal | Financial data | Segmentation and risk features | Restrict access and monitor outliers |
| transaction_history | Core banking | Structured event history | Financial data | Behavioural features | Requires approved extract and retention rules |
| product_holdings | Core banking | Category/list | Financial data | Account-mix features | Minimise to necessary product categories |
| account_closure_date | Core banking | Date | Customer outcome | Derive churn outcome | Requires approved churn definition |
| churn_label | Derived | Boolean | Model outcome | Supervised model target | Must be signed off during Sprint 1 |
| consent_marketing | CRM/contact centre | Boolean | Preference data | Exclude opted-out customers | Query before scoring or export |
| call_note | CRM/contact centre | Text | Potentially sensitive free text | Sentiment signal | Redact unnecessary personal data before analysis |

## Data-quality checks

- Required-column and schema validation.
- Duplicate customer identifier detection.
- Valid ranges for age, balance, and dates.
- Missingness and regional representation reporting.
- Label leakage review after the churn definition is approved.
- Consent and retention checks before scoring or export.
