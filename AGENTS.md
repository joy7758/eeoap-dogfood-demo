# AGENTS.md

This repository is a low-risk demo repository for future EEOAP candidate evaluation.

Do not add secrets, customer data, production logs, or private evidence.

This repository currently does not install EEOAP.

If EEOAP is evaluated later, it must happen on a test branch under a separate explicit command.

Do not claim certification, legal compliance, standardization, production readiness, commercial readiness, publication, or external validation.

## EEOAP Test-branch Evaluation

EEOAP is installed only for test-branch evaluation.

Before completing an EEOAP-related task, run the protocol citation checker and
validator:

```bash
python -m json.tool protocol/manifest.json
python -m json.tool protocol/clause-index.json
python scripts/check_protocol_citations.py
agent-evidence validate-profile examples/minimal-valid-evidence.json
```

Do not claim certification, standardization, legal compliance, production
readiness, commercial readiness, publication, or external validation.

Do not use sensitive data, customer data, production logs, secrets, or private
evidence.
