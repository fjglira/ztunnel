# Submit PR — ztunnel midstream

Before opening or updating a pull request in this repository, verify:

## 1. Upstream-first check

- If the change is a bug fix or feature applicable to upstream ztunnel, open an upstream PR **first**.
- Reference the upstream PR in your OSSM PR description.

## 2. OSSM-only comment convention

All code that is OSSM-specific and not expected to exist upstream must be annotated:

```rust
// OSSM-only: <JIRA-KEY> <one-line reason>
```

OpenSSL/FIPS-specific code must also be gated with `#[cfg(feature = "openssl-tls")]`.

## 3. Checklist

- [ ] OSSM-only comments present on all OSSM-specific hunks
- [ ] Upstream PR opened (if applicable) and linked
- [ ] `cargo build && cargo test && cargo clippy -- -D warnings` passing
- [ ] TLS changes tested with both rustls and `--features openssl-tls`
- [ ] CI passing (`prow.ci.openshift.org`)
