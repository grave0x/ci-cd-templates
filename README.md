# CI/CD Templates

Reusable, production-ready GitHub Actions workflow templates for Rust, Python, Node.js, Go, C, and more. Each template is a complete quality-gate CI pipeline you can copy into your repo and run immediately.

## Quickstart

```bash
# Pick your language and copy the template
cp .github/workflows/ci-rust.yml /your-repo/.github/workflows/ci.yml

# Add Dependabot for automated dependency updates
cp .github/dependabot.yml /your-repo/.github/dependabot.yml
# (edit to uncomment the ecosystems you use)

# Commit and push
git add .github/ && git commit -m "ci: add quality-gate pipeline" && git push
```

That's it. The pipeline runs automatically on every push and pull request.

---

## Templates

### CI Pipelines

| Language | File | Quality Gates |
|----------|------|---------------|
| Rust | [`ci-rust.yml`](.github/workflows/ci-rust.yml) | `cargo fmt --check` → `cargo clippy` → `cargo test` → `cargo build --release` |
| Python (pip) | [`ci-python.yml`](.github/workflows/ci-python.yml) | `ruff check` → `ruff format` → `mypy` → `pytest` → `python -m build` |
| Python (uv) | [`ci-python-uv.yml`](.github/workflows/ci-python-uv.yml) | Same gates, uv-based with lockfile |
| Node.js / TS | [`ci-node.yml`](.github/workflows/ci-node.yml) | `npm ci` → `lint` → `typecheck` → `test` → `build` |
| Bun | [`ci-bun.yml`](.github/workflows/ci-bun.yml) | `bun install` → `lint` → `test` → `build` |
| Go | [`ci-go.yml`](.github/workflows/ci-go.yml) | `go vet` → `gofmt` → `go test -race` → `go build` |
| Java / Kotlin (Maven) | [`ci-java-maven.yml`](.github/workflows/ci-java-maven.yml) | `mvn compile` → `test` → `package` |
| Java / Kotlin (Gradle) | [`ci-java-gradle.yml`](.github/workflows/ci-java-gradle.yml) | `gradle compileJava` → `test` → `jar` |
| C | [`ci-c.yml`](.github/workflows/ci-c.yml) | `cmake` → `make` → `ctest` |
| Shell | [`ci-shell.yml`](.github/workflows/ci-shell.yml) | `shellcheck` → `shfmt` |
| PowerShell | [`ci-powershell.yml`](.github/workflows/ci-powershell.yml) | `PSScriptAnalyzer` → `Pester test` |
| Docker | [`ci-docker.yml`](.github/workflows/ci-docker.yml) | Build → `Trivy scan` (fail on CRITICAL/HIGH) → Push |
| Terraform / OpenTofu | [`ci-terraform.yml`](.github/workflows/ci-terraform.yml) | `fmt -check` → `validate` → `Checkov scan` → `plan` |
| Kubernetes | [`ci-kubernetes.yml`](.github/workflows/ci-kubernetes.yml) | `kubeconform` schema validation → `kubesec` scan → `pluto` deprecation check |
| Ruby / Rails | [`ci-ruby.yml`](.github/workflows/ci-ruby.yml) | `rubocop` → `brakeman` → `rspec` → DB migration → assets precompile |
| Elixir / Phoenix | [`ci-elixir.yml`](.github/workflows/ci-elixir.yml) | `mix format` → `credo` → `dialyzer` → `mix test` → compile |
| Deno | [`ci-deno.yml`](.github/workflows/ci-deno.yml) | `deno fmt --check` → `deno lint` → `deno check` → `deno test` |
| Zig | [`ci-zig.yml`](.github/workflows/ci-zig.yml) | `zig fmt --check` → `zig build test` → `zig build` |
| Flutter / Dart | [`ci-flutter.yml`](.github/workflows/ci-flutter.yml) | `dart format` → `flutter analyze` → `flutter test` → `flutter build web` |
| .NET / C# | [`ci-dotnet.yml`](.github/workflows/ci-dotnet.yml) | `dotnet format` → `dotnet build` → `dotnet test` → `dotnet pack` |
| Haskell (Stack) | [`ci-haskell.yml`](.github/workflows/ci-haskell.yml) | `hlint` → `stack test` → `stack build` |
| Scala (sbt) | [`ci-scala.yml`](.github/workflows/ci-scala.yml) | `scalafmt` → `sbt test` → `sbt package` |
| OCaml (dune) | [`ci-ocaml.yml`](.github/workflows/ci-ocaml.yml) | `ocamlformat` → `dune build` → `dune runtest` |
| Kotlin | [`ci-kotlin.yml`](.github/workflows/ci-kotlin.yml) | `ktlint` → `detekt` → `gradle test` → `gradle jar` |
| Crystal | [`ci-crystal.yml`](.github/workflows/ci-crystal.yml) | `crystal tool format` → `crystal spec` → `crystal build --release` |

