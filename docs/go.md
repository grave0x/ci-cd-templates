# Go CI Template

File: [`.github/workflows/ci-go.yml`](../.github/workflows/ci-go.yml)

## What it checks

| Step | Command | Fails on |
|------|---------|----------|
| Vet | `go vet ./...` | Suspicious constructs |
| Format | `gofmt -l` (non-empty = fail) | Unformatted code |
| Test | `go test -race -count=1 -v ./...` | Test failures |
| Build | `go build ./...` | Compilation errors |

## Customization

- **Go versions**: Edit `go-version` in the matrix strategy.
- **Race detection**: Remove `-race` if you need faster test runs in CI.
- **Build output**: Add `-o <name>` to produce a specific binary.

## Prerequisites

- A `go.mod` at the repo root
- For releases: GoReleaser config (`.goreleaser.yaml`) or just push a tag (Go modules auto-publish on tag)
