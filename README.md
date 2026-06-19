User Service
=============

CI notes
--------

- The repository's GitHub Actions workflow (`.github/workflows/ci.yml`) runs `mvn verify` on pushes and pull requests to `main`.
- The CI job reads `ANTHROPIC_API_KEY` from repository secrets. If this secret is not set, the workflow will emit a warning; some integration tests that call the Claude/Anthropic API may be skipped or fail.

Setting the secret
------------------

1. Go to your GitHub repository Settings → Secrets → Actions → New repository secret.
2. Add `ANTHROPIC_API_KEY` with your Anthropic API key.

Local test commands
-------------------

Run unit tests and verify locally:

```bash
./mvnw -B test
```

Run full verification (including integration phases):

```bash
./mvnw -B verify
```

Run tests that require the Anthropic secret
-----------------------------------------

If you have `ANTHROPIC_API_KEY` set in your environment and want to run tests that exercise the Claude/Anthropic integration, activate the Maven profile `with-anthropic`:

```bash
./mvnw -Pwith-anthropic -B verify
```