### Infrastructure CI

| Platform | File | Quality Gates |
|----------|------|---------------|
| Ansible | [`ci-ansible.yml`](.github/workflows/ci-ansible.yml) | `yamllint` → `ansible-lint` → `molecule test` |
| Pulumi | [`ci-pulumi.yml`](.github/workflows/ci-pulumi.yml) | `pulumi preview` (PR) → `pulumi up` (push) |
| AWS CDK | [`ci-cdk.yml`](.github/workflows/ci-cdk.yml) | `cdk synth` → `cdk diff` → `cdk deploy` |
| Helm | [`ci-helm.yml`](.github/workflows/ci-helm.yml) | `helm lint` → `helm template` → `helm push` (tag) |
| Packer | [`ci-packer.yml`](.github/workflows/ci-packer.yml) | `packer fmt --check` → `packer validate` → `packer build` |

### Release Pipelines

| Language | File | Publishes To |
|----------|------|-------------|
| Rust | [`release-rust.yml`](.github/workflows/release-rust.yml) | crates.io + GitHub Release (binary) |
| Python | [`release-python.yml`](.github/workflows/release-python.yml) | PyPI via trusted publishing |
| Node.js | [`release-node.yml`](.github/workflows/release-node.yml) | npm with provenance |
| Go | [`release-go.yml`](.github/workflows/release-go.yml) | Go module (tag) + GoReleaser binaries |
| Semantic Version | [`release-semantic.yml`](.github/workflows/release-semantic.yml) | Auto-version + changelog from Conventional Commits; publishes to npm/PyPI/crates.io |
| Docker Multi-Arch | [`release-docker-multiarch.yml`](.github/workflows/release-docker-multiarch.yml) | Multi-arch build (amd64 + arm64) → Trivy scan → Cosign sign → GHCR push |

### Deploy Pipelines

| Platform | File | Description |
|----------|------|-------------|
| GitHub Pages | [`deploy-github-pages.yml`](.github/workflows/deploy-github-pages.yml) | Build + deploy static sites (Hugo, Jekyll, Astro, 11ty) to Pages |
| AWS ECS / Fargate | [`deploy-aws-ecs.yml`](.github/workflows/deploy-aws-ecs.yml) | Build Docker → push to ECR → deploy to ECS with zero downtime |
| Cloudflare Pages | [`deploy-cloudflare-pages.yml`](.github/workflows/deploy-cloudflare-pages.yml) | Build + deploy static sites to Cloudflare Pages |
| Firebase Hosting | [`deploy-firebase.yml`](.github/workflows/deploy-firebase.yml) | Build + deploy web apps with PR preview channels |
| Google Cloud Run | [`deploy-google-cloud-run.yml`](.github/workflows/deploy-google-cloud-run.yml) | Build container → push to GCR → deploy to Cloud Run |

### Automation

