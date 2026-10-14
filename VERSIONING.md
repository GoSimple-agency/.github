# Versioning & deprecation policy

How the Tezga API and its SDKs are versioned, and what we promise before anything changes.
This is the commitment integrators can plan against.

## Semantic versioning

The SDKs follow [Semantic Versioning](https://semver.org): `MAJOR.MINOR.PATCH`.

- **PATCH** — bug fixes, no change to how you call the SDK.
- **MINOR** — new, backward-compatible features.
- **MAJOR** — a breaking change to the SDK surface.

Before `1.0.0` a package is still stabilizing, so a **minor** bump may carry a breaking
change; those are always written up in the package's `CHANGELOG.md`.

## The API contract

The REST API is described by a single OpenAPI contract
([`openapi.json`](https://tezgafiskal.com/api/openapi.json)), currently **1.6.0**. New
fields and new endpoints are added in a backward-compatible way: existing calls keep
working, so adding a field is never a breaking change — your integration should ignore
fields it does not know.

## Deprecation

When something has to be retired:

1. It is marked **deprecated** in the OpenAPI contract and the SDK `CHANGELOG.md`, with the
   replacement named.
2. A notice goes out in [Discussions → Announcements](https://github.com/orgs/GoSimple-agency/discussions).
3. The deprecated behavior keeps working for at least **6 months** after that notice before
   it is removed.

Security fixes are the exception: a change needed to close a vulnerability can ship faster,
and we will say so when it does.

## Supported runtimes

CI tests every release on the runtimes the SDKs declare:

- **JavaScript / TypeScript** — Node.js 22 and newer.
- **PHP** — 8.1 through 8.5.

When a language version reaches end of life, dropping it is treated as a **major** SDK
change and announced the same way as any other deprecation.

## Questions

Ask in [Discussions](https://github.com/orgs/GoSimple-agency/discussions), or email
**info@gosimple.agency**.
