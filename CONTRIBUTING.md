# Contributing to NoMore403

Contributions are welcome. Useful areas include bug fixes, better payloads, new bypass techniques, raw HTTP improvements, frontend fingerprinting, tests, and documentation.

## Responsible Use

NoMore403 is intended for authorized security testing, bug bounty work, penetration testing, security reviews, and regression testing.

Do not include private target data, credentials, tokens, customer data, or non-public vulnerability details in issues, pull requests, commits, tests, fixtures, or screenshots. Redact real hostnames unless they are intentionally public test targets.

If you need to report a vulnerability in NoMore403 itself, follow [SECURITY.md](SECURITY.md).

## Development Setup

Requirements:

- Go 1.24 or later
- `curl` in `PATH` for techniques that exercise curl-based request behavior

Build and test locally:

```bash
go test ./...
go build ./...
```

Before opening a pull request, format Go code:

```bash
gofmt -w .
```

## Project Structure

- `main.go`: CLI entry point
- `cmd/`: command implementation, request logic, bypass techniques, output, and tests
- `payloads/`: payload lists used by techniques
- `README.md`: user-facing usage and behavior documentation

## Reporting Bugs

Please use the bug report template and include:

- NoMore403 version or commit SHA
- operating system and architecture
- Go version, if building from source
- exact command and flags, with sensitive data redacted
- expected behavior
- actual behavior
- minimal reproduction steps
- relevant output, preferably with `-v` if it is safe to share

For target-specific behavior, use a local reproduction or a public test target when possible.

## Proposing Features or Techniques

Before adding a new technique, check that it represents a distinct behavior and is not already covered by existing path, header, method, frontend, or raw HTTP logic.

Good technique proposals usually include:

- the parsing, normalization, or trust-boundary behavior being tested
- why the result differs from existing techniques
- an example request shape
- expected signals in output
- tests that verify the generated request shape, filtering, scoring, or replay behavior

## Payload Changes

Payload list changes should stay focused. Avoid adding very large lists unless there is a clear reason and the runtime impact is acceptable.

When adding payloads, prefer entries that are:

- reproducible
- meaningfully different from existing entries
- useful across common frontend, proxy, CDN, WAF, or application stacks
- documented in the pull request when the behavior is not obvious

## Pull Requests

Pull requests should be scoped and easy to review.

Before submitting:

- run `gofmt -w .`
- run `go test ./...`
- run `go build ./...`
- update documentation if behavior, flags, output, or payload expectations change
- add or update tests for code behavior changes

By contributing, you agree that your contribution will be licensed under the project's MIT License.
