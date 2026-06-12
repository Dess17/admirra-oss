# Contributing

Thanks for your interest in Admirra OSS.

## Development workflow

1. Fork the repository.
2. Create a feature branch.
3. Keep changes focused and documented.
4. Run backend and frontend checks before opening a pull request.
5. Describe integration/API changes clearly, especially if they affect metrics, attribution, synchronization, or token handling.

## Pull request checklist

- No secrets, tokens, database dumps, or service account files are committed.
- Metrics calculations are covered by tests or a clear manual verification note.
- API changes are reflected in schemas and documentation.
- UI changes are checked on desktop and mobile widths where applicable.
- Background sync changes are safe to retry and do not duplicate data.

## Security-sensitive changes

Please be extra careful with:

- OAuth token storage and refresh;
- webhook verification;
- user credentials;
- advertising account access;
- report links;
- multi-tenant data isolation.

If you find a vulnerability, do not open a public issue with exploit details. See `SECURITY.md`.
