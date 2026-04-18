<div align="center">

# <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/grapitydev/grapity.dev/main/assets/favicon.svg"><img alt="Grapity" width="40" src="https://raw.githubusercontent.com/grapitydev/grapity.dev/main/assets/favicon.svg"></picture> Grapity

### **Gravity for APIs.**

Where every API contract is validated, versioned, and ready to ship — across specs, gateways, and teams.

</div>

---

A spec that breaks backward compatibility doesn't enter the registry. A spec without proper versioning doesn't enter the registry. Everything downstream — gateway config, generated clients, AI context, audit trails — is derived from contracts you can trust.

**Pre-launch. Building in public.** All packages are Apache 2.0.

```bash
grapity registry push ./openapi.yaml --name payments-api
grapity gateway provision --spec payments-api@1.0.0 --env staging --profile public-api
grapity gateway diff --spec payments-api --env staging --env prod
```

**Website:** [grapity.dev](https://grapity.dev)