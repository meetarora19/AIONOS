# Architecture — Veridian Internal IT Service Agent

```text
                    ┌──────────────────────┐
                    │   Employee Request   │
                    └──────────┬───────────┘
                               ↓
                    ┌──────────────────────┐
                    │Intent Classification │
                    │ (issue + risk type)  │
                    └──────────┬───────────┘
                               ↓
              ┌────────────────────────────────┐
              │ Grounded Policy Retrieval      │
              │ KB-01..KB-10 + Asset Policy    │
              └───────────────┬────────────────┘
                              ↓
                    ┌──────────────────────┐
                    │ Decision + Guardrail │
                    │ resolve / clarify /  │
                    │ route / escalate     │
                    └───────┬───────┬──────┘
                            │       │
                    ┌───────▼──┐ ┌──▼──────────┐
                    │ Response │ │ Ticket      │
                    │ + source │ │ creation    │
                    └───────┬──┘ └──┬──────────┘
                            └───────┬┘
                                    ↓
                           ┌────────────────┐
                           │ Audit Trail    │
                           │ JSON export    │
                           └────────────────┘
```

## Design choices
- Local deterministic policy set prevents unsupported answers.
- Explicit escalation states reduce risky autonomous approvals.
- Source ID is displayed with each answer.
- Ticket creation is triggered for routed/escalated cases.
- Audit data captures the decision path.
