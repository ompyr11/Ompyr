# OMPYR Authentication & Identity System

## 1. Purpose

The OMPYR Authentication & Identity System is the central identity and access foundation of OMPYR.

It securely manages:

- Founder identity
- User accounts
- Agent identities
- Department identities
- Sessions
- Devices
- Authentication
- Authorization
- MFA / 2FA
- Password management
- API authentication
- Service-to-service authentication
- Security events
- Audit logs

Core principle:

> Identity must be verified before access is granted.

Authentication answers:

"Who are you?"

Authorization answers:

"What are you allowed to do?"

Both systems must remain separate.

---

# 2. Identity Architecture

```text
                    OMPYR IDENTITY CORE
                           │
            ┌──────────────┼──────────────┐
            │              │              │
            ▼              ▼              ▼
        Founder          Users          Agents
            │              │              │
            └──────────────┼──────────────┘
                           ▼
                    Authentication
                           │
                    ┌──────┴──────┐
                    ▼             ▼
                  MFA          Session
                    │             │
                    └──────┬──────┘
                           ▼
                    Authorization
                           │
                           ▼
                    Permission Engine
                           │
                           ▼
                     OMPYR Services
