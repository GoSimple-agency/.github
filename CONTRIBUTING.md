# Contributing

Thanks for helping improve the Tezga SDKs. This applies to every repository in the
GoSimple organization.

## Before you start

- **Questions** go to [Discussions → Q&A](https://github.com/orgs/GoSimple-agency/discussions), not issues.
- **Security problems** go through [SECURITY.md](./SECURITY.md), never a public issue.
- **New features**: open a discussion or an issue first, so we can agree on the approach
  before you write code.

## Ground rules

- **Field names mirror the official contract.** Request and response fields must match
  [the OpenAPI specification](https://tezgafiskal.com/api/openapi.json) exactly. Do not
  rename or translate them; the SDKs stay in step with the API by design.
- **No real data.** Never commit or paste API keys (`tzg_…`), webhook secrets, real PIBs,
  customer names or receipts. Use made-up values in tests and examples.
- **Keep the SDKs thin.** They forward requests and parse responses. Validation and
  business rules belong to the API.

## Pull requests

1. Keep each pull request to one change.
2. Add or update tests for the behaviour you change.
3. Run the suite locally before you push:
   - JavaScript/TypeScript: `npm ci && npm test`
   - PHP: `for t in test/*_test.php; do php -d error_reporting=-1 "$t"; done`
4. Update the README and `CHANGELOG.md` when behaviour changes.

CI runs the same checks on every pull request and must pass before merge.

## License

By contributing, you agree that your contribution is licensed under the license of the
repository you contribute to.
