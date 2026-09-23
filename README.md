# Python CI Checks | Unit Testing 
<img width="240" height="240" alt="icons8-python-240" src="https://github.com/user-attachments/assets/e0632c0c-b531-4ef2-bdfd-4a67d0d1fb9d" />

---

# Author

| **Author**    | **Created On** | **Version** | **Last Edited On** | **L0 Reviewer** | **L1 Reviewer** | **L2 Reviewer** |
| ------------- | -------------- | ----------- | ------------------ | --------------- | --------------- | --------------- |
| Vashishtha Prakash | 21-09-2026     | v1.0        | 21-09-2026         | Sunny/Shubham   | Shreya / Nikita  | Piyush Upadhyay   |

---
## Table of Contents

* [1. Introduction](#1-introduction)
* [2. What](#2-what)
* [3. Why](#3-why)
* [4. Workflow Diagram](#4-workflow-diagram)
* [5. Different Tools & Comparison Matrix](#5-different-tools--comparison-matrix)
* [6. Advantages of this CI Design](#6-advantages-of-this-ci-design)
* [7. POC Evidence (Execution Results)](#7-poc-evidence-execution-results)
  * [Pipeline Stage View Evidence](#pipeline-stage-view-evidence)
  * [Automated Headless Testing Result Console Logs](#automated-headless-testing-result-console-logs)
* [8. Best Practices Followed](#8-best-practices-followed)
* [9. Recommendation & Conclusion](#9-recommendation--conclusion)
* [10. Contact Information & References](#10-contact-information--references)
* [11. References](#11-references)

---

## 1. Introduction
The Attendance REST API is a critical core backend module responsible for handling workforce logging data, transactions, and validation metrics across the microservices ecosystem. This project delivers an automated Continuous Integration (CI) configuration script (Jenkinsfile) designed to handle multi-stage validation gates—including environment checking, sandboxed dependency tracking, static source analysis, and headless unit test assertions—on a centralized cloud automation worker.

---

## 2. What 

### The "What"
An automated, isolated validation framework triggered upon incoming changes to the code repository that orchestrates:
* **Dependency Sandbox Isolation:** Building an isolated runtime environment (`venv`) to guarantee package version lock-in without system pollution.
* **Static Syntax Analysis:** Scanning backend source files using lint rules (`flake8` framework hooks) to intercept programmatic anomalies before compilation.
* **Functional Logic Verification:** Executing headless testing pipelines via `pytest` to validate application endpoint modules (router, client, models, and utils).

## 3. Why
* **Guaranteed Reliability on Critical Paths:** Attendance data calculations have direct downstream impacts on core organizational matrices. Automating checks ensures broken changes never compromise live microservice flows.
* **Bypassing PEP 668 Multi-Distribution Conflicts:** Modern Linux enterprise layers (Ubuntu 24.04/22.04) enforce strict `externally-managed-environment` rules. This architecture safely isolates application binaries away from critical OS root paths.

---

## 4. Workflow Diagram
The structural automation flow of the Python Attendance API CI execution pipeline managed dynamically by the Jenkins server node:

```text
[ Developer Push via SSH/Token ] ──> [ GitHub Account (Fork) ]
                                              │
                                              ▼ (Jenkins Automation Trigger)
                                     [ Jenkins CI Server ]
                                              │
         ┌────────────────────────────────────┴────────────────────────────────────┐
         ▼                                    ▼                                    ▼
 [Environment Check] ───────────────> [Install Dependencies] ──────────────> [Lint Checking (Flake8)]
 (Python 3.12 & Pip Validation)       (Clean Virtualenv Activation)         (Static Quality Gate)
                                                                                   │
                                                                                   ▼
                                                                             [Unit Testing]
                                                                          (Pytest Framework Suite)
```

---

## 5. Different Tools & Comparison Matrix

To optimize build speed and maintain server layer stability, the following tooling choices were finalized for this pipeline execution:

| Tool Category | Selected Option | Alternatives Considered | Selection Rationale |
| :--- | :--- | :--- | :--- |
| **Automation Engine** | **Jenkins** | GitHub Actions / GitLab CI | Delivers direct hardware access on standalone enterprise servers, private node execution, and granular logging outputs. |
| **Isolation Gateway** | **Python Virtualenv (venv)**| Poetry / Pipenv | Native Python `venv` avoids translation errors and bypasses complex PEP 517 wheel compiler mismatches (such as legacy `pyyaml` bottlenecks) by fetching clean pre-compiled binaries directly. |
| **Testing Engine** | **Pytest** | Unittest (Built-in standard) | Offers clean test fixtures, powerful extension plugins (`pytest-cov`), zero code boilerplate, and transparent terminal logs. |
| **Static Code Analyzer**| **Flake8 / Pylint** | SonarQube (Heavyweight hooks) | Lightweight, low memory footprint, executes execution checks within milliseconds on high-velocity branch pushes. |

---

## 6. Advantages of this CI Design
* **Early Defect Catching:** Logical regressions or syntax bugs within the core attendance tracking handlers are intercepted immediately during the active sprint loop.
* **Dependency Health:** Dynamic isolated wheel configurations lock out third-party framework discrepancies between independent developer local systems and production.
* **Zero Host Interferences:** All library packages are completely caged inside the active Jenkins workspace directory, keeping the primary server operating system untouched.

---

## 7. POC Evidence (Execution Results)

The multi-stage Python pipeline is fully integrated and running with complete **SUCCESS (Green Status)** on the cloud infrastructure instance.

### Pipeline Stage View Evidence
*Visual proof from the Jenkins UI illustrating the continuous delivery workflow executing consecutively with no blocking errors:*

<!-- PLACEHOLDER FOR JENKINS STAGE VIEW SCREENSHOT -->
```text
[ INSERT JENKINS STAGE VIEW SCREENSHOT HERE - e.g., showing green blocks for SCM Checkout, Environment Check, Install Dependencies, Lint Checks, and Unit Tests ]
```

### Automated Headless Testing Result Console Logs
*Detailed runtime summaries showing the system executing logic checks across underlying python subcomponents (router, client, models, utils):*

<!-- PLACEHOLDER FOR JENKINS CONSOLE OUTPUT SCREENSHOT -->
```text
[ INSERT PYTEST RUN CONSOLE LOG SCREENSHOT HERE - showing passing test execution logs and code verification matrix outputs ]
```

---

## 8. Best Practices Followed
* **Cloud Infrastructure Guardrails:** The hosting AWS Security Group is strict—administrative port boundaries (SSH Port 22 and Jenkins UI Port 8080) are firewall-restricted exclusively to specific authorized corporate node IPs.
* **Binary Wheel Enforcement:** Problematic Python build dependencies are forced to initialize from target native binaries (`--only-binary=:all:` flag structures), entirely avoiding pipeline hanging states or compiler setup errors.
* **Clean Workspace Execution:** Automated recursive environment wipes (`rm -rf venv`) prevent stale caching issues during fresh execution triggers.

---

## 9. Recommendation & Conclusion
The implementation proves that bundling native Python environment sandboxing with a clean Pytest framework inside automated Jenkins stages builds a high-velocity, reliable quality control check. It is recommended to lock this pipeline configuration as a strict merging pre-requisite for all feature branches into the main integration repository branch.

---

## 10. Contact Information & References

| **Name**           | **Email**                                                                                     |
| ------------------ | --------------------------------------------------------------------------------------------- |
| Vashishtha Prakash | [vashishtha.prakash.snaatak@mygurukulam.co](mailto:vashishtha.prakash.snaatak@mygurukulam.co) |

---

## 11. References

  * [Jenkins Pipeline DSL Syntax Manual](https://jenkins.io)
  * [Pytest Headless Test Execution Framework Docs](https://pytest.org)
  * [Python Virtual Environments Architecture Specifications](https://python.org)
