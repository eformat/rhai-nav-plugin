# rhai-nav-plugin

A minimal OpenShift dynamic console plugin that defines the shared "RHAI" top-level navigation section.

Other RHAI plugins (rhai-workshop-plugin, rhai-code-demo-plugin) reference `"section": "rhai"` in their nav items. This plugin must be deployed first so the section exists.

## Architecture

- Only defines a `console.navigation/section` extension — no pages or exposed modules
- Uses an init container (ose-cli) to auto-enable itself in the console
- Deployed as its own namespace `rhai-nav-plugin` with nginx serving the plugin manifest

## Build & Deploy

```bash
# Build and push image
make podman-push

# Deploy via GitOps
oc apply -k ./gitops

# Or deploy both the nav plugin and another RHAI plugin together
oc apply -k ./gitops && oc apply -k ../rhai-code-demo-plugin/gitops
```

## Project Structure

- `console-extensions.json` - Defines the `console.navigation/section` with id `rhai`
- `gitops/` - Kubernetes manifests (Namespace, ServiceAccount, RBAC, Deployment, Service, ConsolePlugin)
- `Makefile` - Build/push targets using podman
