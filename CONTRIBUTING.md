# Contributing

Sonatelle projects favor careful, maintainable work over broad claims or hurried scope. Keep changes small, honest, and easy to review.

## Development Flow

- Work in a focused branch for each change.
- Keep one branch and one pull request centered on one intent.
- Do not mix unrelated refactors, formatting changes, generated files, or cleanup with behavior changes.
- Read the project `README.md`, `AGENTS.md`, and any project-level `CONTRIBUTING.md` before changing code.
- Prefer the smallest change that solves the problem clearly.
- Update documentation when behavior, supported formats, commands, or limitations change.
- For security-sensitive code, include tests for failure paths and edge cases.

## Branch Names

Use short, lowercase branch names with hyphens:

```text
area/short-description
```

Examples:

```text
brand/add-profile-assets
docs/update-profile-readme
fix/path-validation
chore/refresh-generated-assets
```

## Commits

Use Conventional Commits for commit subjects:

```text
type(scope): concise change
```

Examples:

```text
feat(cli): add config file loading
fix(paths): reject parent-directory traversal
docs(profile): add organization README
test(paths): cover absolute path rejection
chore(brand): add generated mark assets
```

Guidelines:

- Common types include `feat`, `fix`, `docs`, `test`, `refactor`, `chore`, `build`, `ci`, and `perf`.
- Use a short lowercase scope when it clarifies the area changed.
- Use the imperative mood when practical: `add`, `fix`, `document`, `block`.
- Keep the subject specific and factual.
- Use a body when the reason, tradeoff, or risk is not obvious.
- Do not claim support or behavior that is not implemented.
- Do not commit unrelated local changes.
- Agent-assisted work must not create commits until the proposed commit message has been shown to the user and explicitly approved.

## Pull Requests

Pull requests should explain:

- What changed.
- Why it changed.
- How it was verified.
- Any limitations, follow-up work, or compatibility concerns.

Prefer small pull requests. If a change needs broad restructuring, split preparatory cleanup from behavior changes where practical.

## Verification

Run the checks that match the files changed. If a check cannot be run, say why in the pull request.

For Rust projects, the usual baseline is:

```text
cargo fmt --check
cargo clippy --all-targets --all-features -- -D warnings
cargo test --all-features
```

Projects may define stricter or more specific commands. Follow the project-level instructions when they exist.

## Security-Sensitive Work

Path handling, filesystem operations, authentication, password handling, and parser code are high-risk areas.

For these changes:

- Add tests for malformed input and rejected paths.
- Cover absolute paths, parent-directory traversal, and platform-specific path behavior when relevant.
- Keep error mapping explicit.
- Document unsupported behavior and external dependencies honestly.
- Do not weaken safety defaults for convenience.

## Review Expectations

Reviewers should focus on correctness, safety, maintainability, and whether public claims match implemented behavior. Style comments are useful when they improve clarity, but broad rewrites should have a clear reason.
