# Inter-system debugging: tests, coverage, and GitHub Actions

**Status:** Completed exercise, evidence checked 2026-10-18  
**Source exercise:** [GitHub Skills — Test with Actions](https://github.com/skills/test-with-actions)  
**Portfolio entry:** [Applied-AI-Systems-Engineering](https://github.com/Applied-AI-Systems-Engineering/Applied-AI-Systems-Engineering)  
**Exercise repository:** [skills-test-with-actions](https://github.com/Applied-AI-Systems-Engineering/skills-test-with-actions)

## What I debugged

I traced a deliberately re-enabled Fibonacci test through several connected GitHub systems: the Skills lesson issue, the pull request, the Actions runner, pytest, the coverage reporter, and the coverage threshold gate. The first failure was a bad expected value. Fixing that exposed a second, independent failure: the test suite passed, but coverage remained below the workflow's 90% requirement.

## Evidence trail

| Stage | System and evidence | What it showed |
| --- | --- | --- |
| Lesson tracking | [Skills issue #1](https://github.com/Applied-AI-Systems-Engineering/skills-test-with-actions/issues/1) | GitHub Actions opened the interactive lesson issue and closed it after the exercise. |
| Change under test | [Pull request #3](https://github.com/Applied-AI-Systems-Engineering/skills-test-with-actions/pull/3) | Re-enabling the instructor's disabled Fibonacci test intentionally exposed the failure. |
| Test failure | [Actions run 1](https://github.com/Applied-AI-Systems-Engineering/skills-test-with-actions/actions/runs/38394905647) | `test_get_nth_fibonacci_ten` expected 89, but the implementation returned 55: 4 passed, 1 failed. The log also showed only 88% coverage, but the test step failed before the separate coverage gate ran. |
| Independent quality gate | [Actions run 2](https://github.com/Applied-AI-Systems-Engineering/skills-test-with-actions/actions/runs/38395188946) | The test step passed, the coverage report ran, and the later `Fail if below threshold` step failed. This separated a test assertion problem from a coverage-policy problem. |
| Verified completion | [Actions run 4](https://github.com/Applied-AI-Systems-Engineering/skills-test-with-actions/actions/runs/38396193873) · [completion PR #4](https://github.com/Applied-AI-Systems-Engineering/skills-test-with-actions/pull/4) | All 7 tests passed, the 90% gate passed at 100% statement coverage, and the completion evidence was merged. |

## Root cause and repair

The implementation defines the Fibonacci sequence with `F(0)=0` and `F(1)=1`; therefore `F(10)=55`. The re-enabled test expected 89, which is `F(11)` under that indexing. The correct repair was to fix the test expectation, not to change a working calculation.

That revealed an independent coverage gap. The module had two untested negative-input branches: a negative circle radius and a negative Fibonacci index. Adding `pytest.raises(ValueError)` checks for both exercised those branches. The final suite had 7 passing tests and 100% statement coverage of this small exercise module.

## Debugging method

1. Follow the same change across the lesson issue, pull request, workflow run, job, and individual step.
2. Read the failing assertion before changing application code; compare the test's indexing convention with the function's actual contract.
3. Treat the test command and the coverage threshold as separate gates. A green test step does not mean the whole workflow passed.
4. Verify the repair at the last workflow step and confirm that the corresponding pull request was merged.

## Scope

This is an attributed training exercise using a small Python module. The evidence demonstrates diagnosis across GitHub issue tracking, pull-request state, Actions execution, pytest, and coverage enforcement. It does not claim production readiness or broad application coverage. The original exercise remains linked so reviewers can inspect the source runs directly.
