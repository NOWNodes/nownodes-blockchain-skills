# Security Playbook

## API Key Storage

- Store `NOWNODES_API_KEY` in local `.env`, CI secret stores, deployment platform secrets, or a secret manager.
- Do not commit real keys.
- Do not include keys in screenshots, logs, issue text, test fixtures, or generated examples.

## Rotation

Rotate keys when:

- A key is pasted into a public channel.
- A key appears in git history.
- A developer leaves the project.
- CI/deployment environments are compromised.
- The application moves between staging and production.

## Leaked Key Response

1. Treat the key as compromised.
2. Revoke or rotate it in the NOWNodes account.
3. Update CI, cloud, local, and secret-manager values.
4. Redeploy affected services.
5. Search logs and repositories for the leaked value if the user asks and permissions allow it.
6. Never repeat the leaked key in the response.

## Log Redaction

Redact `api-key`, authorization headers, query strings that may contain credentials, private keys, mnemonics, and signed payloads.

## Signing Boundary

NOWNodes provides node/API access. Private-key custody and transaction signing should stay in the user's wallet, HSM, backend signer, or secure client code.

For broadcast methods:

- Use `<SIGNED_RAW_TRANSACTION>` placeholders in examples.
- Explain duplicate/nonce risks.
- Ask for explicit confirmation before running any broadcast.
