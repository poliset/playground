Act as two reviewers working sequentially inside this repository:

1. Maker: produce a deep, evidence-based, read-only plan for upgrading this Angular project by exactly one major version hop.
2. Checker: independently review the Maker’s output against repository evidence and identify gaps, weak assumptions, unsupported claims, missed files, missed packages, and overstated confidence.

Do not make any code changes. Do not edit, create, or delete files. Do not run any command that changes repository state. Repository inspection and analysis only.

Before starting, ask exactly this question if the user has not already provided the answer:
“Which folders or paths should be excluded from analysis, if any? Examples: dist, coverage, node_modules, generated code, vendor snapshots, build output, large test fixtures.”

After the user answers, honor those exclusions throughout the analysis and list them in the report.

Primary goal:
Create a trustworthy one-hop Angular major upgrade plan based on actual repository evidence, then verify the quality of that plan with a separate checker pass.

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
- The Checker must critique the Maker, not merely restate it.

Use this output structure exactly:

# Angular One-Hop Upgrade Assessment

## 0) Scope and exclusions
- Objective
- Confirmed current Angular version
- Intended target major version
- Included analysis scope
- Excluded folders/paths
- Limits of analysis caused by exclusions or missing files

## 1) Maker report

### 1.1 Executive summary
- Current version
- Target next-major version
- Overall complexity: low / medium / high
- Top risks
- Top benefits

### 1.2 Evidence reviewed
Group by:
- Dependency manifests
- Angular/build config
- TypeScript/linting
- Testing
- CI/CD
- Application architecture
- Shared libraries/internal packages

### 1.3 Dependency baseline
Create a table with:
- Package
- Current version found
- Category
- Why it matters
- Likely action: keep / verify / upgrade / replace / remove
- Confidence: high / medium / low
- Evidence source

Include Angular packages, Angular CLI/build packages, TypeScript, RxJS, zone.js, Angular ESLint, testing packages, AG Grid if present, UI/component libraries, and any Angular-coupled tooling.

### 1.4 Package compatibility assessment
Create a table with:
- Package or package group
- Why impacted by the Angular hop
- Compatibility concern
- What repo evidence supports this
- Recommended action
- Blocking risk if ignored

### 1.5 File and area impact analysis
Create a table with:
- File path or area
- Why likely impacted
- Impact type: config / compile / runtime / build / lint / test / CI
- Expected scope: none / small / medium / large
- What to inspect
- Confidence
- Evidence source

Also include:
#### Likely repo-wide search targets
List APIs, imports, builders, config keys, patterns, and symbols that should be searched because they may be affected by the upgrade.

### 1.6 Breaking-change and deprecation watchlist
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

### 1.7 Recommended upgrade sequence
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

### 1.8 Commands to run later
Provide recommended commands only. Do not run them.
Group by:
- Inventory
- Upgrade
- Cleanup
- Validation
- Build/test verification

### 1.9 Risks, blockers, and unknowns
Create a table with:
- Risk or unknown
- Evidence
- Why it matters
- How to resolve it
- Blocking status

### 1.10 Suggested work breakdown
List actionable tickets with:
- Title
- Scope
- Owner type
- Estimated effort: S / M / L
- Dependencies
- Done criteria

## 2) Checker report

The Checker must independently assess the Maker output using repo evidence and produce the following:

### 2.1 Verification summary
- Overall confidence in Maker output: high / medium / low
- Whether the Maker stayed within read-only scope
- Whether exclusions were respected
- Whether the target was truly one major-version hop

### 2.2 Findings quality check
For each category below, rate: complete / partial / weak / unsupported
- Current version identification
- Target version logic
- Package inventory completeness
- Package compatibility reasoning
- File impact coverage
- Breaking-change analysis
- Upgrade sequencing
- Commands recommended
- Risks and unknowns
- Ticket/work breakdown

### 2.3 Missed or weak items
Create a table with:
- Item
- Why it appears missing or weak
- What evidence should have been used
- Severity
- Recommended correction

### 2.4 Unsupported claims
List any statements from the Maker that are not supported by clear repo evidence.

### 2.5 Overconfidence check
List places where confidence should be lowered because the evidence is indirect, incomplete, excluded, or ambiguous.

### 2.6 Final corrected view
- Most trustworthy conclusions
- Most important unresolved questions
- Highest-risk blind spots
- Whether the plan is good enough to use for execution planning

## 3) Final consolidated assessment
Provide a short consolidated view that:
- keeps the Maker’s useful findings,
- applies the Checker’s corrections,
- highlights any remaining manual verification needed before humans act on the plan.

Quality bar:
- The Checker must meaningfully challenge the Maker.
- Do not simply repeat the same points twice.
- Prefer evidence over confidence.
- Be specific about files, packages, folders, and repo patterns.
