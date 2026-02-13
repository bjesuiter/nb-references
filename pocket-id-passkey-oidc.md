---
title: "Pocket ID - Passkey OIDC Provider for Self-Hosting"
anchor: "Simple OIDC SSO provider with passkey-only authentication for self-hosted services"
tags: [sso, oidc, passkey, self-hosting, authentication, security]
description: "A simple OpenID Connect provider that uses only passkeys for authentication - no passwords needed"
source_url: "https://pocket-id.org/
---

## Reference

### Summary
Pocket ID is a modern OpenID Connect (OIDC) identity provider focused on passwordless authentication using Passkeys. It's designed as a simpler alternative to complex solutions like Keycloak or ORY Hydra.

### Key Features
- **Passkey-only authentication** - No passwords, uses WebAuthn/FIDO2
- **Simple OIDC provider** - Easy to set up and use
- **Physical security key support** - Works with YubiKey and other hardware tokens
- **Self-hosted** - Complete control over your authentication
- **Works with self-hosted apps** - Compatible with any app supporting OIDC/OAuth2

### Comparison to Alternatives
| Provider | Complexity | Password Support |
|----------|------------|------------------|
| Pocket ID | Low | Passkeys only |
| Keycloak | High | Passwords + Passkeys |
| ORY Hydra | Medium-High | Passwords + Passkeys |

### Why Passkeys Only?
- Eliminates password security vulnerabilities
- Phishing-resistant authentication
- Simple login with physical keys or device passkeys
- The future of authentication

### Use Cases
- Single sign-on for multiple self-hosted services
- Synology DSM authentication
- Secure access to home lab services
- Replace basic auth with modern authentication

### Resources
- **Website**: https://pocket-id.org/
- **GitHub**: https://github.com/pocket-id/pocket-id
- **Reddit Discussion**: https://www.reddit.com/r/selfhosted/comments/1eq9mh2/

### Related
- OAuth2-Proxy for reverse proxy authentication
- Keycloak for more complex identity management
