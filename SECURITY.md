# Security Policy

## Reporting vulnerabilities

Please do not disclose security issues publicly before maintainers have had time to investigate and fix them.

For now, report suspected vulnerabilities privately to the repository maintainer through GitHub.

## Sensitive data

Never commit:

- `.env` files;
- OAuth access or refresh tokens;
- API keys;
- bot tokens;
- private keys;
- service account JSON files;
- database dumps;
- production logs with customer data.

## Supported security areas

Security reviews are especially welcome for:

- OAuth flows;
- token encryption and storage;
- webhook signature checks;
- tenant isolation;
- synchronization workers;
- report sharing links;
- AI assistant context boundaries.
