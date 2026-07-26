# Brainstorm: 60 New Workflow Templates for ci-cd-templates

**Context:** `github.com/grave0x/ci-cd-templates` currently has 27 workflows + 2 composite actions. The goal is to reach 87+ items by adding 60 new, useful, production-ready templates.

---

## Step 1: Understand the Opportunity

**Product:** A reusable CI/CD workflow template repository for GitHub Actions.

**Target Segment:** Developers and teams who use GitHub for hosting and want battle-tested, copy-paste-ready CI/CD pipelines without reinventing the wheel every time they start a new project.

**What users want:**
- A workflow for every language/framework they actually use
- More than just CI — deploy, release, automation, compliance
- Templates that work as-is but are easy to customize
- Coverage for infra (Terraform, K8s, Docker) as well as apps
- Automation that saves time (labeling, merging, changelogs)

**Competitive landscape:** GitHub's starter workflows (~50 templates), actflow (community), various scattered Gist collections. Gap: most are shallow (just `npm test && npm build`), none cover the breadth of infrastructure + security + deploy + automation together.

---

## Step 2: Ideate from Three Perspectives

### Product Manager Lens (20 ideas) — Market fit, value creation, competitive advantage

| # | Idea | Why |
|---|------|-----|
| 1 | **Ruby/Rails CI** | Ruby powers millions of sites; Rails alone is ~10% of web. Huge untapped audience. |
| 2 | **PHP/Laravel CI** | Laravel dominates CMS/ecommerce; WordPress alone is 40%+ of the web. |
| 3 | **.NET/C# CI** | Enterprise standard; .NET 8 is cross-platform and growing fast. |
| 4 | **Flutter/Dart CI** | Flutter is the fastest-growing cross-platform mobile framework. |
| 5 | **Swift CI** | iOS/macOS developers are underserved in the Actions template space. |
| 6 | **Ruby on Rails Deploy (Kamal)** | Kamal is the new hotness for Rails deploys — no one has a good template. |
| 7 | **Vercel + Cloudflare Pages Deploy** | Most popular Jamstack hosts; every JS project ships to one of these. |
| 8 | **AWS ECS / EKS Deploy** | "Deploy to ECS" is a daily ask on every team using AWS. |
| 9 | **GitHub Pages Deploy (static sites)** | Free hosting, works with any SSG (Hugo, Jekyll, 11ty, Astro). |
| 10 | **Google Cloud Run Deploy** | Serverless container platform; cheaper than Cloud Run for many workloads. |
| 11 | **Azure Web App Deploy** | Enterprise Azure users need this daily. |
| 12 | **Slack/Teams/Discord Notification** | Every team wants build notifications in their chat tool — yet no standard template. |
| 13 | **New Contributor Welcome** | Open-source projects benefit from greeting first-time contributors. |
| 14 | **PR Size Labeler** | Size-based labels (XS/S/M/L/XL) help reviewers prioritize. |
| 15 | **Auto-Request Reviewers (Blame-Based)** | Automatically request reviewers based on git blame of changed files. |
| 16 | **Weekly Dependency Summary** | A scheduled comment/issue summarizing outdated deps. |
| 17 | **Changelog Enforcer** | Fail PR if no changelog entry is added for user-facing changes. |
| 18 | **Renovate Auto-Merge Config** | Pair with Renovate for zero-touch dep updates (complement to Dependabot). |
| 19 | **GitHub Release Publisher** | Publish release assets (binaries, tarballs) when a tag is pushed. |
| 20 | **Multi-Arch Docker Build** | Build + push for linux/amd64 + linux/arm64 simultaneously. |

---

### Product Designer Lens (20 ideas) — UX, onboarding, engagement

| # | Idea | Why |
|---|------|-----|
| 21 | **Issue templates (bug/feature/config)** | Every repo needs them, nobody wants to write them from scratch. |
| 22 | **PR template with checklist** | Consistent PR descriptions improve review velocity. |
| 23 | **Spellcheck on docs** | Nothing erodes trust like typos in READMEs. |
| 24 | **Markdown link check** | Broken links in docs = bad UX for users. |
| 25 | **Welcome first-time contributor** | A friendly comment on first PR increases retention. |
| 26 | **Stale issue/PR close with warnings** | Reduce noise in issue tracker — already exists, but needs variants. |
| 27 | **PR environment comment** | Post a link to the preview deployment on every PR. |
| 28 | **Auto-assign issue to author** | Let contributors self-assign by mentioning "take" in a comment. |
| 29 | **Lock resolved conversations** | Auto-lock closed issues after 30 days to prevent necroposting. |
| 30 | **Issue label validation** | Require at least one label on every new issue. |
| 31 | **PR size badges in comment** | Visual indicator of PR complexity for reviewers. |
| 32 | **Deploy preview URL in PR** | Auto-comment with preview link for Vercel/Netlify/Cloudflare. |
| 33 | **Conventional issue titles** | Enforce format like `[Bug]:` or `[Feature]:` on new issues. |
| 34 | **Triage new issues** | Auto-label unlabeled issues as `needs-triage`. |
| 35 | **First-good-issue auto-reply** | When someone comments on a `good-first-issue`, auto-respond with guidance. |
| 36 | **PR congratulations on first merge** | Small dopamine hit for new contributors. |
| 37 | **Scheduled issue reminder** | Comment on stale-but-important issues to keep them alive. |
| 38 | **Release notes to Discord** | Cross-post new releases to a Discord channel. |
| 39 | **Codeowners enforcement** | Block merge if required CODEOWNERS haven't approved. |
| 40 | **README badge generator** | Generate dynamic badge URLs for CI status, coverage, etc. |

