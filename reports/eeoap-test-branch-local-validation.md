# EEOAP Test-branch Local Validation

## Scope

Self-controlled candidate repository test-branch evaluation only.

## Classification

`CANDIDATE_TEST_BRANCH_LOCAL_PASS`

## Commands

- `git diff --check`
- `.venv/bin/python -m json.tool protocol/manifest.json`
- `.venv/bin/python -m json.tool protocol/clause-index.json`
- `.venv/bin/python scripts/check_protocol_citations.py`
- `.venv/bin/python scripts/check_protocol_citations.py --manifest protocol/manifest.json --clause-index protocol/clause-index.json --clauses-md docs/protocol/clauses.md --pr-template .github/pull_request_template.md --root .`
- `.venv/bin/python -m pip install -e /Users/zhangbin/GitHub/agent-evidence`
- `.venv/bin/agent-evidence validate-profile --schema schema/execution-evidence-operation-accountability-profile-v0.1.schema.json examples/minimal-valid-evidence.json`
- `.venv/bin/python -m pytest tests`

## Results

- `git diff --check`: PASS.
- JSON check for `protocol/manifest.json`: PASS.
- JSON check for `protocol/clause-index.json`: PASS.
- Protocol citation checker default invocation: PASS, `"ok": true`.
- Protocol citation checker explicit-root invocation: PASS, `"ok": true`.
- Local editable install of source validator: PASS.
- Validator smoke test on `examples/minimal-valid-evidence.json`: PASS,
  `"ok": true`, with explicit repository-local schema path.
- Candidate package tests: PASS, `1 passed`.

## Negative Controls

- `negative_controls/bad-clause-index.json`: expected non-zero exit observed;
  checker reported `invalid_clause_id_format:BAD-001`.
- `negative_controls/missing-related-file-clause-index.json`: expected non-zero
  exit observed; checker reported `missing_related_file`.
- `negative_controls/bad-evidence.json`: expected non-zero exit observed;
  validator reported `schema_violation` for missing required `actor`.

## Install Friction

- Remote GitHub Actions initially failed because the pip-installed validator did
  not expose the default schema path expected by the CLI.
- Fix applied on the candidate test branch: include
  `schema/execution-evidence-operation-accountability-profile-v0.1.schema.json`
  and invoke `agent-evidence validate-profile` with explicit `--schema`.

Negative controls were used as local temporary files and are not part of the
candidate test-branch commit.

## Claim Scope

- External pilot started: no.
- External users contacted: no.
- Invitation sent: no.
- Certification claimed: no.
- Standardization claimed: no.
- Commercial readiness claimed: no.
- Production readiness claimed: no.
- External validation claimed: no.
