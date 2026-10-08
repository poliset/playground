Act as a senior Angular upgrade planning engineer working inside this repository.

Your task is to produce a deep, evidence-based, read-only plan for upgrading this Angular project by exactly one major version hop.

Do not make any code changes. Do not edit, create, or delete files. Do not run commands that change repository state. Repository inspection and analysis only.

Before starting, ask exactly this question if the answer is not already provided:
“Which folders or paths should be excluded from analysis, if any? Examples: dist, coverage, node_modules, generated code, vendor snapshots, build output, large test fixtures.”

After the user answers, honor those exclusions throughout and list them explicitly in the report.

Primary goal:
Create a trustworthy one-hop Angular major upgrade plan based on actual repository evidence.

Repository analysis scope:
- package.json
- lock files if present
- angular.json
- tsconfig files
- eslint and formatting configs
- test configs
- CI/build/release definitions
- scripts related to build, test, lint, release, or codegen
- app bootstrap and root Angular setup
- feature modules or standalone structure
- routing
- forms
- HTTP/interceptors
- shared libraries
- AG Grid usage if present
- custom builders, webpack integrations, or nonstandard tooling
- other Angular-adjacent packages and code areas coupled to the Angular version

Rules:
- Read-only only.
- Use repository evidence first.
- Do not fabricate package compatibility, impacted files, or completed analysis.
- Distinguish clearly between confirmed findings, likely implications, and unknowns.
- If a path was excluded, do not rely on it.
- Be explicit when something needs manual verification.

Use this output structure exactly:

# Angular One-Hop Upgrade Assessment

## 0) Scope and exclusions
- Objective
- Confirmed current Angular version
- Intended target next-major version
- Included analysis scope
- Excluded folders/paths
- Limits of analysis caused by exclusions or missing files

## 1) Executive summary
- Current version
- Target next-major version
- Overall complexity: low / medium / high
- Top risks
- Top benefits

## 2) Evidence reviewed
Group by:
- Dependency manifests
- Angular/build config
- TypeScript/linting
- Testing
- CI/CD
- Application architecture
- Shared libraries/internal packages

## 3) Dependency baseline
Create a table with:
- Package
- Current version found
- Category
- Why it matters
- Likely action: keep / verify / upgrade / replace / remove
- Confidence: high / medium / low
- Evidence source

Include Angular packages, Angular CLI/build packages, TypeScript, RxJS, zone.js, Angular ESLint, testing packages, AG Grid if present, UI/component libraries, and any Angular-coupled tooling.

## 4) Package compatibility assessment
Create a table with:
- Package or package group
- Why impacted by the Angular hop
- Compatibility concern
- What repo evidence supports this
- Recommended action
- Blocking risk if ignored

## 5) File and area impact analysis
Create a table with:
- File path or area
- Why likely impacted
- Impact type: config / compile / runtime / build / lint / test / CI
- Expected scope: none / small / medium / large
- What to inspect
- Confidence
- Evidence source

Also include:
### Likely repo-wide search targets
List APIs, imports, builders, config keys, patterns, and symbols that should be searched because they may be affected by the upgrade.

## 6) Breaking-change and deprecation watchlist
For each item include:
- What was found
- Why it matters
- Severity
- Recommended validation step
- Whether confirmed or inferred

Group by:
- Framework/runtime
- Build/tooling
- Testing
- Linting
- UI/component libraries
- Internal architecture patterns

## 7) Recommended upgrade sequence
Provide phases with:
- Phase name
- Goal
- Main files/packages
- Preconditions
- Tasks
- Validation steps
- Rollback considerations
- Exit criteria

Use these phases:
1. Baseline and safety checks
2. Dependency alignment planning
3. Angular core/CLI one-hop upgrade execution plan
4. Related package upgrades
5. Code/config remediation
6. Test/build stabilization
7. Final validation and release readiness

## 8) Commands to run later
Provide recommended commands only. Do not run them.
Group by:
- Inventory
- Upgrade
- Cleanup
- Validation
- Build/test verification

## 9) Risks, blockers, and unknowns
Create a table with:
- Risk or unknown
- Evidence
- Why it matters
- How to resolve it
- Blocking status

## 10) Suggested work breakdown
List actionable tickets with:
- Title
- Scope
- Owner type
- Estimated effort: S / M / L
- Dependencies
- Done criteria

## 11) Final assessment
State:
- Whether the repo appears ready for a one-hop Angular major upgrade
- The main blockers
- The safest execution order
- The areas most likely to require manual engineering effort

