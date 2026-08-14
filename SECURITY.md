# Security policy

## Reporting a vulnerability

If you believe you have found a security vulnerability in the Steep MCP
server, the manifests in this repository, related Steep infrastructure, or
the Steep product, please report it privately to
[security@steep.app](mailto:security@steep.app).

Please include:

- A description of the issue and its impact
- Steps to reproduce
- Any proof-of-concept or affected versions

Do not file a public GitHub issue for security reports.

## Scope

In scope:

- The Steep MCP server (hosted at the production HTTPS endpoint)
- The OAuth flow used to authorize MCP clients
- Manifests in this repository
- Other Steep services and infrastructure (same mailbox)

## How we handle reports

Steep does not operate a bug bounty program and does not offer compensation
for vulnerability reports.

Reports are reviewed at Steep’s discretion. Continuous automated scanning is
Steep’s primary vulnerability detection path. External reports are considered
when they indicate a serious issue; Steep may not acknowledge or investigate
every submission.

Do not perform penetration testing, vulnerability scanning, load testing, or
other security assessments of Steep’s services without Steep’s prior written
consent. Reporting a finding privately is welcome; unauthorized testing is
not.

Steep will not pursue legal action against reporters who contact us in good
faith via security@steep.app, avoid privacy violations, data destruction, and
service disruption, and do not publicly disclose the issue before Steep has
had a reasonable opportunity to review it.

For Steep’s broader security practices, see
[https://steep.app/security](https://steep.app/security).
