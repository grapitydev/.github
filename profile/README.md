<div align="center">

# <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/grapitydev/grapity.dev/main/assets/favicon.svg"><img alt="Grapity" width="40" src="https://raw.githubusercontent.com/grapitydev/grapity.dev/main/assets/favicon.svg"></picture> Grapity

### **Gravity for APIs.**

Where every API contract is validated, versioned, and ready to ship — across specs, gateways, and teams.

</div>

---

Grapity is the missing enforcement layer between *"we have API specs"* and *"those specs reliably drive everything else."*

A spec that breaks backward compatibility doesn't enter the registry. A spec without proper versioning doesn't enter the registry. Everything downstream — gateway config, generated clients, AI context, audit trails — is derived from contracts you can trust.

## Platform Layers

| Layer | Product | Purpose |
|-------|---------|---------|
| L1 | **Grapity Registry** | Contract guardian. Validates compat, enforces semver, manages deprecation. |
| L2 | **Grapity Gateway** | From spec to production. Generates Kong/APISIX config, policy profiles, drift detection. |
| L3 | **Grapity Forge** | Typed clients and consumers, forged from specs. |
| L4 | **Grapity Schema** | AsyncAPI specs and schema registries, kept in sync. |
| L5 | **Grapity Hub** | Every API in one place. Browse, explore, diff. |
| L6 | **Grapity Mind** | Specs compressed for AI. LLM-optimised representations. |

## Status

**Pre-launch. Building in public.**

Phase 1 delivers Grapity Registry and Grapity Gateway. Follow along.

## Quick Look

```bash
# Validate and register your spec
grapity registry push ./openapi.yaml --name payments-api

# Provision to Kong, no ticket needed
grapity gateway provision --spec payments-api@1.0.0 --env staging --profile public-api

# Diff environments, catch drift
grapity gateway diff --spec payments-api --env staging --env prod
```

## Links

- **Website:** [grapity.dev](https://grapity.dev)
- **Vision document:** [grapity-foundational-doc.md](https://github.com/grapitydev/grapity.dev/blob/main/grapity-foundational-doc.md)

---

<div align="center">

*The API is what Grapity revolves around.*

</div>