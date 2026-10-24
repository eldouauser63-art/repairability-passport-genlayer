# Repairability Passport

RepairabilityPassport creates a versioned record for an exact manufacturer/model using public repair manuals and parts documentation. The selected checks cover repair manuals, parts catalogs, tool requirements, disassembly, repair procedures, and battery replacement. Independent validators compare supported checks and missing evidence before storing DOCUMENTED, PARTIAL, or INSUFFICIENT_DATA. It does not certify parts availability or official repairability.

## Repository

- Repository name: `repairability-passport-genlayer`
- Description: Creates versioned, evidence-backed repairability assessments for exact product models.
- Contract file: `repairability_passport.py`
- Runner dependency: pinned `py-genlayer:1jb45aa8ynh2a9c9xn3b7qqh8sm5q93hwfp7jqmwsfhh8jpz09h6`

## Intended workflow

See the public methods and state transitions in `repairability_passport.py`. The contract uses independent leader/validator execution for web evidence and writes persistent state only after the consensus call returns.

## Validation before deployment

Run from the repository root:

```bash
genvm-lint check repairability_passport.py
genvm-lint schema repairability_passport.py
pytest tests/direct/ -v
# Then run the configured integration tests against the target GenLayer environment.
```

Static syntax checks are not a substitute for GenVM lint, schema validation, or consensus integration tests.

## Scope and limitations

This contract evaluates the evidence submitted through its public interface. It does not guarantee the truth of an off-chain source, replace legal/professional review, or make an external system perform an action unless an integration is explicitly implemented.
