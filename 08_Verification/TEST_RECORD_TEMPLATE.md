# Verification Test Record Template

Copy this file for each test, then rename it using the test ID (for example, `TST-001-fc-power-on.md`). Do not mark a test as passed without recorded evidence.

## Test identification

- Test ID:
- Title:
- Date / time:
- Requirement ID(s):
- Test owner:
- Status: NOT RUN / PASS / FAIL / BLOCKED
- Hardware revision(s):
- Firmware target and version:
- Configuration file / commit:

## Objective

What requirement or risk does this test address?

## Setup

- Wiring / configuration:
- Battery or bench supply settings:
- Instruments and model:
- Instrument settings / calibration status:
- Environmental conditions:
- Safety precautions:

## Procedure

1.
2.
3.

## Acceptance criteria

Define the pass/fail threshold before running the test.

- Expected result:
- Pass criteria:
- Fail criteria:

## Observations and measurements

| Step | Observation / measurement | Units | Expected range | Result |
|---|---|---|---|---|
| 1 | TBD | TBD | TBD | NOT RUN |

## Evidence

- Photos:
- Betaflight CLI / configuration dump:
- Blackbox / logs:
- Scope or logic-analyzer captures:
- Raw data file:

Store evidence in the repository and link it here. Preserve original captures where practical.

## Conclusion

- Outcome: NOT RUN / PASS / FAIL / BLOCKED
- Interpretation:
- Deviations from procedure:
- Limitations / uncertainty:
- Follow-up action / issue:
- Retest required: YES / NO

## Review rule

A diagram or planned procedure is not a test result. Record the exact hardware, configuration, conditions and observed evidence. Keep the test marked NOT RUN or BLOCKED if the setup is not yet available.