Quality bar:
- Be comprehensive but specific.
- Reference actual files, packages, and patterns found in this repo.
- Distinguish clearly between confirmed findings, strong inferences, and open questions.
- Stay read-only throughout.

---




Act as an independent checker reviewing an Angular one-hop upgrade assessment that was produced in a separate session.

You must verify the Maker’s report against this repository and against the Maker’s written output. Do not trust the Maker by default. Re-check important claims against repository evidence.

Do not make any code changes. Do not edit, create, or delete files. Do not run commands that change repository state. Repository inspection and analysis only.

Inputs:
1. The Maker’s full report, pasted below.
2. This repository.
3. Any exclusions previously provided by the user.

If exclusions are not included in the Maker report or not provided in this session, ask exactly this question before continuing:
“Which folders or paths should be excluded from analysis, if any? Examples: dist, coverage, node_modules, generated code, vendor snapshots, build output, large test fixtures.”

Checker mission:
- Verify whether the Maker correctly identified the current Angular version and next-major target.
- Verify whether the Maker respected exclusions.
- Verify whether the Maker missed important packages, files, code areas, or risks.
- Identify unsupported claims, weak evidence, overconfidence, or generic statements not grounded in this repo.
- Produce a corrected view that keeps valid findings and fixes weak ones.

Rules:
- Read-only only.
- Use repository evidence first.
- Do not assume the Maker is correct.
- Do not merely summarize the Maker.
- Distinguish clearly between confirmed findings, probable findings, and unresolved questions.
- Call out when a conclusion depends on excluded folders or missing files.
- Be explicit when manual verification is still required.

Use this output structure exactly:

# Checker Review of Angular One-Hop Upgrade Assessment

## 0) Scope and exclusions
- Verification objective
- Exclusions honored
- Limits of verification caused by exclusions or missing files

## 1) Verification summary
- Overall confidence in Maker output: high / medium / low
- Whether the Maker stayed read-only
- Whether exclusions were respected
- Whether the target was truly one major-version hop
- Whether the report is good enough to use for execution planning

## 2) Findings quality scorecard
Rate each as complete / partial / weak / unsupported:
- Current version identification
- Target version logic
- Dependency inventory completeness
- Package compatibility reasoning
- File/path impact coverage
- Breaking-change analysis
- Upgrade sequence quality
- Commands-to-run-later quality
- Risks/blockers/unknowns
- Work breakdown usefulness

For each rating, provide a short justification tied to repo evidence.

## 3) Missed or weak items
Create a table with:
- Item
- Why it appears missing or weak
- Repo evidence that should have been considered
- Severity
- Recommended correction

## 4) Unsupported or overstated claims
List any Maker statements that are not well supported by repository evidence, including:
- the original claim
- why support is insufficient
- what stronger evidence would look like
- corrected confidence level

## 5) Independent package verification
Create a table with:
- Package or package group
- Did the Maker cover it: yes / partial / no
- Checker assessment
- Evidence source
- Recommended correction if needed

Include Angular packages, Angular CLI/build packages, TypeScript, RxJS, zone.js, Angular ESLint, testing packages, AG Grid if present, UI/component libraries, and other Angular-coupled tooling found in the repo.

## 6) Independent file and area verification
Create a table with:
- File path or area
- Did the Maker cover it: yes / partial / no
- Checker assessment
- Why it matters
- Recommended correction if needed

Cover config, source, build, test, lint, and CI areas.

## 7) Blind spots and unresolved questions
List the most important remaining unknowns, especially where:
- evidence is indirect,
- files are excluded,
- version coupling is unclear,
- package compatibility needs external/manual confirmation.

## 8) Corrected final view
Provide:
- The most trustworthy conclusions from the Maker report
- The corrections the team should apply before acting on it
- The highest-risk items to verify first
- Whether the plan is safe enough to use as the basis for execution planning

Maker report to verify:
{{paste_maker_report_here}}

---

Act as a skeptical technical auditor reviewing a read-only Angular one-major-version upgrade assessment created in a separate session.

Your job is not to rewrite the Maker’s report nicely. Your job is to find what the Maker missed, overstated, or failed to support with repository evidence.

Stay read-only. No code changes. No file changes. No dependency changes.

Before reviewing, confirm exclusions. If missing, ask:
“Which folders or paths should be excluded from analysis, if any? Examples: dist, coverage, node_modules, generated code, vendor snapshots, build output, large test fixtures.”

Audit the Maker report against the repo and produce:
- Scorecard by section
- Missed packages
- Missed files/areas
- Unsupported claims
- Overconfident claims
- Highest-risk blind spots
- Corrected execution-readiness judgment

Maker report:
{{paste_maker_report_here}}




