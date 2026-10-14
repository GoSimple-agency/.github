# Security policy

Tezga issues legally binding fiscal receipts, so we treat security reports as a priority.

## Reporting a vulnerability

**Do not open a public issue or discussion.** Report privately, either:

- through **Report a vulnerability** on the affected repository's *Security* tab, or
- by email to **info@gosimple.agency** with `SECURITY` in the subject.

Please include the affected component (an SDK, the REST API, webhooks or the MCP
connector), the steps to reproduce, and the impact you observed. Use test data only: never
send real API keys, buyer data or receipts.

We will confirm we received your report, keep you updated while we work on it, and credit
you once it is fixed if you want us to.

## Scope

- [tezga-sdk-js](https://github.com/GoSimple-agency/tezga-sdk-js) and
  [tezga-sdk-php](https://github.com/GoSimple-agency/tezga-sdk-php)
- The Tezga REST API and webhook delivery
- The Tezga MCP connector

Testing against accounts or data that are not yours is out of scope. Do not run load or
denial-of-service tests against production.
