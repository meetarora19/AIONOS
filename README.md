# Veridian Corp Internal IT Service Agent

AIONOS Agentic AI Factory — Assignment 2.

## Run
```bash
pip install -r requirements.txt
streamlit run app.py
```

The prototype is intentionally source-grounded: it uses only the supplied Veridian data pack. No external policy facts are introduced.

## What it demonstrates
- Issue/intent understanding
- Policy retrieval by category
- Follow-up/clarification for ambiguous cases
- Direct resolution for simple requests
- Escalation for security, privileged, or unclear requests
- Structured ticket creation
- Source citation in every response
- Audit trail with JSON export
- Existing request and ticket queue for context

## Demo scenarios
1. Guest Wi-Fi → resolve directly.
2. Phishing → immediate Security escalation.
3. Finance-server admin access → do not approve; escalate.
4. VPN expiry → explain renewal / contractor distinction.
5. Dead 3.5-year laptop → route to IT + Finance because early replacement needs verified failure and Finance sign-off.

## Architecture
User → Intent Classification → Policy Retrieval → Decision/Guardrails → Response
                                      ↓
                              Ticket / Escalation
                                      ↓
                                  Audit Trail


## Visible UI
The app includes a searchable Knowledge Base showing all supplied policies, a request queue, ticket queue, agent reasoning trace, and an auditable decision history. The **Analyze All 15 Requests** control performs source-grounded batch triage so the audit trail can be demonstrated without manually running every request.