---

### Software Engineer Lens (20 ideas) — Technical innovation, APIs, platform

| # | Idea | Why |
|---|------|-----|
| 41 | **Elixir CI (mix)** | Elixir/Phoenix is production-grade; credo + dialyzer + exunit are standards. |
| 42 | **Zig CI** | Zig is the hottest new systems language; build + test + fmt pipeline. |
| 43 | **Deno CI** | Deno is growing; `deno lint` + `deno test` + `deno compile`. |
| 44 | **Haskell CI (stack/cabal)** | Academia + fintech rely on Haskell; stack test + hlint. |
| 45 | **Scala CI (sbt)** | Big data/Spark ecosystem runs on Scala; scalafmt + sbt test. |
| 46 | **GraphQL Schema Lint** | Breaking schema changes in CI prevent production incidents. |
| 47 | **OpenAPI/Swagger Lint** | API-first teams need spectral lint + diff checks. |
| 48 | **Buf Proto Lint + Breaking** | gRPC teams: check for breaking proto changes in CI. |
| 49 | **SQLFluff Lint** | Data teams need SQL style enforcement in CI. |
| 50 | **Ansible Lint + Molecule** | Infrastructure-as-code for Ansible users. |
| 51 | **Pulumi CI** | Cross-cloud IaC; `pulumi preview` + `pulumi up`. |
| 52 | **CDK Synth + Diff** | AWS CDK Infrastructure as Code in TypeScript/Python. |
| 53 | **Helm Lint + Template + Test** | Kubernetes package manager validation pipeline. |
| 54 | **Packer Validate + Build** | Build golden AMIs/VM images in CI. |
| 55 | **SBOM Generation** | Supply-chain security: generate CycloneDX/SPDX SBOMs. |
| 56 | **OpenSSF Scorecard** | Automate security posture assessment for each repo. |
| 57 | **CodeQL Analysis** | GitHub-native semantic code analysis. |
| 58 | **TODO-to-Issue** | Scan code for `TODO`/`FIXME`/`HACK` and create tracking issues. |
| 59 | **Semantic Release** | Auto-version + auto-publish based on conventional commits. |
| 60 | **Composite Action: Docker Buildx** | Reusable action for multi-arch Docker build with caching. |

---

## Step 3: Prioritize Top 5

Weighted by: Core value delivery × Speed to validate × Differentiation potential

### #1 🥇 Ruby/Rails CI (`ci-ruby.yml`)
**Why:** Ruby has 5M+ repos on GitHub. Rails is still the default web framework for startups. There are ZERO good, modern Ruby CI templates in the starter workflows (the old ones use `gem install` instead of `bundle`). Massive gap.

**Gates:** `rubocop` → `bundle exec rspec` → `bundle exec rails db:test:prepare` → `bundle exec rails test`

**Assumptions to test:** Rails devs will use a template they can copy in one `curl` command.

### #2 🥈 Semantic Release / Auto-Versioning (`release-semantic.yml`)
**Why:** "How do I automate releases?" is the #1 question after CI is green. Semantic Release paired with conventional commits automates changelogs, version bumps, and npm/cargo/pypi publishing. No template repo covers this well.

**Gates:** Extract version from commit history → update manifest → create tag → publish

**Assumptions to test:** Devs want fully automated releases, not just CI.

### #3 🥉 Deploy Preview Environment (`deploy-preview.yml`)
**Why:** Every team using Vercel/Netlify/Cloudflare wants "preview URL on every PR". The config is fiddly (permissions, secrets, commenting). A single composable template that works across all three providers is a win.

**Gates:** Build → Deploy to preview → Comment URL on PR → Teardown on merge

**Assumptions to test:** Teams will adopt this instead of configuring it per-provider.

### #4 🏅 Docker Multi-Arch Build (`release-docker-multiarch.yml`)
**Why:** Single-arch Docker images are deprecated in practice — everyone needs amd64 + arm64. The setup (QEMU, buildx, manifest) is boilerplate. A template that includes Trivy scan + multi-arch + attestation is differentiated.