| File | Purpose |
|------|---------|
| [`dependabot-auto-merge.yml`](.github/workflows/dependabot-auto-merge.yml) | Auto-approve + auto-merge Dependabot minor/patch PRs that pass CI |
| [`stale.yml`](.github/workflows/stale.yml) | Close stale issues (60d) and PRs (30d) automatically |
| [`pr-labeler.yml`](.github/workflows/pr-labeler.yml) | Auto-label PRs by changed file paths (config in [`labeler.yml`](.github/labeler.yml)) |
| [`release-drafter.yml`](.github/workflows/release-drafter.yml) | Auto-draft release notes as PRs merge (config in [`release-drafter.yml`](.github/release-drafter.yml)) |
| [`conventional-commit.yml`](.github/workflows/conventional-commit.yml) | Enforce Conventional Commits format on PR titles |
| [`code-coverage.yml`](.github/workflows/code-coverage.yml) | Generate + upload coverage reports to Codecov |
| [`security-audit.yml`](.github/workflows/security-audit.yml) | Weekly scheduled vulnerability scanning (cargo-audit, npm audit, pip-audit, govulncheck) |
| [`markdown-lint.yml`](.github/workflows/markdown-lint.yml) | Lint Markdown documentation files |
| [`link-checker.yml`](.github/workflows/link-checker.yml) | Check for broken URLs in docs, runs weekly + on push |
| [`deploy-preview.yml`](.github/workflows/deploy-preview.yml) | Per-PR preview deployments on Vercel/Netlify/Cloudflare with auto-cleanup |
| [`security-compliance.yml`](.github/workflows/security-compliance.yml) | Weekly SBOM generation + OpenSSF Scorecard + CodeQL analysis |
| [`welcome-contributor.yml`](.github/workflows/welcome-contributor.yml) | Welcome first-time contributors with automated greeting |
| [`todo-to-issue.yml`](.github/workflows/todo-to-issue.yml) | Scan code for TODO/FIXME and create tracking issues |
| [`lock-closed-issues.yml`](.github/workflows/lock-closed-issues.yml) | Auto-lock closed issues/PRs after 30 days to prevent necroposting |
| [`pr-size-label.yml`](.github/workflows/pr-size-label.yml) | Auto-label PRs as XS/S/M/L/XL by lines changed |
| [`changelog-enforcer.yml`](.github/workflows/changelog-enforcer.yml) | Require changelog entry for user-facing changes (supports `skip-changelog` label) |

### Configuration Templates

| File | Purpose |
|------|---------|
| [`.github/dependabot.yml`](.github/dependabot.yml) | Dependabot config — all ecosystems, commented, ready to uncomment |
| [`.github/labeler.yml`](.github/labeler.yml) | PR label rules (used by `pr-labeler.yml`) |
| [`.github/release-drafter.yml`](.github/release-drafter.yml) | Release notes categorization (used by `release-drafter.yml`) |
| [`templates/renovate/default.json`](templates/renovate/default.json) | Renovate config with auto-merge for minor/patch |

### Composite Actions

Reusable actions you can call from any workflow in the same repo (or fork):

| Action | Purpose |
|--------|---------|
| [`.github/actions/setup-rust`](.github/actions/setup-rust/action.yml) | Install Rust toolchain with clippy + rustfmt + cache |
| [`.github/actions/setup-python-uv`](.github/actions/setup-python-uv/action.yml) | Install Python + uv + restore deps from lockfile |

---

## Design Principles

**Quality gates that cannot be skipped.** Every pipeline checks formatting, lints, tests, and build — if any step fails, the PR blocks. No silent skips, no `--allow-failure` on critical checks.

**Faster is safer.** Small, frequent changes are easier to debug than large batch deploys. CI should finish in under 10 minutes; parallel jobs and caching keep it fast.

**Shift left.** Catch formatting issues at `cargo fmt --check`, not in code review. Catch type errors at `tsc --noEmit`, not in prod.

**Dependabot is free security.** Automated dependency updates catch vulnerable transitive deps before they become incidents. Pair it with auto-merge for zero-touch maintenance of patch releases.

---

## Notes

- All CI templates use `push` and `pull_request` triggers on both `main` and `master`.
- Python templates gracefully handle missing test/lint scripts — they skip steps that aren't configured.
- Release templates verify the tag matches the manifest version before publishing.
- See the per-language docs in `docs/` for more detail on each template.

## License

CC0 1.0 Universal — do whatever you want with these templates.
