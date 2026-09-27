# 08 — Verification Plan

![Engineering V-model connecting requirements and design to implementation, verification and validation](../images/engineering_v_model.svg)

*Figure 1 — The project V-model. Verification evidence must be linked to the implemented revision.*

## Purpose

Verification establishes whether the implementation satisfies its technical requirements. Validation establishes whether the complete aircraft is suitable for its intended mission. The two are related but not interchangeable.

## Verification levels

| Level | Scope | Typical evidence |
|---|---|---|
| L1 — Static inspection | Part identity, polarity, soldering, wiring and clearances | Inspection checklist and photographs |
| L2 — Powered bench | FC boot, sensor detection, receiver, video and motor outputs | Configuration screenshots, logs and test records |
| L3 — Controlled system | Arming, failsafe, hover and basic controllability | Flight log, Blackbox and recorded observations |

## Verification workflow

1. Identify the requirement and applicable hardware/firmware revision.
2. Define the test setup, stimulus and expected response.
3. Execute the test under the documented safety conditions.
4. Record the observed response and attach evidence.
5. Assign PASS, FAIL, BLOCKED or NOT RUN.
6. Record defects and corrective actions; repeat affected tests after changes.

## Pass criteria

A test is PASS only when:
- the expected result is defined before execution;
- the observed result meets that criterion;
- the tested hardware and firmware revisions are recorded; and
- evidence is retained, with repeatability or limitations documented.

A planned test is not a passed test. A design review or manufacturer specification is not evidence of successful physical integration.

## Result states

| State | Meaning |
|---|---|
| DESIGNED | Intended behavior or architecture is documented |
| VERIFIED | Checked against a defined criterion with evidence |
| MEASURED | A physical quantity was obtained using a documented method |
| SIMULATED | Result comes from a model or simulation, not physical hardware |
| TBD | Evidence or a design decision is still outstanding |

## Test records

Store executed results in [results/](results/). Each record should include:
- test ID and requirement reference;
- date and operator;
- hardware and firmware revisions;
- setup and test conditions;
- expected and observed results;
- verdict and evidence links;
- defects, corrective action and retest status.

Use [test_matrix.md](test_matrix.md) to track coverage and [test_procedures.md](test_procedures.md) for the execution steps.