**Gates:** Setup QEMU → Setup Buildx → Build multi-arch → Scan → Push manifest

**Assumptions to test:** Projects are willing to add 3 extra minutes to CI for arm64 support.

### #5 🏅 SBOM + Scorecards + CodeQL (`security-compliance.yml`)
**Why:** Supply-chain security is now mandatory (EO 14028, SLSA, SSDF). Most teams don't know where to start. A single "security compliance" workflow that runs SBOM generation + OpenSSF Scorecard + CodeQL in parallel is a turnkey solution.

**Gates:** Parallel: `SBOM (CycloneDX)` + `Scorecard` + `CodeQL Analyze` → Upload all artifacts

**Assumptions to test:** Teams will run compliance workflows that don't block PRs (scheduled).

---

## Step 4: Key Assumptions to Validate

1. **Reach:** Are these languages/use-cases actually represented in the audience? (Check: GitHub language stats for the user's repos.)
2. **Freshness:** The existing GitHub starter workflows are stale (many use `actions/checkout@v2`, `setup-node@v1`). Replacements that use current versions are valuable.
3. **Composability:** A workflow that references `grave0x/ci-cd-templates/.github/workflows/ci-ruby.yml@main` is more useful than a copy-paste — but requires the user to trust an external source. Both approaches should be documented.
4. **Adoption friction:** The #1 barrier is "which template do I pick?" — a `templates/index.json` or a CLI selector would help.

---

## Appendix: Complete 60-Item List by Category

### Language CI (20)
1. Ruby/Rails — rubocop, rspec, brakeman
2. PHP/Laravel — phpcs, phpstan, phpunit
3. Elixir/Phoenix — credo, dialyzer, exunit
4. .NET/C# — dotnet format, test, pack
5. Flutter/Dart — flutter analyze, test, build
6. Swift — swiftlint, swift test
7. Zig — zig fmt, test, build
8. Deno — deno lint, test, compile
9. Haskell — hlint, hpack, stack test
10. Scala — scalafmt, sbt test, coverage
11. Kotlin — detekt, ktlint, gradle test
12. OCaml — ocamlformat, dune runtest
13. Nim — nimble test
14. Crystal — crystal spec, build
15. R — lintr, testthat, R CMD check
16. Lua — luacheck, busted
17. Julia — Pkg.test
18. Fortran — fpm build, test
19. PureScript — purs lint, test
20. Erlang/OTP — rebar3 ct, dialyzer

### Deploy & Publish (10)
21. Vercel — deploy preview + prod
22. Cloudflare Pages — deploy
23. GitHub Pages — build + deploy
24. AWS S3/CloudFront — sync + invalidate
25. Firebase Hosting — deploy
26. Netlify — deploy preview + prod
27. Google Cloud Run — build + deploy
28. AWS ECS — build + push + deploy
29. Azure Web App — deploy
30. Railway/Render — deploy trigger

### Infrastructure as Code (8)
31. Ansible — ansible-lint + molecule test
32. Pulumi — preview + up
33. AWS CDK — synth + diff + deploy
34. Helm — lint + template + test + push
35. Packer — validate + build
36. Kustomize — build + diff
37. Crossplane — validate composition
38. Serverless Framework — lint + deploy

### Automation & Quality (10)
39. Semantic Release — auto-version + publish
40. OpenSSF Scorecard — security posture
41. SBOM Generation — CycloneDX/SPDX
42. CodeQL Analysis — semantic code scan
43. TODO-to-Issue — tracking from code
44. Changelog Enforcer — require entry
45. PR Size Labeler — automated sizing
46. Enforce CODEOWNERS — block without approval
47. Renovate Auto-Merge Config
48. Weekly Dependency Report

### Contributor Experience (7)
49. Welcome First Contributor
50. PR Environment Comment
51. Auto-Assign Issue
52. Lock Resolved Conversations
53. Issue Label Validation
54. Stale Warnings (variant with comment)
55. Congratulations on First Merge

### Lint & Validation (5)
56. GraphQL Schema Lint
57. OpenAPI/Swagger Lint (spectral)
58. Buf Proto Lint + Breaking
59. SQLFluff Lint
60. Spellcheck (codespell)

---

## Implementation Priority Matrix

```
                    High Impact             Medium Impact
Quick to build      Ruby, Semantic Release,  GraphQL lint, Buf, 
(< 30 min)          Deploy Preview, Spellcheck SQL lint, Issue templates

Moderate effort     Docker multi-arch,       Scala, Haskell, OCaml
(30-60 min)         SBOM + Scorecard, Ansible Elixir, Zig

Takes time          Flutter, .NET,           Packer, Crossplane,
(60+ min)           AWS ECS, Google Cloud Run Weekly dep report, CODEOWNERS
```
