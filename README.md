# UK Bank Customer Analytics Delivery Plan

This repository converts the Module 1 vision into an executable delivery plan for a UK retail bank. The project addresses high customer churn and low cross-sell conversion caused by static demographic segmentation, disconnected customer data, and the absence of an agreed churn definition.

## Proposed solution

- Segment customers into four behavioural personas.
- Estimate churn propensity after labelled outcome data becomes available.
- Explain predictions with SHAP and monitor fairness across gender, age band, and region.
- Translate approved scores into adviser recommendations with human review.
- Monitor business value, model stability, system reliability, and privacy controls.

## Current data constraint

The P6 UK customer profile dataset supports exploratory analysis and initial segmentation but does not contain churn labels, transaction history, salary, or longitudinal behaviour. Prediction work therefore depends on approved core-banking extracts and a signed-off churn definition.

## Repository structure

```text
.
├── data/
│   ├── raw/
│   └── processed/
├── docs/
│   ├── api_specification.md
│   ├── data_dictionary.md
│   ├── model_card_template.md
│   ├── raid_log.md
│   ├── sprint_backlog.md
│   └── submission_checklist.md
├── src/
│   ├── churn_predictor.py
│   ├── data_loader.py
│   ├── explainability.py
│   ├── preprocessing.py
│   └── segmentation_model.py
├── tests/
│   ├── test_predictions.py
│   └── test_schema.py
└── requirements.txt
```

## Delivery sequence

Work is planned across seven two-week sprints, numbered 0 to 6. Segmentation precedes churn prediction so the bank can receive useful customer insight while labelled churn data and governance approvals are being secured. See [the sprint backlog](docs/sprint_backlog.md) for the ticket-to-deliverable mapping.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pytest
```

Do not commit customer data, secrets, salts, or credentials. Raw personal data must remain in approved UK-hosted storage.
